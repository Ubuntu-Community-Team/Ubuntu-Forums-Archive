---
title: "Wired connection broken!"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Jimmy9pints on 2008-11-27
Ahh! I am very frustrated so please help me if you can.

I have an old laptop which I just made a clean install of Intrepid. Everything was working **wonderfully** apart from the same old problem I have always had...yes you guessed it, the wireless networking. 

It's usually not a great problem because I used the laptop here at home with a cable. I used it like that for a couple of days. Then, because I was going to a friend's house, I thought I would have a quick bash (excuse the pun) at fixing the wireless. 

This was pretty simple to do on my girlfriend's (new) laptop. Her inbuilt wireless card is an atheros AR5007EG. And simply by updating the backports with:
```
sudo apt-get install linux-backports-modules-intrepid-generic
```
and rebooting, the problem was solved. 

In the case of this old laptop, I have a USB tp-link TL-WN821N. 

I tried the same thing because I believe it's an Atheros based chipset. However, far from fixing the wireless, running this command completely broke the wired connection. This has left my little laptop completely useless!!!! No wireless and no wired connections!

So, after googling like mad (on this, my other computer), I tried a bunch of things. Then, in a desperate attempt to get things sorted (and since this was a very new install which used to work fine before I updated), I reinstalled Ubuntu. And guess what...it didn't work. Still broken. 

Then I found an article which sounded promising which advised changing the etc/network/interfaces to contain:
```
auto eth0
iface eth0 inet static
address 192.168.1.185
netmask 255.255.255.0
gateway 192.168.1.1
```

When I ran some command, I can't remember which now sorry, instead of eth0 it said my network card was pan0. So me being so clever and all, I tried substituting the above with pan0 - - obviously this was to now avail. Nowm y connection is still broken and the network manager icon from the system tray has disappeared. Oh what a mess!   

Please help if you can. 

Thanks,

James.

---

### Post by Jimmy9pints on 2008-11-27
Anybody?

---

### Post by Jimmy9pints on 2008-11-30
Once more. Anybody got any idea where I even start with this?

Thanks,

James.

---

