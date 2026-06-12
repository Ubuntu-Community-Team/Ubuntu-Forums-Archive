---
title: "Network manager applet very flakey"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by JaggedOne on 2007-11-26
My network manager applet in ubuntu gutsy is being very flakey. Every time I close my laptop, sending the computer into memory suspension, and open it back up it breaks. 

There are three different ways that it breaks.

1. It will let me select and try to connect to a wireless network, but will spend forever connecting and never ever connect.

2. It will claim to be connected to whatever network I was connected to before I closed my laptop, however there is no network connectivity. Trying to connect to other networks at this point does absolutely nothing. 

3. It will simply say that it can not find any network devices. Nothing that I can find will change that message.

All three of these basically mean that I have no internet connection. The only fix I have found is to reboot and do a system restore every time.

I don't know if it is related but every time I reboot I get a weird message:
It says in red font "the system is rebooting" and below that some error about "G_IS_AN_OBJECT"

Please help.

---

### Post by JaggedOne on 2007-11-29
anyone?

---

### Post by tommcd on 2007-11-29
Run "sudo ifconfig -a" to find the name of your network device. If it is wireless device it will probably be wlan0. If wired ethernet it will likely be eth0. If you have more than 1 device, th device that has an inet address and a " Link encap:Ethernet" will be the one you want. Like this:
```

eth0      Link encap:Ethernet  HWaddr 00:11:D8:AD:4C:59  
          inet addr:192.168.0.117  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:426796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:298806 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:587641733 (560.4 MiB)  TX bytes:22992988 (21.9 MiB)
          Interrupt:17 Base address:0xc000 


```

So if it is wireless, and it is called wlan0, and you connect by dhcp, then do:
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
(to disable and reenable your wireless)
then do:
sudo dhclient wlan0 (to get an ip address) 
Hope this helps. If it works it will save you from rebooting at least.

---

### Post by JaggedOne on 2007-11-29
Very very very helpfull. Thanks :D

---

### Post by xardy on 2007-11-30
I have this problem too even when not closing he laptop lid. When i'm at school just working in ubuntu my wireless connection just drops and network manager still says I'm connected, when trying to select another network the manager doesn't do anything. Had to reboot everytime to get a new connection. Seems like a bug to me

Anyway thx for the workaround tommcd

---

### Post by danpre on 2008-04-06
I have found working[ solution]("https://bugs.launchpad.net/dell/+bug/172522") for DELL XPS m1330:

Note 1: This is ONLY necessary if your wireless lan interface is called "*_rename" I think.
Note 2: The names of your networks interfaces will change on first reboot

sudo rm /etc/udev/rules.d/70-persistent-net.rules
Then reboot to regenerate it.

DANIeL

---

