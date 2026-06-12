---
title: "New To Linux and PHP"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by mkozlov on 2010-07-22
Hello everybody,

I'm fairly new to the whole Ubuntu scene so bare with me. My goal is to learn how to use Ubuntu and PHP within the coming months.

So far I am running Ubuntu and I have purchased web hosting and a domain through Site5.com. I will be asking lots of questions about PHP so if you need to info about my current PHP setup you can find it [here]("http://174.121.239.98/info.php").

So Site5 has a decent File Manager, but I was wondering: which Ubuntu program I should use to sync with my server? For now I will simply be playing around with simple PHP files to learn the basics. I am currently learning through w3schools.com (dont hesitate to suggest better resources, I am willing to buy books).

Is there a specific directory where I should be uploading my files? I noticed there is one called www, do I put them here?

As far as testing out my PHP files should/can I do this offline or should I just stick my Site5 server which has PHP pre-installed.

Also If anyone can refer me to a basic guide that will explain what on earth all the existing files on my server are doing? I would really like to know. I assume they have to do with PHP and MySQL or something? I have read about PHP and MySQL before and somewhat grasp the big picture, but would really like to know what is happening on my server behind the scenes.

Any help is greatly appreciated. Thank you for your time!

---

### Post by mkozlov on 2010-07-22
> **mkozlov said:**
> 
Is there a specific directory where I should be uploading my files? I noticed there is one called www, do I put them here?

Okay so I answered my own questions. Gotta put the files in the folder called public_html, this makes sense:).

---

### Post by natex on 2010-07-22
Hi.
This may be of some interest to you.

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

natex

---

### Post by Paqman on 2010-07-23
> **mkozlov said:**
> 
As far as testing out my PHP files should/can I do this offline or should I just stick my Site5 server which has PHP pre-installed.


Either way is fine. Up to you really. Ubuntu's standard file browser (Nautilus) can do FTP access, by the way. So working with files on your remote server doesn't really feel any different from working with local ones.

---

### Post by mkozlov on 2010-07-23
Wow thanks! I didn't realize it was this easy and convenient!

---

### Post by iMisspell on 2010-07-24
Heres some thoughts and ideas...

If you plan on learning PHP more then likely, some where along the lines, you will end up working with a data-base, MySQL is a common choice - so you might think about installing that on your home/test server.

Something else, an editor.
To start off and learn how to do things you might think about just using a plan text editor and then work your way to a more advanced editor (personaly, i use _[Geany]("http://www.geany.org/")_ when i need to do quick edits, but if im working on a big project i use [_phpeclipse]("http://www.eclipse.org/downloads/")_, some people like _[Netbeans]("http://netbeans.org/features/php/")_ and if you search around, you will find many more).

Some links which you might find useful...
[http://www.php.net](http://www.php.net) (using the search to the top right with 'function list')
[http://www.phpbuilder.com/](http://www.phpbuilder.com/)
[http://www.phpfreaks.com/](http://www.phpfreaks.com/)

You can also download the PHP doc to your home server:
[http://www.php.net/download-docs.php](http://www.php.net/download-docs.php)
And then edit your */etc/apache2/sites-available* file and add the following, just above </VirtualHost>
```

    Alias /phpdocs/ "/CHANGE/PATH/TO/DOWNLOADED/DOCS/"
    <Directory "/CHANGE/PATH/TO/DOWNLOADED/DOCS/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

```

And then edit your */etc/php5/apache2/php.ini* file (studying this file will help you also, its pretty well documented).
- Find: 'error_reporting = ...' and change it to *error_reporting = E_ALL | E_STRICT | E_DEPRECATED*
- Find: 'docref_root = ...' and change that to *docref_root = "/phpdocs/"*

And then restart apache '*sudo /etc/init.d/apache2 restart*' 
The above edits will: If you create an error in your php code, it will display the error along with a link to your local PHP Docs which should give you more info on how to resolve the problem.


As time goes by (and this is something which i really wish i start to do shortly after i started to coding, not years later :( ) is look into a local (running on your home server) _[SVN server]("https://help.ubuntu.com/community/Subversion")_.

And if you have questions, there are many forums out there, but posting in _[Development & Programming > Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")_ here will get your some useful answers.


Best of luck.

_

---

### Post by bigboy_pdb on 2010-07-24
> **mkozlov said:**
> As far as testing out my PHP files should/can I do this offline or should I just stick my Site5 server which has PHP pre-installed.

You should set up your own local test server. There are a number of reasons why:

[LIST]
[*] Testing will be quicker since you don't have to wait for uploads and downloads to finish.
[*] People who are visiting your site won't think that there's something wrong with it if you're making changes or debugging.
[*] If your scripts have any problems that cause the code to be displayed, people won't see them.
[*] You can run extensions, such as debuggers like xdebug or Zend debugger.
[/LIST]

---

### Post by mkozlov on 2010-07-25
Wow, thanks guys. I'm gonna try this stuff soon. Still haven't reached the MySQL portion of the lessons, will post on my progress/problems as I go.

---

### Post by MattBD on 2010-07-25
I suggest referring to [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) for guidance on how to set up your own local web server. I personally have a LAMP server on my netbook, with the root directory set to be a folder in my /home called Sites since that makes it extremely convenient to edit files.

---

