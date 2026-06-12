---
title: "i need advice to set up a simple network"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by benner on 2007-01-28
I am a teacher with 3 machines humming along nicely with edubuntu on them.  the machine on my desk is currently running windows but i have been given the go ahead to wipe it, use it as a server and set up a little network in the class.  we have a couple more computers with deaad hard disks that i will try to run as thin clients.  if all goes well, we will begin to expand into more open-source territory.  the plan is to eventually have half of the machines in the school running linux.  the problem is, i am the go-to guy and i ahve never done anything like this before.  i have been running linux at home and in my class for 6 months and am comfortable with desktop editions, i know a handful of command line prompts to do some basic trouble shooting.  that's it.  so, the questions...

(a) am i over my head here

(b) where should i start learning the what's, where's and how's (for dummies and noobs)

I assume that i need to download the server edition and i'm pretty sure that it has no gui.  so,

(c) is ubuntu the easiest way to go for this?

---

### Post by zalberico on 2007-01-28
That sounds great, I think you can do it.
If you go trying to find information and help through the internet you'll probably get frusturated because of it being spread out and a pain to get the information you need.  I would suggest a book (ironically).  The O'reilly guides are good ones to look at.  There are also some that I believe are distro specific.  This should help with making the search for information easier.  As far as which distro would be best, I have used many and been frusturated by many (Fedora brought me into a murderous rage running on PPC) and ubuntu seems to be the easiest to do anything on.  Good luck! ubuntu does also have commercial support you may want to look into as well.
zman -only one measly cup of ubuntu

---

### Post by bward1 on 2007-01-28
First I would like to applaud your efforts to include linux at school.  I attend a science and tech high school and we have two labs which use linux, and that is where I was introduced to it.  I have never done anything with the linux terminal server project, but it is used at my school for one of the labs.  Basically I know it can be done, and I have heard that it isn't too difficult, but I haven't any experience in the field.  Here is a link that may help [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

If you are just going to have a couple of computers in one classroom with only a couple of classes, than this is probably something that wouldn't be entirely too difficult.  I would use NFS to share your files between the different computers (not if everyone is running a thin client) and that is easy to setup and use.  [http://www.ubuntuforums.org/showthread.php?t=249889](http://www.ubuntuforums.org/showthread.php?t=249889)

Expanding to the rest of the school is something that would take a lot of experience and knowledge of networking and server applications.  In the systems lab (linux lab) at my school we have an image server that holds the image for all of the other computers (what applications and configurations all of the computers should have).  Then they use kerberos, which I frankly don't know what it does, except for security stuff.  AFS is used to allow all users to access their files regardless of which computer they are on.  LDAP is used for the user database.  The lab is student run (which is pretty cool, but dont think that just because high school students can do it that it is easy) and I am friends with some of the administrators, so I hear what they are doing but dont know enough to be able to tell you how to do it.  Ohh and it also interfaces with the windows servers for the rest of the school so we can access our files from either linux or windows with the same username and password.  That is just magic as far as I am concerned.  In conclusion, spreading to the rest of the school is probably well over your head, and mine as well.

I would think that ubuntu would be a good option.  Most of the computers in our lab use debian, which is a sister distro to ubuntu, and actually one of the admins was thinking at one point of switching to ubuntu.  If you have experience with ubuntu I would say go with it.

You can do everything in the desktop edition you can do with the server edition.  It is just a matter of which packages come preinstalled and which ones you have to install yourself.  The desktop cd comes with a desktop environment but doesn't come with things like a web server.  You can install them if you want, but you aren't limited to just desktop software (unlike windows).  Likewise the server edition comes with a webserver and other servery applications but doesn't come with a graphical environment.  You can install any graphical environment you want from there, but it doesn't come with it.

I'm sure that everyone in this forum would be more than willing to help you to include linux in the educational experience for you students.  Hopefully I have provided at least a basic idea of what types of applications you might want to use.

---

### Post by benner on 2007-01-29
thanks for taking the time.  i just finished downloading 6.10 and am reading the how to.  i'm sure you will see more questions from me in the near future.  cheers!

here i go...

---

### Post by dmizer on 2007-01-29
don't be afraid of the text only server.  more often than not, you don't even need to look at the thing.  and there are some fantastic tools to allow you a point and click web based interface for complete server configuration (no gui) ... called webmin.

i would highly suggest sticking with dapper (verson 6.06) for a server only configuration.  it's support is long from over, and it's far more stable for such endeavors. also, because it's a more mature distribution, there's more documentation available for it.

there's a great list of server howto's listed here: [http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

---

### Post by kosmic on 2007-01-29
Also you can read more about LTSP here -> [http://wiki.ltsp.org/twiki/bin/view/Ltsp/Documentation](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Documentation)

I will advise you it can make you go nuts tryng to install LTSP, you need to know how networks works before you try to expand your LTSP beyond your class room.

---

### Post by aruscito on 2007-01-29
I need some help. I received the 6.06 cd so I can use it in my classroom.  I installed it on an Pentium 3 PC with 256 RAM.  The desktop runs fine and I can connect the school network, but I cannot access the ubuntu system from my windows xp pc on my desk.  Pings ok, but cannot do much else.

I want to be able to access the ubuntu machine so I can have my students set up their web pages on it, on for internal access while in my class.  It needs to be a simple server.  Any suggestions, did I order the wrong CD?

Andy

---

### Post by punx45 on 2007-01-29
as for the gui/no gui discusion - there is no rule that says a server can't have a gui! my box toaster is a PIII 'server' (http, nfs, ssh) and it was gui based until i went headless with it.
one caveat is that i would suggest not using gnome if the server is older hardware.   try xfce (xubuntu, or just install xfce with synaptic and then choose it as the session at the login screen.) 

also, try to use the terminal as much as you can, and just use the gui when you need to.

---

### Post by kosmic on 2007-01-29
> **aruscito said:**
> I need some help. I received the 6.06 cd so I can use it in my classroom.  I installed it on an Pentium 3 PC with 256 RAM.  The desktop runs fine and I can connect the school network, but I cannot access the ubuntu system from my windows xp pc on my desk.  Pings ok, but cannot do much else.

I want to be able to access the ubuntu machine so I can have my students set up their web pages on it, on for internal access while in my class.  It needs to be a simple server.  Any suggestions, did I order the wrong CD?

Andy

For your Windows Workstations share files with your Linux box you need to install SAMBA and configure it. If you need more help with Samba just search the forum for SAMBA or File sharing

---

### Post by dmizer on 2007-01-29
> **aruscito said:**
> I need some help. I received the 6.06 cd so I can use it in my classroom.  I installed it on an Pentium 3 PC with 256 RAM.  The desktop runs fine and I can connect the school network, but I cannot access the ubuntu system from my windows xp pc on my desk.  Pings ok, but cannot do much else.

I want to be able to access the ubuntu machine so I can have my students set up their web pages on it, on for internal access while in my class.  It needs to be a simple server.  Any suggestions, did I order the wrong CD?

Andy

you'll need to install:
apache2
php
mysql
howto's are listed at the website in my post above.

you'll also likely need an ftp server set up so they can upload their files.  for that, use the third link in my sig.  an ftp server is more complex, but necessary unless you plan to move (by hand) every student's file from the samba shared directory to the web server directory.

most likely you received the ubuntu (gnome desktop) cd.  which is too much for your computer if you're just going to be using it as a server.  there may be an option to install a LAMP server in the menu, but i'm not sure (been too long now)

---

### Post by punx45 on 2007-01-29
> **dmizer said:**
> you'll also likely need an ftp server set up so they can upload their files.  for that, use the third link in my sig.  an ftp server is more complex, but necessary unless you plan to move (by hand) every student's file from the samba shared directory to the web server directory.

SFTP would also work.   and i found openSSH fairly easy to set up.   also, it may not be a great example for the kids as far as secure use but the http document root could be shared over samba/nfs and they could save the files there as they work on them.

ED: oops. that was a reply to a separate question in this thread.. well. same goes to everyone :-P

---

### Post by koenn on 2007-01-30
> **benner said:**
> I am a teacher with 3 machines humming along nicely with edubuntu on them.  
...
we have a couple more computers with deaad hard disks that i will try to run as thin clients.

There's one thing I don't understand here. 
You already have 3 edubuntu's running. You're thinking about thin clients. All this is in a classroom setting. 
Your description has "Edubuntu" written al over it : Edubuntu ***is*** designed as a server for thin clients. Any one of the 3 Edubuntu you already have, or your computer if you install Edubuntu on it, could be the serving a desktop + all edubuntu apps to your diskless clients. 
So unless you have some other sort of server in mind I thing you should install Edubuntu (in Termminal Server Mode; it can also be setup as a desktop system).
 Did I miss something here (I only glanced over the replies in this thread, did not read all of them fully) ?

And no, I wouldn't say you're in over your head. There might be a couple of hurdles to take, but overall, it-s very do-able.

---

