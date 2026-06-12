---
title: "Possible problem with mod_rewrite ... no CMS running fine."
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by michal-urban on 2014-06-03
Hi,


Im running Ubuntu 14.04 32bit minimal install on my home server, with MySQL and PHP5 from repositories. 

I tried installing Bolt CMS few times but always, after finishing the process, I end up with "The requested URL /bolt/bolt/users/edit/ was not found on this server."  I decided this was most likely the fault of Bolt so I moved on. BUT ... I ended up with same problems with other CMS systems ... Anchor and Redaxscript to mentions just two. So, I came back to Bolt and tried to check my servers setting.

I found out that the directories (like /bolt/bolt/users/edit/) dont really need to be in the directory tree: "There is no folder because it uses mod_rewrite to route everything through the index.php file." (as it says in some of the forums I visited).


So I tried to check if mod_rewrite is configured fine on my server.  First, I did:
```

> a2enmod rewrite
Module rewrite already enabled
```


Then, I read somewhere, that
```
What a2enmod does is simply create a symbolic link, so the following two are the same, both proper, solution:
ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/
```
So I checked if the file /etc/apache2/mods-enabled/rewrite.load is present (and it is).


And finally, I tried to find out other ways to check this. So, I tried making a PHP file with this content ...
```
<?php
 if(!function_exists('apache_get_modules') ){ phpinfo(); exit; }
 $res = 'Module Unavailable';
 if(in_array('mod_rewrite',apache_get_modules())) 
 $res = 'Module Available';
?>
<html>
<head>
<title>A mod_rewrite availability check !</title></head>
<body>
<p><?php echo apache_get_version(),"</p><p>mod_rewrite $res"; ?></p>
</body>
</html>
```
... and running it. The answer is: "mod_rewrite Module Available".


So, now im royally f*cked, unless of course some of you helps me ... I have no idea what to do now. 


Thanks in advance! :)

---

### Post by spjackson on 2014-06-05
I'm not an expert on Apache configuration, but I am pretty sure that in addition to enabling the module (which you appear to have done successfully) there are two further steps which perhaps you should check. This is my reference for information [http://book.cakephp.org/2.0/en/installation/url-rewriting.html](http://book.cakephp.org/2.0/en/installation/url-rewriting.html)

You need a .htaccess file in the DocumentRoot containing rewrite rules. I imagine that these are provided by the various CMS that you have tried. Nevertheless, it would be worth checking. You also need the Apache configuration for the site to have "AllowOverride All". On my Ubuntu server this is done in /etc/apache2/sites-available/default but it might be somewhere else.

---

### Post by michal-urban on 2014-06-05
Todal, I tried checking and changing cofigs again and it looks like I may had some mixup in some of the config files ... and finally I got it working. The mess was probably with stuff configured on more than one place. Thanks for your reply anyway! :)

---

### Post by hpalma on 2014-10-09
Hi, i'm having the exact same problem when installing bolt in Ubuntu. Can you provide some clues on what you did to make it work ?
Thanks.

---

### Post by michal-urban on 2014-10-09
Im sorry, but I can provide no clues, sorry. :-( I just kept changing config files and suddenly it started working. I cant even look at the files because my home server broke down - some motherboard failure which also wrecked the hard drive. Good luck!

---

