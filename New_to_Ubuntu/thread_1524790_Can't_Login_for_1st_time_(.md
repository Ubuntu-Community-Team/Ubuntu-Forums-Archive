---
title: "Can't Login for 1st time :("
date: 2010-07-05
forum: New to Ubuntu
---

### Post by mel_the_snowbird on 2010-07-05
Hi:
 
Enviro: Ubuntu Server 10.04 software on a Dell Laptop.
 
Problem:
 
I finally got 10.04 installed on my Dell laptop from a USB this afternoon. The install 'seemed' to go O.K.
 
I've *never* used Linux before (I've just arrived from years of working Windows XP Pro and from its Command Prompt -- and before that MS-DOS)
 
When I booted my laptop for the 1st time it said:
 
syntel login: (I entered 'Mel Smith' here)
password: (I entered what I 'thought' was my password)
 
But it keeps saying:
 
Login incorrect
syntel login:
 
(I tried every variation I could think of -- to no avail)
 
Well, I guess I've forgotten the login name *and* the password. But I really don't want *any* login or password, I just want the machine to boot without 'logging in', and without entering a password. Its my own machine in my own home/office. Ultimately I want it to host an Apache Server which I now have on a Win XP Pro (sp3) machine in my office.
 
But, the system won't let me get in.
 
Do I have to re-install *again* ?
 
(after all these years of work, I'm back in kindergarten again :(( )
 
Thanks for any help offered.
 
-Mel Smith

---

### Post by jtarin on 2010-07-05
Do you or did you belong to a group of this name "syntel"?
This is not a proper login prompt. You should see something similar to [[COLOR="Blue"]this[/COLOR]]("http://ubuntulinux.co.in/blog/ubuntu/ubuntu-10-04-lucid-installation-step-by-step-screenshots/") during the install and completion to login screen. Here in the example the users name is "ubuntulinux"

---

### Post by askreet on 2010-07-05
Hey there, welcome to the forums.

My first question is: why are you using Ubuntu Server?  You mention having never used Linux before and this is on a Laptop -- I would assume you'd want some sort of GUI...

But let's assume you knew it would not have a GUI and prefer that (which I can relate to!):

You should have set up your initial username during the installation prompts, it would not be "Mel Smith" as spaces are not allowed in the username field on UNIX systems (to my knowledge).

There are many ways to break into a Linux box from the console and reset a users password, but at this point I'd recommend you reconsider using Ubuntu Server.  Even though you want to run an Apache web server, you probably want Ubuntu Desktop.  During the installation screens for Ubuntu Desktop you will enter your full name, and the username field will auto populate with your first name (you can change this if you like).

Ubuntu Desktop can be configured to auto-login into a graphical environment upon bootup.  Apache Web Server can be configured (and is configured by default once installed) to start with the system as well.

I hope you find this helpful... :)

- Kyle

---

### Post by jtarin on 2010-07-05
The server thing went right by me.....I second the recommendation above tnis post by "asktreet".

---

### Post by mel_the_snowbird on 2010-07-05
> **jtarin said:**
> Do you or did you belong to a group of this name "syntel"?
This is not a proper login prompt. You should see something similar to [[COLOR=blue]this[/COLOR]]("http://ubuntulinux.co.in/blog/ubuntu/ubuntu-10-04-lucid-installation-step-by-step-screenshots/") during the install and completion to login screen. Here in the example the users name is "ubuntulinux"
 
I don't have a 'group' called syntel.  That is the name of my old defunct company (Syntel Data Systems Ltd.) 
 
I remember inputting the name 'Syntel' sometime during the long, and arduous installation from the USB stick.  I also remember putting in 'Mel Smith' at one stage, and also remeber typing in my password also at one stage (e.g., 'xxxxxxxx')
 
   The login prompt I posted was the *exact* login prompt I received.
 
 
-Mel

---

### Post by mel_the_snowbird on 2010-07-05
> **askreet said:**
> Hey there, welcome to the forums.
 
My first question is: why are you using Ubuntu Server? You mention having never used Linux before and this is on a Laptop -- I would assume you'd want some sort of GUI...
 
   I don't want any GUI -- I have Win XP Pro on two other machines in my office.  I want to learn Linux as a future base for my Apache Server.
 
 
But let's assume you knew it would not have a GUI and prefer that (which I can relate to!):
 
   Yes !
 
 
You should have set up your initial username during the installation prompts, it would not be "Mel Smith" as spaces are not allowed in the username field on UNIX systems (to my knowledge).
 
   I also tried melsmith and MELSMITH 
 
There are many ways to break into a Linux box from the console and reset a users password, but at this point I'd recommend you reconsider using Ubuntu Server.
 
   That is what I installed (I think) the Ubuntu Server 10.04
 
 Even though you want to run an Apache web server, you probably want Ubuntu Desktop. During the installation screens for Ubuntu Desktop you will enter your full name, and the username field will auto populate with your first name (you can change this if you like).
 
   I don't understand the previous paragraph ??
 
Ubuntu Desktop can be configured to auto-login into a graphical environment upon bootup. Apache Web Server can be configured (and is configured by default once installed) to start with the system as well.
 
   So, how do I 'auto-login' when I can't even get into Ubuntu in the 1st place ??
 
 
I hope you find this helpful... :)
 
- Kyle
 
Thanks Kyle ! 
 
-Mel

---

### Post by askreet on 2010-07-05
Okay so, you do in fact want to use Ubuntu Server.

I don't know of a way (though there probably is one) to auto login as a user on the command line.  Besides, once you get things going you may want to remotely administer the box via PuTTY or the like.  That will definitely require a password! :)

I just verified that you can't, in fact, use a space in an Ubuntu username.  Have you tried logging in as 'mel' (all lowercase)?  

What I tried to say (poorly) was that Ubuntu installer asks you for your 'Full Name', where you might enter 'Mel Smith' then converts your first name to an all-lowercase username.  In Linux-land everything is case sensitive so, as a rule, we try to keep things simple and lower-case!

---

### Post by sandyd on 2010-07-05
> **askreet said:**
> Hey there, welcome to the forums.

My first question is: why are you using Ubuntu Server?  You mention having never used Linux before and this is on a Laptop -- I would assume you'd want some sort of GUI...

But let's assume you knew it would not have a GUI and prefer that (which I can relate to!):

You should have set up your initial username during the installation prompts, it would not be "Mel Smith" as spaces are not allowed in the username field on UNIX systems (to my knowledge).

There are many ways to break into a Linux box from the console and reset a users password, but at this point I'd recommend you reconsider using Ubuntu Server.  Even though you want to run an Apache web server, you probably want Ubuntu Desktop.  During the installation screens for Ubuntu Desktop you will enter your full name, and the username field will auto populate with your first name (you can change this if you like).

Ubuntu Desktop can be configured to auto-login into a graphical environment upon bootup.  Apache Web Server can be configured (and is configured by default once installed) to start with the system as well.

I hope you find this helpful... :)

- Kyle
hmm lets see...
a) all linux usernames don't have spaces
b) passwords are CaSe Sensitive.

try a) first.
type in "mel" as the username

damn. you guys beat me to it.

---

### Post by mel_the_snowbird on 2010-07-05
> **carlee said:**
> hmm lets see...
a) all linux usernames don't have spaces
b) passwords are CaSe Sensitive.
 
try a) first.
type in "mel" as the username
 
damn. you guys beat me to it.
 
Hi Carlee and others:
 
 
   I got in !!!
 
   I typed in Mel MELSMITH, etc, etc. Finally, I typed in 'mel' and my password, and I got in !!!
 
   So now I come here to tell you folks about my thrill of getting in, and lo and behold Carlee had the answer for me if I had looked earlier this evening !!
 
   I guess Ubuntu just took the first portion of my user name (i.e., 'Mel' of Mel Smith) then lowercased it !
 
   *Now* my user prompt is:   [EMAIL="'mel@syntel"]'mel@syntel[/EMAIL]: ~$_'
 
   What is *that* ???    (I'm used to C:\>  in the Windows Command Prompt)
 
   Then I tried entering:  'shutdown -h now'
 
   and it wouldn't let me. Said I had to be 'Root'
 
   OTOH, it also said to try:  sudo shutdown -h now
 
   and *that* worked !
 
   (But I *really* want to be root, and not bother with logging in or passwords.)
 
Thanks Carlee and y'all -- I'm going to start learning now ...
 
-Mel Smith

---

### Post by mel_the_snowbird on 2010-07-05
Askreet:
 
   I didn't notice your message till now, only Carlee's
 
Please see my response to her, and Thank You for finding my error !
 
btw, I'm a computer programmer using a derivative of C++ (called xHarbour).  I use this language to build the CGI portion of my website(s).  I'll be (slowly) moving my Apache Server software and ancillary S/W to Ubuntu over the next several months. I come with much Windows Command Prompt experience, but *no* Linux whatsoever -- except my initiation under fire this afternoon and evening.
 
Thanks again,
 
-Mel Smith
 
-Mel

---

