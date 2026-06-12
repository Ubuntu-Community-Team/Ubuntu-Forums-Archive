---
title: "Getting xampp up and running"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Bruv on 2009-06-29
> XAMPP is now up and running. The best way to verify this is to open a browser and type localhost in the address bar and hit the Enter key. You should be redirected to the XAMPP welcome page.

This post was appended to the end of another thread but I have got no response. So thought it better to make another thread.

I have downloaded and got running xampp in WinXP so I could work on Prestashop E-commerce site.
I wanted to do the same in Ubuntu and followed instructions from the other thread and everything appears to have installed correctly.
Only thing is.....when I open a browser and type in localhost.....all I get is a message "It works!"


Have I missed something ?

---

### Post by halitech on 2009-06-29
that means you have Apache running which should have php and mysql running.

---

### Post by Celauran on 2009-06-29
> **Bruv said:**
> This post was appended to the end of another thread but I have got no response. So thought it better to make another thread.

I have downloaded and got running xampp in WinXP so I could work on Prestashop E-commerce site.
I wanted to do the same in Ubuntu and followed instructions from the other thread and everything appears to have installed correctly.
Only thing is.....when I open a browser and type in localhost.....all I get is a message "It works!"


Have I missed something ?

Apache is definitely up and running. Without knowing which thread you're referring to, I can't know which instructions you followed. Did you install XAMPP or did you install apache + php + mysql?

```
ps aux | grep mysql
```

will tell you if MySQL is running.

```
whereis php5
```

will tell you whether or not php5 is installed (it doesn't run as a daemon, so ps won't do).

If both are installed/running, you should be good to go.

---

### Post by jimv on 2009-06-29
That's what it's supposed to do.  Now you need to follow Prestashop's documentation to get it installed.

---

### Post by Bruv on 2009-06-29
I have installed LAMP apparently which will do the same job, I hope.
[The other thread where I got the advice]("http://ubuntuforums.org/showpost.php?p=7516015&postcount=15")

I am trying to move over from Windows and still have a lot to learn.
Getting Prestashop working on localhost on windows was a challenge, and knowing the application is open source assumed it would naturally be better in Ubuntu

I have not downloaded Prestashop in Ubuntu as yet, until I see how things work first, it is step by step to limit my confusion.

---

### Post by Celauran on 2009-06-29
Alright, so you haven't installed XAMPP, you installed the LAMP stack. Same end result, really. Sounds like everything is fine, though.

---

### Post by Bruv on 2009-06-29
My problem is now how to progress to download and install the shopping cart on Ubuntu.
My Printer doesn't work in Ubuntu so I have to swop back and forth to print instructions.
I had used instructions for another cart to install on Windows.
So now I am back on Windows to print instructions for Ubuntu install, so I can go at it step by step.

Hopefully I will not be back.
Thanks very much for your help.....a little reassurance helps us newbies dontcha know ?

---

### Post by Celauran on 2009-06-29
There's a README in the Prestashop .zip file. You just need to download Prestashop, unzip to your DocumentRoot, and point your browser to it. This will bring you right to the installer script.

---

### Post by Bruv on 2009-06-29
You will have to be very patient with me sorry.
Where do I find my DocumentRoot ?
Is it simply Documents ?

---

### Post by wojox on 2009-06-29
Apache DocumentRoot should be /var/www

---

### Post by Iowan on 2009-06-29
It won't cover everything, but [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page can be a good place to start.

---

### Post by Bruv on 2009-07-06
I am still having problems.

I just cannot get the Prestashop files into the var/www folder.
If I tell you what I have done so far (don't laugh at my ignorance)
I have downloaded the Prestashop zip and extracted it to a folder on my desktop.
Then as much as I try I fail to move the files to where they need to go.
I have changed the permissions.....I think.
Select all/ copy/ then pasting to the folder doesn't work.

Any advice would be very happily received.

---

### Post by wojox on 2009-07-06
Open terminal

```
gksu nautilus
```

Now try copy/paste.

---

### Post by Bruv on 2009-07-06
That command returned the following.> Initializing nautilus-share extension

** (nautilus:6604): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown
Is that good ?
Doesn't appear to be to me, but I know nothing.

---

### Post by Celauran on 2009-07-06
> **Bruv said:**
> I am still having problems.

I just cannot get the Prestashop files into the var/www folder.
If I tell you what I have done so far (don't laugh at my ignorance)
I have downloaded the Prestashop zip and extracted it to a folder on my desktop.
Then as much as I try I fail to move the files to where they need to go.
I have changed the permissions.....I think.
Select all/ copy/ then pasting to the folder doesn't work.

Any advice would be very happily received.

Try this:
```
sudo cp -R ~/Desktop/prestashop /var/www/
```

---

### Post by Bruv on 2009-07-06
Eureka or something.

That command copied the folder to var/www, now I need to empty its contents to var/www, I am sure I read that somewhere.

---

### Post by Celauran on 2009-07-06
> **Bruv said:**
> Eureka or something.

That command copied the folder to var/www, now I need to empty its contents to var/www, I am sure I read that somewhere.

Check the README. I don't remember needing to empty it; you should access it via [http://localhost/prestashop](http://localhost/prestashop)

---

### Post by Bruv on 2009-07-06
You are right of course.

Many thanks for the help and the patience.
(Anybody want to sort out my shopping cart now its up and running ?)
Only joking......thanks again

---

### Post by Bruv on 2009-07-07
I am doing great ....honestly.
I have installed GD Library as requested during install, but now I am flummoxed by the following list of files that need their permissions changed.
I have searched on this site. but cannot find anything relevant
Just point me in the right direction please.


  * Write permissions on files and folders:
    * /config
    * /tools/smarty/compile
    * /sitemap.xml
    * Write permissions on folders and subfolders/recursively:
    * /img
    * /mails
    * /modules
    * /themes/prestashop/lang
    * /translations
    * /upload
    * /download


Many thanks.

---

