---
title: "See's network but no internet"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Versial on 2009-01-11
Ok...So I've only had Ubuntu for about a month.  I have gotten pretty much the hang of it.  I did a lot of work on it while I was home.  But here is my problem...I am a soldier in Iraq, and now that I have come back I am trying to get on the internet through the network set up here.  My computer is dual booted with vista, and that is how I have to use the internet now.  In order to get the access you have to log into the local page and sign in.  Now Ubuntu see's that the network is plugged in (via Ethernet), but I can't get any thing to load into Firefox.  Not even the local page.  My Firefox settings are the same as they are in Vista so I am kinda stuck.  I have been on other public networks before with it and had no problems.  So some help would be appreciated.  BTW...hopefully there is an answer that doesn't involve downloading or at least big files like a couple megs.  The internet here sux really bad.  Thnx

---

### Post by andresmh on 2009-01-11
You should check the Windows network configuration and try to replicate it in Ubuntu. Check if Windows is set up to get a dynamic IP via DHCP or if it's using a static IP. Check what's are your DNS servers and your gateway. Also check if there is some sort of proxy. All those parameters need to be the same in Ubunt. You can configure that in the Gnome Network Configuration applet.

---

### Post by handydan918 on 2009-01-11
Check to see if you are getting an IP assigned by doing ```
sudo ifconfig
``` or if wireless, ```
sudo iwconfig
```

You might also consider installing wicd rather than using networkmanager. A lot of people seem to solve their problem that way. You can [download wicd here]("http://apt.wicd.net/pool/extras/w/wicd/") with Vista if needed, and then just boot to Ubu and mount your windows partition to access the .deb.

---

### Post by Versial on 2009-01-11
Ok...andresmh, thanks for the quick reply, I looked into what you said.  Everything under Ubuntu's configuration seems to be the same as windows.  As far as IP's and DHCP and there is no proxy but still nothing.

handydan918...I will try the program it just might take a while to download it.  So maybe by tommorro it will be finished and I can get back to you.

---

### Post by Versial on 2009-01-12
Ok handydan918 I downloaded wicd and tried to install it.  It says that it conflicted with my network manager so i removed and rebooted.  And it still says the same thing.  So I am not really sure how to continue.

---

### Post by superprash2003 on 2009-01-12
as mentioned in post no 3.. to find out where exactly the problem lies.. please post output of the following from the terminal
1)ifconfig
2)cat /etc/resolv.conf
3)ping google.com
4)ping 74.125.45.100

---

### Post by Versial on 2009-01-21
Ok I finally got this fixed.  I installed wicd network manager.  And it saw that the network login page had a bad security encryption.  That was it.  I got an exception from there and it's worked since.  Thanks for help everyone.

---

