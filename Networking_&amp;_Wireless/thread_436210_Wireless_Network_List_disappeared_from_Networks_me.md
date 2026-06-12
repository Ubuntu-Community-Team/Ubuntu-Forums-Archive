---
title: "Wireless Network List disappeared from Networks menu on Feisty"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by peewee.j on 2007-05-07
I'm using 7.04 (Feisty) on a Dell Latitude D620 and it was a real hassle getting the wireless to work because of the Broadcom card or whatever, but I finally got everything up and working using these very forums.

I then moved and got DSL internet for the first time. Trying to set it up on Linux without an existing connection to look stuff up with proved to be tricky... I was using PPPoE.
Anyway, sometime in my efforts to get it working (which I did using "sudo pppoeconf" wizard thing), my wireless seems to have gone all crazy.... 
When I click on the Networks icon at the top right of my screen now, I have wired, but then where there used to be a list of Wireless connections before manual configuration, there is just Dial-up Connections....
What happened to my wireless?!
I now have my wireless router up and completely functioning with my DSL modem, so i don't need the PPPoE settings anymore, or that dial-up option thing. I just want my wireless back!
Does anyone know how I might go about doing this?
I checked and all of the drivers and everything are still functioning for wireless, and my wifi light is still green when I have my laptop on.

Any help would be GREATLY appreciated, as I'm very new with all this linux stuff :S

Thanks

---

### Post by Floppyjoe on 2007-05-07
Goto System/Administration/Network to disable your dial-up adapter and enable roaming on the wireless adapter.

---

### Post by peewee.j on 2007-05-07
Trust me, I've tried that :(
Checked again, and the modem connection is definitely disabled, but still appears in the list. Wireless is roaming enabled.

---

### Post by Floppyjoe on 2007-05-08
Can you post your /etc/network/interfaces file minus any private information(passwords,etc)
```
sudo gedit /etc/network/interfaces
```
Maybe there is a way to get rid of the dial-up info there but for some reason i don't think so.

---

### Post by peewee.j on 2007-05-08
Here it is:




auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp



auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth1

iface eth1 inet manual


iface eth0 inet dhcp

auto eth0



Thanks for the help :)

---

### Post by chander on 2008-03-09
I have the same problem in one of my laptop. I am new to Linux and i installed ubuntu 7. 
NDISWRAPPER Installed in my machine and i configured my wireless network. It was working fine until i restarted my machine. When next time i logon, i could see wireless network is available but it is not listing all the wireless network available.

/etc/network/interface has the following,

auto lo
iface lo inet loopback

what should i do next ?. 

Thanks in advance,
Chander

---

