---
title: "Acer 7520-5071 Fresh Install, I am stumped!"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by carl99fan on 2008-07-19
This is my orignal post in the General thread.

[http://ubuntuforums.org/showthread.php?t=857454](http://ubuntuforums.org/showthread.php?t=857454)

I have read the stickys and I still don't get it.
Sorry some if this is still over my head.

---

### Post by carl99fan on 2008-07-19
I still have Visa on this machine as well. if I am reading this correctly all I need to do is get the drivers from windows and bring them to the ndswrapper or something like that. if this is true I THINK I have found the drivers I need, although I don't understand which one it is or how to use is when I obtain it.

---

### Post by jeremyswalker on 2008-07-20
You need to compile the patched driver and install it. Download from: [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz]("http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz"). Hopefully you have some way of connecting your laptop to the net, like a wired connection. You need to be sure you have certain packages. In a terminal, type: 
```
sudo apt-get install build-essential make
```

  After those are installed, navigate to the directory location of the downloaded driver tarball in the terminal. Now type:
```
tar -xvzf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007.tar.gz
make
sudo make install
reboot
```


  This is all I had to do on my laptop. I have the same wireless card as you. However, if this does not work for you, there is a much more involved and thorough tutorial that may: [http://ubuntuforums.org/showthread.php?t=795984]("http://ubuntuforums.org/showthread.php?t=795984").

---

### Post by zipperback on 2008-07-20
Please provide the output from:

```

lspci

```

I have an acer laptop and can probably help you.

I have a fresh install of Hardy 8.04 on it and Wifi works no problem.

- zipperback
:popcorn:

---

### Post by carl99fan on 2008-07-20
> **zipperback said:**
> Please provide the output from:

```

lspci

```

I have an acer laptop and can probably help you.

I have a fresh install of Hardy 8.04 on it and Wifi works no problem.

- zipperback
:popcorn:

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by carl99fan on 2008-07-20
> **jeremyswalker said:**
> You need to compile the patched driver and install it. Download from: [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz]("http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz"). Hopefully you have some way of connecting your laptop to the net, like a wired connection. You need to be sure you have certain packages. In a terminal, type: 
```
sudo apt-get install build-essential make
```

  After those are installed, navigate to the directory location of the downloaded driver tarball in the terminal. Now type:
```
tar -xvzf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007.tar.gz
make
sudo make install
reboot
```


  This is all I had to do on my laptop. I have the same wireless card as you. However, if this does not work for you, there is a much more involved and thorough tutorial that may: [http://ubuntuforums.org/showthread.php?t=795984]("http://ubuntuforums.org/showthread.php?t=795984").


It does not like the second line of code you provided. And i am not cool enough to make needed changes lol

but I did download and I do this: tar -xvzf madwifi-nr-r3366+ar5007.tar.gz but that is as far as I was able to get for now.... :(

---

### Post by carl99fan on 2008-07-20
> **jeremyswalker said:**
> You need to compile the patched driver and install it. Download from: [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz]("http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz"). Hopefully you have some way of connecting your laptop to the net, like a wired connection. You need to be sure you have certain packages. In a terminal, type: 
```
sudo apt-get install build-essential make
```

  After those are installed, navigate to the directory location of the downloaded driver tarball in the terminal. Now type:
```
tar -xvzf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007.tar.gz
make
sudo make install
reboot
```


  This is all I had to do on my laptop. I have the same wireless card as you. However, if this does not work for you, there is a much more involved and thorough tutorial that may: [http://ubuntuforums.org/showthread.php?t=795984]("http://ubuntuforums.org/showthread.php?t=795984").
OK. I did it, i was not used to changing directories but I figured it out, as it was the second time. I still don't see any action.
I will retry old steps now.

---

### Post by carl99fan on 2008-07-20
I have found some good instructions HERE: [https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64](https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64)

Now I notice is says my system needs to be clean...
Well I have tried so many things at this point although I'm not sure what he is talking aout, I AM sure my system is no longer "clean"

Could someone please advise me on how I may clean or purge so I can "start over"

Thank you.

---

### Post by carl99fan on 2008-07-20
> **carl99fan said:**
> I have found some good instructions HERE: [https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64](https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64)

Now I notice is says my system needs to be clean...
Well I have tried so many things at this point although I'm not sure what he is talking aout, I AM sure my system is no longer "clean"

Could someone please advise me on how I may clean or purge so I can "start over"

Thank you.

No that is not going to help. the links are no good, and it's just not right.

---

### Post by jeremyswalker on 2008-07-21
If you followed all of my steps, try left clicking on the network manager icon in the notification area of the panel. If it shows the wireless network you want to connect to, then click on it. You will need to provide the access key of the network you are trying to connect to.

If it does not show your network after left clicking, try right clicking and make sure "Enable Wireless" is checked. If that is not even an option, then post the output of the following commands:
```
ifconfig
```
```
iwconfig
```

I know that your card will work, so have faith.:)

---

### Post by carl99fan on 2008-07-21
john@john-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:77:ba:ca  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe77:baca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69039094 (65.8 MB)  TX bytes:14805915 (14.1 MB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35426 (34.5 KB)  TX bytes:35426 (34.5 KB)

john@john-laptop:~$

---

### Post by carl99fan on 2008-07-21
john@john-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

john@john-laptop:~$

---

### Post by jeremyswalker on 2008-07-22
Hmmm...
Try to type:
```
sudo modprobe ath_pci
```
See if that brings up any options from the network manager applet (same way I described in a previous post). If not, run the ifconfig command again. You are looking for a device with a notation such as 'ath0' or 'wlan0'. If nothing, then I would recommend following the in-depth guide I mentioned earlier. It seems a lot of people were having success with it. 

But, let's review the steps you took.

Step one: Downloaded the patched madwifi driver.
Step two: Extracted packaged driver.
Step three: Installed packages: build-essential and make
Step four: Within the newly created driver directory, entered code:  make
Step five: Then: make install
Step six: reboot

If those steps did not work, please note any errors that were displayed during the 'make' and 'make install' process. As I said, these worked for me. At this point, if this doesn't make your card work, follow the more in-depth guide. Just don't give up! Like I said, I have the same card, and mine works.

---

### Post by jeremyswalker on 2008-07-22
By the way, where in Ohio are you? I'm on the outskirts of Toledo, myself.

---

### Post by carl99fan on 2008-07-22
I will try later. I am reinstalling Ubuntu the owner of this unit wants Ubuntu and Ubuntu only on it. So I am going to wipe it and install Ubuntu over the old VISTA lol

I am smiling the whole time...

I will retry everything .....I say about 10-10:30pm EST

Without saying too much in forums.... I am VERY Close.
Airport Hwy

Small world.

---

### Post by jeremyswalker on 2008-07-23
WOW! I'll say you are. I think that's the first time I've ever talked to someone that close. I'm close to the truck stops, on the other side. It certainly is a small world.

---

### Post by carl99fan on 2008-07-23
john@john-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:77:ba:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:682 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:795937 (777.2 KB)  TX bytes:146698 (143.2 KB)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17000 (16.6 KB)  TX bytes:17000 (16.6 KB)


john@john-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


**And here is my output from the make install deal.**

john@john-laptop:~/Desktop$ cd madwifi-ng-r3366+ar5007
john@john-laptop:~/Desktop/madwifi-ng-r3366+ar5007$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-20-generic/build SUBDIRS=/home/john/Desktop/madwifi-ng-r3366+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-20-generic'
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath/if_ath.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath/if_ath_radar.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath/if_ath_pci.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath/ath_pci.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_hal/ah_os.o
  HOSTCC  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_hal/uudecode
  UUDECODE /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_hal/x86_64-elf.hal.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_hal/ath_hal.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/amrr/amrr.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/minstrel/minstrel.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/onoe/onoe.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/sample/sample.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/if_media.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_skb.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_beacon.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_crypto.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_crypto_none.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_input.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_node.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_output.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_proto.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_scan.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_wireless.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_linux.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_monitor.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_rate.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_acl.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_scan_ap.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_scan_sta.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_xauth.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_wep.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_tkip.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_ccmp.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_acl.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_xauth.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_scan_sta.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/ath/ath_pci.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath/ath_pci.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_hal/ath_hal.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_hal/ath_hal.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/sample/ath_rate_sample.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_acl.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_acl.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_ccmp.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_ccmp.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_scan_ap.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_scan_sta.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_tkip.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_tkip.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_wep.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_wep.ko
  CC      /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_xauth.mod.o
  LD [M]  /home/john/Desktop/madwifi-ng-r3366+ar5007/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-20-generic'
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/tools'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wlanconfig.c
gcc -o ath_info -g -O2 -Wall ath_info.c
make[1]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/tools'
john@john-laptop:~/Desktop/madwifi-ng-r3366+ar5007$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-20-generic/build SUBDIRS=/home/john/Desktop/madwifi-ng-r3366+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-20-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-20-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.24-20-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath'
test -d //lib/modules/2.6.24-20-generic/net || mkdir -p //lib/modules/2.6.24-20-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.24-20-generic/net
make[1]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath'
make[1]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_hal'
test -d //lib/modules/2.6.24-20-generic/net || mkdir -p //lib/modules/2.6.24-20-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.24-20-generic/net
make[1]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_hal'
make[1]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/amrr'
test -d //lib/modules/2.6.24-20-generic/net || mkdir -p //lib/modules/2.6.24-20-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.24-20-generic/net
make[2]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/amrr'
make[2]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/onoe'
test -d //lib/modules/2.6.24-20-generic/net || mkdir -p //lib/modules/2.6.24-20-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.24-20-generic/net
make[2]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/onoe'
make[2]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/sample'
test -d //lib/modules/2.6.24-20-generic/net || mkdir -p //lib/modules/2.6.24-20-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.24-20-generic/net
make[2]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/sample'
make[2]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/minstrel'
test -d //lib/modules/2.6.24-20-generic/net || mkdir -p //lib/modules/2.6.24-20-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.24-20-generic/net
make[2]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate/minstrel'
make[1]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/ath_rate'
make[1]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/net80211'
test -d //lib/modules/2.6.24-20-generic/net || mkdir -p //lib/modules/2.6.24-20-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.24-20-generic/net; \
	done
make[1]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/net80211'
(export KMODPATH=/lib/modules/2.6.24-20-generic/net; /sbin/depmod -ae 2.6.24-20-generic)
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/tools'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/tools'
make -C ./tools  install || exit 1
make[1]: Entering directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig ath_info; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
make[1]: Leaving directory `/home/john/Desktop/madwifi-ng-r3366+ar5007/tools'
john@john-laptop:~/Desktop/madwifi-ng-r3366+ar5007$ 


Hell man, I work on Enterprise blvd, near the Meijer on Alexis.
I am doing this for a friend, but I really just wanted more experience Installing Ubuntu and to give the 64 bit version a try..... 
I was not able to get it all done last night, as my router was in need of being reset but I was 2 busy watching first48 to notice.
Useless information.....my forte' 

Still no luck.........

---

### Post by jeremyswalker on 2008-07-24
So you are trying this on the 64-bit version?


I am actually up around there quite a bit. The mechanic's shop for the place I work is on Matzinger, by the tracks near Enterprise.

---

### Post by jeremyswalker on 2008-07-24
If you are using 64-bit, check out this link: [http://ubuntuforums.org/showthread.php?t=816780]("http://ubuntuforums.org/showthread.php?t=816780")

I haven't had any experience with the 64 bit version.

---

### Post by carl99fan on 2008-07-26
I just got the Laptop back today.

I am installing the 32 bit version.

I will let you know.

---

### Post by carl99fan on 2008-07-26
> **jeremyswalker said:**
> You need to compile the patched driver and install it. Download from: [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz]("http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz"). Hopefully you have some way of connecting your laptop to the net, like a wired connection. You need to be sure you have certain packages. In a terminal, type: 
```
sudo apt-get install build-essential make
```

  After those are installed, navigate to the directory location of the downloaded driver tarball in the terminal. Now type:
```
tar -xvzf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007.tar.gz
make
sudo make install
reboot
```


  This is all I had to do on my laptop. I have the same wireless card as you. However, if this does not work for you, there is a much more involved and thorough tutorial that may: [http://ubuntuforums.org/showthread.php?t=795984]("http://ubuntuforums.org/showthread.php?t=795984").

Thanks for helping me through this.

I am posting from the Laptop and I am wireless.

Thought I was the only Linux user in the city!! lol

If you stop by my website in my signature you can send me E-mail.

---

### Post by jeremyswalker on 2008-07-26
Awesome! Congrats! I knew it would work. I'll have to take a crack at a 64-bit version someday.

I'm sure there are more of us around town. Linux is growing.

---

