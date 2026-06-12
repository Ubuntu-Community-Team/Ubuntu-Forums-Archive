---
title: "Ubuntu 7.04 wifi setup problem"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by anurag_sagar on 2009-08-01
I have a Dell Inspiron 1501 laptop on which I have installed Ubuntu 7.04 Feisty Fawn and I do not know how to connect to my wireless network with it. My WLAN card has the following details:
 
Dell Wireless 1390 WLAN Mini-Card
Manufacturer: Broadcom
 
Here are a couple of things that I have noted:
1) The WiFi light (flourescent light above the keyboard) of the laptop is not on (which indicates that Wifi is working) when I boot from Ubuntu.
 
2) Ubuntu did not prompt for any restricted driver usage for the WLAN card at the time of installation (I saw some websites which suggested it would give me a such a prompt)
 
It would be great if someone could guide me on how to do this setup.
 
Thanks...
Anurag.

---

### Post by albert s on 2009-08-01
may not be off much help to you as im really new to all this ubuntu,
but when i first put ubuntu 9.04 on my dell inspiron laptop i had to hard wire to internet to download the updates and get the driver for my dell wireless broadcom card.
HTH.

---

### Post by slakkie on 2009-08-01
lspci or lsusb to display all the details of your wireless card please.

Be aware that 7.04 is EOL, thus not supported anymore by Canonical and by most members of the community.

Found this:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

But before you can execute those steps first do this:

```

sudo perl -p -i.feistyEOL -e 's/(?:(?:\w+.)?archive|security).(ubuntu.com)/old-releases.$1/' /etc/apt/sources.list
sudo aptitude update && sudo aptitude upgrade

```

And now follow the howto/tutorial.

---

