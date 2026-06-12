---
title: "Want to switch to Ubuntu Server with WEB enabled, but..."
date: 2009-10-06
forum: New to Ubuntu
---

### Post by dan40 on 2009-10-06
Hi there,

I'm fairly new to Ubuntu, I have workstation installed in a VMWare virtual machine running under Vista as my base OS, and like it so far.  I can't say that I know a lot about it but I'm learning as I go along.

I figured this was as good a forum to post in for my problem.  I have a Windows 2003 server with IIS 6.0 and FrontPage server extensions that I want to convert over to Ubuntu server, and for the most part I think this would be easy, except that I love editing my web pages using either FrontPage or Expression Web 2.  There is no easy solution for editing existing web pages and sites and I would like to continue using FrontPage or Expression Web if I can.

Now, if there is such an animal as FrontPage server extensions for Linux that will allow me to edit my web pages from Vista running FrontPage, that would be great!  But then there's the idea of how I can port all of my web pages and sites from Windows 2003 server to Ubuntu server, and opening all of the ports, installing MySQL and PHP, managing file locations, etc., etc., etc.  I'm not a novice setting these up on Windows servers but might run into some difficulty with Linux.

If anyone has had a similar experience converting their Windows server to Linux, please advise, I'll need all the help I can get.

Thanks!
Dan

---

### Post by yknivag on 2009-10-06
You can still use FrontPage to edit your pages without using the "extentions".  That will also mean your pages work in browsers other than MSIE too.

---

### Post by dan40 on 2009-10-06
Will I be able to set up multiple web domains on the same server like I can with IIS?

---

### Post by yknivag on 2009-10-06
Yes.  Apache is the grand-daddy of all web server software.  It's been around a lot longer than IIS and has a lot more features!

---

### Post by dan40 on 2009-10-06
This is almost like buying a new car - you really can't part with your existing car, but the one you're looking at is bright, shiny, new and smells good on the inside.  :)

One really has to make a firm commitment to switch, but if you have trouble deciding you have to wonder if it really is for you or not.  Hence my dilemma... I'm sure Ubuntu would work fine for me, but I already know that Windows 2003 Server with IIS is already working for me and it's going to be difficult to make a commitment.

What I'm planning is totally do-able, correct?  Is there a lot of compiling or can I just use the installer to put MySQL and PHP on using the opt-get command?

---

### Post by louieb on 2009-10-06
installing in Ubuntu is as easy as ```
sudo tasksel install lamp-server
``` 

For administration you might want to look at things like webmin and phpmyadmin.

---

### Post by dan40 on 2009-10-06
Louieb: Thanks, presumably this command will install all the server components necessary to run a web server with PHP and MySQL?  You didn't specify what this command does, but using my powers of deduction, it was elementary.  :)

I know how to use phpmyadmin with my current set up so that won't be a problem.

If I make backups of my existing databases, can I store them on my Windows workstation and retrieve them back into Linux when I'm re-importing them into my web server?

---

