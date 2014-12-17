idiom
=====

Idiom is a new translation system for AngularJS that allows you to read in the current scope to provide 
context-based translations - no more thing(s), s/he, his/her, you actually know what you're writing about.

#Translation files

Add a folder to your project containing one json file per language (en.json, fr.json, de.json...). In the file,
a simple key-value system allows you to write your translations :

<pre>
{
    "title": "Title",
    "description": "This is my description"
}
</pre>

You then need to set the translation folder and add the directives to your module:

<pre>
idiom.addTranslations('/path/to/my/folder', function(){
    idiom.translate('my.key');
});
var module = angular.module('app');
idiom.addDirectives(module);
</pre>

In your view, you can use the directives to translate content :
<pre>
&lt;i18n&gt;my.key&lt;/i18n&gt;
&lt;input type="button" i18n-value="my.key" /&gt;
&lt;input type="text" i18n-placeholder="my.key" /&gt;
</pre>

Your translations can directly use your current scope:

<pre>
{
    "welcome": "Welcome, {{user.name}}!",
    "description": "<span ng-if="user.male">He</span><span ng-if="user.female">She</span>'s awesome!"
}
</pre>

