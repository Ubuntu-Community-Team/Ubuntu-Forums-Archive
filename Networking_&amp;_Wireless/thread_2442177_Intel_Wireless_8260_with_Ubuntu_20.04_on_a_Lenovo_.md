---
title: "Intel Wireless 8260 with Ubuntu 20.04 on a Lenovo T460s"
date: 2020-04-30
forum: Networking &amp; Wireless
---

### Post by abraham.varricatt on 2020-04-30
Hello folks!

After installing Ubuntu 20.04 LTS on a Lenovo T460s laptop, I discovered that the wifi didn't work out-of-the-box. Eventually, I figured out how to get it functioning and am making this post to help others who may find themselves in a similar situation. It is important to note that I reinstalled Ubuntu from a bootable USB drive more than once to validate that these instructions work without a wired ethernet connection. 


Here is what I started off with,
ubuntu-20.04-desktop-amd64.iso ( md5sum: ea28c4fd933be55f9f01a5fa9e868490 )

**$ sudo dmesg | grep iwlwifi**

```

[    7.907731] iwlwifi 0000:04:00.0: Found debug destination: EXTERNAL_DRAM
[    7.907732] iwlwifi 0000:04:00.0: Found debug configuration: 0
[    7.908183] iwlwifi 0000:04:00.0: loaded firmware version 36.77d01142.0 op_mode iwlmvm
[    7.944448] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    7.954431] iwlwifi 0000:04:00.0: Applying debug destination EXTERNAL_DRAM
[    7.954786] iwlwifi 0000:04:00.0: Allocated 0x00400000 bytes for firmware monitor.
[    8.025068] iwlwifi 0000:04:00.0: base HW address: 14:ab:c5:c1:a1:bf
[    8.427584] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
[   10.921892] iwlwifi 0000:04:00.0: Applying debug destination EXTERNAL_DRAM
[   11.085450] iwlwifi 0000:04:00.0: Applying debug destination EXTERNAL_DRAM
[   11.166371] iwlwifi 0000:04:00.0: FW already configured (0) - re-configuring

```


**$ sudo lshw -C Network**


```

  *-network                 
       description: Wireless interface
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 3a
       serial: 14:ab:c5:c1:a1:bf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-26-generic firmware=36.77d01142.0 ip=192.168.0.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:130 memory:f4000000-f4001fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 21
       serial: 54:e1:ad:0c:24:3c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair

```

To get the wifi working, all I needed to do was edit a single text file. Yes, just a single text file. No need to installing random firmware from the internet or even compile new drivers! All that's needed is a text editor and the patience to power-cycle your system. The file in question is this one,

```

$ sudo vi /etc/modprobe.d/iwlwifi.conf

```

Yes, you will need to use sudo to edit the file. Here is how it looked like before any edits,

```

$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```


This is where things get tricky. The edit you need to make is going to depend on the kind of wifi network you are attempting to connect to. In my case, I am able to switch the wifi network on my router between a N network (running at 5G) and a G network (running at 2.4G), so I tested on both.


**_N network (running at 5G):_**

You need to enable antenna aggregation by adding the following line to the end of the file, 

```
options iwlwifi 11n_disable=8
```

Yes, it's weird that the setting is labelled "disable", but I was able to connect to my N-network with it! Here is how things should look like after you are done,

```

$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8

```

After making the edit, I power cycled my laptop. i.e. to turn it off and on again with the power button. Perhaps rebooting would also work, but I didn't try. When the system came online, after logging in, I was able to use the top-right menu to select my wifi network, enter the password and get connected. Opening Firefox to [https://www.speedtest.net/](https://www.speedtest.net/) gave me these results,

* ping 9ms
* download 143.82 Mbps
* upload 21.64 Mbps


**_G network (running at 2.4G):_**

You need to disable 802.11n by adding the following line to the end of the file, 

```
options iwlwifi 11n_disable=1
```

Here is how things should look like after you are done,

```

$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1

```

After making the edit, power-cycling my laptop and logging in, I was able to connect to my wifi network. :D Checking speedtest gave me the following results,

* ping 9ms
* download 21.58 Mbps
* upload 21.38 Mbps


It is very unfortunate that we can't switch between a G and N network without a reboot, but I'm happy that at least now the T460s connects. 

Hope this post helps others! (Please reply if it does, I'd like to know)

References (i.e. other internet places which helped me solve this issue):
[https://bugs.launchpad.net/ubuntu/+source/backport-iwlwifi-dkms/+bug/1849891](https://bugs.launchpad.net/ubuntu/+source/backport-iwlwifi-dkms/+bug/1849891)    (Markus's comment at #5 helped to point me in the right direction!)
[https://wiki.archlinux.org/index.php/Network_configuration/Wireless#iwlwifi](https://wiki.archlinux.org/index.php/Network_configuration/Wireless#iwlwifi)   ( the archlinux wiki is surprisingly useful! )


Yours sincerely,
Abraham V.

---

### Post by slickymaster on 2020-04-30
*Thread moved to **Networking & Wireless**.*

---

### Post by jeremy31 on 2020-04-30
This is an old upstream kernel bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630)
The only time I needed to use the 11n_disable=8 was for an old Intel Wifi+WiMax chipset for it to connect on an 11N only AP

---

### Post by abraham.varricatt on 2020-04-30
@jeremy31,

Skimming over the launchpad.net discussion you linked, it does not appear the to be the same issue as what I faced. The problem solved in the first post is of not being able to connect to a wifi network, but the launchpad issue talks of slower speeds after the wifi connection has been established.

If the Lenovo T460s had connected to the wifi network (i.e. being able to visit google.com or ubuntuforums.com on a browser) after a fresh 20.04 install, it is unlikely that I would have dug into any of this.  

-Abraham V.

---

### Post by jeremy31 on 2020-04-30
It is likely where the entire thing started.  Many devices have been added to iwlwifi since then and it all depends on the code for each device on how it is affected.  I have used Intel 3160/3165 wifi on HP laptops without needing to use the 11n_disable parameter, but I did need to disable wifi power management with ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by hygy2 on 2020-05-15
I have the same problem on a lenovo P50 with this intel card.

Is there a final solution?

---

### Post by Marcelo Fernández on 2020-08-10
Hi!

I've had exactly this issue with my Intel 8260 Wireless controller in my Lenovo T460s notebook. This is my device id:
```
$ lspci -nn
[...]
Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
```

... and I can confirm #5 answer has fixed the issue (changing /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf setting from 3 to 2).

> **jeremy31 said:**
> It is likely where the entire thing started.  Many devices have been added to iwlwifi since then and it all depends on the code for each device on how it is affected.  I have used Intel 3160/3165 wifi on HP laptops without needing to use the 11n_disable parameter, but I did need to disable wifi power management with ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

This is the upstream kernel bug:
[https://bugzilla.kernel.org/show_bug.cgi?id=203709](https://bugzilla.kernel.org/show_bug.cgi?id=203709)

It can be quickly identified searching for "No beacon heard and the time event is over already" in the dmesg output log.

Thank you!

---

