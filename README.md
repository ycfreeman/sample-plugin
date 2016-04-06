# Automagic push to deploy your wordpress plugin to wordpress plugin directory

Aggregation of useful scripts and modifications to get push to deploy working the way i want 

- forked from https://github.com/wp-cli/sample-plugin
- added a modified deployment script from https://github.com/GaryJones/wordpress-plugin-git-flow-svn-deploy
- modified script:
    - now takes 5 arguments: <Plugin Slug> <Main File> <Tag Version> <SVN Username> <SVN Password>
    - takes a .svnignore file contains paths to deployment scripts and git related stuff, so these wont get pushed to the plugin directory
- .travis.yml contains the workaround from https://github.com/dmakhno/travis_after_all because you dont want your plugin get deployed multiple times

---

## Usage
you can use this project as your base project, or wget/curl the scripts in your .travis.yml

### Setup
- add your PLUGINSLUG, MAINFILE to .travis.yml or set them in travis Settings > Environment Variables
- set your SVNUSER, SVNPASS in travis Settings > Environment Variables, remember to *not* turn on Display value in build log
- or use [Encrypted Variables](https://docs.travis-ci.com/user/environment-variables#Encrypted-Variables) feature in travis
- *never write your username and passwords in plain text in a public repository!!*

### Release
- tag your github release to match your version number
- let travis handles it all for you
- travis should send you email by default if it fails, if you want notifications to somewhere else, [check out travis documentations](https://docs.travis-ci.com/user/notifications/)