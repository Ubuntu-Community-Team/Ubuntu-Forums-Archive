---
title: "restart network on every boot??"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by Grone1985 on 2008-09-27
Hi!

So I just configured my wireless but for some reason I have to run this command on every boot: sudo /etc/init.d/networking restart
Is there any way to make this be done by itself?
Thanks in advance!

---

### Post by lswb on 2008-09-27
Assuming you have made no changes to the stock runlevel and init setup of your installation, Try putting a link to it in /etc/rc2.d like so:

sudo ln -s /etc/init.d/networking /etc/rc2.d/S15networking

If that doesn't work delete the link and try editing the file /etc/rc.local to include the line "/etc/init.d/networking start" (do not use sudo in this file, it is run at startup with root permissions)


FYI, quick and very oversimplifed explanation: The scripts referenced by the links in the rcx.d directories, if the name begins with "S", are run at startup with the argument "start", in numerical order. I am guessing at 15 being a good place just based on some of the other links I see in my own rc2.d directory (hardy defaults to runlevel 2 at startup) Google "runlevels init startup" or similar for explanation. If you are really interested search for "upstart" as well.

---

### Post by Iowan on 2008-09-27
Check **/etc/network/interfaces**.  It should have an "auto" line for your wireless interface.  I can provide editing details if you need them.

---

### Post by lisati on 2008-09-27
Have a look [here]("http://ubuntuforums.org/showpost.php?p=1351902&postcount=2")

---

### Post by charonred on 2008-10-12
I was having similar problems and this solution/work-around seems to have fixed my 'Hardy' wireless connection & password/key problems so that my network is detected and connected, and keeps working even after re-booting.

NOTE: I wouldn't remove 'Network Manager' as that may kill your ethernet connection (it may not, but it has on one PC).

My laptop which runs Hardy, but with the KDE instead of Gnome, gave me a hint on how to get wireless working - it connects fine as it uses 'kwifi' and not 'Network Manager'.

As I use Gnome on my other PCs I went looking for something similar.

I used Synaptic to install 'wifi-radar' - I then put in the relevant settings into it and presto, I have wireless networking; and then I rebooted, and yep I still had wireless - after several reboots I still had wireless, so I recommend using 'wifi-radar' instead of Gnome's sometimes buggy 'Network Manager' 

(note: I'm using WEP, but I think it'll still work with WPA)

---

### Post by ehering on 2008-10-27
> **lswb said:**
> 
If that doesn't work delete the link and try editing the file /etc/rc.local to include the line "/etc/init.d/networking start" (do not use sudo in this file, it is run at startup with root permissions)



Thanks man, I was having the same issue and that did it for me. Thanks a lot for helping all the ubuntu noobs like me ...

cheers

---

### Post by ww711 on 2008-10-27
Is this fixed in II 8.10?

---

