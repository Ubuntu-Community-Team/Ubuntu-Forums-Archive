---
title: "Ubuntu 6.10 Edgy not detecting my network card"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by acidity on 2007-01-21
Hello

I hope somebody can help me here. Google and IRC have not been of much help.

I just got an old server from my proff. It has a 3Com vortex ethernet card. 

This is my first usage of Ubuntu and for the life of me I cant get it recognise my card. My prof. said that I have to 3c59x module in the kernel to get the network to work. Doing a google, it looks like 3c59x module has been broken from kernel 2.6.8 and Ubuntu 6.10 is using 2.6.17-10.

Thus Ubuntu is not detecting nor I am able to install the drive?

I tried following: http://linuxhelp.blogspot.com/2005/01/how-to-install-network-card-in-linux.html but all the files and paths given in the article are not presnet in Ubuntu e.g. /etc/modules etc. 

So how do I get my network card up and running?

PS: Its just a CLI based system now so any GUI solutions will not work :(

---

### Post by acidity on 2007-01-21
Okie, some more research. I was able to get 3c59x module up using modprobe and i can confirm it by doing lsmod...

But still its not recognising the nic and i cant get eth0 up and running. ifconfig just returns info about the loopback adapter.

What should i do now?

---

### Post by TANGUN on 2007-02-10
Is this an ISA card? If so I think you may need to manually add the eth0 to the 'interfaces' and 'modules' files. If you still need help, post again.  I finally got my card to be recognized this way, still working on accessing the internet.

---

### Post by acidity on 2007-02-20
Ok, so I got little time yesterday to work on this problem again but with same results.

My Ubuntu is not detecting the network card even though when I start off with E Live 0.4.2, i detects everything and I can even browse. Therefore, there is something wrong with the Ubuntu distro.

So I took down all the info when I do ifconfig in Elive:

```

eth0      Link encap:Ethernet  HWaddr 00:04:76:9C:71:B9  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fe9c:71b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2579815 (2.4 MiB)  TX bytes:536767 (524.1 KiB)
          Interrupt:10 Base address:0xac00 

```

I know that the card uses a generic 3c59x driver.

In Ubuntu, I tried the following things:

1.) Do a **modprobe 3c59x** and Ubuntu says that it successfuly loaded up the module. I can verify it by using **lsmod | grep 3c59** and it returns two entries.

2.) I tried to manually configure the network card as shown at: [http://www.gentoo.org/doc/en/handbook/2005.0/handbook-amd64.xml?part=1&chap=3](http://www.gentoo.org/doc/en/handbook/2005.0/handbook-amd64.xml?part=1&chap=3) . But its giving the error always like: [B]SIOCSIIFADDR: No Device Found
eth0: Error while getting interface flags:No such devices
[/B]

3.) I manually try to boot it up by using ```
ifup eth0
``` and ```
dhclient eth0
``` without any success.

4.) Then I tried to change the modules and interface files manually with details like:

```

alias eth0 3cf9x

```

Still Ubuntu cannot detect the card. One person said that I have to recompile the kernel but I want to make sure that I have tried all combination before taking up that front. Since I dont have Internet connection on that machine, I have to copy each and every file from CD to the machine everytime a new package is required. So if I have to recompile from source what all packages I would require that I can copy in one shot in a CD and try to do it in my box.

Any ideas?

---

