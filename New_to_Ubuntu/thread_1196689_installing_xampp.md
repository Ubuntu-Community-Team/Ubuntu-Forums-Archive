---
title: "installing xampp"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by pilotind on 2009-06-25
I am a true beginner and have only been working at learning ubuntu for a couple of weeks.  I't trying to install xampp from the terminal by using the command:
tar xvfz xampp-linux-1.7.1.tar.gz -C/opt.
I get error messages saying it can not mkdir for a number of directories.  I don't know to overcome this problem.  Help.

Pilotind

---

### Post by Celauran on 2009-06-25
Do you have write permission to the necessary directories? You may need to prefix the tar command with sudo.

---

### Post by Divider on 2009-06-25
Also Xampp is for windows.

Lammp is for linux. :)


and you have to run as root. sudo is the command to do so.

---

### Post by halitech on 2009-06-25
Why not just go into synaptic or Add/Remove programs and install the components you need instead of farting around trying to get things extracted and put in the proper places?

---

### Post by wojox on 2009-06-25
Go here and read the documentation. 
[http://www.apachefriends.org/en/faq-xampp-linux.html](http://www.apachefriends.org/en/faq-xampp-linux.html) 
And yes xampp is for linux. The x stands for cross platform.

---

### Post by pilotind on 2009-06-25
I think so,I typed in sudo then it asked for a password which I entered; it seemed to be accepted.  How can I make sure?

---

### Post by vishnuvardan on 2009-06-25
$ changes to # while moving to sudo

---

### Post by pilotind on 2009-06-25
when I first started trying this installation, I googled it seemed that most information said not to do the installation this way, so I didn't.

---

### Post by halitech on 2009-06-25
> **pilotind said:**
> when I first started trying this installation, I googled it seemed that most information said not to do the installation this way, so I didn't.

not do the installation which way?

---

### Post by pilotind on 2009-06-25
There clearly is an xampp for linux also.  I simply followed directions from the download site.
  Thanks

---

### Post by pilotind on 2009-06-25
thanks, one more bit of info.  It did change to # so now I'll try again.

---

### Post by pilotind on 2009-06-25
It seemed to be extracted but when I try to do the upgrade I get a command not found message.

---

### Post by pilotind on 2009-06-25
using the add/remove programs or synaptic.

---

### Post by Celauran on 2009-06-25
Is it working now? If it's not, I'm going to second the suggestion to just install apache2, mysql-server, and php5 from repos. Saves an awful lot of headaches.

---

### Post by jimv on 2009-06-25
Sometimes these forums amaze me...some dude is trying having trouble installing XAMPP and no one tells him that he can install the LAMP package with a few clicks?

Here's what you do...this will install Apache, Mysql, and PHP:

Go to System > Administration > Synaptic Package Manager

Go to Edit > Mark Packages by Task

Put a check on "LAMP Server" and click OK

Click Apply.  

This will install everything you need to develop/use web apps that use PHP/MySQL.  It's pretty much the same thing as XAMPP, but without all the hassle, and the applications will also stay up-to-date.

---

### Post by Celauran on 2009-06-25
> **jimv said:**
> Sometimes these forums amaze me...some dude is trying having trouble installing XAMPP and no one tells him that he can install the LAMP package with a few clicks?

You're kidding, right? At least two people told him it would be easier to install from repos.

---

### Post by jimv on 2009-06-25
> **Celauran said:**
> You're kidding, right? At least two people told him it would be easier to install from repos.

It's not quite the same thing telling someone new that they can "install ur stuff from the repoz" and telling them how to actually do it.  The first piece of advice is essentially worthless, the second it helpful.

---

### Post by halitech on 2009-06-25
> **halitech said:**
> Why not just go into synaptic or Add/Remove programs and install the components you need instead of farting around trying to get things extracted and put in the proper places?

> **pilotind said:**
> when I first started trying this installation, I googled it seemed that most information said not to do the installation this way, so I didn't.

> **halitech said:**
> not do the installation which way?

> **pilotind said:**
> using the add/remove programs or synaptic.

> **Celauran said:**
> Is it working now? If it's not, I'm going to second the suggestion to just install apache2, mysql-server, and php5 from repos. Saves an awful lot of headaches.

> **jimv said:**
> It's not quite the same thing telling someone new that they can "install ur stuff from the repoz" and telling them how to actually do it.  The first piece of advice is essentially worthless, the second it helpful.

if you bothered to read all the replies, it was asked if they tried to do it that way and the response was
> **pilotind said:**
> when I first started trying this installation, I googled it seemed that most information said not to do the installation this way, so I didn't.
so obviously he/she was not interested in trying to do it that way or they would have asked for more information on installing that way. Why they were advised not to is beyond me because installing anything outside the repos represents a security/system risk in my opinion.

---

### Post by jimv on 2009-06-25
> **halitech said:**
> if you bothered to read all the replies, it was asked if they tried to do it that way and the response was

so obviously he/she was not interested in trying to do it that way or they would have asked for more information on installing that way. Why they were advised not to is beyond me because installing anything outside the repos represents a security/system risk in my opinion.

"I am a true beginner and have only been working at learning ubuntu for a couple of weeks."

I doubt he knew to ask, so I don't see your point.

---

### Post by wojox on 2009-06-25
The advent of Java 2 Enterprise Edition™ dramatically changed the software landscape by providing an integrated middleware stack that greatly simplified the task of writing and deploying Java™ applications. For a while, the open source community was left behind because it lacked a similar integrated architecture.

Recently, with the introduction of integrated open source stacks like XAMPP from Apache Friends, this situation has started to change. These stacks are still quite simple and rudimentary when compared with J2EE, but they are nevertheless an important step on the way to fuller systems integration. PHP 5.0 (which makes PHP fully object oriented) is a good indicator that this trend will accelerate.

The focus of this article is on one of the integrated, open source stacks: XAMPP from Apache Friends.

Introducing XAMPP

XAMPP is a full-featured AMPP (Apache MySQL, PHP, Perl) package that is one of the few non-commercial AMPP middleware stacks available on Linux. With its tight integration, XAMPP makes it possible to run anything from a personal home page to a full-featured production site (though only for development purposes; XAMPP is not meant to be used on a production server due to security issues).

XAMPP really shines in the following areas:

    * It is easy to install and set up.
    * It contains a number of useful packages that make it easy to do things like generate traffic reports and accelerate PHP content.
    * It has been thoroughly tested on the SUSE, Red Hat, Mandrake, and Debian Linux distributions, as well as on Windows® and Solaris.

For this article, we will install XAMPP under Mandrake Linux 10.0. Let's start by looking at the default packages that come with XAMPP.

Basic packages

Basic packages include system, programming, and server software:

    * Apache, the famous Web server
    * MySQL, an excellent, free, open source database
    * PHP, the programming language (in versions 4.3.8 and 5.0.1 at the time of this writing)
    * Perl, the programming language
    * ProFTPD, an FTP server
    * OpenSSL, for secure sockets layer support

Graphics packages

XAMPP includes the following graphics-related packages:

    * GD, the "Graphics Draw" library
    * libpng, the official PNG reference library
    * libjpeg, the official JPEG reference library
    * ncurses, the character graphics library

Database packages

And what would an integrated stack be without some database packages such as:

    * gdbm, the GNU implementation of the standard UNIX® dbm library
    * SQLite, an extremely small, zero-configuration SQL database engine
    * FreeTDS, a database library that gives UNIX and Linux programs the ability to talk to Microsoft® SQL and Sybase databases

XML packages

For XML development, XAMPP includes the following:

    * expat, an XML parser library
    * Salbotron, an XML toolkit
    * libxml, an XML C parser and toolkit for GNOME

PHP packages

For PHP development, XAMPP includes the following:

    * PEAR, the PHP library
    * A pdf class that generates dynamic PDF documents with PHP
    * TURCK MMCache, a PHP performance enhancer

Other packages

And finally, XAMPP demonstrates its versatility by including the following packages:

    * zlib, a compression library
    * mod_perl, which embeds a persistent Perl interpreter in Apache
    * gettext, a toolset that assists GNU packages in producing multi-lingual messages
    * mcrypt, an encryption program
    * Ming, a Flash (SWF) output library
    * Freetype2, a software font engine
    * IMAP C-Client, a mail program API

Now let's talk about installing XAMPP.

Back to top

Installing and daemonizing

To install XAMPP, download the latest binary from the Apache Friends Web site (see Resources for a link). Untar it to /opt using the following command:

tar xvfz xampp-linux-1.4.7.tar.gz -C /opt

That's it! XAMPP is now installed in /opt/lampp. Any previous installations that were in /opt have been overwritten. If you are running an older version of XAMPP and don't want to download the entire package again, Apache Friends has an upgrade package available for download.

Now that everything is installed, let's start the new daemons. Change your current working directory to /opt/lampp (cd /opt/lampp) and enter the following:

./lampp start

You should see the following:

Starting XAMPP for Linux 1.4.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

XAMPP is now up and running. The best way to verify this is to open a browser and type localhost in the address bar and hit the Enter key. You should be redirected to the XAMPP welcome page.

---

### Post by halitech on 2009-06-25
obviously they did know about synaptic because they said they were advised not to use it from googled sites so they wanted to do it manually. I wasn't going to bother typing out how to do it in a method they weren't interested in using.

---

### Post by Bruv on 2009-06-28
> XAMPP is now up and running. The best way to verify this is to open a browser and type localhost in the address bar and hit the Enter key. You should be redirected to the XAMPP welcome page.


I have been working on a downloaded shopping cart, and stumbled through what is required to get it up and running.
I have got xampp working on Win XP and have just gone through the process of installing on Ubuntu.
When I open a browser and type in localhost it returns a message that says
"Its Working"

Have I missed something out somewhere ?

---

### Post by eel on 2009-08-02
Thanks Jimv!!!!!!
It sure does pay to be nice and be clear at the risk of telling people something they might already know, i am not a total noob anymore but there are still so many things to be learned! Being cocky and showing of that you know the slang & lingo does not make for good karma (: 

I had never seen the whole 'mark packages by task' before, wow :D

---

### Post by Kezz Kezz on 2009-08-17
> **Bruv said:**
> 
When I open a browser and type in localhost it returns a message that says
"Its Working"

Have I missed something out somewhere ?

Hi I'm trying to get xampp/lampp on ubuntu and I'm getting the "It's working" message too :confused: I'm a complete linux newbie so can anyone tell me where I've gone wrong?

---

### Post by halitech on 2009-08-17
> **Kezz Kezz said:**
> Hi I'm trying to get xampp/lampp on ubuntu and I'm getting the "It's working" message too :confused: I'm a complete linux newbie so can anyone tell me where I've gone wrong?

you didn't do anything wrong if you are getting the message that "It works!" It means everything installed and you are seeing the default page that it puts up when apache is running.

---

