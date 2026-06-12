---
title: "wireless trouble"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by The Drew on 2006-12-01
I didn't want to add my problem to the existing thread, so I started my own.  I apologize if that is bad protocol.

I saw on the other thread that the person was asked to post the results of several things, so I'll post those to see if it helps:

***
first:  "ifconfig -a"
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:99:E6:FB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:4A:47:54  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6496 (6.3 KiB)  TX bytes:6496 (6.3 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

***
second:  "cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


***
third:  "iwlist scanning"

lo        INterface does not support scanning
eth1      No scan results
eth2      Interface does not support scanning
sit0      Interface does not support scanning


***
Last:  "sudo lshw -C network"

  *-network
       description: Ethernet interface
       product: 88E8036 Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:99:e6:fb
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sky2 driverversion=1.4 firmware=N/A link=no multicast=yes port=twisted pair
       resources: iomemory:b4000000-b4003fff ioport:3000-30ff irq:58
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@06:04.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:4a:47:54
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-26-386 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:b8004000-b8005fff irq:169


***
Any help would be greatly appreciated.  I hope to be able to get my wireless internet running on Ubuntu so that I can leave Windows behind....

---

### Post by spd106 on 2006-12-02
Hi,

Try this thread, [http://www.ubuntuforums.org/showthread.php?t=285809](http://www.ubuntuforums.org/showthread.php?t=285809)
report any problems or success back here.

Good luck

---

### Post by The Drew on 2006-12-02
where do I go on the web to download ndiswrapper?

---

### Post by The Drew on 2006-12-03
okay.

I got ndiswrapper and the proper drivers.

my current hurdle:
When I get to the step in the ndiswrapper installation step that says to put in "make uninstall" it comes up with a message saying that it doesn't recognize "make" as a command.

Is there something I'm missing/screwing up?

Thanks in advance.

---

### Post by spd106 on 2006-12-03
No, don't try to build it from source without trying the pre-built version first.

As the guide I linked says, go to the 'System' menu, then 'Administration', then open 'Synaptic Package Manager'.

In here click on reload to refresh the package list then scroll down until you see ndiswrapper-utils. Double click on it and then click apply.

Since you've used the terminal before, you can use this command instead, ```
sudo apt-get update && sudo apt-get install ndiswrapper-utils-1.8 ndiswrapper-common
```

Either way this is the better solution as you won't have to install gcc, kernel headers etc. Nor will you have to rebuild ndiswrapper every time there is a kernel update. Though you will have to go down this path if it doesn't work.

Consider installing ndisgtk as well, this is a gui wrapper for the ndis wrapper for the wireless driver.

---

### Post by spd106 on 2006-12-03
Just for completeness, the make tool, along with the other packages needed will be installed with the 'build-essential' meta package.

Do a search in the wiki for ndiswrapper to find a guide for the build from source process.

---

### Post by The Drew on 2006-12-03
I can't get ndiswrapper through Synapse because I cannot connect to the internet through Ubuntu.

I tried to install the build-essential package earlier, and was given "error:  dependency is not satisfiable: gcc"

---

### Post by The Drew on 2006-12-03
update:  I got ndiswrapper through the Ubuntu disk, and I got some drivers from the 4318 howto thread.  But I ran into some problems, and something messed up.  I'm in the process of finding out exactly what.  I think the log says something about not being able to find the drivers to install.

They are currently on my desktop, should I put them somewhere else?

---

### Post by spd106 on 2006-12-03
Make sure that when you run the driver install that you are in the directory that contains the driver. In your case you probably want to cd to the Desktop. ```
cd Desktop
```
Sorry, I'm used to installing from the alternate cd, which contains the ndiswrapper-utils package. So there's no need to download it, apt just asks for the disk to be inserted. I'm not sure if that's the case with the desktop/live cd.

Build-essential relies on a net connection since there are a lot of dependencies. It would take a lot of work to find them all.

---

### Post by The Drew on 2006-12-03
Problems solved!
I am currently online on Ubuntu through my wireless connection.

Thanks for the help.

---

### Post by jamiebux on 2006-12-15
I have a question. I got my wireless working, somewhat, using the bcm43xx tarball. The only problem I'm having is that I can't scan for networks. Even in the bcm43xx script install log, it says that my wireless card will not scan. I have used Network Manager and wifi radar, but nothing has worked. I really need help with this on. I have a Pavilion dv5210 laptop and I have upgraded and configured the wireless card in my BIOS. I really don't know what to do next. Any ideas would help please. My wireless card actually worked perfectly in Freespire. Nothing else did though. 8)

---

