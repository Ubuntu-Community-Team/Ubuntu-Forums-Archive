---
title: "Need help with getting Ethernet to work on my laptop with xubuntu."
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by seanwilson684 on 2013-10-26
So basically, I need to get my Ethernet to work (not broken just needs drivers or whatever)
the Ethernet is: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Currently only my Wi-Fi is working. I would like to be able to use Ethernet.

---

### Post by seanwilson684 on 2013-10-26
anyone?

---

### Post by chili555 on 2013-10-26
Please try:```
sudo modprobe b44
```Now is your ethernet working? If so, let's undo the faulty blacklist. First, tell us:```
lspci -nn | grep -e 0200 -e 0280
```

---

### Post by seanwilson684 on 2013-10-26
ok here is a copy/paste of my console:
sean@sean-6400:~$ sudo modprobe b44
[sudo] password for sean: 
sean@sean-6400:~$ lspci -nn | grep -e 0200 -e 0280
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
sean@sean-6400:~$

---

### Post by chili555 on 2013-10-26
One last bit of diagnostics:```
lsmod | grep -e wl -e b4
ifconfig
```We are getting very close to the fix!

---

### Post by seanwilson684 on 2013-10-26
sean@sean-6400:~$ lsmod | grep -e wl -e b4
b44                    31137  0 
b43                   351961  0 
bcma                   39645  1 b43
mac80211              526519  1 b43
cfg80211              436243  2 b43,mac80211
ssb                    50834  3 b43,b44,ssb_hcd
sean@sean-6400:~$

---

### Post by seanwilson684 on 2013-10-26
it seems to have worked:
```
sean@sean-6400:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:15:c5:b4:2b:4e  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feb4:2b4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4464 (4.4 KB)  TX bytes:14514 (14.5 KB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:55614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3967609 (3.9 MB)  TX bytes:3967609 (3.9 MB)


wlan0     Link encap:Ethernet  HWaddr 00:18:f3:54:bd:70  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:7:780:725:218:f3ff:fe54:bd70/64 Scope:Global
          inet6 addr: fe80::218:f3ff:fe54:bd70/64 Scope:Link
          inet6 addr: 2601:7:780:725:9479:cad1:76c2:fc49/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1729236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1195665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2157070056 (2.1 GB)  TX bytes:142068174 (142.0 MB)
```

---

### Post by seanwilson684 on 2013-10-26
only thing is I cant use both connections at once even though it says I am connected via wifi and ethernet

---

### Post by chili555 on 2013-10-26
Indeed it did! Let's see if there is a blacklist we need to undo:```
ls /etc/modprobe.d/
cat /etc/modprobe.d/blacklist.conf
```Thanks.

Why would you want to use both connections at once?

---

### Post by seanwilson684 on 2013-10-26
For a PXE server to install on another laptop, it has no USB boot and broken dvd drive. Do I need to run [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/modprobe.d/blacklist.conf with sudo?[/FONT][/COLOR]

---

### Post by seanwilson684 on 2013-10-26
ok just for seeing it I did it without root:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
#blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

---

### Post by seanwilson684 on 2013-10-26
I posted a second time on accident.

---

### Post by chili555 on 2013-10-26
> Do I need to run cat /etc/modprobe.d/blacklist.conf with sudo?No.

Are you running Network Manager? I suspect running both wired and wireless at the same time will be tricky to impossible with NM. You will probably need to remove it and populate /etc/network/interfaces. That's a different question for a different thread.

No problem with the blacklist.conf file. How about the other command?

---

### Post by seanwilson684 on 2013-10-26
I am using the default network manager in ubuntu, and here:
sean@sean-6400:~$ ls /etc/modprobe.d/
alsa-base.conf           blacklist-framebuffer.conf   dkms.conf
blacklist-ath_pci.conf   blacklist-modem.conf         iwlwifi.conf
blacklist.conf           blacklist-oss.conf           mlx4.conf
blacklist.conf~          blacklist-rare-network.conf  ndiswrapper.conf
blacklist-firewire.conf  blacklist-watchdog.conf      vmwgfx-fbdev.conf

---

### Post by chili555 on 2013-10-26
Man, oh man! You have a lot of strange stuff in there! Let's see what's in a few files and clean some things up:```
cat /etc/modprobe.d/ndiswrapper.conf
cat /etc/modprobe.d/iwlwifi.conf
cat /etc/modprobe.d/dkms.conf
```Let's also get b44 to load automatically:```
sudo -i
echo b44 >> /etc/modules
exit
```Network Manager is designed to connect ethernet OR wireless and will probably never do what you are trying to do. You need to ask this PXE question in another new thread and get an expert answer.

---

### Post by seanwilson684 on 2013-10-26
sean@sean-6400:~$ cat /etc/modprobe.d/ndiswrapper.conf
```
alias pci:v000014E4d0000170Csv0000017Bsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00000188sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00000189sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv0000018Dsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00000196sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00000198sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00000199sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv0000019Bsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv0000019Esd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv0000019Fsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001A2sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001A4sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001ABsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001AFsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001B5sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001BDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001C9sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001CAsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001CBsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001CDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001D4sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001D7sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001D8sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001E5sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001E9sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001EDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001EEsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001EFsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F1sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F2sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F3sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F4sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F5sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001F6sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001FCsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000001FDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000008B0sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00001004sd000017AAbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00001014sd000017AAbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00001016sd000017AAbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00001019sd000017AAbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv0000123Bsd000010CFbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00003095sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00003098sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv00003099sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv000082C4sd00001033bc*sc*i* ndiswrapper
alias pci:v000014E4d0000170Csv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000001sd00001179bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000159sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000017Bsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000188sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000189sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000018Dsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000196sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000198sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00000199sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000019Bsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000019Esd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000019Fsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001A2sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001A4sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001ABsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001AFsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001B5sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001BDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001C9sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001CAsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001CBsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001CDsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001D4sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001D7sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000001D8sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000008B0sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000008BCsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000585Csd00001462bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv0000590Csd00001462bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv000080A8sd00001043bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv00008401sd000014E4bc*sc*i* ndiswrapper
alias pci:v000014E4d00004401sv*sd*bc*sc*i* ndiswrapper
sean@sean-6400:~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
sean@sean-6400:~$ cat /etc/modprobe.d/dkms.conf
# modprobe information used for DKMS modules
#
# This is a stub file, should be edited when needed,
# used by default by DKMS.
```

---

### Post by chili555 on 2013-10-26
The only one I see that is troublesome is ndiswrapper. Let's fix it:```
sudo apt-get remove --purge ndiswrapper*
sudo rm /etc/modprobe.d/ndiswrapper.conf 
```You should be all set!

---

### Post by seanwilson684 on 2013-10-26
ok

---

