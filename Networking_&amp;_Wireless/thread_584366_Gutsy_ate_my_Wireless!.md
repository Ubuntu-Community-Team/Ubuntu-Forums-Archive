---
title: "Gutsy ate my Wireless!"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by nimbuscott on 2007-10-20
I did a clean install of Gutsy and now my wireless which worked fine in the last two Ubuntu releases no longer works. Wired Ethernet connects fine but wireless does not. I have tried various remedies including ndsiwrapper and wicd to no avail. Here is my ifconfig & the contents of my etc/network/interfaces:

```
eth0      Link encap:Ethernet  HWaddr 00:D0:59:CC:BC:9A  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fecc:bc9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:685847 (669.7 KB)  TX bytes:151595 (148.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4408 (4.3 KB)  TX bytes:4408 (4.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:3B:07:0E:6A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-3B-07-0E-6A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

etc/network/interfaces

```
auto lo
iface lo inet loopback
```

I have also tried using open DNS nameservers (208.67.222.222 & 208.67.220.220) in an attempt at manual configuration with no joy.

IBM Thinkpad A31 with Hawking Technologies HWC54d using rt2500 driver in the PCMCIA slot.Connecting to Linkysis WRT54GX wireless router using WPA2 Shared Key AEP encryption (tried no encryption- still no joy).

Any ideas?

---

### Post by dr_agon on 2007-11-04
I spent hours on the same problem - the wifi connection worked in Feisty, and was gone in Gutsy. I have card with rt2400, and this was the problem. There are plenty of threads about RaLink adapters not working in Gutsy.
For me changing drivers from rt2400pci supplied with Gutsy to rt2400 from serialmonkey helped. Hope it will help to you too.

---

### Post by spenc083 on 2007-11-04
I'm having the same problem with my Dell Latitude. I tried running the Gustsy upgrade but it crashed my system. 6 months of info, gone...Most of my doc's are backed up on Google. Any-who, I decided to do a clean install which ran without a hitch, now the only problem is my wireless. I'm able to see the card but not able to config using static or DHCP. Fiesty, no problem with wi-fi. I'm also experiencing the same issue with my Macbook. The Mac install don't see the wi-fi card at all. 

Helplessly wireless....

---

### Post by gilf on 2007-11-04
You might take a look at this:

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by xshakakee on 2007-11-05
Since gilf will toot his own horn, I'll jump in as well.

First, take a look at:

[[COLOR="SandyBrown"]_http://ubuntuforums.org/showthread.php?t=602180_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=602180")

and check out the tutorials that it references.  There is also a WPA-specific tutorial by wieman01.  Check out both stickies (RT2500 and WPA).  They're really good, but I had to write my own because a) I have a huge ego, and b) his instructions didn't *quite* work for me.  I just got to this stage by trial and error.

Anyway, for anyone still having problems, please post the contents of their lsmod, iwpriv, and ifconfig outputs:```

sudo lsmod
sudo iwpriv
sudo ifconfig
```

Leave out any confidential information, such as SSID and passkeys.  Thanks.

---

