---
title: "wireless problems in Edgy Eft"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by kpagpa on 2007-03-18
Hi friends,

Yesterday, a did a clean install of Ubuntu 6.10 because I was having problems having loaded Beryl and some other packages.  Wireless worked fiine in Dapper, and even when I updated to 6.10 using synaptic, wireless was fine.  Having done the clean install from the CD, I am having problems connecting!  I am hoping that someone can help me see what's going wrong.

When I do iwconfig, this is what it says for eth1:      

           IEEE 802.11g  ESSID:"varahi"  
           Mode:Managed  Frequency:2.447 GHz  Access Point: 02:0E:2E:8A:38:95   
           Bit Rate:54 Mb/s   Tx-Power:15 dBm   
           Retry limit:15   RTS thr: off   Fragment thr: off
           Power Management: off
           Link Quality=77/100  Signal level=-59 dBm  Noise level=-60 dBm
           Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:570   Missed beacon:0


I think this is connected, yes?

If so, there are still some problems.   When I go to the network monitor and try to switch to eth1, it isn't an option.  All I have is 'lo'.   

Also, since Network Manager is not included in the CD install of Edgy, how can I get it?   I've tried downloading the tarballs and compiling, but it won't work.  Is there a compiler in the basic version of 6.10, and if so, how can I use it?

In short, what do I have to do now to connect?   Any help would be gratefully received.

---

### Post by Kobalt on 2007-03-18
> **kpagpa said:**
> When I go to the network monitor and try to switch to eth1, it isn't an option.  All I have is 'lo'
Simply click into the text bar, erase *l*o and type in *eth1*, your signal power should appear and you'll be able to set up your network by clicking on Configure.
You'll install Network-manager through Synaptic very simply when you're connected, your card seems top be ready to get you flyin' :)

---

### Post by kpagpa on 2007-03-18
Hi Kobalt,

Many thanks for your help:)   I did what you said, but there still seems to be a problem in somuch as I can now access eth1, but it keeps flipping between idle and disconnected.  I switched off my wireless encryption and it can connect okay with that.   I'm downloading the Network Manager, so hopefully I should be able to get it working with encryption very soon.

Thanks very much, you're a :KS

---

### Post by Kobalt on 2007-03-18
I hope your problem can be solved with network-manager, though it could also be a driver issue... 
Post back when you're done then.

You're welcome :)

---

### Post by kpagpa on 2007-03-18
Hi Kobalt,

I've got network manager now, but it says "no network connection".  I'm still connected unencrypted with no problems.  Do you have any suggestions for how I might be able to fix this?  It worked fine in Dapper!  I had a keyring set up so that I just typed my password to connect.

Thanks for all your help.

---

### Post by Kobalt on 2007-03-18
You might have to comment a few things in your /etc/network/interfaces file, since network-manager needs a clean one to handle it itself. Can you please post the output of ```
cat /etc/network/interfaces
```

---

### Post by gottria on 2007-03-18
When I installed a fresh copy of 6.10 my WIFI worked but it was detected as eth0 instead of wlan0.

---

### Post by kpagpa on 2007-03-18
Hi Kobalt,

This is the output of  etc/network/interfaces:

auto lo
iface lo inet loopback


#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid varahi
wireless-key s:

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

In the guides I have read, it says to comment everything out except the 'lo' entry, but I found that when I configure eth1, it writes to this file so that it's no longer clean.

The wireless key is blank because I'm using unencrypted at the moment.

Any ideas?

P.S., gottria, thanks for the tip, but my system definitely detects my wireless as eth1 when I do iwconfig

---

### Post by Kobalt on 2007-03-18
I would suggest you to turn this part : 
> auto eth1
iface eth1 inet dhcp
wireless-essid varahi
wireless-key s:
Into this :
> auto eth1
iface eth1 inet dhcp

Then : 
```
sudo ifdown eth1
sudo ifup eth1
```
And finally restart Network-manager.

---

### Post by kpagpa on 2007-03-18
It worked!  It's as you say - the file must be clean for the network manager work properly.

My wireless is working perfectly now :)   Thanks so much for your kind attention and advice

Here's some :popcorn: 

You rock!

---

### Post by Kobalt on 2007-03-18
I do rock ;) 
Thanks !

---

