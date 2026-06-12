---
title: "Host sites at home"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by exeQutor on 2008-11-23
Hi,

What would it take to host my sites on my home PC, which is running in Ubuntu?

---

### Post by nickdbliss on 2008-11-23
hi exeQutor,
Well to host ur website at home you will need to turn ur pc into a webserver. For that you ll need to install apache2 webserver, Php if you need php and Mysql for database. Furthermore you will need to have a static ip address or you can use dynamic one but in that case procedure is slightly different. 

For installing Apache, PHP and MYsql or LAMP you can check this website:
[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100)

There are numerous tutorials on this. But read your ISP TOS as some ISPs don't allow residential web servers.

---

### Post by exeQutor on 2008-11-23
Hi nickdbliss,

Thanks for the reply.

I already have XAMPP installed. What I am looking for actually is a step-by-step tutorial on how to make my Ubuntu powered PC to host my personal site.

As I just have switched from Windows, I really am quite idea-less on what to do and where to go first..

---

### Post by nickdbliss on 2008-11-23
> **exeQutor said:**
> Hi nickdbliss,

Thanks for the reply.

I already have XAMPP installed. What I am looking for actually is a step-by-step tutorial on how to make my Ubuntu powered PC to host my personal site.

As I just have switched from Windows, I really am quite idea-less on what to do and where to go first..

Yeah that is obvious if u r coming from windows. 
So you might be knowing u need to put content in www folder or documentroot directory and also has to start the server. 

STEP1: To do so go to the terminal and type
code: /opt/lampp/lampp start
for stopping use stop instead of start. same follows for restart.

Once ur server is running and u have some content in /opt/lampp/htdocs/ try checking it using ur web browser. In the address bar type: [http://localhost](http://localhost) . If it shows the content it is working else some problem is there.

STEP:2 Now for outside world to access ur server, u need to assign a domain name to ur server. You can use dyndns.com to create an account. But first make sure u completed the first step.

---

