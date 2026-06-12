---
title: "Wireless Network issue"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by awais_rauf on 2008-03-20
Hi

        I just switched from windows to ubuntu. Some days before i setup my wireless card by installing bcm43xx-fwcutter while in the LiveCD enviornment and it worked fine. But now when i installed ubuntu wireless is not working. I have installed and uninstalled bcm43xx-fwcutter many times hoping it will work but it hasn't. I did lshw and the results are below

 *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 03
       serial: 00:0b:7d-xx-xx-xx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=32 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

Can anyone help me out.

---

### Post by dstew on 2008-03-20
It seems the driver is installed, and the card is working. Post the output of ```
iwconfig
```

---

### Post by awais_rauf on 2008-03-20
eth1      IEEE 802.11b/g  ESSID:"RAUFSNETWORK"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr: off   Fragment thr: off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by dstew on 2008-03-20
It is not connected to the access point. Disable the connection in the Networking window, and then try to enable it again. Make sure you are entering the passcode correctly.

---

### Post by awais_rauf on 2008-03-21
I did sudo** ifdown eh1** and then **sudo ifup eth1**

awais@RAUFS-LAPTOP:~$ **sudo ifup eth1**
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0b:7d:-XX-XX-XX
Sending on   LPF/eth1/00:0b:7d:XX-XX-XX
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I also tried enabling and disabling the connection in network windows but it doesnt work.

---

### Post by Eiríkr on 2008-03-21
Sometimes with the "already a pid file" messages, you need to force the command through.  Try running:
```
sudo ifdown eth1
sudo ifup --force eth1
```
This will clear out the existing pid (process ID) file.  I used to get similar error messages when my networking got borked somehow in the upgrade process from Xubuntu 6.10 to 7.04, such that networking *thought* it was coming up during boot, but I'd be left with nothing -- not even loopback -- and would have to force the commands through.  This made my Xubuntu box risky as a server as any power cycling would leave the box inaccessible via the network, so in the move to 7.10, I opted for a fresh install on a newly formatted partition.  :)  One reason I began several years ago keeping my personal data on a separate partition.  :D  But I digress.

Cheers,

Eiríkr

---

### Post by awais_rauf on 2008-03-21
Output of **lsmod** is:

Module Size Used by
arc4 2944 2
ecb 4608 2
blkcipher 7556 1 ecb
ieee80211_crypt_wep 6272 1
isofs 36412 1
udf 87204 0
i915 25856 2
drm 83348 3 i915
rfcomm 42136 2
l2cap 26240 11 rfcomm
bluetooth 57060 4 rfcomm,l2cap
ppdev 10244 0
snd_atiixp_modem 17160 0
snd_via82xx_modem 16264 0
snd_intel8x0m 18572 5
speedstep_lib 6404 0
cpufreq_stats 7232 0
cpufreq_powersave 2688 0
cpufreq_conservative 8072 0
cpufreq_userspace 5280 0
cpufreq_ondemand 9612 0
freq_table 5792 2 cpufreq_stats,cpufreq_ondemand
sbs 19592 0
container 5504 0
dock 10656 0
battery 11012 0
ac 6148 0
button 8976 0
video 18060 0
nls_iso8859_1 5120 1
nls_cp437 6784 2
vfat 14080 1
fat 54300 1 vfat
ipv6 273892 8
parport_pc 37412 0
lp 12580 0
parport 37448 3 ppdev,parport_pc,lp
pcmcia 41388 0
joydev 11328 0
snd_intel8x0 34972 1
snd_ac97_codec 100644 4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,s nd_intel8x0
ac97_bus 3200 1 snd_ac97_codec
snd_pcm_oss 44672 0
snd_mixer_oss 17664 1 snd_pcm_oss
snd_pcm 80388 8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,s nd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 33152 0
snd_seq_midi 9600 0
snd_rawmidi 25728 1 snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
bcm43xx 127336 0
yenta_socket 27532 1
rsrc_nonstatic 14080 1 yenta_socket
pcmcia_core 40980 3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211softmac 31360 1 bcm43xx
ieee80211 35656 2 bcm43xx,ieee80211softmac
ieee80211_crypt 7040 2 ieee80211_crypt_wep,ieee80211
snd_seq 53232 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 24324 2 snd_pcm,snd_seq
snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
pcspkr 4224 0
iTCO_wdt 11940 0
iTCO_vendor_support 4868 1 iTCO_wdt
snd 54660 23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,s nd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_o ss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_tim er,snd_seq_device
soundcore 8800 1 snd
serio_raw 8068 0
psmouse 39952 0
shpchp 34580 0
pci_hotplug 32704 1 shpchp
snd_page_alloc 11400 5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,s nd_intel8x0,snd_pcm
intel_agp 25620 1
agpgart 35016 3 drm,intel_agp
af_packet 24840 8
evdev 11136 5
ext3 133896 1
jbd 60456 1 ext3
mbcache 9732 1 ext3
sg 36764 0
sd_mod 30336 5
sr_mod 17828 1
cdrom 37536 1 sr_mod
ata_piix 17540 5
b44 28300 0
mii 6528 1 b44
ata_generic 8452 0
libata 125168 2 ata_piix,ata_generic
scsi_mod 147084 4 sg,sd_mod,sr_mod,libata
ehci_hcd 36492 0
uhci_hcd 26640 0
usbcore 138632 3 ehci_hcd,uhci_hcd
thermal 14344 0
processor 32072 1 thermal
fan 5764 0
fuse 47124 3
apparmor 40728 0
commoncap 8320 1 apparmor


Output of **dmesg** commands are:

awais@RAUFS-LAPTOP:~$ dmesg | grep b43
awais@RAUFS-LAPTOP:~$ dmesg | grep bcm43xx
[ 23.216000] bcm43xx driver
awais@RAUFS-LAPTOP:~$ dmesg | grep wlan*
awais@RAUFS-LAPTOP:~$ dmesg | grep wlan0

---

### Post by awais_rauf on 2008-03-21
I tried the force command but it also doesnt work

ubuntu@ubuntu:/usr/bin$ sudo ifup --force eth1
/etc/network/if-pre-up.d/wpasupplicant: 124: start-stop-daemon: Input/output error
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0b:7d:-xx-xx-xx
Sending on   LPF/eth1/00:0b:7d-xx-xx-xx
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Eiríkr on 2008-03-21
Could you please post the results of the following:
```
ifconfig
cat /etc/network/interfaces
```

Cheers,

Eiríkr

---

### Post by awais_rauf on 2008-03-21
**[SIZE="2"]IFCONFIG[/SIZE]**

awais@RAUFS-LAPTOP:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43--xx-xx-xx
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe6d:a908/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:137658 (134.4 KB)  TX bytes:18477 (18.0 KB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:0B:7D:xx-xx-xx
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:546 (546.0 b)
          Interrupt:11 Base address:0xc000 

eth1:avah Link encap:Ethernet  HWaddr 00:0B:7D-xx-xx-xx  
          inet addr:169.254.4.223  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



**[SIZE="2"]/etc/network/interfaces[/SIZE]**

awais@RAUFS-LAPTOP:/etc/network$ cat interfaces 
auto lo
iface lo inet loopback




iface eth0 inet dhcp



iface eth1 inet dhcp
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid RAUFSNETWORK

















auto eth0





auto eth1

---

### Post by Eiríkr on 2008-03-21
I notice your eth0 connection does have an IP address assigned.  Presumably this is a wired connection?  I've read before that the Network Manager app in Ubuntu is problematic in that it only allows one active connection at a time; I'm not sure if that's what's going on here, but you might want to look at [post=1169984]step 20 in this guide[/post] and try disabling eth0, then restarting your network:
```
sudo /etc/init.d/networking restart
```
... and see if that helps.

Cheers,

Eiríkr

---

### Post by shivam.seth on 2008-03-23
Hey guys I am also facing exactly the same problem with my wLan. Actually I somehow configured it to work before with help of a friend who searched Ubuntu forum for this problem and found the solution but due to a crash, I had to reinstall Ubuntu 7.10 again. Now, I don't remember how I corrected the problem before(...ya  I am that dumb..:confused:..) but I can tell you the exact reason why the b43xx-fwcutter is not working. Actually, **When Ubuntu boots, it loads B44 drivers instead of B43, so your computer does have the proper B43 driver but it is not loaded. Instead of it, B44 is loaded which obviously won't work!**. So if you can just find which file to edit and how to edit for making appropriate changes for this problem. I remember using "alias" command to link B44 to B43 so whenever B44 is called for loading, B43 gets loaded instead. I am very new to Linux so still I couldn't figure the whole thing out myself. Hope my input will narrow the problem!

Eiríkr .... any solution for this????

---

### Post by Eiríkr on 2008-03-23
No idea myself, I'm not so good on the driver end of things.  

Anyone else have a clue?

Cheers,

Eiríkr

---

### Post by shivam.seth on 2008-03-23
> **Eiríkr said:**
> I notice your eth0 connection does have an IP address assigned.  Presumably this is a wired connection?  I've read before that the Network Manager app in Ubuntu is problematic in that it only allows one active connection at a time; I'm not sure if that's what's going on here, but you might want to look at [post=1169984]step 20 in this guide[/post] and try disabling eth0, then restarting your network:
```
sudo /etc/init.d/networking restart
```
... and see if that helps.

Cheers,

Eiríkr

Actually Ubuntu gives preference to Wired network connection over Wireless, so if you have a wired Lan jack plugged in, it will use Lan instead of ur wLan, so try to plug out your Lan wire whenever you want to use your wireless connection!

---

### Post by Eiríkr on 2008-03-23
The trouble appears to be the Network Manager program, which only allows one active interface at a time.  Many folks have recommended replacing NM with WICD, which unfortunately is not included in the Ubuntu repositories and must instead be downloaded from [its Sourceforge page]("http://wicd.sourceforge.net/").

Cheers,

Eiríkr

---

### Post by shivam.seth on 2008-03-23
> **Eiríkr said:**
> The trouble appears to be the Network Manager program, which only allows one active interface at a time.  Many folks have recommended replacing NM with WICD, which unfortunately is not included in the Ubuntu repositories and must instead be downloaded from [its Sourceforge page]("http://wicd.sourceforge.net/").

Cheers,

Eiríkr

So do you think changing to WICD will do the trick??? If its that easy, I will give it a try the very first hour I reach my college tomorrow!

---

### Post by Eiríkr on 2008-03-23
I've not done it myself, but if you search this Networking forum for "wicd", you should find plenty of posts from people who've had success with WICD and multiple interfaces.  :)

Cheers,

Eiríkr

---

### Post by shivam.seth on 2008-03-23
I think I got what I have been searching for .....[COLOR="SeaGreen"]**THE SOLUTION**[/COLOR]

After installing bcm43xx-fwcutter and extracting the firmware. Reboot! If your wLan light turned ON, then this should work for you as well ....

Run **echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist**

This should do the job. Reboot after doing so and try connecting. 

I still have to try it myself. I will come back to this thread with my results tomorrow!

I got this solution from [http://ubuntuforums.org/showthread.php?t=649038&highlight=solved+b43]("http://ubuntuforums.org/showthread.php?t=649038&highlight=solved+b43")

This thread might further help you!

---

### Post by shivam.seth on 2008-03-26
try doing **echo 'alias eth1 b43' | tee /etc/modprobe.d/b43**

This worked for me. No need to edit the blacklist file I told in my previous post!

---

