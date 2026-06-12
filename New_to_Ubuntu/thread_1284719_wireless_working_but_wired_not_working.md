---
title: "wireless working but wired not working"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by baltadt on 2009-10-06
My wireless on my laptop was plug n play but I am having a problem with my wired. it recognizes it but will not access the internet. It is a new siemens gigaset wireless modem. I am running Ubuntu 9.04 on a compaq CQ50-211NR. please help. Thank you.

---

### Post by baltadt on 2009-10-07
Please anyone help...this is extremely annoying. It is my first major problem with ubuntu.

---

### Post by kevdog on 2009-10-08
please post more info about your wired card, etc.  I cant tell anything right now about your setup.

---

### Post by Arndt on 2009-10-08
> **baltadt said:**
> My wireless on my laptop was plug n play but I am having a problem with my wired. it recognizes it but will not access the internet. It is a new siemens gigaset wireless modem. I am running Ubuntu 9.04 on a compaq CQ50-211NR. please help. Thank you.

I have the same problem, with a card called Attansic. What works for me now is to use wireless instead of wired.

---

### Post by Peter09 on 2009-10-08
Juat a point - you will not be able to establish a wireless and wired connection to the same access point at the same time - without routing problems.

Can we see the output of the command

```
ifconfig
```

---

### Post by theDaveTheRave on 2009-10-08
> **baltadt said:**
> My wireless on my laptop was plug n play but I am having a problem with my wired.

now that is strange, can you confirm your network card is working with the following
```
lshw -C network
```
and or
```
 ifconifg
```



>  it recognizes it but will not access the internet. It is a new siemens gigaset [COLOR="Magenta"]wireless[/COLOR] modem.


so am I right in assuming that the card has both the ethernet and wireless capabilities simultaneously (or at least built into the same "device"), rather than 2 separate dedicated devices? Or is it in fact a [COLOR="Magenta"]wireless [/COLOR]enabled router?

Also the product spec from [compaq]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01570477&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN#N852") seems to suggest that these are build in (is it a replacement / external / usb) card, or the standard one?

if so it may be that you need to physically (or "programatically") turn off the [COLOR="Magenta"]*wireless *[/COLOR]portion to be able to use the "[COLOR="Magenta"]*wired*[/COLOR]" portion.

but we'll need to wait and see.

David

---

### Post by baltadt on 2009-10-08
eth0      Link encap:Ethernet  HWaddr 00:1f:16:46:99:ca  
          inet6 addr: fe80::21f:16ff:fe46:99ca/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:861127 (861.1 KB)  TX bytes:40850 (40.8 KB)
          Interrupt:253 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:656 (656.0 B)  TX bytes:656 (656.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:98:66:c7  
          inet addr:192.168.254.2  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe98:66c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:275371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:201554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:374191177 (374.1 MB)  TX bytes:22149660 (22.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-98-66-C7-36-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by theDaveTheRave on 2009-10-09
OK so your system is definately seeing both the cards at the same time.

any chance of posting the results of the

```

lshw -C network

```

also you may need to manualy bring up the interface, to do so try
```

sudo ifup eth0

```
or if that doesn't do anything
```

sudo ifconfig eth0 up

```

you may need to bring the interface < down > first, then back < up > ap again after, so use <ifdown eth0> or <ifconfig eth0 down>

then if you re do the <ifconfig> you should find that the eth0 interface has an inet address.

David.

ps. I know this is probably the worst question ever, but are you sure that the network cable is OK? it is the only other thing I could think of as to why the interface isn't getting an IP address automatically, which is what ethernet interfaces normaly do in my experience!). I am assuming that you have another pc that you can test it on?

---

### Post by Arndt on 2009-10-09
> **baltadt said:**
> My wireless on my laptop was plug n play but I am having a problem with my wired. it recognizes it but will not access the internet. It is a new siemens gigaset wireless modem. I am running Ubuntu 9.04 on a compaq CQ50-211NR. please help. Thank you.

If you perchance have Windows on the same computer, determine whether Windows can run both wireless and wired. The answer may point the way to locate the problem.

---

### Post by tarps87 on 2009-10-09
When you posted the output of ifconifg did you have the wired connection plugged in?
If so I reckon it is either the card is not set up, or more likely your wire connection is not using DHCP and therefore it is not being assigned an ip address.
Can you post the output of
```
cat /etc/network/interfaces
```

If you have any other computers on the wired network could you post one of their ip's, thanks.

---

### Post by baltadt on 2009-10-10
[QUOTE=theDaveTheRave;8076509]OK so your system is definately seeing both the cards at the same time.

any chance of posting the results of the

```

lshw -C network

```

 *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:46:99:ca
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:98:66:c7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.254.2 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:17:8a:d0:d4:8b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by baltadt on 2009-10-10
> **tarps87 said:**
> When you posted the output of ifconifg did you have the wired connection plugged in?
If so I reckon it is either the card is not set up, or more likely your wire connection is not using DHCP and therefore it is not being assigned an ip address.
Can you post the output of
```
cat /etc/network/interfaces
```

If you have any other computers on the wired network could you post one of their ip's, thanks.

I did not have the etho cable plugged in. Wired works fine on my wifes computer. I works fine on vista(I'm dual booting) but I was also told to try and disconnect my wireless before connecting to etho...have not had a chance to try this should I?

---

### Post by Peter09 on 2009-10-10
typing the route command

```
route
```

will show you how your machine is using the interfaces.

---

### Post by theDaveTheRave on 2009-10-13
> **baltadt said:**
> 

```

lshw -C network

```

 *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:46:99:ca
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 

so I did a quick search for your card on google [MCP78S].

it seems that you are not lone in having troubles with this card, check out [this thread]("http://ubuntuforums.org/showthread.php?t=1111496") on the ubuntu forum.

I also found this forum [thread on the web]("http://www.linux-solved.com/post/MCP78S-network-troubles-SOLVED-36548.html"), it seems this chap solved his problem, and it was somehow related to the modules that had been instaled.

according to that thread we need to see what modules you need, and what you have.

Can you run each of these commands separately.
```

lspci

```
then
```

lspci -v

```

it also seems it would be best if you could do this from a live CD, if you have one floating around.

I think we will be able to get this workin.

David

---

### Post by tarps87 on 2009-10-14
> **baltadt said:**
> I did not have the etho cable plugged in. Wired works fine on my wifes computer. I works fine on vista(I'm dual booting) but I was also told to try and disconnect my wireless before connecting to etho...have not had a chance to try this should I?

If you tell it to use the wired connection, you can do this using the network app), it may disconnect the wireless but either way it should connect to the wireless.
With windows machines if it is not assigned an ip it will make one up, this is not usually the behaviour with Ubuntu.
Looking at the output of the previous commands it is highly likely that the card is working, so before messing about with drivers and modules try this (if it doesn't work then check the drivers)

On on of the windows machines connected to the wired network, preferably your dual boot, now run the command **ipconfig** make a note of the ipaddress, subnet and gateway.
Now boot the Ubuntu install and type
```

sudo ifconfig eth0 down
sudo ifconfig eth0 *ipaddress* netmask *subnet*
route add default gw *gateway*
sudo ifconfig eth0 up

```

Some of these steps may not be needed depending on your setup, but if you do them all this will determine if there is a problem with the driver.

Note: If you ran the ipconfig command on a different pc change the last section of the ip e.g 192.168.123.**3** 192.168.123.**32**

Note2: You can do this by the GUI but I don't remember how :)

---

### Post by theDaveTheRave on 2009-11-16
baltadt

did you ever get this problem sorted out?

if so, put instructions in here (if you can remember them) for any other users that may have a problem.

Or point people in the direction of where you went to solve your problem.

Remember to mark the thread as "solved".

David

---

### Post by baltadt on 2009-12-20
This might help others but when I turned off wireless and then connected it was fine.

---

### Post by theDaveTheRave on 2009-12-23
baltadt,

just out of curiosity, have you tried the following.

when you are connected via the ethernet device (ie a cable) you obviously have your wifi 'turned off'

what happen when you turn your wifi back on again?? does your ethernet get knocked out again, or does it stay connected ?

Either way this is a curious situation, I was of the impression that a computer would allways default to a wired connection when available. I guess that somehow something has given priority to the wifi card? Maybe it is related to the instaled modules.

On which note, what modules do you currently have installed for networking?


I would be interested to better understand this situation so if anyone has any ideas / comments I would personally be very gratefull.

---

