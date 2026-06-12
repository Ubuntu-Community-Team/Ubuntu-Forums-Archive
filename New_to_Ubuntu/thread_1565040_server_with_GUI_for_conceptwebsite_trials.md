---
title: "server with GUI for concept/website trials"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Sapphirrix on 2010-08-31
[COLOR=DimGray]Hey all, 

I've been working with a media group that we started back a few years, and recently we've discussed starting up a website for ourselves. 
someone suggested we 'dive into the deep end' and try to get a bunch of different parts to the site (such as a blog, forums, a few information pages, email etc.) 
I called them up on this and said it was likely that we'd have problems building it

so after bouncing a few ideas off each other about this someone suggested we put together a server on a LAN to trial run some things... 

being the person with the most free time (and free computers) it fell on me to get something going[/COLOR]

[COLOR=Black]so, I grabbed a copy of Ubuntu 9.04 Server[/COLOR] out of my Brother's collection of Linux distros and got around to installing it... it didn't take me long to flail uselessly at the keyboard wondering how to use it.

with the state of my net connection being low bandwidth shared between the family I can't really download much however I was wondering if the community here has any ideas for a distro with a GUI appropriate for hosting a web server full of aforementioned bits n bobs, or if _there is_/_it's worth getting_ a GUI for my current setup...


system stats for the box come out to something like
~2 GHz P4 
2GB RAM
ATI Radeon 9550 256MB Graphics card
On-board sound
On-board wired network (100 base)
D-link Wireless G network card)
~100GB worth of hard-drive space (2*40GB + 1*20GB)
CD/DVD drive 


Thanks for reading /and helping
Sapph[FONT=Arial][/FONT]

---

### Post by anewguy on 2010-08-31
I'm not a server guy, but I do know you can install the desktop GUI's to ubuntu server.  The server installation just doesn't include them.

Dave

---

### Post by kmsalex on 2010-08-31
I *think* that when you say gui for the server you mean the interface that the user accessing your site will see, in which case the most used is [wordpress]("http://wordpress.org/"). If your talking about puting a gui on your side of the server so you can work and configure it then you should just do a stander Ubuntu desktop install. 

PS: why did you use 9.04? especially for a server instead of 10.04 *LTS*.

---

### Post by silverglade00 on 2010-08-31
You might want to install webmin on the server. It will let you do most things through a web interface.

---

### Post by uRock on 2010-08-31
Install the Ubuntu Server image, then in the cli run ```
sudo apt-get install ubuntu-desktop
``` which will give you the full ubuntu GUI.

---

### Post by bodhi.zazen on 2010-08-31
Gnome adds very little to a server as most tasks are either starting stopping services, installing software, or editing config files.

If you want a gui, use a web interface. There are several, webmin, phpmyadmin ...

See also :

[http://www.debianhelp.co.uk/apacheweb.htm](http://www.debianhelp.co.uk/apacheweb.htm)

---

### Post by Sapphirrix on 2010-08-31
thanks, I'll give webmin or similar a go
and see what happens from there

---

