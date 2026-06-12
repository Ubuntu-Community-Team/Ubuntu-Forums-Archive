---
title: "WIFI problem in Dell inspiron 910 mini"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by jack_sparrow2 on 2014-04-29
Hi,

I have recently installed lubuntu 14.04 lts in my notebook but the wifi isn't running. All the rest is working fine, including ethernet, what could I do? I have tried everything I have found on the internet and I am afraid to have messed up something. Anyway, I think the wifi driver is well installed but it looks as if the wifi was off, I can't enable it with FN+2 command.

I need help please.

Thanks

---

### Post by wildmanne39 on 2014-04-29
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by kc1di on 2014-04-29
could you go to a terminal and type the following commands and list the outputs here.
```
 rfkill list all
```
Then
```
 lsmod
```  also ```
lspci
```

---

### Post by jack_sparrow2 on 2014-04-30
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

Hi,
here is the archive, is it secure for me to attach it? Please tell me if I should edit some part. Thanks. 
PS: I have got also a "wireless script" archive. Do you need it?

---

### Post by jack_sparrow2 on 2014-04-30
> **kc1di said:**
> could you go to a terminal and type the following commands and list the outputs here.
```
 rfkill list all
```
Then
```
 lsmod
```  also ```
lspci
```

Hi, herter is the info:


```
 rfkill list all
```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


```
 lsmod
```

Module                  Size  Used by
joydev                 17101  0 
hid_generic            12492  0 
dell_laptop            17808  0 
compal_laptop          19199  0 
snd_hda_codec_realtek    51029  1 
dcdbas                 14448  1 dell_laptop
snd_hda_intel          42730  1 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
usbhid                 47035  0 
coretemp               13195  0 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
i915                  705396  2 
hid                    87604  2 hid_generic,usbhid
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
drm_kms_helper         46907  1 i915
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
snd_timer              28584  2 snd_pcm,snd_seq
psmouse                91033  0 
rfcomm                 53664  8 
videodev              108503  2 uvcvideo,videobuf2_core
serio_raw              13230  0 
btusb                  27580  0 
bnep                   18895  2 
jmb38x_ms              18222  0 
bluetooth             342263  22 bnep,btusb,rfcomm
snd                    60871  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   243792  3 i915,drm_kms_helper
parport_pc             31981  0 
lpc_ich                16864  0 
ppdev                  17391  0 
soundcore              12600  1 snd
arc4                   12536  2 
memstick               16174  1 jmb38x_ms
i2c_algo_bit           13197  1 i915
b43                   356470  0 
bcma                   42043  1 b43
mac80211              545990  1 b43
cfg80211              409394  2 b43,mac80211
mac_hid                13037  0 
video                  18903  1 i915
ssb                    51854  1 b43
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
r8169                  61562  0 
mii                    13654  1 r8169
sdhci_pci              18535  0 
sdhci                  37779  1 sdhci_pci


```
lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by kc1di on 2014-04-30
you have the same card I do in my Laptop - You have the b43 driver installed though that will work with the bcm4312 I find that the WL/sta driver works much better for me.  I know some will argue the point.  but lets try it and see if you can get on line.

in a terminal type: ```
sudo apt-get install bcmwl-kernel-source 
```
you may also have to blacklist the b43 driver module you can do that by typing ```
gksu gedit
``` 
you will have to enter your passwd.
when it comes up navigate to /etc/modprobe.d/blacklist.conf  open that file and add b43 to the end of the list found there also add ssb after b43  save the file and reboot. 
see if wireless is now working.

---

### Post by jack_sparrow2 on 2014-04-30
> **kc1di said:**
> you have the same card I do in my Laptop - You have the b43 driver installed though that will work with the bcm4312 I find that the WL/sta driver works much better for me.  I know some will argue the point.  but lets try it and see if you can get on line.

in a terminal type: ```
sudo apt-get install bcmwl-kernel-source 
```
you may also have to blacklist the b43 driver module you can do that by typing ```
gksu gedit
``` 
you will have to enter your passwd.
when it comes up navigate to /etc/modprobe.d/blacklist.conf  open that file and add b43 to the end of the list found there also add ssb after b43  save the file and reboot. 
see if wireless is now working.


I can't do the last step. typing I type ```
gksu gedit
```, I enter my password and nothing happens. Where should I enter this commands: "navigate to /etc/modprobe.d/blacklist.conf",open that  file and add "b43" to the end of the list found there also add ssb after  "b43".

---

### Post by kc1di on 2014-04-30
which version of ubuntu are you using?  is it 14.04 or lubuntu or something else?

you can also do it with the command sudo gedit (that is if you are using ubuntu or gnome) if it's mate then believe you would substitute pluma for gedit , if you using lubuntu I'm not sure what he text editor is you'll have to find it. xubuntu would be leafpad.  for kubuntu it's kate.
you can also use nano but it's a little more complicated.

---

### Post by jack_sparrow2 on 2014-04-30
It's lubuntu lts 14.04.

The text editor is leafpad.

---

### Post by kc1di on 2014-04-30
Couldn't remember been a while since i've use lubuntu.

---

### Post by jack_sparrow2 on 2014-04-30
any more help please?

---

### Post by kc1di on 2014-04-30
> **jack_sparrow2 said:**
> any more help please?

```
gksu leafpad
``` and do what I told you before with /ect/modeprobe.d/blacklist.conf

Reboot. should work.

---

### Post by jack_sparrow2 on 2014-04-30
> **kc1di said:**
> ```
gksu leafpad
``` and do what I told you before with /ect/modeprobe.d/blacklist.conf

Reboot. should work.

I've done it. But who should I add b43 and ssd? with # before them or without it? If put it witout, and Im going to reboot. Lets see.

This is how I've put it (it is a copy & paste frome the last lines of that archive):

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

b43
ssb

---

### Post by jack_sparrow2 on 2014-04-30
it doesnt work this way. The thing is that there are no options of wifi, where do they should appear???

I'll try putting # before each line, this way and lets see:
.
.
.
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# b43
# ssb

---

### Post by jack_sparrow2 on 2014-04-30
it doesn't work.
But where should wifi options appear? In network connections I suppose, isn't it? The ethernet connection at least is there. It's like if wifi wouldn't exist. I think I will have to go back to windows or something... It's quite a pitty because this distro (lubuntu) is perfect for a notebook. Windows OS are too heavy.

---

### Post by kc1di on 2014-04-30
no it's without the # mark. (the # sign tells the machine to ignore that line of code. )

you installed the bcmwl-kernel-source Package?

---

### Post by jack_sparrow2 on 2014-04-30
yes I did and this is the response:

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
bcmwl-kernel-source ya está en su versión más reciente.
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  linux-headers-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

It is in spanish, hecho means done and the line at the end means that bcmwl-kernel-source is already in its latest version.

---

### Post by wildmanne39 on 2014-04-30
I am just watching.:popcorn:

---

### Post by kc1di on 2014-04-30
ok let me see the output of ```
lsmod 
``` again

Thanks

feel free to jump in Wild Man :)

---

### Post by jack_sparrow2 on 2014-04-30
Module                  Size  Used by
joydev                 17101  0 
snd_hda_codec_realtek    51029  1 
hid_generic            12492  0 
snd_hda_intel          42730  1 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
dell_laptop            17808  0 
compal_laptop          19199  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
dcdbas                 14448  1 dell_laptop
snd_rawmidi            25135  1 snd_seq_midi
coretemp               13195  0 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
psmouse                91033  0 
videobuf2_memops       13170  1 videobuf2_vmalloc
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
videobuf2_core         39258  1 uvcvideo
serio_raw              13230  0 
videodev              108503  2 uvcvideo,videobuf2_core
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
usbhid                 47035  0 
snd                    60871  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  705396  2 
lpc_ich                16864  0 
drm_kms_helper         46907  1 i915
rfcomm                 53664  8 
btusb                  27580  0 
hid                    87604  2 hid_generic,usbhid
bnep                   18895  2 
bluetooth             342263  22 bnep,btusb,rfcomm
drm                   243792  3 i915,drm_kms_helper
soundcore              12600  1 snd
jmb38x_ms              18222  0 
memstick               16174  1 jmb38x_ms
i2c_algo_bit           13197  1 i915
parport_pc             31981  0 
arc4                   12536  2 
ppdev                  17391  0 
b43                   356470  0 
bcma                   42043  1 b43
mac80211              545990  1 b43
video                  18903  1 i915
cfg80211              409394  2 b43,mac80211
mac_hid                13037  0 
ssb                    51854  1 b43
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
r8169                  61562  0 
mii                    13654  1 r8169
sdhci_pci              18535  0 
sdhci                  37779  1 sdhci_pci

---

### Post by kc1di on 2014-04-30
b43 and ssb  are still being loaded and wl is not loaded did you reboot?

```
b43 356470 0 
bcma 42043 1 b43
mac80211 545990 1 b43
video 18903 1 i915
cfg80211 409394 2 b43,mac80211
mac_hid 13037 0 
ssb 51854 1 b43
```

Lets try this ```
modprobe -r b43 ssb
modprobe wl
```  
if you get no error message give it a minute and see if you have wireless activated.

---

### Post by jack_sparrow2 on 2014-04-30
Sorry dude, the first lsmod was without doing what you had said before ('cos I deleted the lines you told me to add, b43 and ssb, when I saw it didn't work). I repost the lsmod after doing what you said (the thing with the leafpad and after rebooting and everything.
Module                  Size  Used by
joydev                 17101  0 
hid_generic            12492  0 
snd_hda_codec_realtek    51029  1 
dell_laptop            17808  0 
compal_laptop          19199  0 
snd_hda_intel          42730  1 
dcdbas                 14448  1 dell_laptop
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
uvcvideo               71309  0 
snd_hwdep              13272  1 snd_hda_codec
lpc_ich                16864  0 
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
coretemp               13195  0 
i915                  705396  2 
videobuf2_vmalloc      13048  1 uvcvideo
psmouse                91033  0 
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
serio_raw              13230  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
videodev              108503  2 uvcvideo,videobuf2_core
snd_seq_midi           13132  0 
usbhid                 47035  0 
jmb38x_ms              18222  0 
snd_seq_midi_event     14475  1 snd_seq_midi
hid                    87604  2 hid_generic,usbhid
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
drm_kms_helper         46907  1 i915
snd                    60871  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
btusb                  27580  0 
drm                   243792  3 i915,drm_kms_helper
rfcomm                 53664  8 
bnep                   18895  2 
bluetooth             342263  22 bnep,btusb,rfcomm
memstick               16174  1 jmb38x_ms
parport_pc             31981  0 
ppdev                  17391  0 
arc4                   12536  2 
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
b43                   356470  0 
bcma                   42043  1 b43
mac80211              545990  1 b43
video                  18903  1 i915
mac_hid                13037  0 
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
sdhci_pci              18535  0 
r8169                  61562  0 
sdhci                  37779  1 sdhci_pci
mii                    13654  1 r8169

Anyway i see it appears the same. So I've tried to do what you have last said and it gives me a couple of errors.

---

### Post by jack_sparrow2 on 2014-04-30
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'b43'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 58: ignoring bad line starting with 'ssb'
modprobe: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'b43': Operation not permitted
modprobe: FATAL: Module ssb is in use.

---

### Post by jack_sparrow2 on 2014-04-30
this with the second comand:
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 57: ignoring bad line starting with 'b43'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 58: ignoring bad line starting with 'ssb'
modprobe: ERROR: could not insert 'wl': Operation not permitted

---

### Post by jack_sparrow2 on 2014-04-30
If you don't have any more suggestions I think I am going to give puppy linux or another distro thought for notebooks a chance to see wether it automatically detects wifi, because this is really disapointing and frustrating.

Anyway I THANK YOU ALL for your help, specially [**[COLOR=#000000]kc1di[/COLOR]**]("http://ubuntuforums.org/member.php?u=1839")!!! 

What I don't know is wether puppy linux or another distro of that type have LTS version. Any recommendation??

---

### Post by kc1di on 2014-04-30
what the errors were was because I forgot to tell you that you needed sudo first.  the commands should have looked like this.
```
sudo modprobe -r b43 ssb
sudo modprobe wl
```

I would suggest you try PCLinuxOS  it is very good at auto detecting your wireless card. 
However there is no reason we should not be able to get in going in ubuntu also. 
Good Luck whatever you decide.

---

### Post by wildmanne39 on 2014-04-30
Sorry, I have had a long week and fell a sleep for a while, if you post a new wireless file I will have  a look to see where your current connection is at and see if we can fix it, the b43 with LP-PHY is what you need.

---

### Post by jack_sparrow2 on 2014-05-01
> **kc1di said:**
> what the errors were was because I forgot to tell you that you needed sudo first.  the commands should have looked like this.
```
sudo modprobe -r b43 ssb
sudo modprobe wl
```

I would suggest you try PCLinuxOS  it is very good at auto detecting your wireless card. 
However there is no reason we should not be able to get in going in ubuntu also. 
Good Luck whatever you decide.

Ít gives me the same error as before even adding "sudo" before.:(

---

### Post by jack_sparrow2 on 2014-05-01
> **Wild Man said:**
> Sorry, I have had a long week and fell a sleep for a while, if you post a new wireless file I will have  a look to see where your current connection is at and see if we can fix it, the b43 with LP-PHY is what you need.



Lets take another chance! here is the paper.

---

### Post by wildmanne39 on 2014-05-01
Hi, lets get this working, sorry I went to eye Doctor this morning and he dilated my eyes and I have not been able to see all day.

Please do:
```
sudo apt-get purge bcmwl-kernel-source
``` 
Then open your blacklist file and put a # in front of:
```
blacklist b43
blacklist ssb
blacklist bcma
```
Do:
```
sudo leafpad /etc/modules
```
remove one of the b43's and then save and close the file.
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```

Also there is a bug in lubuntu 14.04 where network manager is not showing up in the panel here is a workaround.
[http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing/451599#451599](http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing/451599#451599)
after you do all of this please reboot and if your network name has special characters in it like _ please remove them. 

Set your channel in your router to 1 or 11 and make sure encryption is set to wpa2 AES. 
If it will not connect run and post a new file so we can make sure the changes took effect.
Thanks

---

### Post by jack_sparrow2 on 2014-05-02
Hi,

I'm sorry but I get lost at the second step. I think this is my blacklist archive, where should I add #? Shoul I also delete the last two lines that I had added in the previous tryings of solving the problem?

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
blacklist bcm43xx

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

b43
ssb

---

### Post by jack_sparrow2 on 2014-05-02
> **Wild Man said:**
> 
Also there is a bug in lubuntu 14.04 where network manager is not showing up in the panel here is a workaround.
[http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing/451599#451599](http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing/451599#451599)


SOLVED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Finally!!!! Thank you so much for your help. Now I am a happy and full user of Lubuntu 14.04 LTS. Muchísimas graciaaaaaaaaaaaaaaaaaaaaaaas!!!!!  :D:D:D:D:D:D
I post the solution here, hope it is helpful for someone else.
[B]
SOLUTION:
Lubuntu 14.04: The Network Manager icon doesn't show up by default for some users by default. Until the Lubuntu developers fix [this]("https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1308348"), here's how to get the Network Manager icon back.[/B]


To fix the Network Manager not showing up on the panel issue, from the Lubuntu menu select *Preferences > Default applications for LXSession*,  then click on the Autostart tab and under "Manual autostarted  applications" type "nm-applet", then click the "+ Add" button on the  left. Now log out, log back in and you should see the Network Manager icon on the panel.
Then restart pc.

Note that if you ran nm-applet with "sudo", like it was suggested in  some other places, nm-applet may no longer start without sudo (because  sudo changes some permissions or maybe something else is causing this  for some users?) and I'm not sure how to fix that.

The solution in this article (without sudo) was tested and is working on  my netbook as well as on a fresh Lubuntu 14.04 installation in  VirtualBox.

---

### Post by wildmanne39 on 2014-05-02
Glad it is working and that you found the answer on askubuntu useful.
Enjoy!

---

### Post by TechieZero on 2014-08-14
> **kc1di said:**
> you have the same card I do in my Laptop - You have the b43 driver installed though that will work with the bcm4312 I find that the WL/sta driver works much better for me.  I know some will argue the point.  but lets try it and see if you can get on line.

in a terminal type: ```
sudo apt-get install bcmwl-kernel-source 
```

Installing this package **fixed my issue immediately** --- I did _not _have to edit the blacklist configs.

This was right after a fresh install of Lubuntu 14.04 on to the Dell Inspiron 910.

Thanks!!!

---

