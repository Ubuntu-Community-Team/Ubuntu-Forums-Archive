---
title: "Help with PHP"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by methodicalx on 2009-11-23
Let me start by saying that I am a complete newb when it comes to Ubuntu and PHP. I am having a difficult time getting PHP to work on the Apache sever. I will explain in detail everything that I have done with hopes of someone discovering my error and helping get this to work.
 
I installed both Apache and PHP 5 using lamp, following the tutorial from [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
 
When I try to open PHP files from the text editor or directly from the folder where I have the files saved, I get a download/ save request prompt.
 
Now, I have several php files located in [http://localhost]("http://localhost/"). When I open these files using the links from [http://localhost]("http://localhost/") PHP works correctly. All of the files displayed in [http://localhost]("http://localhost/") are files that WERE located in the folder "websites" that I designated to store my webpages WHEN I initially set-up PHP and Apache .
 
I thought that everything was working and started to develop and save additional web pages to the folder "websites", thinking that I would be able to access/ test those pages through [http://localhost]("http://localhost/"). However, none of the new web pages are showing up under [http://localhost]("http://localhost/"), even though I am saving them in the same folder. 
 
Where did I go wrong? Is there a way to "refresh" localhost to have these new pages show up? I am assuming that PHP was installed correctly to a certain degree, as those PHP files work from localhost. 
 
I have been working on this for several days. Please help!

---

### Post by cbabbage on 2009-11-23
So to clarify the problem, your PHP files work if they're in the localhost folder, but not when they're in a separate folder? If so, have you tried putting the new PHP pages in the localhost folder? I believe localhost is the only default folder to run PHP files from. 

There is a way to add additional folders, but it's a while since I've done it so I'll need to look up how to do it in Ubuntu.

---

### Post by methodicalx on 2009-11-23
You are correct.  The pages that are stored in localhost work.  but the new pages that I save do not show up in localhost.

---

### Post by cbabbage on 2009-11-23
I can't give you the exact steps, because I haven't got apache set up on my Ubuntu. However, I did some web development some time ago on Slackware. In order to get the server looking in places other than localhost, you need to edit one of the configuration files. On Slackware, it was /etc/httpd/httpd.conf. Opening the file with a text editor gives you instructions on how to modify docroot. 
In Ubuntu, I believe the configuration file may be called apache.conf. So look for either httpd.conf or apache.conf ; first place to look is /etc.
Either configuration file should have instructions on how to make changes to docroot. It goes without saying that you should back up the original before you start.

Hope this helps,
CB.

---

### Post by Roger Allott on 2009-11-23
My guess is that you haven't set permissions right for your subfolders.

Make sure you are owner of all subfolders of your localhost folder, which by default is /var/www/.

---

### Post by methodicalx on 2009-11-24
I think that I have everything set-up correctly.  The only problem that i am having is changing the permission to my var/www/ folder so that I can save documents to it..  This is a root folder, do I have to log into root to change the permission?

---

### Post by Roger Allott on 2009-11-25
> **methodicalx said:**
> I think that I have everything set-up correctly.  The only problem that i am having is changing the permission to my var/www/ folder so that I can save documents to it..  This is a root folder, do I have to log into root to change the permission?

You need to run a sudo command in terminal.

The command you need will be something like:
```
sudo chmod rw /var/www/
```

After you run that, it will ask you to enter the root password.

However, please note that I'm very green when it comes to CLI stuff, so double-check that command with someone more competent than me.

---

### Post by Jive Turkey on 2009-11-25
put your files into the /var/www/, or a subfolder thereof.  To make your user own the folder you can use the command: 
```
chown -R <username> /var/www
```
you will then be able to read write delete and probably execute the files in that folder.
If you manipulate the folders there with a sudo command you may also end up giving the ownership to root.

localhost isnt a folder its a relative network address, you are going to confuse a lot of people talking about the localhost folder.  aside from that there is nothing stopping you from making a folder named localhost, but for the love of god, don't.

localhost is what you can put in your browser's address bar to view sites hosted on your own machine.  but you see when you are talking about hosting webpages localhost isn't a very good name for it.  Another equivalent to localhost is 127.0.0.1 for most computers.  So, in most cases [http://localhost](http://localhost) and [http://127.0.0.1](http://127.0.0.1) mean the same thing.

To get started hosting web pages on your machine, use the default folder until you figure out how to manipulate Apache better.  It looks like you may have changed the default during the initial setup.

I suggest you go and switch it back on my server(s) my apache directives for particular sites are in /etc/apache2/sites-available

in that directory you will find the configuration files for your sites, there should be one named "default."

To open it, got to a terminal and type (that's applications > accessories > terminal) the command```
sudo gedit /etc/apache2/sites-available/default
```

One of the first directives should say "DocumentRoot /whatever/directory"

Change that back to /var/www if it doesn't say that already.  Make sure there is no trailing slash ie-/var/www/ <--that's wrong and will cause errors.

save the file, then do "save as" name it whatever you like, the name of your site is fine, and save it to the same directory.

You could have your documentroot wherever you want but it might catch up to you in ways you can't predict or recognize later on.

Now for the good stuff:
```
sudo a2ensite name-of-the-site-file-you-just-saved
```
enables the site described by the file and Apache will serve it.  You might also notice that the command makes a link to this file in the folder /etc/apache2/sites-enabled.  This is an ubuntu only feature as far as I know and its pretty nice IMO.

```
sudo a2dissite name-of-file
```
This is another helpful tool and will take down the site.

```
sudo apache2ctl (start|stop|restart)
``` will start stop or restart apache, this is helpful if you make changes in apache's own config files and need to apply the changes.

Changes to your *.php files should not require any special refresh of the server to see the changes you have made other than refreshing your browser.  You should figure out how to make your testing browser not use any cache or clear your cache to be able to really see certain changes.  Everyone gets tripped up by thier browsers use of cached content when they are developing websites.  Opera has some really nice features for this, firefox has some good plugins for this too.  Double clicking the files on your local computer *should* open them for editing.

Now when you are ready to test your page in the browser (make a bookmark ftw) use [http://localhost/page.php](http://localhost/page.php) or whatever to help your computer know that apache is serving the file to your browser and not nautilus (nautilus is the program that shows your folders and stuff on ububuntu and other Gnome based linux desktops).

Good luck and have fun!

---

### Post by Roger Allott on 2009-11-26
Note: when I said "double-check that command with someone more competent than me", I was referring to someone like Jive Turkey!

---

### Post by Jive Turkey on 2009-12-01
> **Roger Allott said:**
> Note: when I said "double-check that command with someone more competent than me", I was referring to someone like Jive Turkey!

Don't be so sure [http://www.urbandictionary.com/define.php?term=jive+turkey]("http://www.urbandictionary.com/define.php?term=jive+turkey")

---

