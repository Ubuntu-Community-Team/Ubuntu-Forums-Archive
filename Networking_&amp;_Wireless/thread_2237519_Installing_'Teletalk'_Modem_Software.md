---
title: "Installing 'Teletalk' Modem Software"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by zuhair2 on 2014-08-02
**Hey there fellas! I'm new to Linux (as in completely, a n00b, beginner, newbie, a[B]becedarian, trainee, tenderfoot, rookie, recruit, novice etc etc...**)[/B]
I've been struggling, since yesterday, to install this modem 'software' in Ubuntu 14.04.
The installation file is a Shell Script (.sh).
I figured out most of the stuff (I think...).
This is what I've been doing:
```
[I]Copying the file to the desktop.
Extracting the .tar.gz file.
Placing the files ('install.sh', 'Teletalk_3G' (another tar.gz), 'zr') in the '/opt' folder.
Opening the terminal, and....
typing 'sudo -i'. *Enter*
typing '*my password*' *Enter*
dragging the 'Install.sh' file from the 'opt' folder into the terminal
*Enter*
[/I]
```

Apparently, I had to do a bit of research to know I had to do these.
There isn't any specific tutorial on installing this bit of software.

My problem is.....
it installs and all, but it refuses to open.
A closer look at the terminal log (appearing after the installation) shows everything goes smoothly until it says it can't find this directory, it goes something like '*/usr/share/applications/desktop.*.cache*'.
And from there everything goes wrong (or so I think).
Help, anyone?

I leave a copy of the file here [PCL_TLKBGL.tar.gz]("http://wikisend.com/download/332904/PCL_TLKBGL.tar.gz") in dearest hope that someone can make it work.

---

### Post by wildmanne39 on 2014-08-02
*Thread moved to **Networking & Wireless**.*

---

### Post by zuhair2 on 2014-08-03
Anyone?
Help?
Need internet connection on Ubuntu really quickly, you know...

---

### Post by praseodym on 2014-08-03
Hi,

why do you need a modem software? What kind of modem is it? PPPoE/DSL? Or an UMTS stick/Modem? Please explain in detail how you want to connect.

If it is a stick, please show

```
uname -a
lsusb
usb-devices
rfkill list
lsmod
```

---

### Post by zuhair2 on 2014-08-03
Here is a screenshot of the software running on OS X.

                          [IMG]http://sharebin.net/Bpc.png[/IMG]

---

### Post by coffeecat on 2014-08-03
It's a 3G stick. Please post the output of the commands praseodym asked for in post #4. There's a good chance that the stick will work with Ubuntu's Network Manager without you having to install anything else.

---

### Post by zuhair2 on 2014-08-04
Here they are:

```
uname -aLinux myusername 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


lsusb
Bus 004 Device 002: ID 1c4f:0026 SiGma Micro Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 19d2:2003 ZTE WCDMA Technologies MSM 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


 usb-devices
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-32-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-32-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=2003 Rev=00.00
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE WCDMA Technologies MSM
S:  SerialNumber=MF193EZTED010000CP261718ZN.L7CJ1TG9A9C.MN4_35161H2B&&&&&&&&&&&&0
C:  #Ifs= 5 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-32-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=093a ProdID=2510 Rev=01.00
S:  Manufacturer=PixArt
S:  Product=USB Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-32-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1c4f ProdID=0026 Rev=01.10
S:  Manufacturer=SIGMACHIP
S:  Product=USB Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid


rfkill list


lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39835  1 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391196  10 bnep,rfcomm
option                 46608  0 
snd_hda_codec_hdmi     46254  1 
usb_wwan               20429  1 option
usb_storage            62209  1 
usbserial              45014  2 option,usb_wwan
joydev                 17381  0 
gpio_ich               13476  0 
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
coretemp               13435  0 
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
serio_raw              13462  0 
lpc_ich                21080  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
radeon               1522422  3 
ttm                    85115  1 radeon
drm_kms_helper         53081  1 radeon
drm                   303102  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
mac_hid                13205  0 
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
psmouse               106678  0 
r8169                  67581  0 
mii                    13934  1 r8169
```

I tried 'sakis3g', but it doesn't work. Says "Failed to connect".

---

### Post by praseodym on 2014-08-04
Is it shown as a storage device on your desktop or file manager? If yes, unmount it. Please check:
```

sudo apt-get install usb-modeswitch
```
Reboot and re-plug the modem. Do you know this posting:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by zuhair2 on 2014-08-05
I could not get your commands to work.
But I got the modem to work myself! :p
This is what I did.
```
Ejected the modem 'disk'.
Then configured Sakis3G.
```

Thanks anyways fellas!

**P.S. How do I edit the post title to [SOLVED], or do the moderators take care of that?**
**EDIT:.......Found the button!**

---

### Post by zuhair2 on 2014-08-06
Here are the instructions I followed, in detail:
[FONT=arial][URL="http://ubuntuforums.org/showthread.php?t=2237998&p=13091057#post13091057"]
**[SIZE=5][GUIDE] Getting your Teletalk 3G Modem to work on Ubuntu 14.04[/SIZE]**[/URL][/FONT]

---

### Post by Jahidul_Hamid on 2014-08-25
I didn't have any problem installing it Linux Mint. It ran exactly the way it should. But in ubuntu I can't run the software although the drivers are installed just like it installed in Linux Mint.

---

### Post by Mahmudur_Rahman on 2014-08-25
Im having the issue. Installed it properly , the launcher icon is there but when i click on it nothing happens. Please help me with proper guidelines.

---

### Post by Jahidul_Hamid on 2014-08-30
> **Mahmudur_Rahman said:**
> Im having the issue. Installed it properly , the launcher icon is there but when i click on it nothing happens. Please help me with proper guidelines.

You need to isntall the ia32-libs first. Then whenever you run that software you need to run it with root privillege and before running it make sure that the modem usb drive is unmounted.

---

