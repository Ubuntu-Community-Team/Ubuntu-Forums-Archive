---
title: "EW-7728In, Ralink chipset problem with drivers"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by Retor on 2008-06-29
Hi. Newbie Ubuntu attempt. 



The drivers for my PCI wireless network card wasn't downloaded automaticly, so I'm hoping for some assistance here. 

Ubuntu says: Ralink Unknown device 0601

Card: Edimax, [EW-7728In]("http://www.edimax.com/en/produce_detail.php?pd_id=225&pl1_id=1&pl2_id=44"), nMax Wireless 802.11n PCI Card

I downloaded the files at the bottom, but have no idea what to do with them. So I googled. 

I found a thread that said: "the 0601 is a Ralink RT2800 chipset, it's pretty new". Then it instructed another guy to download [files here]("http://www.ralinktech.com/ralink/Home/Support/Linux.html"), but have no idea what to do with those either.

I found some other threads like [this one]("http://ubuntuforums.org/archive/index.php/t-609746.html") and [this one]("http://ohioloco.ubuntuforums.org/showthread.php?p=4054304"), that just plain scares me.

This might be necessary: 
2.6.24-19-generic


So. Any ideas? Any ideas that a newbie can understand.

---

### Post by chili555 on 2008-06-29
Scare you? C'mon, compiling from source is just clean fun!

First, be sure you have *build-essential* and *linux-headers-generic* installed. Synaptic is your friend. Then open a terminal and do, each command separately and in order:```
lspci -v
sudo lshw -C network
```Please verify you have a rt2860 device. If so, please proceed, if not, post back and tell us what you really have. Now do:```
wget http://www.ralinktech.com.tw/data/drivers/2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2
tar -xvzf 2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2
cd 2008_0522_RT2860_Linux_STA_v1.6.1.0
sudo su
```If your card will connect using WPA, we will have some adjustments to make:```
gedit os/linux/config.mk
```In line 11, change *HAS_WPA_SUPPLICANT=n* to *HAS_WPA_SUPPLICANT=y*; in line 14, change *HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n* to *HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y*. Proofread, save and close. Now, do:```
make
cp RT2860STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
make install
modprobe rt2860sta
```Does your device wink, blink and spring to life? Can you connect?

---

### Post by shaunconn on 2008-07-05
Hi

My make doesn't work - but it might be some of my dependencies since this is an initial install.  

When I try the make I get:

 make
make -C tools
make[1]: Entering directory `/home/shaun/Desktop/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools'
gcc -g bin2h.c -o bin2h
bin2h.c:28:19: error: stdio.h: No such file or directory
bin2h.c:29:20: error: string.h: No such file or directory
bin2h.c:30:20: error: stdlib.h: No such file or directory
bin2h.c: In function ‘main’:
bin2h.c:34: error: ‘FILE’ undeclared (first use in this function)
bin2h.c:34: error: (Each undeclared identifier is reported only once
bin2h.c:34: error: for each function it appears in.)
bin2h.c:34: error: ‘infile’ undeclared (first use in this function)
bin2h.c:34: error: ‘outfile’ undeclared (first use in this function)
bin2h.c:42: warning: incompatible implicit declaration of built-in function ‘memset’

Any ideas what I'm missing?

Shaun

---

### Post by chili555 on 2008-07-05
Yes. You are missing *build-essential* and *linux-headers-generic* which you can install, given an ethernet connection, with Synaptic.

---

### Post by shaunconn on 2008-07-05
Excellent

Many thanks - all works now!

Regards
Shaun

---

### Post by Retor on 2008-07-08
> **chili555 said:**
> Does your device wink, blink and spring to life? Can you connect?

Yes. Phew! It finally works. :)

The first day I attempted this, Ubuntu continuously froze. Then I went away for some days. Today it worked after:
- I had trouble downloading due to proxy problems
- the bz2 wouldn't unzip, cause it wasn't gzip format. But it worked when I used File Browser to unarchive.
- it wouldn't build cause I was missing some build-essential and stuff
- Then no Wireless folder so I had some "make install" trouble
- Finally roaming didn't work so I had to set it up manually

But it was also kind of exciting. In a technological adventurous way.

Thanks. I wouldn't be here without your help! :)

---

### Post by rrcs on 2008-07-24
> **Retor said:**
> - Then no Wireless folder so I had some "make install" trouble
I'm having the same troubles as you - what did you do here?

> **Retor said:**
> - Finally roaming didn't work so I had to set it up manually
I'm betting I will run into this problem, too, should I get so far - may I ask in advance for info on setting up the connection manually?

---

### Post by Retor on 2008-07-24
> **rrcs said:**
> I'm having the same troubles as you - what did you do here?


I'm betting I will run into this problem, too, should I get so far - may I ask in advance for info on setting up the connection manually?

I think I created the folders using File Browser, but can't remember anymore. Perhaps I should have written it down. 

I think I wrote in the name of the wireless network, set the encryption and wrote in the password. Yes. And I have to do this every time I connect. 

But I can't remember either for sure just now, as I'm in a mountain cabin on another computer. 

Hope it helps.

---

### Post by Half-Left on 2008-09-10
I just brought this card to get a better sign and thanks for the steps, working perfect, 100% sign.

---

### Post by hypher on 2008-09-21
I just bought this card as well, and got it working using the above steps. However, I am unable to use the 802.11n features of the card (I have an 802.11n network running on the 5ghz band and the card cannot see it). I tried setting the HAS_DOT11N_DRAFT3_SUPPORT flag to y in the config file, but that didn't fix it.

Any thoughts?

Thanks

P.S. I used the latest version of the driver, 1.7.0.0 rather than 1.6.1.0 as was specified above.

---

### Post by blauer-affe on 2008-11-25
i got another Wlan (Hama wlan 300 PCI) card i just cant get working...
my lshw -C network output:

*-network:0 UNCLAIMED   
       description: Network controller
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2

i tryed ndiswrapper and it clyms hardware present but it doesnt work...
i also tryed th steps posted here, make ends with:

/home/blaueraffe/Desktop/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.c:672: error: ‘struct net_device’ has no member named ‘nd_net’
make[2]: *** [/home/blaueraffe/Desktop/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.o] Error 1
make[1]: *** [_module_/home/blaueraffe/Desktop/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [LINUX] Error 2

im using Ubuntu 8.10 x64 
build-essential and linux-headers-generic are installed

looking forward to some answers, thx for your time!

---

### Post by blauer-affe on 2008-11-25
some progress...
i used the driver: 
RT2860PCI/mPCI/PCIe/CB(RT2760/RT2790/RT2860/RT2890)
RT2860WebUI 
from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

compiled it (no problems with make this time)

and set it up (following the README)
```
$ sudo cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
$ sudo /sbin/insmod os/linux/rt2860sta.ko
$ modprobe rt2860sta
```

now my lshw -C network output shows:
```

blaueraffe@blaueraffe-desktop:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=rt2860 latency=32 maxlatency=4 mingnt=2 module=rt2860sta
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth0
       version: 03
       serial: 00:50:70:aa:01:f6
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5788-v3.01 ip=192.168.178.26 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:ad:c9:b7:87:95
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT2860 Wireless


```
(NetXtreme BCM5788 Gigabit Ethernet is my lan card i currently use to post this)
but wlan is still not available...

any ideas?

---

### Post by blauer-affe on 2008-11-27
bump

---

### Post by blauer-affe on 2008-11-29
No ideas how i can get this card running?

---

### Post by M.Thulin on 2008-12-13
Hi  i have tried this and failed..  make log as follows

make -C tools
make[1]: Går till katalogen "/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools"
gcc -g bin2h.c -o bin2h
make[1]: Lämnar katalogen "/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools"
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux modules
make[1]: Går till katalogen "/usr/src/linux-headers-2.6.27-9-generic"
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/md5.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/mlme.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/action.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/ba_action.o
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/ba_action.c: I funktion "convert_reordering_packet_to_preAMSDU_or_802_3_packet":
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/ba_action.c:1391: varning: tilldelning skapar heltal från pekare utan typkonvertering
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/eeprom.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/dfs.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/assoc.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/aironet.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/auth.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/sync.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/sanity.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/connect.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/wpa.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.o
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c: I funktion "duplicate_pkt":
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:545: varning: att skicka argument 1 till "memmove" skapar pekare av ett heltal utan typkonvertering
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:547: varning: att skicka argument 1 till "memmove" skapar pekare av ett heltal utan typkonvertering
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c: I funktion "ClonePacket":
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:606: varning: tilldelning skapar heltal från pekare utan typkonvertering
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c: I funktion "update_os_packet_info":
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:628: varning: tilldelning skapar heltal från pekare utan typkonvertering
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c: I funktion "wlan_802_11_to_802_3_packet":
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:648: varning: tilldelning skapar heltal från pekare utan typkonvertering
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c: I funktion "send_monitor_packets":
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:842: varning: format "%d" förväntar typ "int", men argument 3 har typ "long unsigned int"
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:889: varning: tilldelning skapar heltal från pekare utan typkonvertering
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:897: varning: tilldelning skapar heltal från pekare utan typkonvertering
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.o
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.c: I funktion "rt_ieee80211_if_setup":
/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.c:672: fel: "struct net_device" har ingen medlem med namnet "nd_net"
make[2]: *** [/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_main_dev.o] Fel 1
make[1]: *** [_module_/home/magnus/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux] Fel 2
make[1]: Lämnar katalogen "/usr/src/linux-headers-2.6.27-9-generic"
make: *** [LINUX] Fel 2

a lil translation wich might not me needed.. 
Fel 2 = error 2 
and i also get a warning abt a created INT that dont get a type conversion

i have downloaded and installed autoconf.. since a similar problem could be fixed by doing that..  but as u see not in this case   since im total newb on this i need some help   how do i fix it  ..well apart from prolly using tha v1.7... to begin with ;)

brgds M.Thulin

---

### Post by stevena0 on 2009-01-12
Thanks for these instructions, got me up and running in no time.

---

### Post by glisten on 2009-02-25
Hello,

I followed the instructions and it works. I had to set roaming mode in the System -> Administration -> Network -> Wireless connections -> properties. I don't really know why roaming mode works but manual does not yet. Probably some error with the passkey.

Thanks for the help!

Jim

---

### Post by Phlex_de on 2009-06-14
I am planning on switching to Ubuntu..
My card is the [_EW-7728In_]("http://www.edimax.com/en/produce_detail.php?pd_id=225&pl1_id=1&pl2_id=44") from Edimax as well.

I just wanna check before wiping my windows partition because it confuses me that first it says RT2800 and later rt2860.

Is this a RT2860? So do I need the appopiate driver from the [_Ralink Page_]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")? 

lspci -v
```

05:05.0 Network controller: RaLink **RT2800** 802.11n PCI
	Subsystem: Edimax Computer Co. Device 7728
	Flags: bus master, slow devsel, latency 32, IRQ 20
	Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: **rt2860**
	Kernel modules: **rt2860sta**

```

lshw -C network
```

 *-network
       description: Wireless interface
       product: **RT2800** 802.11n PCI
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:05:05.0
       logical name: ra0
       version: 00
       serial: 00:1f:1f:2a:82:02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**rt2860** latency=32 maxlatency=4 mingnt=2 
       module=**rt2860sta** multicast=yes wireless=**RT2860** Wireless

```(testing with 9.04)

---

### Post by chili555 on 2009-06-14
> configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 **module=rt2860sta** multicast=yes wireless=RT2860 WirelessIt looks like you have everything you need right now. Does it see networks when you click the Network Manager icon? After you supply your encryption details, WEP, WPA, etc., does it connect or try?

---

### Post by carcar1 on 2009-06-14
Seriously soemthing is weird I have the same chipset and mine works 100 % out of the box?

---

### Post by Phlex_de on 2009-06-15
you two got me thinking.. 
I chose to hide my SSID before and connect manually but couldn't get it to work.

SSID Broadcast is now on. **It Works!**
I just need to click my network and type my password. I don't even need to select my encryption, ubuntu already had it right.

Thanks!



_edit:_ 
I tried turning SSID Broadcast off. DHCP worked, static IP as well but only for a while. 
I chose static-ip and removed the "Search Domains" field to force a disconnect. After that I could not get a connection although all options were back to the previous working setup. 
It kept asking for the password. Checking the "Show password"-box revealed what seemed like a hex-unicode-kinda phrase to me, no matter what I inserted before.

Turning SSID Broadcast on again got me connected and online in no time.

---

### Post by complience on 2010-04-12
I'm getting the following error when I run the 'make' command,im fairly sure i have all the require repos.

root@ubuntu-antec:~/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0# make
make: Warning: File `Makefile' has modification time 2.1e+08 s in the future
make -C tools
make[1]: Entering directory `/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools'
make[1]: Warning: File `Makefile' has modification time 2.1e+08 s in the future
gcc -g bin2h.c -o bin2h
make[1]: warning: Clock skew detected. Your build may be incomplete.
make[1]: Leaving directory `/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools'
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: Warning: File `/usr/src/linux-headers-2.6.31-14-generic/arch/x86/Makefile_32.cpu' has modification time 2.4e+08 s in the future
make[2]: Warning: File `scripts/Makefile.lib' has modification time 2.4e+08 s in the future
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/md5.o
In file included from /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/md5.c:40:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/include/rt_config.h:90:2: error: #error "Build for being controlled by NetworkManager or wext, please set HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y"
make[2]: *** [/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/md5.o] Error 1
make[1]: *** [_module_/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2
root@ubuntu-antec:~/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0# install
install: missing file operand
Try `install --help' for more information.
root@ubuntu-antec:~/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0# make install
make: Warning: File `Makefile' has modification time 2.1e+08 s in the future
make -C /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux'
make[1]: Warning: File `Makefile.6' has modification time 2.1e+08 s in the future
mkdir: cannot create directory `/etc/Wireless': File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2860sta.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2860sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux'
make: *** [install] Error 2
root@ubuntu-antec:~/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0#

---

### Post by complience on 2010-04-12
Dont think it liked the config changes i made to allow WPA, to i reverted them back, but now im getting a new error

root@ubuntu-antec:~/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0# make
make: Warning: File `Makefile' has modification time 2.1e+08 s in the future
make -C tools
make[1]: Entering directory `/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools'
make[1]: Warning: File `Makefile' has modification time 2.1e+08 s in the future
gcc -g bin2h.c -o bin2h
make[1]: warning: Clock skew detected. Your build may be incomplete.
make[1]: Leaving directory `/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools'
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: Warning: File `/usr/src/linux-headers-2.6.31-14-generic/arch/x86/Makefile_32.cpu' has modification time 2.4e+08 s in the future
make[2]: Warning: File `scripts/Makefile.lib' has modification time 2.4e+08 s in the future
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/md5.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/mlme.o
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/mlme.c:4261: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/action.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_data.o
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_data.c: In function ‘RTMP_FillTxBlkInfo’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_data.c:947: warning: label ‘FillTxBlkErr’ defined but not used
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_wpa.o
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_wpa.c: In function ‘AES_GTK_KEY_WRAP’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_wpa.c:798: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/spectrum.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/aironet.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sync.o
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sync.c:1303: warning: unused variable ‘ByteValue’
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sync.c:1601: warning: the frame size of 1304 bytes is larger than 1024 bytes
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sync.c:983: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sync.c:724: warning: the frame size of 1256 bytes is larger than 1024 bytes
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sync.c:584: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/connect.o
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/connect.c:321: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/wpa.o
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/wpa.c: In function ‘CCKMPRF’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../sta/wpa.c:1838: warning: the frame size of 1044 bytes is larger than 1024 bytes
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_linux.o
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_linux.c:1002: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.o
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:1554: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:1555: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2
root@ubuntu-antec:~/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0# make install
make: Warning: File `Makefile' has modification time 2.1e+08 s in the future
make -C /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux'
make[1]: Warning: File `Makefile.6' has modification time 2.1e+08 s in the future
mkdir: cannot create directory `/etc/Wireless': File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2860sta.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2860sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux'
make: *** [install] Error 2
root@ubuntu-antec:~/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0# make install
make: Warning: File `Makefile' has modification time 2.1e+08 s in the future
make -C /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux'
make[1]: Warning: File `Makefile.6' has modification time 2.1e+08 s in the future
mkdir: cannot create directory `/etc/Wireless': File exists
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2860sta.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2860sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/liminal/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux'
make: *** [install] Error 2
root@ubuntu-antec:~/Desktop/2008_0918_RT2860_Linux_STA_v1.8.0.0#

---

### Post by chili555 on 2010-04-12
My system has rt2860sta.ko in it already; doesn't yours? Moreover, it's a later version that what you are trying to compile here.```
sudo updatedb
locate rt2860sta.ko
```

Also, a file built in 2008 is unlikely to work well with your newer modern, sleek 2.6.31 kernel.

Shall we try to get your device working with what's already in the kernel? Please post:```
lspci -nn
```You can omit everything not wireless.

---

### Post by complience on 2010-04-12
Hi - I dont have a etho connection so I can't update with a simple sudo command. If nonstandard repository are required i will move them from another machine with usb. 

Heres my lspci output:

liminal@ubuntu-antec:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part [1002:5956]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C) [1002:597c]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D) [1002:597d]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:05.0 Network controller [0280]: RaLink RT2800 802.11n PCI [1814:0601]
02:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. Device [1106:3403]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
04:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV630 [Radeon HD 2600XT] [1002:9588]
04:00.1 Audio device [0403]: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series] [1002:aa08]
liminal@ubuntu-antec:~$

---

### Post by chili555 on 2010-04-12
> I dont have a etho connection so I can't update with a simple sudo command.My suggestion, *sudo updatedb*, updates the searchable database on your computer; it does not require an internet connection.> RaLink RT2800 802.11n PCI [[COLOR="Red"]1814:0601[/COLOR]]Your device is claimed by the built-in driver:```
modinfo rt2860sta | grep 0601
alias:          pci:v0000[COLOR="Red"]1814[/COLOR]d0000[COLOR="Red"]0601[/COLOR]sv*sd*bc*sc*i*
```Please do:```
sudo modprobe rt2860sta
iwconfig
```Was a wireless interface created, wlan0 perhaps? If so, can you click the Network Manager icon and connect?

If not, let's find out what's going wrong. Please post:```
dmesg | grep -i rt2
```Thanks.

---

### Post by complience on 2010-04-13
I do see a wifi icon in my top menubar, but it doesn't pick anything up and I know there are at least 5 different types of wifi signals in the area 
```

liminal@ubuntu-antec:~$ sudo updatedb
[sudo] password for liminal: 
liminal@ubuntu-antec:~$ sudo modprobe rt2860sta
liminal@ubuntu-antec:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

liminal@ubuntu-antec:~$
```

---

### Post by chili555 on 2010-04-13
> can you click the Network Manager icon and connect?

If not, let's find out what's going wrong. Please post:
Code:

dmesg | grep -i rt2

How about it? There may be clues in there.

---

### Post by complience on 2010-04-13
I can click the network icon I just dont see any wireless networks to join.

liminal@ubuntu-antec:~$ dmesg | grep -i rt2
[   11.441202] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.442942] rt2860 0000:01:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
liminal@ubuntu-antec:~$ 
liminal@ubuntu-antec:~$

---

### Post by chili555 on 2010-04-13
Please try:```
sudo iwconfig ra0 mode managed
sudo iwconfig ra0 rate auto
sudo iwlist wlan0 scan
```If you get scan results, try Network Manager again.

---

### Post by complience on 2010-04-13
wlan0 interface doesn't support scanning

---

### Post by chili555 on 2010-04-13
> **complience said:**
> wlan0 interface doesn't support scanningSorry; I goofed.```
sudo iwlist ra0 scan
```

---

### Post by complience on 2010-04-13
Okay tightened all the aerials in the back of the card & did a scan.

Managed to pickup a very weak signal for the WEP wifi network I want to connect to.

But when I try to connect it just spins out, never manages it.

Not sure why the signal is so low or why it can only pickup one network

---

### Post by chili555 on 2010-04-13
Let's try:```
sudo iwconfig ra0 power on
sudo iwconfig ra0 txpower 10
```If 10 errors, try 9, 8, etc. until it sticks. If it doesn't error, try 11, 12, etc. Then scan and try to connect again.

---

### Post by complience on 2010-04-13
Error for wireless request 'set power management' (8DB2):
  GET failed on device ra0: Operation not supported

---

### Post by complience on 2010-04-14
> **complience said:**
> Error for wireless request 'set power management' (8DB2):
  GET failed on device ra0: Operation not supported

faulty card you think?

it seems odd

---

### Post by Lucretius on 2010-04-14
works out of the box for me..

speaking of which

does anyone know if full wireless N support is on the way?

Ralink's website states the Linux driver has wireless N support yet I am only connecting at G speeds

---

### Post by chili555 on 2010-04-14
> **complience said:**
> faulty card you think?

it seems oddLet's take another look:```
sudo iwpriv ra0
```Thanks.

---

### Post by complience on 2010-04-15
given up, gone for one of these instead
Asus PCE-N13 802.11 b/g/n Wireless PCI-Express Adapter

---

### Post by georgecamilleri@gmail.com on 2010-05-09
> **chili555 said:**
> Scare you? C'mon, compiling from source is just clean fun!

First, be sure you have *build-essential* and *linux-headers-generic* installed. Synaptic is your friend. Then open a terminal and do, each command separately and in order:```
lspci -v
sudo lshw -C network
```Please verify you have a rt2860 device. If so, please proceed, if not, post back and tell us what you really have. Now do:```
wget http://www.ralinktech.com.tw/data/drivers/2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2
tar -xvzf 2008_0522_RT2860_Linux_STA_v1.6.1.0.tar.bz2
cd 2008_0522_RT2860_Linux_STA_v1.6.1.0
sudo su
```If your card will connect using WPA, we will have some adjustments to make:```
gedit os/linux/config.mk
```In line 11, change *HAS_WPA_SUPPLICANT=n* to *HAS_WPA_SUPPLICANT=y*; in line 14, change *HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n* to *HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y*. Proofread, save and close. Now, do:```
make
cp RT2860STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
make install
modprobe rt2860sta
```Does your device wink, blink and spring to life? Can you connect?


I've just downloaded the latest drivers (1.8.0.0) from the Edimax website, and followed your instructions up the the [make] command. I'm getting the following output:

make -C tools
make[1]: Entering directory `/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools'
/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.32-22-generic/build SUBDIRS=/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_info.o
/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_info.c: In function ‘RTMPIoctlGetSiteSurvey’:
/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_info.c:1922: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_info.c:1922: error: (Each undeclared identifier is reported only once
/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_info.c:1922: error: for each function it appears in.)
/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_info.c:1922: error: implicit declaration of function ‘signal_pending’
/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_info.c:1922: error: implicit declaration of function ‘schedule_timeout’
make[2]: *** [/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/cmm_info.o] Error 1
make[1]: *** [_module_/tmp/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [LINUX] Error 2

I'm running 10.04 (Lucid). I have the build-essential (11.4 build 1) and linux-headers-generic packages installed.

When I did [sudo iwconfig wlan0 power on] I got the following: 
Error for wireless request "Set Power Management" (8B2D) :
    GET failed on device wlan0 ; Network is down.

If I run [lspci -v] I get:
01:07.0 Network controller: RaLink RT2800 802.11n PCI
    Subsystem: Edimax Computer Co. Device 7728
    Flags: bus master, slow devsel, latency 64, IRQ 19
    Memory at dffb0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2860
    Kernel modules: rt2860sta

Why the <access denied>?

Where am I going wrong?

---

### Post by chili555 on 2010-05-10
> Where am I going wrong?First, the correct driver, rt2860sta is already in your system and in use! Second the vintage 2008 driver from Edimax's site is too old; it is version 1.8.0.0. The version in your kernel now is:```
$ modinfo rt2860sta
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        [COLOR="Red"]1.8.1.1[/COLOR]
```Third, if *make* errors out, all bets are off; everything after that is bound to be an error, too.> Why the <access denied>?Generally, to see the full capabilities, you need to run the command as sudo:```
sudo lspci -v
```May we see:```
iwconfig wlan0
lsmod | grep rt2
```Thanks.

---

### Post by georgecamilleri@gmail.com on 2010-05-10
Hi, thanks for the reply. What can I do to use a more updated driver?

Here is the output I got using sudo lspci and iwconfig:

iwconfig wlan0
wlan0     RT2860 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod | grep rt2
rt2860sta             481561  0

---

### Post by chili555 on 2010-05-10
> What can I do to use a more updated driver?Let's try to coax this one to life first. Please post:```
sudo iwconfig wlan0 mode managed
sudo iwlist wlan0 scan
dmesg | grep 286
```Thanks.

---

### Post by georgecamilleri@gmail.com on 2010-05-10
Hi, this is what I got :(

george@asus-am2:~$ sudo iwconfig wlan0 mode managed
[sudo] password for george: 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Network is down.
george@asus-am2:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

george@asus-am2:~$ dmesg | grep 286
[    0.191286] pci 0000:00:09.0: PME# disabled
[    8.457165] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    8.462593] rt2860 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[    9.816482] !!! RT2860 Initialized fail !!!
[   11.066664] !!! RT2860 Initialized fail !!!
[ 1730.298415] !!! RT2860 Initialized fail !!!
[ 1731.767075] !!! RT2860 Initialized fail !!!
[ 1742.718138] !!! RT2860 Initialized fail !!!
[ 1808.539146] !!! RT2860 Initialized fail !!!
[ 1826.802068] !!! RT2860 Initialized fail !!!
[ 1827.821730] !!! RT2860 Initialized fail !!!
[ 1828.928075] !!! RT2860 Initialized fail !!!
[ 1829.933125] !!! RT2860 Initialized fail !!!
[ 1865.556141] !!! RT2860 Initialized fail !!!
[ 1869.173766] !!! RT2860 Initialized fail !!!
[ 1958.410517] !!! RT2860 Initialized fail !!!
[ 2030.231647] !!! RT2860 Initialized fail !!!
[ 2031.289790] !!! RT2860 Initialized fail !!!
[ 3325.191852] !!! RT2860 Initialized fail !!!

---

### Post by georgecamilleri@gmail.com on 2010-05-12
Help. Anyone. Please.

I just tried to shutdown the connection, then start it up again, and got the following output:

george@asus-am2:~$ sudo ifconfig wlan0 down
george@asus-am2:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not permitted

---

### Post by georgecamilleri@gmail.com on 2010-05-15
Bump

---

### Post by complience on 2010-06-17
George try

sudo iwconfig wlan0 down
sudo iwconfig wlan0 up

> **georgecamilleri@gmail.com said:**
> Help. Anyone. Please.

I just tried to shutdown the connection, then start it up again, and got the following output:

george@asus-am2:~$ sudo ifconfig wlan0 down
george@asus-am2:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not permitted

---

### Post by georgecamilleri@gmail.com on 2010-06-17
> **complience said:**
> George try

sudo iwconfig wlan0 down
sudo iwconfig wlan0 up

Hi Complience,

Thanks for your concern. I got the following output:

george@Asus-AM2:~$ sudo iwconfig wlan0 down
[sudo] password for george: 
iwconfig: unknown command "down"

When I did sudo iwconfig wlan0 I got:

george@Asus-AM2:~$ iwconfig wlan0
wlan0     RT2860 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thanks again
George

---

### Post by lister171254 on 2010-06-24
I have a similar problem after upgrading form 9 to 10. The card worked in karmic as this is what I used during the upgrade.

The card is up, I can scan the network and everything seems to be ok, but when I try to connect, I get prompted for the WPA password every two minutes without connecting. I'm sure the password is correct and have disabled all security to verify and have the same result.

Following is the output from some common commands:

>>> sudo lspci -v

03:07.0 Network controller: RaLink RT2800 802.11n PCI
	Subsystem: Edimax Computer Co. Device 7728
	Flags: bus master, slow devsel, latency 32, IRQ 21
	Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta

>>>> iwconfig wlan0
wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.422 GHz  Access Point:   Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-56 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


>>>>> lsmod | grep rt2
rt2860sta             542482  1 


>>>>> sudo iwlist wlan0 scan

         Cell 01 - Address: 00:1F:33:23:E7:3C
                    Protocol:802.11b/g/n
                    ESSID:"TheAustrians2"
                    Mode:Managed
                    Channel:3
                    Quality:89/100  Signal level:-55 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

>>>>> dmesg | grep 286

[    0.344286] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[   12.899374] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   13.095343] rt2860 0000:03:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[66855.738286] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 427

---

### Post by lister171254 on 2010-06-24
Something else I noticed when I upgraded.

Before the upgrade the device was ra0, after the upgrade the deive is wlan0. I guess that means that I must have followed one of the many instruction for installing the drivers (ie. [http://ubuntuforums.org/showthread.php?t=1045703](http://ubuntuforums.org/showthread.php?t=1045703) ).

Comments please.

---

### Post by lister171254 on 2010-06-24
Just (re)installed the driver as per instructions, the outcome's the same:
1) The device comes up
2) I can see all wireless networks
3) My router prompts for the WPA password
4) it fails to connect

I then disabled the security on the router and could connect without any problems so I guess this would point to the Security setting. 
the log shows these errors, but not sure if this is the problem:

un 25 11:08:08 MusicPc kernel: [   13.754803] I/F(wlan0) Key1Str is Invalid key length! KeyLen = 0!
Jun 25 11:08:08 MusicPc kernel: [   13.754819] I/F(wlan0) Key2Str is Invalid key length! KeyLen = 0!
Jun 25 11:08:08 MusicPc kernel: [   13.754834] I/F(wlan0) Key3Str is Invalid key length! KeyLen = 0!
Jun 25 11:08:08 MusicPc kernel: [   13.754849] I/F(wlan0) Key4Str is Invalid key length! KeyLen = 0!
Jun 25 11:08:08 MusicPc kernel: [   13.755081] 1. Phy Mode = 5
Jun 25 11:08:08 MusicPc kernel: [   13.755082] 2. Phy Mode = 5
Jun 25 11:08:08 MusicPc kernel: [   13.773060] RTMPSetPhyMode: channel is out of range, use first channel=1
Jun 25 11:08:08 MusicPc kernel: [   13.780650] 3. Phy Mode = 9
Jun 25 11:08:08 MusicPc kernel: [   13.785071] MCS Set = ff ff 00 00 01


Thanks

---

### Post by endesign on 2010-09-08
Hi folks

I had read that the drivers for this card, which I've just bought, were built in to the latest kernels - certainly for 9.10 and 10.04. Initially my wireless wasn't working with this card and my router - and I almost thought about compiling them from the v1.8 source drivers at the Edimax website. I'm running 10.04.

but a few posts on here mentioned unhiding the SSID. Mine was hidden - worked fine when connecting to a Belkin G USB dongle previously - but when I unhid my SSID the Edimax card found the router and connected no problem and has been working really well since!

It does appear it just doesn't like hidden SSIDs much!):P

---

### Post by Schuby007 on 2011-02-01
> **endesign said:**
> Hi folks

I had read that the drivers for this card, which I've just bought, were built in to the latest kernels - certainly for 9.10 and 10.04. Initially my wireless wasn't working with this card and my router - and I almost thought about compiling them from the v1.8 source drivers at the Edimax website. I'm running 10.04.

but a few posts on here mentioned unhiding the SSID. Mine was hidden - worked fine when connecting to a Belkin G USB dongle previously - but when I unhid my SSID the Edimax card found the router and connected no problem and has been working really well since!

It does appear it just doesn't like hidden SSIDs much!):P

Hi,

I just purchased this card to install in an older Dell desktop running 10.04. So all you had to do was install the card, boot up and it worked straight away? (as long as your SSID isn't hidden - which mine isn't)

Thank you.

---

