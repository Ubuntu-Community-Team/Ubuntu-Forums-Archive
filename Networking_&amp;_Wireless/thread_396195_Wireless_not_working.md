---
title: "Wireless not working"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Pizarro on 2007-03-29
I have just installed 6.10 on an compaq nx6125. After much reading I have failed miserably to get the wireless to work. The card is a broadcam BCM4138 airforce one 54g 802.11g revision 02 according to   lspci. I have installed fwcutter and ndiswrapper.  I have managed to extract some fw files into lib/firmware but don't know if this is right or what to do next.

---

### Post by spd106 on 2007-03-29
Could you post the output of these commands please? You can wrap the output in ```
 tags to allow better use of space.
[CODE]sudo lshw -class network
```
```
ndiswrapper -v
```
```
lsmod
```

This is probably the best and most comprehensive guide [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

### Post by Pizarro on 2007-03-29
martyn@martyn-laptop:~$ sudo lshw -class network
Password:
  *-usb                   
       description: Bluetooth wireless interface
       product: HP Integrated Module
       vendor: Broadcom Corp
       physical id: 2
       bus info: usb@1:2
       version: 1.00
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
  *-network:0
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 03
       serial: 00:0f:b0:be:a5:f3
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5788-v3.26 ip=192.168.1.103 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d0000000-d000ffff irq:169
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:2c:b0:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-11-generic link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d0010000-d0011fff irq:50
martyn@martyn-laptop:~$ 




martyn@martyn-laptop:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.22
vermagic:       2.6.17-11-generic SMP mod_unload gcc-4.1
martyn@martyn-laptop:~$ 



martyn@martyn-laptop:~$ lsmod
Module                  Size  Used by
sg                     44584  0 
hci_usb                21268  2 
arc4                    3712  0 
ieee80211_crypt_wep     7936  0 
binfmt_misc            16012  1 
rfcomm                 51360  0 
l2cap                  31744  5 rfcomm
bluetooth              64644  7 hci_usb,rfcomm,l2cap
fglrx                 481012  8 
powernow_k8            16576  0 
cpufreq_userspace       6560  0 
cpufreq_stats           9312  0 
freq_table              7104  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3456  0 
cpufreq_ondemand       10928  1 
cpufreq_conservative    11272  0 
video                  22920  0 
tc1100_wmi             10632  0 
sbs                    20928  0 
sony_acpi               7704  0 
pcc_acpi               19968  0 
i2c_ec                  7808  1 sbs
i2c_core               29312  1 i2c_ec
hotkey                 14536  0 
dev_acpi               17540  0 
button                  9888  0 
battery                14088  0 
container               6656  0 
ac                      8328  0 
asus_acpi              21924  0 
ipv6                  334432  10 
af_packet              29452  6 
sbp2                   29448  0 
scsi_mod              181424  2 sg,sbp2
lp                     16584  0 
pcmcia                 49048  0 
joydev                 14208  0 
bcm43xx               148500  0 
tsdev                  11136  0 
yenta_socket           33420  1 
rsrc_nonstatic         16896  1 yenta_socket
pcmcia_core            52772  3 pcmcia,yenta_socket,rsrc_nonstatic
ieee80211softmac       40704  1 bcm43xx
ieee80211              39112  2 bcm43xx,ieee80211softmac
ieee80211_crypt         9216  2 ieee80211_crypt_wep,ieee80211
tifm_7xx1              11264  0 
tg3                   119044  0 
tifm_core              12928  1 tifm_7xx1
sdhci                  22796  0 
mmc_core               40456  1 sdhci
snd_atiixp_modem       21900  0 
pcspkr                  5248  0 
snd_atiixp             26644  1 
snd_ac97_codec        127064  2 snd_atiixp_modem,snd_atiixp
snd_ac97_bus            4352  1 snd_ac97_codec
snd_pcm_oss            57344  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm               108168  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              31112  1 snd_pcm
evdev                  14592  2 
parport_pc             43560  1 
parport                49932  2 lp,parport_pc
psmouse                51088  0 
serio_raw              10244  0 
snd                    79016  9 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              14112  1 snd
snd_page_alloc         13200  3 snd_atiixp_modem,snd_atiixp,snd_pcm
shpchp                 49068  0 
pci_hotplug            38912  1 shpchp
ext3                  164880  1 
jbd                    74024  1 ext3
ohci1394               40776  0 
ieee1394              387704  2 sbp2,ohci1394
ehci_hcd               40456  0 
ohci_hcd               25988  0 
usbcore               167840  4 hci_usb,ehci_hcd,ohci_hcd
ide_generic             2944  0 
ide_cd                 39584  0 
cdrom                  43816  1 ide_cd
ide_disk               21248  3 
generic                 7940  0 
atiixp                  9232  1 
thermal                19472  0 
processor              38280  2 powernow_k8,thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit
martyn@martyn-laptop:~$ 


Thank you

---

### Post by W@LT on 2007-03-29
For what it is worth I had a similar problem with a Linksys and a generic usb adaptor..

I upgraded to KUbuntu and used the wireless manager in Kubuntu to find the adaptor and configure it... and it works

Good Luck

W@LT

---

### Post by spd106 on 2007-03-29
Try installing the latest ndiswrapper-utils package to get the right version

```
sudo apt-get install ndiswrapper-utils-1.8
```

Now blacklist bcm43xx by adding it to the /etc/modprobe.d/blacklist file

```
gksudo gedit /etc/modprobe.d/blacklist
```

Now either reboot or follow these commands
```
sudo ifconfig eth1 down
sudo modprobe -r bcm43xx
sudo modprobe ndiswrapper
```

Assuming you have the windows driver installed you should now have a working wifi card. If not you will have to build ndiswrapper from source, the link given in my previous post will tell you how to do that.

---

### Post by Pizarro on 2007-03-29
Think I did the blacklisting but......
martyn@martyn-laptop:~$ sudo ifconfig eth1 down
Password:
martyn@martyn-laptop:~$ sudo modprobe -r bcm43xx
martyn@martyn-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
martyn@martyn-laptop:~$ 

Sorry but I'm lost here. 
I have bcmwl5.sys  (downloaded) and sp33008.exe which I believe is the windows install executable.

---

### Post by spd106 on 2007-03-29
You need to get to a state where you can see something like this```
 ndiswrapper -v
utils version: 1.8
driver version:        1.22
vermagic:       2.6.17-11-generic SMP mod_unload gcc-4.1

```

This require that you have the right utils version installed, the package that shipped with Edgy (1.1) went wrong so you need to download v1.8.

You may have to run these additional commands if it's still not working.
```
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```
Thanks to maclenin @ [http://www.ubuntuforums.org/showthread.php?t=340689](http://www.ubuntuforums.org/showthread.php?t=340689)

---

### Post by Pizarro on 2007-03-29
Used my windows dual boot to extract the inf file and have now got bcmwl5 as an installed driver in Wireless Network Drivers.  Start up WiFi Radar and it finds the router and both next door neighbours routers. On choosing connect I can not get an ip adress. I know its not the router as i just connected using my pismo mac. I'm thinking it's the wifi options in wifi radar The sytem is set up on wpa (checked it on mac) and the password is correct.

---

### Post by Pizarro on 2007-03-29
Anyone know what wifi options should be in wifi radar ?
Mode is master
Channel is auto
Key I have no idea
Security  Restricted (router is wap)
Use wap    what is driver  the wap password ?
Automatic network configuration  dhcp
Connection commands ? I've left empty

        The Frustration of Linux        Everything Has it's Darkside
:confused: :confused: :confused: :confused:

---

### Post by chili555 on 2007-03-29
Do you mean WEP or WPA encryption? Or are you using 'wap' to mean 'wireless access point'? This sentence:> Use wap what is driver the wap password ?means nothing to me.

If you have no idea about 'key', maybe you did not set an encryption key in the router, so leave is blank. Mode should be Managed.

---

### Post by spd106 on 2007-03-29
Since you're asking for a driver I think it's safe to assume you want WPA. The driver will most likely be wext, if that doesn't work then try ndiswrapper.

For the key you should enter the WPA key as configured on the router.

---

### Post by Pizarro on 2007-03-29
Sorry meant wpa.  I'll try the wpa code in here. But then what should i put in the driver box under the wpa heading?


Just seen last post have now tried wext and ndiswrapper  no joy.

---

