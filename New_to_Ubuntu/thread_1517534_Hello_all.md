---
title: "Hello all"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by MerlinCoder on 2010-06-25
Hi everyone!

I am completely and utterly new to Linux, but I concider myself at least semi compitent with computers. Unfortunatly, all my experience comes from windows and I am finding Ubuntu sort of overwhealming.

I have installed the standard 32bit ubuntu desktop, but I would like to host my own apache/php/mysql set up. My free web hosting company keeps screwing me around and I'm getting fed up with it! I know I could set this up on windows without much difficulty, but I'm very keen to start using and enjoying Linux.

Is it possible to configure the standard installation to do this or would it be better to install the server edition?
I am sharing this computer with someone who is keen to learn, but really requires a graphical interface so she can web browse and play games. We are both finding our way around it nicely and really enjoying the simple way of downloading and installing new applications and games (super tux is freaking awesome btw :D), package management makes windows look so outdated!

Idealy I would like to be able to connect to it remotely via a windows box (I have actually managed to connect, once via putty on lan, however I find it very challenging as the only Unix command I know so far, debatably the most useful, is the man command).

I am really looking foward to getting to grips with terminal and learning things like Bash, but right now my absolute priority is getting the web server up and running, even if I have to interface with it through the GUI. 

One concern I have, is that my networks IP changes, the web design guru at my workplace has suggested using [http://www.dyndns.com/](http://www.dyndns.com/) as it will supposedly be able to track the IP changes, have any of you guys had any experience with it?

Wish me luck over the weekend, and sorry for such a generic post. If I run into anything specific I will post again in a more suitable place.

---

### Post by Bachstelze on 2010-06-25
> **MerlinCoder said:**
> 
Is it possible to configure the standard installation to do this

Yes.

> **MerlinCoder said:**
> or would it be better to install the server edition?

Probably not. If you are new, you will have a lot of trouble without a GUI.

> **MerlinCoder said:**
> I am really looking foward to getting to grips with terminal and learning things like Bash, but right now my absolute priority is getting the web server up and running, even if I have to interface with it through the GUI. 

You will probably have to use the command-line to setup Apache anyway. This is not terribly complicated, though, there are a lot of guides out ther, you'll mostly find yourself just copy-and-paste'ing commands, at least at first.

> **MerlinCoder said:**
> One concern I have, is that my networks IP changes,

Your local IP or your public IP? If it's your local IP, you should be able to configure it as static. If it's your public IP, dyndns works very well.

---

### Post by Paresh on 2010-06-25
For setting up LAMP (Lunux, Apache etc), [this site]("http://www.freelydifferent.com/self-hosting/lamp-for-linux-apache-mysql-php/") is a clear guide for new users.

You can set this up via terminal by cutting and pasting the commands, so it will work from windows via putty.

Let us know how you get on, someone will help you through any difficulties.

---

### Post by sica07 on 2010-06-25
Hi,
You should use XAMPP (XAMPP is an easy to install Apache distribution containing MySQL, PHP and Perl). Here you have a simple tutorial about how to install it in Ubuntu:
[http://ubuntuforums.org/showthread.php?t=223410]("http://ubuntuforums.org/showthread.php?t=223410")
I hope it helps ;)

---

### Post by MerlinCoder on 2010-06-25
Hey guys, thanks for the replys.

I would quite like to set up the server little parts at a time so it just contains what I need, I have never used perl before and, although I am very interested in learning it one day, I feel that I need to build up my PHP skills first.

The website is going to be a portfolio piece, I am really hoping to get a job in web development one day and I think this is a good logical first step :).

@Paresh, that guide looks very concise. Thanks! I don't really understand what each step does in terminal although a lot of them are pretty self explanatory like find and mkdir.

@sica07, thanks! that guide looks very easy, although I really don't think I am going to need the perl. I have seen the word XAMPP before many times though, so maybe if I can't set it up on my own it might be worth trying instead.

@Bachstelze, I was talking about my external IP, but my internal one might change too, I have never checked. If it does will it be an issue?

If I can get something up and running over the weekend I will be very happy!

---

### Post by Bachstelze on 2010-06-25
> **MerlinCoder said:**
> 
@Bachstelze, I was talking about my external IP, but my internal one might change too, I have never checked. If it does will it be an issue?

Yes. If you want to make it accessible from the outside, you will need to setup port forwarding in your router, and having a static local IP address will make your life much easier.

---

### Post by MerlinCoder on 2010-06-25
> **Bachstelze said:**
> Yes. If you want to make it accessible from the outside, you will need to setup port forwarding in your router, and having a static local IP address will make your life much easier.

Ahh yes of course it will! Okay thanks for the reminder, I will double check when I get back tonight.

---

### Post by Paresh on 2010-06-25
Use whichever guide you're comfortable with.

if you are unsure, or require further explanations, just ask here, we don't bite (much):)

---

### Post by MerlinCoder on 2010-06-26
[FONT=Arial]I am trying to install the web server now using tasksel install lamp-server.

Before I started, I set up putty, fowarded port 22 and 80, configured the firewall to allow access through those ports and set up a domain with dyndns.

First of all, just to clarify, a tasksel can install more than one package right? I get the feeling that there are going to be several task sels out there to make things a lot easier for common Linux set ups (like this: LAMP).

Well, installation went well, and I got the error that the guide said I would, however the pid are different numbers. That probably isn't an issue though right? I'm expecting p id will be based on systems rather than somethind standard.

The guide then goes on to say type this: [/FONT]
*sudo echo ServerName localhost >> /etc/apache2/apache2.conf*
[FONT=Arial]
[/FONT][FONT=Arial][SIZE=2]or in my case replacing localhost with the domain I registered at [/SIZE][/FONT][FONT=Arial]dynsys[/FONT].
However, I get the following error:

-bash: /etc/apache2/apache2.conf: Permission denied

Do I need to configure the firewall to let me write to files?

---

### Post by MerlinCoder on 2010-06-26
Hmm, I have tried completely disabling the fire wall but I still get the permission denied. :confused:

---

### Post by MerlinCoder on 2010-06-26
Yay fixed it!

This is how:

Enabled the root account
Logged in
Changed file permissions
Logged out
Disabled the root account
Tested on my pc, had a friend to test on his pc
Had a victory snort

Sorted!

---

### Post by Paresh on 2010-06-28
> **MerlinCoder said:**
> First of all, just to clarify, a tasksel can install more than one package right? I get the feeling that there are going to be several task sels out there to make things a lot easier for common Linux set ups (like this: LAMP).


tasksel will install all the packages needed to do the selected task, so for a LAMP server, it will install all the packages, you can also use tasksel to install other things, such as dns server etc.  if you just do ```
sudo tasksel
``` you can select which functions you want to install.

> **MerlinCoder said:**
> [FONT=Arial]
The guide then goes on to say type this: [/FONT]
*sudo echo ServerName localhost >> /etc/apache2/apache2.conf*
[FONT=Arial]
[/FONT][FONT=Arial][SIZE=2]or in my case replacing localhost with the domain I registered at [/SIZE][/FONT][FONT=Arial]dynsys[/FONT].
However, I get the following error:

-bash: /etc/apache2/apache2.conf: Permission denied

Do I need to configure the firewall to let me write to files?

You don't need to configure the firewall, but you do need admin rights.  the 'sudo' before the command should have given you that if you typed in the correct password, but I just tried it and got the same error.

Rather than enabling the root account, try ```
sudo su
```
this will put make you root temporarily and you do not need to add sudo for each command.

Note, you will be root for the duration. While this isn't necessarily bad, you can damage your system beyond repair if you do the wrong command, and since you are already 'root', you won't be asked for a password!

Do not forget to exit when you have finished.  You will need to exit twice (once to exit root, and once to exit the terminal)

---

### Post by MerlinCoder on 2010-06-28
Thanks for the advice.

After using sudo su did you manage to edit the file?

Something went massively wrong and corrupted all my apache config files, I have no idea what I did but I have reloaded ubuntu and have given it another go without enabling root access. 
So far so good, php, mysql and apache are all running locally, however, I still need to edit the files to allow my domain to link to my server.

I am hoping to get this all working by the evening, although theres no massive rush, I still have to finish off the website! (The only issue is my free host is giving me headaches again today which is massively slowing development :().

---

### Post by Paresh on 2010-06-28
I normally use ```
gksudo gedit /etc/apache2/apache2.conf
``` to edit, once I enter the password I'm able to edit normally.

I've never actually used the echo command on the apache folder until today.

By the way, gksudo is the gui equivalent of sudo, it does some extra stuff over sudo and should be used when doing admin operations with graphical applications.  You can use sudo with gui applications, but it is not the recommended way.

---

