---
title: "XAMPP Help"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Enderthexenocide on 2010-03-27
Hey,

I have ubuntu desktop and I downloaded XAMPP and put it on the desktop, How do I install that? and are there any guide to help me set up and get a website going on it? I currently run a website with a hosting company and I need to run it from home but I have over 200 people waiting on me so I need to get this done ASAP.

Thank you,

Enderthexenocide

---

### Post by louieb on 2010-03-27
Welcome to the forum.

If your going to make your website public - you really don't want to use XAMPP - even the XAMAP documentation says its not secure and vulnerable to being hacked. 

To install a lamp server - 
```
sudo tasksel install lamp-server 
```

Lots of steps to get a web-server up and running - here's a start.
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Enderthexenocide on 2010-03-27
Ok, I have a problem, somehow my user root got changed from /home/user to /home

How do I change that back?

It gives me an error and won't let me login,

Thank you,

Ender

---

### Post by Enderthexenocide on 2010-03-27
I am going to reload the OS on it and see if that fixes it.

---

### Post by Enderthexenocide on 2010-03-27
I have ubuntu Desktop 6.10 will that command work on it too?

Thank you

---

### Post by vivek40 on 2010-03-27
is it 6.10 or 9.10??

---

### Post by Enderthexenocide on 2010-03-27
6.10 efty edge

---

### Post by vivek40 on 2010-03-27
However here go the steps:-
1. Install LAMP.
2. You are supposed to put your site in var/www . However for that you might have to change some permission settings. Instead of that put your site anywhere in your profile and then create a symlink between var/www and your target folder which contains the site...

<i really however wont know how to install LAMP on 6.10.. but am sure someone will help you do that>

---

### Post by Enderthexenocide on 2010-03-27
Sorry but I am new to this,

How do I change the permissions? I have never used Ubuntu and my brother is a big ubuntu fan and told me to use it because I have little money to spend on an OS at the moment... but thanks for helping! I will need a lot of it, and thank you for that guide! that will make things much easier. Does that guide apply to Ubuntu 6.10 though?

Thank you

---

### Post by vivek40 on 2010-03-27
I have not used 6.10 but I guess the command given earlier should be the same for installing LAMP. Just install LAMP and post back.. I will help you take it ahead

---

### Post by vivek40 on 2010-03-27
Ok I might not be on the system for long. so here are few steps which will help you get things done.. after you install LAMP:-
* Make a folder in your home folder called THECASE
 * Now go to the terminal and do the following exchanging USER for your user name and WEBSITE for whatever you want your web to be called
type the below Code in the terminal
sudo ln -s /home/USER/THECASE /var/www/WEBSITE
(this creates a symlink between the www/WEBSITE and THECASE, so although you save your files in THECASE , it can be accessed from WEBSITE)
 * Now go to your THECASE folder and create a file called hii.php
 * put in there some php code you would want to be displayed
 * Open your web browser and type [http://localhost/WEBSITE/hii.php](http://localhost/WEBSITE/hii.php)
 *you are done! 
I guess from there you can take it ahead!

---

### Post by louieb on 2010-03-27
The install lamp-server won't work - Support for v6.10 ended in April of 2008. 

Don't even think you can upgrade. - its so out of date. 

Easiest thing to do is get the latest version and do a fresh install.

---

### Post by Enderthexenocide on 2010-03-27
I did the command and I got no response. I tried installing php and apache2 by it's self and it said could not find package,

Thanks

---

### Post by Enderthexenocide on 2010-03-27
I have 9.10 download, I will try that, and message back.

Thanks

---

### Post by vivek40 on 2010-03-27
Visit this link:- gives you a step by step instruction for 6.10
[http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu610-edgy-lamp-server-installation-with-screenshots.html)

---

### Post by Enderthexenocide on 2010-03-27
Thats for Ubuntu server, I have ubuntu desktop. I am just going to install ubuntu 9.10 and message back when I am done, thank you!

---

### Post by aimwin on 2010-04-10
> **louieb said:**
> Welcome to the forum.

If your going to make your website public - you really don't want to use XAMPP - even the XAMAP documentation says its not secure and vulnerable to being hacked. 

To install a lamp server - 
```
sudo tasksel install lamp-server 
```

Lots of steps to get a web-server up and running - here's a start.
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Dear louieb
I would like to know how to check the security of LAMP, as XAMPP has got a function to check the security.

As the warning from  [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

"[COLOR="Magenta"]The default configuration[/COLOR] is not good from a securtiy point of view and it's not secure enough for a production environment - please don't use XAMPP in such environment.

Since LAMPP 0.9.5 [COLOR="Red"]you can make your XAMPP installation secure by calling »/opt/lampp/lampp security«.[/COLOR]
>>>>> and follow instruction from there >>>>>>>>>>

Now to me XAMPP is more secure than default LAMP installation in Ubuntu,
BECAUSE:
1. SINCE XAMPP has security check, and the XAMPP did not say after you enable security you cannot use as LIVE WEBSITE.
ONLY THE DEFAULT INSTALLATION that is prohibit for LIVE WEBSITE.

2. LAMP in default installation in UBUNTU,
   I cannot find the security check function as "/opt/lampp/lampp security" of XAMPP.

I suspect that I may be wrong.
Can some GURU on LAMP please verify this and please give us the security check command or function or program to do that in LAMP in UBUNTU.

And please comment further why LAMP-Ubuntu is more secure than ZAMPP-LAMP.

---

### Post by aimwin on 2010-04-10
> **Enderthexenocide said:**
> Hey,

I have ubuntu desktop and I downloaded XAMPP and put it on the desktop, How do I install that? and are there any guide to help me set up and get a website going on it? I currently run a website with a hosting company and I need to run it from home but I have over 200 people waiting on me so I need to get this done ASAP.

Thank you,

Enderthexenocide

How to install XAMPP and Zencart in UBUNTU 9.10 please see
[http://ubuntuforums.org/showthread.php?p=8496466#post8496466](http://ubuntuforums.org/showthread.php?p=8496466#post8496466)

---

### Post by cariboo on 2010-04-11
If you install the LAMP stack and mod_security, you will end up with a much more secure web site than if you use XAMPP. Have a look at [this]("http://www.debuntu.org/2006/08/13/86-secure-your-apache2-with-mod-security") howto. You will also learn more about how things work, as I understand it, XAMPP uses control panels, this really doesn't allow you to learn how the system works.

---

### Post by Mistah_Transistah on 2010-04-21
> **vivek40 said:**
> However here go the steps:-
1. Install LAMP.
2. You are supposed to put your site in var/www . However for that you might have to change some permission settings. Instead of that put your site anywhere in your profile and then create a symlink between var/www and your target folder which contains the site...

<i really however wont know how to install LAMP on 6.10.. but am sure someone will help you do that>
i found it easyer to just go into sites available directory and gedit the default txt where it says document root and then again where it says directory. but i suppose making virtual links would be better in the case of web hosting...

---

