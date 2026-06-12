---
title: "network manager"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by zvacet on 2007-03-27
I worked with Edgy and never have problem with network connection.few days ago I decided to upgrade to Feisty.I did net upgrade,and everything looks nice.Because of kernel upgrade I had to reboot.Here story begins.I tryed to go to the network,but no connection.I saw network manager icon and click on it to see is it any information I can get from there.On my suprise my address and nameservers are correct.after thst I went to network settings.Everything is O.K.as last resort I looked in etc/network/interfaces and all is correct.So I looked in every possible way to understand why I don´t have connection working and finished without resalt.Only way to start net is to type **pon dsl-provider**.But that is not good enough.i want my connection automaticly.It was long post because I want to explain my situation and provide info for somebody who will help me with this.

---

### Post by zvacet on 2007-03-27
Does anybody cares?


Btw I tryed rp-pppoe with no luck.I use static IP.

---

### Post by Hoosier205 on 2007-03-27
> **zvacet said:**
> I worked with Edgy and never have problem with network connection.few days ago I decided to upgrade to Feisty.I did net upgrade,and everything looks nice.Because of kernel upgrade I had to reboot.Here story begins.I tryed to go to the network,but no connection.I saw network manager icon and click on it to see is it any information I can get from there.On my suprise my address and nameservers are correct.after thst I went to network settings.Everything is O.K.as last resort I looked in etc/network/interfaces and all is correct.So I looked in every possible way to understand why I don´t have connection working and finished without resalt.Only way to start net is to type **pon dsl-provider**.But that is not good enough.i want my connection automatically.It was long post because I want to explain my situation and provide info for somebody who will help me with this.

I had the same problem...

You can't use both the "network manager" and the network utility found in SYSTEM->ADMIN->NETWORK. 

They are both trying to do the same thing basically and causing a conflict. From you panel, go to SYSTEM->ADMIN->NETWORK and disable everything (uncheck) from that first tab. Now, you should be able to set everything up by clicking on that network manager icon w/ the three bars.

That's the advice I was given...hope it works for you.

---

### Post by sirancestor on 2007-03-27
Hoosier is right you cannot use both. You should comment out everything except loopback in your /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
```

and then put # on the beginning of each line except 

auto lo
iface lo inet loopback

Everything else should be "commented out" with #

Your interfaces file should look something like this:

```
auto lo
iface lo inet loopback


#iface eth0 inet dhcp
#address 
#netmask 
#gateway 

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


#auto eth0

```

Save, and reboot.

This of course does not really address your main question but it should make Network Manager active.

---

### Post by zvacet on 2007-03-27
Thank you for your tme but still no luck.Only way to connect is still **pon dsl-provider**.Does anybody else have same idea,advice,suggestion...?

---

