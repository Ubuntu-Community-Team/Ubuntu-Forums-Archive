---
title: "Freaking out (Wireless issues)"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by ATPJOE on 2010-07-01
I Googled this problem a million times, nothing is helping.

I have gotten my WPC54GS card to work on Ubuntu instantly. I decided to try Kubuntu, got that up and running, and no Wireless connection. At first it showed the Auto eth, and 802.11 thing under, but never found any networks or detected the card. So I tried Ndiswrapper. After trying to install the driver with that, now NO WIRELESS shows up ANYWHERE. It's 4AM in the morning, I'm pissed off...been dicking with this for 3 hours. It's never taken me this long to figure something out. Please PLEASE help me solve this. Throw any code at me for terminal. 

Thanks in advance. Im going to go cry now.

---

### Post by bumanie on 2010-07-01
Use this code in terminal > sudo lshw -C network and that will show if the wireless card is enabled or disabled. If it shows as enabled, you have a different issue than I have. Alternatively go to /var/lib/NetworkManger/NetworkManager.state and see if your wireless card is set to false - I can set it to true, but it reverts to false at the next boot. I have not found a fix as yet - possibly a kernel bug from an update, as the card used to work in 10.04. At least this may narrow things down a bit.

---

### Post by ATPJOE on 2010-07-01
> **bumanie said:**
> Use this code in terminal  and that will show if the wireless card is enabled or disabled. If it shows as enabled, you have a different issue than I have. Alternatively go to /var/lib/NetworkManger/NetworkManager.state and see if your wireless card is set to false - I can set it to true, but it reverts to false at the next boot. I have not found a fix as yet - possibly a kernel bug from an update, as the card used to work in 10.04. At least this may narrow things down a bit.

/var/lib/NetworkManger/NetworkManager.state  < that file is blank when I open it up. 

As for the code you had me run, this is what it gave me:
```
joe@Thinkpad:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:d0:59:cc:e4:ea
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=98.193.106.28 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:c0200000-c0200fff ioport:6400(size=64)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:c4000000-c4001fff

```

Also this is what I get when running ```
  tail /var/log/messages

```  :
```
joe@Thinkpad:~$ tail /var/log/messages
Jul  1 04:59:14 Thinkpad kernel: [ 5025.137042] usbcore: deregistering interface driver ndiswrapper
Jul  1 04:59:14 Thinkpad kernel: [ 5025.173096] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jul  1 04:59:14 Thinkpad loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver drivername
Jul  1 04:59:14 Thinkpad loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver drivername
Jul  1 04:59:14 Thinkpad kernel: [ 5025.260276] usbcore: registered new interface driver ndiswrapper
Jul  1 05:03:23 Thinkpad kernel: [ 5274.271276] usbcore: deregistering interface driver ndiswrapper
Jul  1 05:03:23 Thinkpad kernel: [ 5274.355952] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jul  1 05:03:23 Thinkpad loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver lsbcmnds
Jul  1 05:03:23 Thinkpad loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver lsbcmnds
Jul  1 05:03:23 Thinkpad kernel: [ 5274.485777] usbcore: registered new interface driver ndiswrapper

```

Somethings not right. My card is there. But I'm incapable of even clicking on the wireless settings tabs in my network manager thing, it's like it deleted the ability to do that.

---

### Post by nishant.singh28 on 2010-07-01
Just a thought...do you dual boot....If yes, it could have been you turned the WiFi off in the other OS. It happens. Also check if your WiFi antenna is connected properly....could be a loose connection. My webcam wasn't working and turned out to be a hardware fault.

---

### Post by ikeurb on 2010-07-01
Run ```
 ifconfig 
``` to see if the wireless adapter has an ip address.

Open /etc/network/interfaces. Your wireless card should be set up something like

```

# The wireless network interface
auto eth0
iface eth0 inet dhcp

```where eth0 is the name of the wireless card listed when you ran ifconfig.

Then run                                   sudo service network-manager restart

---

### Post by McRat on 2010-07-01
Hate to hijack but:

If a moderator sees this, perhaps you could temporarily change the title and insert paragraph concerning the board's clock being busted.

---

### Post by 3177 on 2010-07-01
If you have a broadcom card as i do, simple try the following.
go to one of your package managers and remove :
broadcom sta common, broadcom sta source.

I've had to do this many times after updating.
wireless pops right up afterwords

---

