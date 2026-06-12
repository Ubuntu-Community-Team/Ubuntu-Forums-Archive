---
title: "VNC how to install and get working"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by syborfical on 2008-02-26
I want to install a VNC server on my linux box. 
So I can put my linux box where ever and still VNC into. just pree the on button. Then logon like normal but through VNC.

I don&#8217;t want to SHH or any crap to get VNC to work. I can do this very annoying 
I just want to be able to put the machines adress in a VNC viewer and connect to my ubuntu machine
Then logon using what ever user run crap then log off. 

 I can install the VNC server bit no worries but it wont auto start or allow me to view anything when I turn the machine on.

Is there a step by step guide that works with Ubuntu 7.10 
And no I don&#8217;t want any go read the internet crap or I&#8217;m leet at linux and you suck. Either saysomething help full or don&#8217;t post 

Thank you

---

### Post by .nedberg on 2008-02-26
Have a look at [this one]("http://www.realvnc.com/products/free/4.1/x0.html")

Basically:

add 

Load "vnc"

to module section in xorg.conf and

Option "SecurityTypes" "VncAuth"
Option "UserPasswdVerifier" "VncAuth"
Option "PasswordFile" "/root/.vnc/passwd"

to the screen section (or Option "SecurityTypes" "None" if you don't want the security...)

It normaly helps to ask nice!

---

### Post by syborfical on 2008-02-26
ive just spend 4 hours installing 7.10 
7.04 i could get VNC to work fine .. i did use some guide last time but cant find it any my last post someone just told me to run --help... 

sorry ill ask nice next time

aslo im adding all what works to my own wiki :p

---

### Post by syborfical on 2008-02-26
THank you it Half works now my screen is funny in VNC :S ...

like whne you try to put the rez to high on a CRT

---

### Post by .nedberg on 2008-02-26
Sorry, can't help to much with that. Try a lower res in xorg.conf, something like 1024x768. Just remove evenything else from the modes line in the Screen section.

---

### Post by syborfical on 2008-02-26
doing that at the moment
I can't beleive VNc was so easy to get going ...  :S completelty differnt to last time i used it ..

---

### Post by chalewa on 2008-02-26
Hm, I am interested in this as well..


Im sure I can get it set up on my linux machine, but then do I need to install some sort of terminal client on windows to get it to work?

---

### Post by syborfical on 2008-02-26
Jsut a VNC viewer like Tight VNC or real VNC

---

### Post by .nedberg on 2008-02-26
There are a lot of other ways of doing this.

I use vnc4server and have it autostart after login (I have my only user autologin so that is fine).

Using xorg.conf in this way lets you VNC on display 0, not 1 or anything above like vnc4server.

---

### Post by chalewa on 2008-02-26
[http://ubuntuforums.org/showthread.php?t=197964](http://ubuntuforums.org/showthread.php?t=197964)

so say i used that guide to set up vnc4server on my computer, what additional steps would i have to take to get it to work over the internet, and just not local network?

---

### Post by .nedberg on 2008-02-26
Depending on what display is forwarded you would open up port 5800+dispal and 5900+display for both TCP and UDP

If display 1 is forwarded then open ports 5801 and 5901, display 2 open 5802 and 5902... You get the idea...

You would connect to your external IP (find it [here]("http://www.nedberg.net/ip.php")), not your internal. I would set up a no-ip account and use the no-ip client on the server.

```

sudo apt-get install no-ip

```

---

### Post by syborfical on 2008-02-26
> **.nedberg said:**
> Sorry, can't help to much with that. Try a lower res in xorg.conf, something like 1024x768. Just remove evenything else from the modes line in the Screen section.

there is a seciont under Xorg.conf

remote. this is the rez ofthe remost computer :P

---

### Post by .nedberg on 2008-02-27
> **syborfical said:**
> there is a seciont under Xorg.conf

remote. this is the rez ofthe remost computer :P
Thanks! I did not know that. Maybe I will try it with one of my boxes!

---

