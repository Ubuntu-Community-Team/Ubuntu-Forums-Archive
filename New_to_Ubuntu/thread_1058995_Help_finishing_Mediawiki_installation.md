---
title: "Help finishing Mediawiki installation"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by newellscott on 2009-02-03
I was successful installing ubuntu-server on an old Sony Desktop for the purpose of hosting a Wiki site. I followed instructions on how to install Mediawiki and was successful here too, until the very last. I open my browser and went to the following url:

[http://10.0.1.191/mediawiki/](http://10.0.1.191/mediawiki/)

I get a page with the pretty yellow flower of Mediawiki with the following instruction:

To complete the installation, move **config/LocalSettings.php** to the parent directory.

I have no experience with command-line stuff being a Mac user my whole life and do not know how to do this. I have only gotten this far because I followed the directions. 

1) Where is the **config/LocalSettings.php** file and how do I move it to the parent directory?
2) What is my parent directory? Is it merely **mediawiki**, the top folder (dir) on my ubuntu server; as in **[http://10.0.1.191/mediawiki/](http://10.0.1.191/mediawiki/)**?

Thanks for any help.

---

### Post by binbash on 2009-02-03
[http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu](http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu) 

navigate to Configure MediaWiki section.Your answer is there

---

### Post by newellscott on 2009-02-03
Thanks Binbash.

I tried the following with no success:

sudo mv config/LocalSettings.php /config/LocalSettings.php
mv: cannot stat `config/LocalSettings.php': No such file or directory

sudo mv config/LocalSettings.php /mediawiki
mv: cannot stat `config/LocalSettings.php': No such file or directory

sudo mv config/LocalSettings.php dir/mediawiki
mv: cannot stat `config/LocalSettings.php': No such file or directory

sudo mv config/LocalSettings.php mediawiki
mv: cannot stat `config/LocalSettings.php': No such file or directory

sudo mv config/LocalSettings.php /
mv: cannot stat `config/LocalSettings.php': No such file or directory

What am I doing wrong?

---

### Post by binbash on 2009-02-03
dude you will go the the mediawiki path for example : 

cd /var/www/public_html/install/ 

then give that command.That is where you installed the media wiki.

---

### Post by newellscott on 2009-02-03
Sorry binbash, what you said did not make any sense to me.

When I enter the following url I get to the ubuntu top directory:

[http://10.0.1.191/](http://10.0.1.191/)

which looks like:

[IMG]http://farm4.static.flickr.com/3344/3250400695_c0aba1f631.jpg?v=0[/IMG]

If I click on the mediawiki link, I get the Mediawiki start page with the instruction to move the **config/LocalSettings.php** file to the parent directory.

The 5th folder down is the Mediawiki folder. I assume this **config/LocalSettings.php** file is inside some directory inside **mediawikli**; am I wrong? 

Perhaps you could help me see into the mediawiki directory. I tried to to a dr command in the terminal and I must have not entered it correctly as it did not list the contents of mediawiki.

Once I find where this config/LocalSettings.php file is I assume I would move it to the parent directory with this command:

**sudo mv config/LocalSettings.php /mediawiki**

if the file is somewhere inside the mediawiki directory, perhaps the command would look something like:

**sudo mv /[missing directory]/config/LocalSettings.php mediawiki/**

Thanks

---

### Post by jimv on 2009-02-03
I think this will work for you.

```
sudo su

(put in your password, that gives you a root terminal so you don't have to worry about sudo-ing for now)

cd /var/www
mv mediawiki/config/LocalSettings.php mediawiki/
```

Your web directory is /var/www in Ubuntu.

Oh, and dr isn't the list directory command in unix, it's ls (LS).

---

### Post by newellscott on 2009-02-03
Thanks jimv

I now know how to search directories. 

For those who run into the same difficulty, below is the method that worked for me.

1) jimv's helpful tip allowed me to find the **LocalSettings.php**. It is located in the config dir which is inside of the **parent** directory. This looks like the following on my computer with the parent directory called **mediawiki**

/var/www/mediawiki/config/LocalSettings.php

I then used the move command (mv) to move the file to the parent directory (mediawiki). Remember, with jimv showing how to go through a root terminal, you do not have to use the sudo command. So, the following is the command line to move the file to the parent:

root@web-server:/home/nscott# **mv /var/www/mediawiki/config/LocalSettings.php /var/www/mediawiki**

make sure there is a space between php and /var.

I then entered the url of the site in my browser and it worked:

[http://10.0.1.191/mediawiki/](http://10.0.1.191/mediawiki/)

My main confusion is obviously a lack of experience with the UNIX command line and commands. Although I did not try moving the file through my root because I was successful with jimv's method, I'm confident it would work that way too, as long as you have the right path.

Thanks again jimv! I still have a little hair left.

---

### Post by jimv on 2009-02-03
Hey, it took me at least a year of casual use to begin getting comfortable with the command line.  I mean, you can do pretty much everything with the gui, but once you learn the command line, it's just faster.

---

