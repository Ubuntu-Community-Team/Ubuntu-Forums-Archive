---
title: "New To Creating Websites"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by wewrotethis on 2011-03-31
Hello,

I am new to Linux, Ubuntu and to creating websites.  I have a hosting company that supports Linux and a mysql database but I still am struggling with where to begin.

There is so much information out there that it is a little overwhelming for the novice, I figured I would join the forum and ask for some help.  I apologize in advance if my questions are remedial or overwhelming themselves.


What programs do I need and how to find them?  (Do I need the Whole LAMP Stack?)

1  If I'm hosting through a third party, do I still need to have Apache 2,0 on my machine?  If so, what exactly does Apache do?


2. To create a website through using Ubuntu and it's programs, do I just need an HTML editor and a PHP program? 


3.  If my hosting company supports mysql, do I still need it on my machine to have the ability to run queries or is that typically done through the hosting company's server?


What is the sequence of creating a website?


1.  Again, with the amount of information out there it is difficult to find a simple explanation of the website building process.

For example, I would love to see a simple overview:  First you build your on-page content in HTML then you use your PHP program to organize and bring this content to life (not sure if that is true but would love that type of simple answer).


How should I learn?

I could ask hundreds of questions here but I think the most important thing to gain is some direction on the best places to gain this type of knowledge for the beginner.  I have seen some great info on the W3 school but would love some advice on resources for building websites using Ubuntu.

Thank you all for your time and any support you can offer!

---

### Post by bodhi.zazen on 2011-04-01
You would run LAMP on your hosting company's server.

You can also run LAMP locally for testing your pages, but you do not need to, you can view the html directly with firefox.

As html and php files are text files you can write them with any text editor. Personally I use bluefish and vim, you could use gedit as well.

If you want to start with a graphical application I suggest kompozer, although take care the code is sloppy.

Start with html (w3w has several tutorials). From there learn css.

You would then add mysql / php / javascript as needed, although for basic web pages you do not need any of these.

---

### Post by Blasphemist on 2011-04-01
I've done a lot of research and learning to prepare to do what you are about to begin. I can explain some things. As long as you choose a normal host, they will provide the lamp stack and the only thing you need on your pc is the browser. They will likely give you a Cpanel access to install the content management system. You can access phpMySQL via your browser to do any database access you need outside of the cms. 

Your biggest choice is the cms. Have you chosen one and learned about how to use it? What purpose do you have for the site? That will guide you on the cms choice. You can usually see tutorials on the host site on installing the cms prior to doing it. I recommend you look at the tutorials available from your host and ideally prior to purchase test their tech support by asking any questions you have.

Most host provide one click installs of the major cms options and your real challenge will be using that cms to create the site. That is where your learning will be done. 

I like Drupal for some site types and WordPress for blogs and more simple sites. 
You can experiment with Drupal free at
[http://www.drupalgardens.com/](http://www.drupalgardens.com/)
The free Wordpress site is
[http://wordpress.com/](http://wordpress.com/)
The Drupal site itself has a ton, and I mean that, of info if you decide to go that way. 
[http://drupal.org/](http://drupal.org/)

The reason to install a lamp stack and Drupal or another cms locally, on your pc, is to use it as a staging site or learning site. I have done that and installed Drupal. I use it to experiment and learn. You can create a site locally and then just use ftp to upload it to the host and go live. This does take a lot of planning.

Linux is the most common hosting platform but there are some that use Windows. I'd choose one that provides Linux and that can be Ubuntu but it really won't matter which server distribution they use.

Apache is the most common open source web server. You'll need to know certain configuration methods depending your choice of cms but your host will largely control Apache.

MySQL or PostgreSQL are the most common database servers for hosts. MySQL is the most common but that may change as people trust Oracle less (they now own MySQL). It shouldn't make much of any difference to you.

Php is a scripting language that is HTML embedded, scripts can be put into HTML to dynamically create pages. It is a part of the stack to be available to the CMS and/or the developer. 

Give me more of what your plans are and I can direct you to more information.

---

### Post by picman1 on 2011-04-01
Hello wewrotethis,

I too am new to Linux so I will not begin to offer advice there but regarding websites, you can certainly use graphical interfaces but if you are looking to learn the code beneath the graphical user interface than I highly recommend The Peachpit Visual Quickstart guide.

These guides are superb at introducing you to computer related subjects and programs
from the ground up. The most recent website book I have of theirs is...

"HTML for the World Wide Web" (5th edition) w/XHTML and CSS by Elizabeth Castro.
   *** the inclusion of CSS is important.

I first learned HTML many years ago with the same book in it's first edition and the same author. She is fantastic and explains everything clearly and thoroughly. There are so many books out there om website creation but if you are looking to do, or even just maintain and troubleshoot your website code, this book is excellent for starters. Good Luck.

Jim

---

