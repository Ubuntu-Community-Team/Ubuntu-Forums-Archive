---
title: "Ubuntu Feisty - Bluetooth problems - sending files and Remuco"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Ciddan on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718](https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718](https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello all!

I'm somewhat of a linux beginner (I've been testing out Ubuntu since 5.10 but never really stuck with it) but I can generally solve my problems by searching this forum or other how-to pages. Theese two I cannot solve though.

I bought myself a bluetooth dongle after seeing a really slick amaroK remote control app called [[COLOR="Blue"]Remuco[/COLOR]]("http://remuco.sourceforge.net/index.php/Remuco"). So, I went home to get it all installed - up and running. That would not be so easy - it turns out. First of all, the bluetooth is quite flaky. I followed [[COLOR="Blue"]this[/COLOR]]("http://news.softpedia.com/news/Transfer-Files-With-Bluetooth-on-Ubuntu-47565.shtml") guide to get it started. After some dabbling around (editing hcid.conf) and disabling the passkey I could get linux to find my device, which is a Sony Ericsson k750i phone. I can also send files FROM the phone TO the computer. I cannot however send files from linux to the phone. Using the gnome-obex-send GUI - it finds no devices, however hcitool inq and hcitool scan both find my phone. How can I get this working?

Now for the second problem - I can't get the Remuco server-side client working. It failes to load due to no pydcop module being found. I have installed python-dcop, which is the right package for debian systems - but it still won't load. Do I need to modprobe or something?

I hope someone can help me with this! I really love this release of Ubuntu and I just want it to work like I want it to this time :) 

P.S I found a related bug in Launchpad - is there a work-around? D.S

---

### Post by Ciddan on 2007-04-26
Bump... No-one? I tried the work-arounds on the Launchpad bug page but that didn't help me with sending files via BT from comp to the mobile...

---

### Post by CRIKEY on 2007-04-28
i have gotten the files onto my phone but i also share the second part of your problem i have tried all that is in my knowledge (very little) to fix it hopefully someone who knows more about this will see this topic

---

### Post by Tazy on 2007-04-28
I came across your request as I am struggling with a similar problem. My goal is quite similar but with a slightly different approach. I might rethink it after reading the pointers you have given.
I am trying to use an ubuntu (Feisty) machine with a USB Bluetooth dongle as a bluetooth access point for my Palm Tugnsten (E2) PDA which has bluetooth but no wifi. My hope is to run slimserver (a music server with web-based interface) so that I can use a simple browser (in my PDA) to control the songs. 
I tried repeating steps identified in this thread but I did not succeed. YMMV
[http://ubuntuforums.org/archive/index.php/t-10500.html](http://ubuntuforums.org/archive/index.php/t-10500.html)

I am able to scan and associate the two devices. But when I attempt 'connect' in my PDA, the connection fails (similar to what's described in above post). I think I'm stuck at properly setting up the ppp side of thinsg. I shall try something like Remuco and post back my results as I have given up on the ppp way.

---

### Post by CRIKEY on 2007-04-28
i can't offer either of you any advice as i use kubuntu and bluetooth worked out of the box for me with a series 40 phone

---

### Post by CRIKEY on 2007-04-28
EDIT: i have created a small archive with just the files necessary to get Remuco Server 0.4.3 working so you don't have to follow all the steps outlines below (attached)

i have managed to solve the second part of the question the one with the remuco server not starting because of pydcop module from what i can see (and please remember i am really new to this so bare with me if I'm wrong) the remuco servers uses python 2.4 but the package it depends on is made for python 2.5 so by going here [http://packages.ubuntulinux.org/cgi-bin/search_contents.pl?searchmode=filelist&word=python-dcop&version=feisty&arch=i386]("http://packages.ubuntulinux.org/cgi-bin/search_contents.pl?searchmode=filelist&word=python-dcop&version=feisty&arch=i386") 

i managed to determine the missing files which i found were

usr/share/python-support/python-dcop/pcop.la
usr/share/python-support/python-dcop/pydcop.py
usr/lib/python-support/python-dcop/python2.5/pcop.so

so i simply copied all these files to the /usr/lib/python2.4 directory and it worked although it gives a runtime warning and says the python api version is 1012 and the module version is 1013 but it still works

so finally i downloaded the edgy .deb of python-dcop from here [http://packages.ubuntulinux.org/edgy/python/python-dcop]("http://packages.ubuntulinux.org/edgy/python/python-dcop")

and then i extracted it with ark (kde archiving tool) and found the three modules mentioned above i then copied them to their directory as seen in the edgy .deb which had them all going into usr/lib/python2.4/site-packages/ 

and remuco works perfectly now i hope that helps you

---

### Post by masala on 2007-04-30
The Remuco server problem on Feisty is indeed related to Python (Edgy used Python 2.4 as default, Feisty has switched to 2.5) and an imprecise python-dcop version information in the Remuco debian package.

However, a new debian package of the Remuco server for Amarok has been released which works on Feisty. See the [news on the Remuco website]("http://remuco.sourceforge.net") or directly go to the [download section]("https://sourceforge.net/project/showfiles.php?group_id=166515").

---

### Post by CRIKEY on 2007-04-30
> **masala said:**
> The Remuco server problem on Feisty is indeed related to Python (Edgy used Python 2.4 as default, Feisty has switched to 2.5) and an imprecise python-dcop version information in the debian package.

However, a new debian package of the Remuco server for Amarok has been released which works on Feisty. See the [news on the Remuco website]("http://remuco.sourceforge.net") or directly go to the [download section]("https://sourceforge.net/project/showfiles.php?group_id=166515").

yay that makes me quite happy that i was able to figure that out by myself

---

