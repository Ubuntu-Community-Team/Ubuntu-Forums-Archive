---
title: "no wired connection on HP Pavillion dv6000"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by pauliebp on 2010-04-14
Hi! I am, yet another Linux newbie, therefore please provide simple answers :) I have been searching all day now to try and solve this, but have not come across a thread that would fully outline a solution to my specific problem. I am keen to make the switch but no internet is really holding me back! 

So: I have installed Ubuntu 9.10 (x64) along side XP on my HP Pavillion dv6000 (AMD Turion64x2/NVIDIA) all is well except that I can not connect to the internet. During my research today I have found that it sees the ethernet adapter (NVIDIA), but I can not make out whether it is active or not. The wireless does not work ether, but that I will attempt to fix ounce this is done. 

Thanks for your replies in advance, help is really appreciated!!!

---

### Post by philinux on 2010-04-14
Open a terminal, Apps>Access>Terminal

Copy and then paste the following one at a time into the terminal. Post back the output.

```
lspci | grep Ethernet
```

Then this.

```
ifconfig 
```

---

### Post by pauliebp on 2010-04-14
Thanks for such a prompt reply! Here is the output:

lspci | grep Ethernet
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:ae:38:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x2000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by gordintoronto on 2010-04-14
Is there any chance the cable is defective, or not fully seated at one end, or it's a crossover cable, for connecting two computers to each other?

What are you connecting to?

---

### Post by agnes on 2010-04-14
Might possibly help, to install [wicd]("http://wicd.sourceforge.net/download.php"), instead of using gnome-network-manager. Because wicd is more advanced, shows more.

> Is there any chance the cable is defective, or not fully seated at one end, or it's a crossover cable, for connecting two computers to each other?
I assume pauliebp has internet working on his XP partition, if not this would be obvious?

---

### Post by pauliebp on 2010-04-15
As in regards to the cable it has no problem when connected to either two of the other computers here, one of which is also running Ubuntu. At the other end there is a switch. 
However I am starting to think that this could be a problem with the actual adapter, as when running XP it has 'limited or no connectivity' through ethernet, I have thus far presumed that it is a Windows bug of some sort and used the wireless. Also I am observing strange behaviour on the switch panel: when running XP the light comes on and stays on (hence no activity) when running Ubuntu it flashes at constant intervals (nothing like the flashing due to activity) and the strangest thing is that it keeps this up also when the HP is powered off!!! 
I will look up and see what 'wicd' is all about and how to install it and then report on any progress. 

I really hoped that this would be easier than Windows but has proven to be quite a challenge, I just noticed that the HP did not wake up properly from sleep mode, but I guess it is sometimes better to learn things the hard way! :D Thanks for the advice so far!!!

---

### Post by pauliebp on 2010-04-15
One more thing! Is it possible to get the wifi working without a connection to the net, say by installing the necessary driver from a USB stick?

---

### Post by bkratz on 2010-04-15
> **pauliebp said:**
> One more thing! Is it possible to get the wifi working without a connection to the net, say by installing the necessary driver from a USB stick?

First what is the wireless card used?

```
lspci | grep Network
```

Should give the answer, if not decode from 

```
lspci -nn
```

---

### Post by pauliebp on 2010-04-15
The output is as follows:
 
lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

---

### Post by bkratz on 2010-04-15
> **pauliebp said:**
> The output is as follows:
 
lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

The first half of this thread should help you with no ethernet access for wireless.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by lidex on 2010-04-15
For info specific to the Pavillion Dv series, look here:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing")
You'll want to bookmark that page.

---

