---
title: "Problems with Belkin: Wireless Desktop Network Card F5D6001"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by sendblink23 on 2008-08-09
Problems with Belkin: Wireless Desktop Network Card F5D6001

Well I was trying to figure how to make it work.. during the process I messed up my BOOT & Lots of other stuff of Ubuntu, so I decided to *Erase partition & Refresh Install again Ubuntu (just to make sure I don't have anything messed up, on any of the commands i had made before from terminal)

Well now that I'm Fresh New again in Ubuntu, can anybody help me out Again how to be able to fix it?? YES I have internet through connected in LAN Ethernet, I updated everything of Ubuntu, I have Flash working on Youtube (still haven't fix the sound for Youtube page)... Anyways I really need to be connected through Wireless *personal Reasons ;) (And the *Wireless doesn't appear in the GUI of NETWORK)

*NOTE I'm a NOOB, so please explain NOOBIE WAY*

---

### Post by sendblink23 on 2008-08-09
Any Help?? its already been posted for 20 minutes?

---

### Post by sendblink23 on 2008-08-09
MEGA TRIPLE BUMP  

i have another question tooo??

This command fixes the sound Problem:
```
killall pulseaudio
```

But everytime I boot back again "Restart", I still go again without any sound, but yes I have to execute again that command always to have sound Working...

ANY WAYS TO KEEPING THAT COMMAND Permanently *ON* Always for every Boot (Restart) of Ubuntu ??

---

### Post by sendblink23 on 2008-08-09
And my hardware does show *Present..

```
sendblink23@sendblink23-desktop:~$ sudo ndiswrapper -l
bel6001 : driver installed
	device (1799:6001) present
sendblink23@sendblink23-desktop:~$ 

```

I was trying to follow This: [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

Here is where i have my problem during this Method:

```
5. Activating your wireless card via terminal

Here is everything you should need to know for bringing up a wireless (or any internet connection) from the terminal. Keep in mind that your wireless connection may not always be called wlan0. For example, my interface is eth1. the command "iwconfig" should give you the interface name.

To scan for a wireless network (essid)
Code:

sudo iwlist wlan0 scan

To bring up the interface
Code:

sudo ifconfig wlan0 up

To bring down the interface
Code:

sudo ifconfig wlan0 down

To connect to a router
Code:

sudo iwconfig wlan0 essid ID key k

where "ID" is the name of the router you want to connect to (returned by iwlist scan wlan0), and "k" is the network key to connect to the router

Now that you know what each command does, here is what most people should have to type into their terminal
Code:

sudo iwlist wlan0 scan
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid ID key k

I am unsure if this terminal method works with WPA encryption, so keep that in mind, as I use WEP because of the difficulty I have had with WPA in general. In theory it should work, but I don't know if thee are any extra steps to it.
```


Well how can i get "Keep in mind that your wireless connection may not always be called wlan0. For example, my interface is eth1. the command "iwconfig" should give you the interface name."

I tried that and this is what it shows for me:
```
sendblink23@sendblink23-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sendblink23@sendblink23-desktop:~$ 

```


Any help there?



,.....

Then ...

I just found this wierd ...

Can anybody verify whats going on here and well can this Info help you guys help me??

```
sendblink23@sendblink23-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:d8:f2:07:16  
          inet addr:10.0.0.64  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fef2:716/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3535677 (3.3 MB)  TX bytes:259133 (253.0 KB)
          Interrupt:21 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:105800 (103.3 KB)  TX bytes:105800 (103.3 KB)


```
```

sendblink23@sendblink23-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:f2:07:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.0.0.64 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Wireless PCI Card - F5D6001
       vendor: Belkin
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
sendblink23@sendblink23-desktop:~$ 
```

---

### Post by sendblink23 on 2008-08-09
Bummp Bummpppp

---

### Post by sendblink23 on 2008-08-10
Hello???  Does anybody want to help me???

---

