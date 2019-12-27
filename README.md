Welcome to the AWS CodeStar sample web application
==================================================

This sample code helps get you started with a simple Django web application
deployed by AWS CodeDeploy and AWS CloudFormation to an Amazon EC2 server.

What's Here
-----------

This sample includes:

* README.md - this file
* appspec.yml - this file is used by AWS CodeDeploy when deploying the web
  application to EC2
* buildspec.yml - this file is used by AWS CodeBuild to build and test
  your application
* requirements/ - this directory contains requirements files that describe
  the Python dependencies required for your Django application in different
  environments
* requirements.txt - this file is used to install production Python dependencies
* ec2django/ - this directory contains your Django project files. Note that this
  directory contains a Django config file (settings.py) that includes a pre-defined
  SECRET_KEY. Before running in a production environment, you should replace this
  application key with one you generate
  (see https://docs.djangoproject.com/en/1.11/howto/deployment/checklist/#secret-key for details)
* helloworld/ - this directory contains your Django application files
* manage.py - this Python script is used to start your Django web application
* scripts/ - this directory contains scripts used by AWS CodeDeploy when
  installing and deploying your application on the Amazon EC2 instance
* supervisord.conf - this configuration file is used by Supervisor to control
  your web application on the Amazon EC2 instance
* template.yml - this file contains the description of AWS resources used by AWS
  CloudFormation to deploy your infrastructure
* template-configuration.json - this file contains the project ARN with placeholders used for tagging resources with the project ID

Getting Started
---------------

These directions assume you want to develop on your local computer, and not
from the Amazon EC2 instance itself. If you're on the Amazon EC2 instance, the
virtual environment is already set up for you, and you can start working on the
code.

To work on the sample code, you'll need to clone your project's repository to your
local computer. If you haven't, do that first. You can find instructions in the
AWS CodeStar user guide.

1. Create a Python virtual environment for your Django project. This virtual
   environment allows you to isolate this project and install any packages you
   need without affecting the system Python installation. At the terminal, type
   the following command:

        $ virtualenv .venv

2. Activate the virtual environment:

        $ activate ./venv/bin/activate

3. Install development Python dependencies for this project:

        $ pip install -r requirements/dev.txt

4. (Optional) Enable Django's debug mode for development:

        $ export DJANGO_DEBUG=True

5. Start the Django development server:

        $ python manage.py runserver

6. Open http://127.0.0.1:8000/ in a web browser to view your application.

What Do I Do Next?
------------------

Once you have a virtual environment running, you can start making changes to
the sample Django web application. We suggest making a small change to
/helloworld/templates/index.html first, so you can see how changes pushed to
your project's repository are automatically picked up by your project pipeline
and deployed to the Amazon EC2 instance. (You can watch the pipeline progress on
your project dashboard.) Once you've seen how that works, start developing your
own code, and have fun!

To run your tests locally, go to the root directory of the sample code and run
the `python manage.py test` command, which AWS CodeBuild also runs through
your `buildspec.yml` file.

To test your new code during the release process, modify the existing tests or
add tests to the tests directory. AWS CodeBuild will run the tests during the
build stage of your project pipeline. You can find the test results
in the AWS CodeBuild console.

Learn more about AWS CodeBuild and how it builds and tests your application here:
https://docs.aws.amazon.com/codebuild/latest/userguide/concepts.html

Learn more about AWS CodeStar by reading the user guide. Ask questions or make
suggestions on our forum.

User Guide: http://docs.aws.amazon.com/codestar/latest/userguide/welcome.html
Forum: https://forums.aws.amazon.com/forum.jspa?forumID=248

How Do I Add Template Resources to My Project?
------------------

To add AWS resources to your project, you'll need to edit the `template.yml`
file in your project's repository. You may also need to modify permissions for
your project's worker roles. After you push the template change, AWS CodeStar
and AWS CloudFormation provision the resources for you.

See the AWS CodeStar user guide for instructions to modify your template:
https://docs.aws.amazon.com/codestar/latest/userguide/how-to-change-project.html#customize-project-template

What Should I Do Before Running My Project in Production?
------------------

AWS recommends you review the security best practices recommended by the framework
author of your selected sample application before running it in production. You
should also regularly review and apply any available patches or associated security
advisories for dependencies used within your application.

Best Practices: https://docs.aws.amazon.com/codestar/latest/userguide/best-practices.html?icmpid=docs_acs_rm_sec
