---
title: "[SOLVED] Wireless stopped working after 8.10"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by gmstalk on 2008-11-06
I see I am not the only one with this problem. My wireless worked fine on 2.6.24-19. I upgraded to 8.10 and now the wlan0 interface is gone. The suggested fixes do not work for me. I have a Dell Inspiron 1521.

sudo lshw -C Network
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

lspci
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

This is broken in both 2.6.24-21 and 2.6.27-7. Can someone help me please?

---

### Post by gmstalk on 2008-11-07
ifconfig shows no wlan interface. Does anyone know how to fix this?

---

### Post by epictete on 2008-11-07
Hi Gmstalk I've exactly the same problem: the wifi detection in network-manager was perfect under hardy 2.6.24-19 and doesn't work anymore under hardy with the new -21 version of the kernel and under intrepid.

My wifi device is an intel 4965.

philippe@linux-bqf:~$ dmesg | grep 4965
...
[   33.301621] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4

philippe@linux-bqf:~$ ifconfig
...
wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:89:58:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

---

### Post by gmstalk on 2008-11-07
I got wireless working (wired is not).

I used ndiswrapper for gnome (sudo apt-get install ndisgtk). I uninstalled my driver, and reinstalled it. 

I did 100 other things before, but I think this is the key. Let me know if you used ndiswrapper in the previous version and if uninstalling/reinstalling helps. If not I will share the other things I did that I assume made no difference. 

Now I have to figure out the wired problem. ugh!

---

### Post by epictete on 2008-11-08
I have read this in another post (sorry it's in french!):

[http://forum.ubuntu-fr.org/viewtopic.php?pid=2158899#p2158899](http://forum.ubuntu-fr.org/viewtopic.php?pid=2158899#p2158899)

J'ai réussi a "résoudre" ce problème de plantage en installant :
linux-backports-modules-2.6.27-7-generic (version 2.6.27-7.4) et linux-backports-modules-intrepid-generic (version 2.6.27-7.11).
Mais en faisant cela ma carte réseau RJ45 ne fonctionne plus du tout (plus de eth0, plus de lupiote allumé...)

The guy says that, after installing linux-backports-modules to resolve kernel panic with the pilot of his wifi device, his **wired connection** didn't work anymore. Maybe it could help you...

I never had to use ndiswrapper because network manager always prefectly detected all the wifi networks under 7.10 and 8.04 (with 2.6.24-19 not -21) without anything else to do!

I feel that to lose so fondamental a feature as wifi network, with an LTS release, that is no more functional, is not acceptable for an LTS, entreprise-class distribution!

---

