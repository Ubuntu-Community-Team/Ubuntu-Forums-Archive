---
title: "USB ADSL modem detected, but no internet"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by fluppet on 2007-08-18
I have a Voyager 210 USB ADSL modem. When I ran the Live CD the internet worked straight away - I didn't need to do any configuration. Because I have quite an old computer I used the alternate install CD to install a command-line system, and then installed xorg, icewm, etc. My Modem is still being detected - the required drivers (CDCEther and usbnet) are loaded automatically and it is set-up as eth0, but it isn't allowing me to access the internet.

'ifconfig' didn't show it, but 'ifconfig -a' did, so it must be down. I did 'ifconfig eth0 up' so now 'ifconfig' does show it as running, but I still cannot access the internet. I tried running 'pppoeconf' which says it has found 1 eth device and scans it, but it says that it is unable to find the concentrator or something like that.

I'm sure it can't be too hard to get it going - as I said it worked straight away off the Live CD, so does anyone have any suggestions? Thanks.

---

### Post by Herman on 2007-08-18
Hello fluppet, Would this link be of any use to you?
[http://www.plus.net/support/broadband/hardware/voyager210.shtml](http://www.plus.net/support/broadband/hardware/voyager210.shtml)

Regards, Herman :)

---

### Post by fluppet on 2007-08-18
Thank you for the reply, but unfortunately I don't think it helps me - the page you linked to seems to be just the basic set-up of the modem. The modem is working fine - I am using it right now (from Windows) and I can use it when running Ubuntu as a LiveCD, but it's just when I try to run it from my command-line installation of Ubuntu that it won't allow me to access the internet.

I suspect the problem is that DHCP isn't set-up properly - as I said it knows the modem is there and loads all the drivers, etc., but just won't access anything, I could of course be wrong though and it might be something else that is causing the problem.

BTW: Just in case you didn't realise, I am connecting to the modem via USB. I know you are going to tell me that is a bad way of doing it, etc. but it works with the LiveCD, so it should work with my command-line installation, and that's what I want.

Thanks again.

---

### Post by fluppet on 2007-08-18
I should add that I also had no problem using the modem with DSL-N (DamnSmallLinux-Not). I just run netcardconfig which says it has detected eth0, I tell it to set it up, it says something about enabling DHCP Broadcast and then the internet works.

---

### Post by fluppet on 2007-08-18
Wahoo! Got it :)

I just typed sudo ifconfig eth0 192.168.1.2 up

and then sudo dhclient

and it worked!

The ifconfig step might not have been necessary - I haven't tried it without doing that.

---

### Post by Herman on 2007-08-18
Hey great!, I'm happy you got it! :)
I often use the commands, **sudo ifup -a** and **sudo ifdown -a** when I want to open or close my network connections, those work well for me. :)
Glad you were able to fix it! :) Happy networking!
Regards, Herman

---

