---
title: "disabling ppp (dial up) on boot"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by fara on 2005-10-31
hi

I'm a newbie in ubuntu and I love this distro! :) . I managed to successfully install and run my ubuntu box (ubuntu 5.10). but after configuring my dial up connection in system->administration->networking, my computer connects to the internet automatically on every single boot time. :( 

I removed S14ppp from /etc/rcx.d directories but it still dials up on boot. Where can I find the configuration for boot time dialing?! :confused: 

FYI: i'm using an external 56K serial modem on ttyS1.

regards
faramarz_salehpour

---

### Post by tim_downunder on 2005-11-01
I too am having the same issue. I tried installing BUM (Boot Up Manager) and disabling ppp on boot but the problem remained. The Ubuntu WiKi suggested that it could be the result of having the dialup connection selected as the default internet connection, however my ethernet connection is selected as default and problem remains. 

Any suggestions appreciated!

---

### Post by bruce147 on 2005-11-05
I have the same problem. I am new to linux. I am writing this from windows now so some of my terminology might be slightly off. After configuring my Zoom serial modem under system/networking, Ubuntu connects to hte net during boot up.

Thinking another application might behave differently, I  used the update mechanism, found and downloaded "gnome ppp" for dialup connections. It installed fine, but it won't detect my modem
 
I googled for more info on the gnome ppp gui and the developers website had comments that indicate it won't gnome ppp won't work unless it is installed as root. I am too new to all this to just follow the information posted there.
[http://www.gnomefiles.org/app.php?soft_id=41](http://www.gnomefiles.org/app.php?soft_id=41)
[http://www.gnomefiles.org/comment.php?soft_id=41](http://www.gnomefiles.org/comment.php?soft_id=41)

I would like to know how to configure gnome ppp and or have better control over the default modem program so that it won't connect until I tell it.

---

### Post by bruce147 on 2005-11-06
:) 
As a followup to my previous post. I got gnome ppp dialup utility to do the job! Now I do not have the problem of automatic dialing during logon, and I can click an icon on the menu bar to login or logout at will.

Make sure your serial modem is turned on.
Install the gnome ppp dialup utility. It should appear on your menu bar.
Set the System/Networking utility to "deactivate" for your modem (mine already was, not sure if it must be deactivated during gnome ppp setup)
Using the gnome ppp GUI, fill in the required info... phone number, login info etc
Hit the connect botton to logon to your ISP (it probably won't work).
Close out then and open gnome pp to make sure all info is there. Close again.
Open a terminal and type sudo wvdialconf (This automatically detects your serial modem and silently creats a wvdial configuration profile, which had been lacking before.)
Finally, back on the main window, click on the red phone, the gnome GUI, and you should be ready to connect.

Here is what my terminal session looked like:
bruce147@ubuntu:/$ sudo wvdialconf
Usage: wvdialconf <configfile-name>
        (create/update a wvdial.conf file automatically)
bruce147@ubuntu:/$

I found the above command in wvdialconf(1) in the linux manual pages

---

### Post by fara on 2005-11-07
hi

something magical has happened, my system doesn't dial on boot anymore! i got no explanation. but I still hope to find an answer!! I have not changed anything in my configuration.

:confused: 

faramarz

---

