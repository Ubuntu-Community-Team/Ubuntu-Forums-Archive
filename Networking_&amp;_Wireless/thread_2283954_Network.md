---
title: "Network"
date: 2015-06-26
forum: Networking &amp; Wireless
---

### Post by AmazingTrans on 2015-06-26
[FONT=Helvetica]Today i tried copying the Ubuntu 14.04 bitnami VM to another PC. I select Copied from another machine, and also tried moved from another machine options.

When i power it up, i got the following: The machine could not configure the network interface.
I did ifconfig, i can see eth0 & lo.
```

eth0 LINK encap: Ethernet HWaddr aa:bb:cc:dd:ee:ff
inet6 addr: aabb::xxx:xxxx:xxxx:xxxx/64 scope:link
UP broadcast running multicast MTU:1500 metric:1
Rx packets:43 errors:0 dropped:0 overruns:0 frame:0
Tx packets:33 errors:0 dropped:0 overruns:0 carrier:0
collissions:0 txqueuelen: 1000
rx....
Interrupt:17 ...
lo ....
```

After doing a bunch of googling, i guess the ubuntu eth0 port has the old VM mac address.
From the help here, it seems that i have to rename the old mac to the new VM mac in the /etc/udev/rules.d/70-persistent-net.rules
But, when i last check /etc/udec/rules.d directory, there is only README file.

I tried ifconfig, it seems that there is no IP address associate with eth0 as well.[/FONT]
[FONT=Helvetica]I've tried renaming eth0 to eth1 in the network/interface file. Shutdown, re-generate the VM Mac address, and power back up.
Bitnami reports: The machine could not configure the network interface.'
Tried ifconfig, and I only have lo adapter, does not have eth1 adapter.[/FONT]
[FONT=Helvetica]What should i do here?[/FONT]

---

### Post by TheFu on 2015-06-26
Please post output:
**sudo lshw -C network**

"interfaces" file must match the actual hw name created by the OS during boot. You cannot have 2 systems on the same LAN segment with the same MAC, but if they are on different LANs, then it should be fine.  IME - the MAC address comes from the hypervisor - but I don't know **anything** about bitnami and you didn't mention which hypervisor was being used. The 5 hypervisors that I've used allow changing the MAC in the network settings for each VM. Just change 1 number/letter there (must be hex).

This may be a virtualization question more than a networking question. Hard to tell so far.

---

### Post by AmazingTrans on 2015-06-26
TheFu,

I guess i can't get lshw from apt-get. since i do not have any network connection on my ubuntu.

Not sure what hypervisor, but i am using vmware player to run my ubuntu. And i have selected bridged on the Vmware network settings.
Below here, the HWaddr matches my VMware player network settings.

[http://snag.gy/XihDC.jpg](http://snag.gy/XihDC.jpg) 
[http://snag.gy/m67YE.jpg](http://snag.gy/m67YE.jpg)

Here is my interfaces settings file
[http://snag.gy/p8nnS.jpg](http://snag.gy/p8nnS.jpg)

---

### Post by wildmanne39 on 2015-06-26
Hi, please use thumbnails or url's when posting images because many people have slow connections or a limit on bandwidth.
Thanks

---

### Post by QIII on 2015-06-26
And also use code tags when posting the results of you terminal commands, which will keep the emiticon character strings from turning in to smileys -- as well as making your post much easer to read.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by AmazingTrans on 2015-06-29
Wild Man, QII , got it!
Thanks.
Anybody knows why my eth0 dhcp doesn't get an IP address when i copy the VM from one pc to another PC?

---

### Post by AmazingTrans on 2015-06-29
I got the IP address working when i set the VMWare network to NAT. 
Then, i poweroff the vmware again, and set the network back to bridge, it started working again.
Not sure what I did here, but hopefully it help others.

---

