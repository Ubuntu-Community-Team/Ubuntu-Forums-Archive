---
title: "An interesting ipw3945 problem - (please for the love of god help me)"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by ubuntalicious on 2007-02-22
After trying to coax my dell1390 wireless to work for a couple of weeks, I finally gave in and ordered the intel 3945 card to replace it.  (Dell 640m)

I installed the 3945 and it works great when I boot into Windows, but Ubuntu refuses to even recognize that there is a wireless connection.  In desperation I reinstalled ubuntu from the alternate cd, so I am now running a clean version of Edgy, to eliminate any extraneous causes of the problem.

Here's the weird thing:  In the device manager, the wireless card is detected perfectly under PCI express port 2.  It lists the correct driver to be ipw3945, and everything.  Yet, my Network tool doesn't even show that I have a wireless connection available.  Here is some relevant output:



lshw:
```

        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0c:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ipw3945
                resources: iomemory:efdff000-efdfffff irq:177

```


iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


```


ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 00:15:C5:76:D1:BE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


```



This is very confusing to me because ubuntu seems to see my wireless card, but doesn't do anything with it.  It doesn't seem to be a hardware problem, because it works fine in windows.

One other thing, the wireless "on" light on the laptop stays off even when I press fn-F2 to turn it on (the other function commands seem to work fine).


Any help is most appreciated.


Thanks,
Ben

---

### Post by gradedcheese on 2007-02-23
run "ifconfig -a" and see if it's there...

---

### Post by ubuntalicious on 2007-02-23
> **gradedcheese said:**
> run "ifconfig -a" and see if it's there...

ifconfig -a yeilds:

```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:76:D1:BE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by gradedcheese on 2007-02-23
Is the module loaded?

```

lsmod | grep ipw3945

```

if not:

```

sudo modprobe ipw3945
ifconfig -a

```

---

### Post by ubuntalicious on 2007-02-23
> **gradedcheese said:**
> Is the module loaded?

```

lsmod | grep ipw3945

```

if not:

```

sudo modprobe ipw3945
ifconfig -a

```


yes, it appears to be loaded.

lsmod | grep ipw3945 yeilds:

```

ipw3945               124576  0 
ieee80211              35272  1 ipw3945

```

and after applying the second set of commands (just for good measure), ifconfig -a is still unchanged.

---

### Post by ubuntalicious on 2007-02-23
I've seen some posts that say that you should upgrade to Edgy .11, which has updated support for the ipw3945 driver, but I did that before and it didn't seem to make a difference.

I will go ahead and install all Edgy updates while I'm waiting for you guys to make some suggestions. :-\"


Thanks again,
Ben

---

### Post by sdide on 2007-02-23
Hey, 

can you do 

# cat /etc/network/interfaces | grep -v ^#

and post output

---

### Post by ubuntalicious on 2007-02-23
cat /etc/network/interfaces | grep -v^# yeilds:

```

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0
```

---

### Post by sdide on 2007-02-23
I'd add the following lines

```
auto eth1
iface eth1 inet dhcp

```

and do a reboot
The interface probably wont get an IP from DHCP, but at least you should see the interface.

and, please do a 

# cat /proc/net/dev
 and post output

---

### Post by ubuntalicious on 2007-02-23
I added those lines to /etc/network/interfaces and rebooted, but there seems to be no change in anything.  eth1 is still not recognized.

as for the /proc/net/dev output:

```
Inter-|   Receive                                                |  Transmit
 face |bytes    packets errs drop fifo frame compressed multicast|bytes    packets errs drop fifo colls carrier compressed
    lo:     100       2    0    0    0     0          0         0      100       2    0    0    0     0       0          0
  eth0:  361529     543    0    0    0     0          0         6    57617     392    0    0    0     0       0          0
  sit0:       0       0    0    0    0     0          0         0        0       0    0    0    0     0       0          0

```

by the way, i have eth0 hooked up to my network right now, so that's why you see packets there.

---

### Post by sdide on 2007-02-23
hmmm

Can you post  iftab?

# cat /etc/iftab

---

### Post by ubuntalicious on 2007-02-23
cat /etc/iftab:

```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac *my NIC's MAC displayed here* arp 1

```

Thanks for your help so far.

---

### Post by sdide on 2007-02-23
I am not sure.

Somehow your wireless is missing its MAC address.
It didn't list in lshw either. Which mine does.
you should have had a eth1 entry in iftab. 

try 

# discover --enable=pci

but thats a guess.

---

### Post by ubuntalicious on 2007-02-23
nope, no dice.  I'll check my bios and see if there's anything weird with Dell's management of a different wireless card, but i really doubt that.

any other suggestions?

---

### Post by sdide on 2007-02-23
Post 
/var/log/boot

---

### Post by ubuntalicious on 2007-02-23
I've been looking at some other threads and it seems that some other people with eht dell e1505 are having a very similar problem (which was never resolved).  I'm wondering if the fact that my wireless toggle button Fn-F2 doesn't switch it on and off is the problem.  Seems a little bit like the chicken and the egg...  Is is off because it's not working, or is is not working because it's off????

---

### Post by sdide on 2007-02-23
If that really is the case, it sounds hardware related. 
I did have a similar problem once, with bluetooth on my T42p. To turn it on, I needed to write "enable" to a file in the /proc filesystem.

echo enable > /proc/acpi/ibm/bluetooth

in your case it could be something similar, or it could be a BIOS setting. I don't know.

---

### Post by featherking on 2007-02-23
FWIW, i could never get my wireless running unless i changed the wireless bios setting to 'always on'

Running a dell e1405 and the ipw3945, basically same as you..

---

### Post by ubuntalicious on 2007-02-24
Okay, the bios is now set to have wireless always enabled, and this seems to be the case because the wireless light is always on when I boot windows.  So that eliminates the bios as the possible culprit.

Booting back into Ubuntu, however, the light still stays off.  The other function keys work in ubuntu, so I'm inclined to believe that the function keys aren't the problem.  With the wireless always enabled in the bios, this is a moot point anyway.  

So it must be something else.  Any other thoughts?

---

### Post by sdide on 2007-02-24
Hey, 

I am out of options myself, have you checked the link below?

[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

---

### Post by gradedcheese on 2007-02-24
indeed, at this rate I'd serious consider grabbing the linux-headers-`uname -r` package, downloading the driver source from the link sdide posted, and building the latest version for your kernel.  You'll also need the build-essential package, otherwise it's not a very difficult thing to do.

---

### Post by daemon15 on 2007-02-24
I've been following this thread while trying to figure out  a very similar problem.  I've an ASUS Z96J with the 3945 and Edgy detected the card fine, loaded drivers, and lit the indicater LED but the network tool wouldn't show the interface.  I seem to have solved the problem so I'll throw out what I think happened.

My laptop has a core 2 duo so I had to change the default kernel from 2.6.17-11-386 to 2.6.17-11-generic to get SMP working.  What I failed to do was change the linux-restricted to match the generic kernel.  After installing linux-restricted-modules-2.6.17-11-generic and rebooting, wireless show up properly.

I'm away from my wireless network so I haven't gotten further but I'll post as I make progress.

---

### Post by ubuntalicious on 2007-02-24
Okay, I have my wireless working.  Thanks for the suggestions.

What ended up working was when I installed the linux restricted package for my system (in my case linux-restricted-modules-2.6.17-11-generic_2.6.17.7-11.1_i386.deb).  I had tried doing this before but I think that it didn't work those times because I had already killed my wireless in a different way when trying to update the 80211 driver (required for a manual update of the ipw3945 driver) due to install errors.

So hopefully my experience will be useful to others.  Here's what to do if you are in my situation:

FIRST try installing the most updated linux-restricted-modules package onto your system and reboot.  For me, that's all it took.  This satisfies the need to install the updated ipw3945 drivers by hand, and since the manual process is much more prone to problems (as was very much true in my case), I'd avoid it unless you're sure it's what you need to do. 


Gradedcheese, sdide, and daemon15: thanks for your help, I appreciate it!

---

### Post by trubblemaker on 2007-02-27
glad to see you found help, while I was searching for help for you I found an interesting power saving link for ipw3645 and ipw2200 so I'll post it here as you all seem to use the same card

[http://ubuntuforums.org/showthread.php?t=339089](http://ubuntuforums.org/showthread.php?t=339089)

cheers.

---

### Post by dphoebus on 2007-03-05
Check this article out....

[http://www.ubuntuforums.org/showthread.php?p=2253754#post2253754]("http://www.ubuntuforums.org/showthread.php?p=2253754#post2253754")

Hope this helps everyone...

---

### Post by locu on 2007-04-16
can anyone post for me who i can update my system to 

linux-restricted-modules-2.6.17-11-generic_2.6.17.7-11.1_i386.deb as im hoping it will solve my wireless problem to

---

