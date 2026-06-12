---
title: "No network connection in Lubuntu 14.04."
date: 2014-07-24
forum: Networking &amp; Wireless
---

### Post by Advice Pro on 2014-07-24
I did add the nm pplet via The Default applications for LXSession and if I right-click on the icon in the taskbar I have Enable Networking checked, yet Firefox reads Server not found.

---

### Post by varunendra on 2014-07-27
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Advice Pro on 2014-07-29
I forgot to mention that Lubuntu is on Virtualbox.  This is the output to the command in your links post:

```
--2014-07-29 14:49:40--  [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... failed: Name or service not known.
wget: unable to resolve host address ‘dl.dropbox.com’
```

---

### Post by varunendra on 2014-07-29
There is also a way to manually download and run the script, mentioned in the post I linked to.

But since it is a VM, is its virtual network adapter configured and is set to 'Connected' state in the VM's settings?

What is the output of -
```
sudo lshw -C network
ifconfig -a
```?

---

### Post by Advice Pro on 2014-07-30
```

luis@luis-VirtualBox:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 02
       serial: 08:00:27:41:e8:a5
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:19 memory:f0000000-f001ffff ioport:d010(size=8)

```
```

luis@luis-VirtualBox:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 08:00:27:41:e8:a5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:161840 (161.8 KB)  TX bytes:161840 (161.8 KB)
```

---

### Post by varunendra on 2014-07-30
"link=no" in 'lshw' output suggests the virtual network adapter is probably not set to 'connected' in the virtual machine settings. Have you checked them? How have they been configured? NAT? Bridged? Host-Only? Set to "Auto connect when the vm starts"?

If unsure, pleas post a screenshot of the screen that shows the virtual network adapter settings.

If sure that everything is okay there, try this in Lubuntu VM -
```
sudo mii-tool -F 100baseTx-FD eth0
```
I'm not sure mii-tool is installed by default or not in Lubuntu. Even if it is, it does not support all devices, so may fail with some error message. If that happens, you may have to install 'ethtool' somehow.

If things come down to 'ethtool', does..
```
apt-get install --print-uris ethtool
```
..return the download URIs of the package(s) required to install ethtool?

---

