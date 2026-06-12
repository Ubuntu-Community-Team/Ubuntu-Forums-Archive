---
title: "No Network - My Laptop Hangs"
date: 2005-07-11
forum: Networking &amp; Wireless
---

### Post by jjustin01 on 2005-07-11
So far, so good with the networking.  I have a Dell Inspirion 1150 laptop and Ubuntu runs like a champ on it.  WiFi is up and running and so is everything else.  Here's my problem though.

When there is no network around, wireless or wired, my laptop hangs during bootup when it is trying to configure network settings.  It sits there for about 3-4 minutes before finally giving up and moving on.

Is there anyway I can edit a file or change a setting that will get it to give up quicker or know that there is not a network anywhere around me a little faster.

Thanks for the help guys.

---

### Post by dave9191 on 2005-07-11
My workaround about the problem was to start networks manually. No network is started during the computers boot, then when I want a certain network, i pull down a menu and run the corresponding script to the network I want. Doesnt hang on boot, but it doesnt start networks automatically. 

Dave

---

### Post by brim4brim on 2005-07-11
[QUOTE=jjustin01]So far, so good with the networking.  I have a Dell Inspirion 1150 laptop and Ubuntu runs like a champ on it.  WiFi is up and running and so is everything else.  Here's my problem though.

When there is no network around, wireless or wired, my laptop hangs during bootup when it is trying to configure network settings.  It sits there for about 3-4 minutes before finally giving up and moving on.

Is there anyway I can edit a file or change a setting that will get it to give up quicker or know that there is not a network anywhere around me a little faster.

Thanks for the help guys.[/QUOTE]
 It times out of this after a while but if you press control C when it brings up configuring Network interfaces it'll break from the operation.  Unless something more serious is wrong.  I'm using a wireless connection and that's how I get round it.

---

### Post by jjustin01 on 2005-07-13
Well of course it would be that simple.  Control C fixes my isssue.  I wish there was another way, but this way works quite nicely.

I appreciate the help guys.

---

### Post by kleeman on 2005-07-13
ctl-C also stops the lo interface coming up which is not good. Better to look in /etc/network/interfaces and comment out the auto lines eg "auto eth0" or whatever.(leave "auto lo")

---

### Post by dave9191 on 2005-07-13
Yeh, stopping the network script (ctrl - c) on boot isnt the best solution. Best to stop things trying to load automatically and start them manually when you need them.

---

