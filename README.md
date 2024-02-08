<!DOCTYPE html>
<html>
<head>
	<title>Symfony</title>
</head>
<body>
<h1>Symfony useful Commands</h1>
<h4>Symfony workflow steps</h4>
<pre>
	Step 1 − The user sends a request to the application through the browser, say http://www.symfonyexample.com/index.

	Step 2 − The browser will send a request to the web server, say Apache web server.

	Step 3 − The web server will forward the request to the underlying PHP, which in turn sends it to Symfony web framework.

	Step 4 − HttpKernel is the core component of the Symfony web framework. HttpKernel resolves the controller of the given request using Routing component and forward the request to the target controller.

	Step 5 − All the business logic takes place in the target controller.

	Step 6 − The controller will interact with Model, which in turn interacts with Datasource through Doctrine ORM.

	Step 7 − Once the controller completes the process, it either generates the response itself or through View Engine, and sends it back to the web server.

	Step 8 − Finally, the response will be sent to the requested browser by the web server.
</pre>
<h4>Symfony Install</h4>
<pre>
	symfony older version
		composer create-project symfony/skeleton symfony_app ^4.4.0
		composer create-project symfony/website-skeleton:"5.3.x@dev" symfony_app

	symfony latest version
		composer create-project symfony/website-skeleton symfony_app

	Other packages	
	composer create-project symfony/skeleton project_1
	composer require symfony/maker-bundle --dev
	composer require doctrine/annotations  
	composer require symfony/debug-bundle --dev
	composer require symfony/twig-bundle
	composer require symfony/orm-pack
	composer require security
	composer require migrations
	composer require orm-fixtures --dev
	composer require symfony/form
	composer require symfony/validator
	composer require twig/markdown-extra
	composer require twig/inky-extra
	composer require twig/cssinliner-extra
	composer require knplabs/knp-paginator-bundle
	composer require symfonycasts/verify-email-bundle
	composer require symfony/rate-limiter
	composer require symfonycasts/reset-password-bundle
	MESSENGER_TRANSPORT_DSN=doctrine://default?auto_setup=false
	composer require security annotations doctrine
	composer require --dev web-profiler

</pre>	
<h4>Symfony cli</h4>
<pre>
	curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | sudo -E bash
	sudo apt install symfony-cli
	symfony check:requirements
	symfony server:start
</pre>
<h4>Database setup</h4>
<pre>
	.env file
	DATABASE_URL="mysql://root:Admin%40%23438@127.0.0.1:3306/symfony?serverVersion=8&charset=utf8mb4"
	urlencode password

	file /config/packages/doctrine.yaml
	url: '%env(DATABASE_URL)%'
</pre>
<h4>Create database</h4>
<pre>
	php bin/console doctrine:database:create
</pre>
<h4>Drop database</h4>
<pre>
	php bin/console doctrine:database:drop --force
</pre>
<h4>About Project</h4>
<pre>
	php bin/console about
</pre>
<h4>Start project</h4>
<pre>
	symfony serve
	symfony server:start
	php -S localhost:3000 -t public
</pre>	
<h4>Symfony version</h4>
<pre> 	
	php bin/console --version
</pre> 
<h4>Symfony route</h4>
<pre>
	file : config/routes.yaml

	user_login: (route name)
    	path: /login/showloginform (route url)
    	controller: App\Controller\LoginController::showloginform (controller and function name)
    	methods:    GET|HEAD  (Methods)
</pre>
<h4>Route list </h4>
<pre> 
	php bin/console debug:router
</pre> 
<h4>Route name</h4>
<pre>
	php bin/console debug:router app_user
</pre>

<h4>Annotations</h4>
<pre>
	composer require annotations
</pre>

<h4>Annotations route in controller</h4>
<pre>

	1 : #[Route("/about", name:"about")]


	2 : /**
	     * @Route("/about", name="about")
	    */

</pre>

<h4>Symfony view files</h4>
<pre>
	composer require twig
	your-project/templates/
	example : index.html.twig
</pre>	

<h4>Twig syntax</h4>
<pre>
	{{ ... }}, used to display the content of a variable or the result of evaluating an expression;
	{% ... %}, used to run some logic, such as a conditional or a loop;
	{# ... #}, used to add comments to the template (unlike HTML comments, these comments are not included in the rendered page).
</pre>

<h4>Debugging Templates</h4>
<pre>
	check all the application templates
	php bin/console lint:twig

	You can also check directories and individual templates
	php bin/console lint:twig templates/email/
	php bin/console lint:twig templates/users/list.html.twig
</pre>

<h4>Linking to CSS, JavaScript and Image Assets</h4>
<pre>
	composer require symfony/asset
	example : {{ asset('images/logo.png') }}
</pre>

<h4>Cache clear</h4>
<pre>
	php bin/console cache:clear
	php bin/console cache:warmup
</pre>	

<h4>Controller</h4>
<pre> 
	php bin/console make:controller UserController

	symfony console make:controller UserController
</pre> 
<h4>Create a migration</h4>
<pre> 	
	php bin/console make:migration
</pre>
<h4>Run a migration</h4>
<pre>
	php bin/console doctrine:migrations:migrate
	php bin/console doctrine:migrations:migrate 'DoctrineMigrations\Version20230411113326'
</pre>	
<h4>Revert migration</h4>
<pre>
	php bin/console doctrine:migrations:execute --down (version)
</pre>
<h4>Migration status</h4>
<pre>
	php bin/console doctrine:migrations:status
</pre>
<h4>Etity</h4>
<pre>
	php bin/console make:entity
</pre>
<h4>Fixtures</h4>
<pre>
	php bin/console make:fixtures
</pre>
<h4>Redirecting</h4>
<pre>
	return $this->redirect('http://symfony.com/doc');
	return $this->redirectToRoute('homepage');	
</pre>

<h4>The Request and Response Object</h4>

<pre>
	1)  $request->isXmlHttpRequest();
	2)  $request->query->get('page');
    	3)  $request->request->get('page');
    	4)  $request->server->get('HTTP_HOST');
    	5)  $request->cookies->get('PHPSESSID');
    	6)  $request->headers->get('host');
    	7)  $request->headers->get('content-type');
</pre>

<h4>Mail sending with queue</h4>
<pre>
	php bin/console messenger:consume async

	php bin/console messenger:consume async -vv
</pre>	

<h4>Session</h4>
<pre>
	$session->set('my_session', 'test data');

	$session->get('my_session');
</pre>

<h4>Fixtures</h4>
<pre>
	php bin/console mak:fixture

	php bin/console doctrine:fixtures:load
	php bin/console doctrine:fixtures:load --append
	php bin/console doctrine:fixtures:load --purge-with-truncate
</pre>

<h4>Get all form data </h4>
<pre>
	$form = $this->createForm(MyFormType::class);

    	$form->handleRequest($request);

    	if ($form->isSubmitted() && $form->isValid()) {
        	$formData = $form->getData();
        	//Do something with the form data
    	}
</pre>    

<h4>Generate hash password</h4>
<pre>
	symfony console seurity:encode-password
</pre>

<h4>Useful Websites</h4>
<pre>
https://auth0.com/blog/creating-your-first-symfony-app-and-adding-authentication/
https://inchoo.net/dev-talk/symfony/symfony-templating-with-twig/
https://inchoo.net/?s=symfony
https://www.youtube.com/watch?v=3K9YCIC3-iw
https://www.youtube.com/watch?v=XjbIDOIoXTo
https://www.youtube.com/watch?v=5a59HiOeRT4
https://www.youtube.com/watch?v=Yn6OdpRGGqk&list=PLxAEnUvHtm9PXWcooL47xGHCKmYS1nq75
https://zetcode.com/all/#symfony
https://lindevs.com/methods-to-display-flash-messages-in-symfony
https://www.youtube.com/@codewithdary/playlists
https://www.youtube.com/watch?v=QPky3r2prEI
https://www.youtube.com/watch?v=1HiCARUu-Mg&list=PLRkB3CK04Mo8vbftRqjuiwxIkVUtxjeOj&index=5
https://www.youtube.com/watch?v=bvhHsutKZek
https://wouterj.nl/assets/uploads/sfwinterworld21-talk.pdf
</pre>
</body>
</html>
