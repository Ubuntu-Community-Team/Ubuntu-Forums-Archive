---
title: "which CMS"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2011-04-11
Hi guys
I've been recently been setting up a web server based around ubuntu 10.10
I'm hosting my site on it at the moment and will soon possibly be hosting my brothers site.
He has asked if I will be adding a CMS so the un-initiated like himself can edit the site content.
This seems lik a good idea to me as even I dont want to be going through code every time I want to change something.

I'd appreciate your oppinions on whatever CMSs you have used with ubuntu. How easy are they/ how featured, etc.

I dont have any experience with any CMS so I'm open to anything

---

### Post by Simian Man on 2011-04-11
I like Wordpress the best.  It doesn't have all the options that Joomla and Drupal have, but is *far* easier to setup and use.  It can produce some pretty nice looking sites too (more than just blogs).  I'd look at that one first and move on to the more complex ones only if Wordpress can't do all that you need it to.

---

### Post by bigmonmulgrew on 2011-04-11
I plan on adding an online shop in the future. Would wordpress be suitable for this

---

### Post by rbishop on 2011-04-11
I have worked with a few different CMS's over the years and here are my thoughts on the subject.

- PHP-Nuke - Great site with lots of addons etc.  Great for online business' and places where you will have lots of users.
- Wordpress - Great for a basic blog (can do more though).
- gpEasy - An extremely easy to use/edit CMS, very basic in design and doesn't require a db behind it.


These are my experiences over the years, hope it helps in some way.

---

### Post by bigmonmulgrew on 2011-04-11
> **rbishop said:**
> I have worked with a few different CMS's over the years and here are my thoughts on the subject.

- PHP-Nuke - Great site with lots of addons etc.  Great for online business' and places where you will have lots of users.
- Wordpress - Great for a basic blog (can do more though).
- gpEasy - An extremely easy to use/edit CMS, very basic in design and doesn't require a db behind it.


These are my experiences over the years, hope it helps in some way.

Cheers I appreciate the input

---

### Post by mcduck on 2011-04-11
I prefer MODx myself. Much less learning CMS-specific stuff than with most of the others, and highly compatible with web standards. You can pretty much design any kind of site you want and with just a few modifications convert it into a CMS-based site.

Definitely worth checking out if you haven't already spent couple of years learning how to tweak Joomla to do what you'd want it to do... ;)

---

### Post by leg on 2011-04-11
My favourite cms is Drupal but it can be difficult to learn. It has a plugin to turn it into an ecommerce site. If you want specifically an ecommerce site then there are systems available for that. Take a look at [opensourcecms]("http://php.opensourcecms.com/") where you test lots of them.

---

### Post by Blasphemist on 2011-04-11
I agree with leg that Drupal is my cms of choice. WordPress and Drupal are the industry leaders but from what you've described I'd recommend WordPress. Check out this showcase page.
[http://wordpress.org/showcase/](http://wordpress.org/showcase/)

---

### Post by drdos2006 on 2011-04-11
I had to recently ask the same as the OP, which should I use.

Eventually, after using CMSMadeSimple, SilverStripe, Concrete5, Drupal, MODxCMS etc, I finished up with Joomla. Much more powerful for my need and not as hard for a beginner as Drupal.

I also found by using some of the less powerful CMS products that I could not access the CMS from the Internet until I tweaked PHP and Apache. My ISP gives me a dynamic IP and I used DynDns.org to create a registration.

I found it easier to control Apache by using Webmin on my VM server. Webmin also allowed me to backup the MySql database easily and I was able to restore the Joomla database via the command line after deliberately removing and restoring Joomla in the /var/www server directory.
However, most of the tutorials for Jommla are for version 1.5 and not version 1.6, most of the templates are for version 1.6 and not version 1.5 and will not work.

Try the different CMS until you find one that suits you.

regards

---

### Post by bigmonmulgrew on 2011-04-12
> **drdos2006 said:**
> I had to recently ask the same as the OP, which should I use.

Eventually, after using CMSMadeSimple, SilverStripe, Concrete5, Drupal, MODxCMS etc, I finished up with Joomla. Much more powerful for my need and not as hard for a beginner as Drupal.

I also found by using some of the less powerful CMS products that I could not access the CMS from the Internet until I tweaked PHP and Apache. My ISP gives me a dynamic IP and I used DynDns.org to create a registration.

I found it easier to control Apache by using Webmin on my VM server. Webmin also allowed me to backup the MySql database easily and I was able to restore the Joomla database via the command line after deliberately removing and restoring Joomla in the /var/www server directory.
However, most of the tutorials for Jommla are for version 1.5 and not version 1.6, most of the templates are for version 1.6 and not version 1.5 and will not work.

Try the different CMS until you find one that suits you.

regards

Thats actually what I decided to do. I've gone with drupal because its the first that came up in google but I'll try a few and see what I like.

---

