---
title: "Network Monitor 2.12.1 &quot;Configure&quot; button errors"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by cr0atian on 2008-04-30
Folks (yes, that means you),

I would like some assistance with seemingly trivial task and one that isn't going to require your urgent attention, but nevertheless is important to me because of the "annoyance" effect it has on my ever more curious and expanding mind.

I have Ubuntu 8.04 that I '**apt-get dist-upgrade**'-ed from the previous Gutsy release. My eth0 works just fine, I have connection, so that's not a problem at all. The problem is that both the "Network Tools" (aka. gnome-nettool 2.22.0) and the "Network Monitor 2.12.1 have this "Configure" button, which are only capable of producing the following error:

[INDENT]**The interface does not exist**
Check that it is correctly typed and that it is correctly supported by your system.
                            **"[X Close]"**
[/INDENT]

Like I said, everything else works, including my "Network" applet (aka. network-admin), which once unlocked lets me do whatever it's designed to do.

I tried looking into my /etc/network/interface file and made minor clean-up changes just to make it simple and more "conforming" to the Ubuntu standard. Namely removed some non-existent interface, not needed hashed lines and left it with just my lo and eth0 settings. I did '**sudo /etc/init.d/networking restart**' after that, but still no candy.

I tried checking further to see what my Ubuntu thinks it has under the hood and here's the output of '**lshw -C network**', 

[INDENT]  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:7c:68:0d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751-v3.44a ip=192.168.0.217 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s[/INDENT]

Then I also looked at '**sudo ifconfig&&iwconfig**', which shows this:

[INDENT]eth0      Link encap:Ethernet  HWaddr 00:13:72:7c:68:0d
          inet addr:192.168.0.217  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe7c:680d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7367757 (7.0 MB)  TX bytes:3524000 (3.3 MB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:160982 (157.2 KB)  TX bytes:160982 (157.2 KB)

lo        no wireless extensions.

eth0      no wireless extensions.
[/INDENT]

Any idea what's going on? :confused:

Croatian

---

### Post by cr0atian on 2008-05-01
Here I am a day later and I still don't see anyone responding to this topic. Any takers?

Croatian

---

### Post by jeluranni on 2008-05-01
I'm receiving the same error when I click on the configure button. Don't know how to fix it.

---

### Post by Bradl3yJ on 2008-05-01
Same here, can anyone confirm that this IS working for them? I have the error both for eth0 and wlan0

---

### Post by nowshining on 2008-05-01
hmm on gutsy i had to use:

lshw -enable network > ~/network


~/network is the saved txt file in my home folder where all the output info. went. :)

---

### Post by cr0atian on 2008-05-02
Thank you, but there is no such file on my machine. Besides, you are simply redirecting the screen output to a text file. What good will that do other then to be able to send it to someone? Just to humor myself I tried it, but it makes no difference - of course. The output of that command is a simple dump of all devices present on the system, regardless of their relation to the network interface. File or no file, the only network related items I found are those in /etc/network, mainly dealing with the way the system should react to a particular network interface state and the collection of related processes and services it should invoke accordingly.

Croatian

---

### Post by superman66 on 2008-05-16
I am getting the same error message, I am able to view Wireless networks in the Network tool System - Administration - Network. but when i try to configure it from Connection properties i get that error too.

Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

Anyone get this to work??

---

