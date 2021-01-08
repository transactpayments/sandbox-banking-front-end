Welcome to the AWS CodeStar sample web application
==================================================

This sample code helps get you started with a simple Ruby on Rails web application
deployed by AWS Elastic Beanstalk and AWS CloudFormation.

What's Here
-----------

This sample includes:

* README.md - this file
* .ebextensions/ - this directory contains the configuration files that allows
  AWS Elastic Beanstalk to deploy your application
* Gemfile - Gem requirements for the sample application
* Gemfile.lock - this file contains the specific versions of your application
  dependencies
* Rakefile - this file contains scripts available using the `rake` command
* app/ - this directory contains your sample application
* config/ - this directory contains config files for your application
* config.ru - this file contains configuration for Rack middleware
* db/ - this directory contains database files for your application
* lib/ - this directory contains library modules needed by your application
* log/ - this directory contains application log files
* public/ - this directory contains static web assets used by your application
* spec/ - this directory contains the RSpec unit tests for your application
* tmp/ - this directory contains temporary files for your application
* vendor/ - this directory contains third-party code such as plugins and gems
* template.yml - this file contains the description of AWS resources used by AWS
  CloudFormation to deploy your infrastructure
* template-configuration.json - this file contains the project ARN with placeholders used for tagging resources with the project ID

Getting Started
---------------

These directions assume you want to develop on  your development environment or a Cloud9 environment, and not
from the Amazon EC2 instance itself. If you're on the Amazon EC2 instance, the
virtual environment is already set up for you, and you can start working on the
code.

To work on the sample code, you'll need to clone your project's repository to your
local computer. If you haven't, do that first. You can find instructions in the
AWS CodeStar User Guide.

1. Install Rails (see https://guides.rubyonrails.org/getting_started.html)

2. Install bundle:

        $ gem install bundle

3. Install Ruby dependencies for this application:

        $ bundle install

4. Create a secret key for development:

        $ rake secret

5. Set the secret created in the preceding step as an environment variable:

    For *Windows*:

        $ set SECRET_KEY_BASE=YourSecretKey

    For *Linux, macOS, or Unix*:

        $ export SECRET_KEY_BASE=YourSecretKey

6. Create a binstub and start the Rails development server:

        $ rake app:update:bin && rails server

7. Open http://localhost:3000/ in a web browser to view your application.

Before you commit and push changes to your web application, make sure to change the secret key used by your application
in production mode. You can do this by performing the following steps.

1. Open your Ruby on Rails project.

2. On the project's **Dashboard** page, in the **Continuous deployment** tile, choose the **ElasticBeanstalk** link.

3. In the Elastic Beanstalk console, for **Environments**, choose the tile for the Elastic Beanstalk environment.

4. Choose **Configuration**.

5. In the **Software Configuration** tile, choose the gear icon.

6. For **Environment Properties**, find the **SECRET_KEY_BASE** parameter.

7. Replace the existing value (for example, “12345ChangeMeBeforeRealUse67890”) with the value you get by running `rake secret` in a terminal session.

8. Choose **Apply**.

What Do I Do Next?
------------------

Once you have a virtual environment running, you can start making changes to
the sample Rails web application. We suggest making a small change to
/app/views/hello_page/hello.html.erb first, so you can see how changes pushed to
your project's repository are automatically picked up and deployed to the Amazon EC2
instance by AWS Elastic Beanstalk. (You can watch the progress on your project dashboard.)
Once you've seen how that works, start developing your own code, and have fun!

To run your tests locally, go to the root directory of the sample code and run the
`rspec` command, which AWS CodeBuild also runs through your `buildspec.yml` file.

To test your new code during the release process, modify the existing tests or add tests
to the `spec` directory. AWS CodeBuild will run the tests during the build stage of your
project pipeline. You can find the test results in the AWS CodeBuild console.

Learn more about the [RSpec API Documentation](https://rspec.info/documentation).

Learn more about AWS CodeBuild and how it builds and tests your application here:
https://docs.aws.amazon.com/codebuild/latest/userguide/concepts.html

Learn more about AWS CodeStar by reading the User Guide.  Ask questions or make
suggestions on our forum.

User Guide: https://docs.aws.amazon.com/codestar/latest/userguide/welcome.html

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
