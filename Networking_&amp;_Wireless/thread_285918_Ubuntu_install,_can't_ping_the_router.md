---
title: "Ubuntu install, can't ping the router"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by monochaser on 2006-10-27
I just completed my first Linux install of Ubuntu 6.06.1. According to what I'm reading, there are many programs and utilities to complete the install, however they are to be downloaded.

I have no connectivity to my wireless router- but using cat-5 cable and regular ethernet card, not wireless card. I see in Network, eth0 is enabled, and set to DHCP. Not much else in properties. Anyhow, when I ping my default gateway, nothing. The 127.0.0.1 loopback works. 

I am familiar with windows network troubleshooting, so this is quite confusing. My network card is on the list as working w/Ubuntu. Realtek 8139.

A side note, startx from command line comes back telling me I don't have authorization. But only have one user.

here's an odd one, the button to unlatch the cd tray not working, so I use a paper clip. 

Last question, would it be better to switch to another distro? 16 cd's for Debian is daunting. btw, this is a compaq 2004-2005 laptop- M2100 series. Seems to work for others. Looking forward to getting going, but I'm stalled very early in process. Any help- thanks.

---

### Post by yves on 2006-10-27
> Anyhow, when I ping my default gateway, nothing.
What is the message you are getting ?  Ho do you test your ping connectivity ? Opening a terminal, and typing ping with the known address ?

> side note, startx from command line comes back telling me I don't have authorization. But only have one user.

Ubuntu avoids you making real bad mistakes by not giving you admin rights with your userid.  To start X this way you need admin access. So you need to type " sudo startx".  It will ask for a password, which is the one you use with your ID.

> the button to unlatch the cd tray not working, so I use a paper clip. 

If I understand right, you mean pressing the physical button in front of your CD tray doesn't seem to work. In a terminal, you can type "eject cdrom" if I remember (not on Ubuntu right now) or right mouse click on the CDROM icon on your desktop (but since you couldn't start X, this might not be an option ! ). ;)

---

### Post by monochaser on 2006-10-27
Well, something must have happened last night. Yes, I open a terminal and ping my known gateway 192.168.1.1. Today it worked?!  So I opened up FF, and it is working as well. I can proceed with next steps. Thanks for your post, very much appreciated.

---

