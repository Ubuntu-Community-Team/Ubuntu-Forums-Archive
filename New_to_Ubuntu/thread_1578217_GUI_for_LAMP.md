---
title: "GUI for LAMP?"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by jjei on 2010-09-20
I'm new with Ubuntu. I am doing web development and I need to have a local environment for developing and testing websites on my pc. The sites don't have to be accessed anywhere else than my local environment.

I have used MAMP to do this with Mac. Now I have ubuntu installed and I wonder if there is any GUI for these purposes. Or do I just install apache2, php and mysql? I am mostly working on drupal but I am not aware if there are any drupal spesific tools for ubuntu.

Any advices?

I'm running the latest stable version of ubuntu.

Thanks in advance!

---

### Post by Cenotaph on 2010-09-20
well, installing a LAMP server is ubuntu is very easy, all you need is a single command:

sudo tasksel install lamp-server

im not familiar with drupal, but maybe you should check this out:

[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

---

### Post by gandaran on 2010-09-20
> The sites don't have to be accessed anywhere else than my local environment
xampp is easy and would fit exactly your needs.
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by jjei on 2010-10-25
I've been using xampp, and it seems ok. I found also [http://www.webmin.com/](http://www.webmin.com/). 
Any opinions which one to use?

---

### Post by jbrice on 2010-10-25
I do some PHP development and have found the XAMPP option to be best. The main reason is the lack of control over the version of PHP that you get when using the distro. lamp-server install.

By choosing which version of XAMPP you use, it's possible choose an earlier version of PHP - perversely that's quite important to ensure things work on 3rd-party servers which are often several versions behind the bleeding edge. It's also possible to install several different versions of XAMPP so that you are able test against latest as well as older versions of PHP - v. useful.

(When oh when is someone going to produce an XAMPP equivalent as good as WAMP??????)

---

