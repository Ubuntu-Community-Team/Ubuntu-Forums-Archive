---
title: "Wifi adapter Ralink RT2870"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Jeffreylb94 on 2010-10-06
I am new to linux, and I have the xp file for my wifi adapter. I went to [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and downloaded the file called "RT2870USB(RT2870/RT2770)" I go to my desktop, and I'm lost... How do I install? I have the wifi adapter plug in, but nothing happens... I have never used a linux os before, so I need help. Thank you for your help. I really want to use linux, but I can't find out how to install, and I don't have internet cause the desktop is to far to get internet by cable.

---

### Post by roger_1960 on 2010-10-06
Hi

Open the terminal and type in
> 
sudo rmmod rt2800usb

enter your password (it wont show up)

Then wait at least a minute.  (I found this solution by using the search box at the top right of the forum)  Hope it works for you.  If so, you dont need any downloaded file.  This was from post [http://ubuntuforums.org/showthread.php?t=1523341](http://ubuntuforums.org/showthread.php?t=1523341)  See also post #11 in that thread to make the change permanent if it works.

---

### Post by albert s on 2010-10-06
have you tried just plugging it in?
some wifi adapters are plug and play, like the edimax EW-7318USg

---

### Post by Hippytaff on 2010-10-06
If that doesn't work open a terminal (CTRL+ALT+T) and enter this

```

lsusb

```and copy and paste the results. - btw welcome :-)

forgot to say - with the usb wifi effort plugged in ;-)

EDIT - NO NEED TO DO THIS :-)

---

### Post by Calash on 2010-10-06
That chipset is built in and works great with 10.04.  It is the same as in the Buffalo nfinity USB adapter.

I had issues with it on 10.10.  Nothing major, it just requires some blacklisting of modules.

---

### Post by Jeffreylb94 on 2010-10-06
I know have it working, but when I see available wifi routers I click mine... Our is locked, so I enter the correct password, but I don't know if our security is "WEP 40/128-bit key" I have tried all the options multiple times with the correct password, but It will just ask me for the password again... Does anyone know the issue? I did not have to install anything, just re-installed ubuntu, and it shows the routers available, but after about a minute the "Wireless network authentication required" pops right back up

---

### Post by Jeffreylb94 on 2010-10-06
I ran sudo rmmod rt2800usb in the terminal, but it says
"ERROR: Module rt2800 does not exist in /proc/modules" I just downloaded [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) Would this be the issue? Am I using the correct version?

---

### Post by Hippytaff on 2010-10-06
enter
```

lsmod

```

see what modules are there

---

### Post by Jeffreylb94 on 2010-10-06
I did LSMOD and received "Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/2/4GB Flash Drive
Bus 001 Device 006: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 005: ID 03f0:4605 Hewlett-Packard ScanJet G4050
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
"

---

### Post by anewguy on 2010-10-06
It would also help if you could post the outputs of:

ifconfig

iwconfig

sudo lsmod

These will show what, if anything, your computer thinks is available in the way network adapters, including wireless, and what driver it may be trying to use.

The lsmod will list the kernel modules that got loaded at boot - we can use this to see (1) if there is a conflicting module  (2) if a needed module is not getting loaded.

Thanks
Dave ;)

---

### Post by anewguy on 2010-10-06
Also, about it asking over and over for the network password/passphrase, yes, you will need to match the correct encryption type (WEP, WPA, WPA2-PSK AES, etc.).  Is it possible the router also MAC address filtering turned on?  If so, and if your PC is not in the list, you'll just get caught in that loop.

Dave ;)

---

### Post by Jeffreylb94 on 2010-10-06
Would this help? I just copied exactly what is sayed "jeffrey@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:72:b5:24:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:90:3c:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



jeffrey@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


jeffrey@ubuntu:~$ sudo lsmod
[sudo] password for jeffrey:
Module                  Size  Used by
nls_utf8                1069  1
isofs                  29250  1
nls_iso8859_1           3249  2
nls_cp437               4919  2
vfat                    8933  2
fat                    47767  1 vfat
binfmt_misc             6587  1
fbcon                  35102  71
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0
vgastate                8961  1 vga16fb
snd_intel8x0           25588  2
snd_ac97_codec        100646  1 snd_intel8x0
rt2870sta             461811  0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
arc4                    1153  2
snd_seq_dummy           1338  0
snd_seq_oss            26726  0
snd_seq_midi            4557  0
rt2800usb              31531  0
rt2x00usb               9703  1 rt2800usb
snd_rawmidi            19056  1 snd_seq_midi
rt2x00lib              27509  2 rt2800usb,rt2x00usb
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
led_class               2864  1 rt2x00lib
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              205146  2 rt2x00usb,rt2x00lib
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              126517  2 rt2x00lib,mac80211
i915                  285076  3
ppdev                   5259  0
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt               1339  1 rt2800usb
drm_kms_helper         29297  1 i915
dell_wmi                1793  0
parport_pc             25962  1
soundcore               6620  1 snd
intel_agp              24119  2 i915
drm                   162377  4 i915,drm_kms_helper
psmouse                63245  0
dcdbas                  5422  0
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
i2c_algo_bit            5028  1 i915
serio_raw               3978  0
agpgart                31724  2 intel_agp,drm
video                  17375  1 i915
lp                      7028  0
output                  1871  1 video
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0
usb_storage            39425  3
hid                    67032  1 usbhid
tg3                   109324  0
jeffrey@ubuntu:~$
"

---

### Post by Jeffreylb94 on 2010-10-06
I think my encryption type is WEP... How will I know if MAC address filtering turned on? How do I locate these?

---

### Post by Calash on 2010-10-07
> **Jeffreylb94 said:**
> I think my encryption type is WEP... How will I know if MAC address filtering turned on? How do I locate these?

You will need to check your router for that.  If somebody set it up for you they should be able to guide you on how to get that information.  If not you may have to break out the manual or search on the type of router.

What kind is it?  Somebody here may have a similar model and be able to help as well.

---

### Post by Jeffreylb94 on 2010-10-07
> **Calash said:**
> You will need to check your router for that.  If somebody set it up for you they should be able to guide you on how to get that information.  If not you may have to break out the manual or search on the type of router.

What kind is it?  Somebody here may have a similar model and be able to help as well.

My router is Westell versalink 327w

---

### Post by anewguy on 2010-10-08
Roger_1960 mentioned earlier removing the rt2800 modules, but you indicated that the command said none found.  As can be seen from these lines in the output of lsmod, the rt2800usb modules are loaded:

```
rt2800usb 31531 0
rt2x00usb 9703 1 rt2800usb
rt2x00lib 27509 2 rt2800usb,rt2x00usb

```

Now, just exactly why it wouldn't remove the module, I don't know.

I also am not a user of your adapter, so for now we can try roger_1960's advice and see what happens:

sudo rmmod rt2x00usb

sudo rmmod rt2x00lib

sudo rmmod rt2800usb

Then follow the rest of roger_1960's advice and see what happens.

Post the results back here.

Dave ;)

---

### Post by dineshs on 2010-10-08
Please see if the following links can guide
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)
[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)
[http://ubuntuforums.org/showpost.php?p=9767936&postcount=11](http://ubuntuforums.org/showpost.php?p=9767936&postcount=11)

---

### Post by linux-hack on 2010-10-08
> **Jeffreylb94 said:**
> I am new to linux, and I have the xp file for my wifi adapter. I went to [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and downloaded the file called "RT2870USB(RT2870/RT2770)" I go to my desktop, and I'm lost... How do I install? I have the wifi adapter plug in, but nothing happens... I have never used a linux os before, so I need help. Thank you for your help. I really want to use linux, but I can't find out how to install, and I don't have internet cause the desktop is to far to get internet by cable.

This works out of the box on linux ...

---

### Post by Jeffreylb94 on 2010-10-08
> **dineshs said:**
> Please see if the following links can guide
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)
[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)
[http://ubuntuforums.org/showpost.php?p=9767936&postcount=11](http://ubuntuforums.org/showpost.php?p=9767936&postcount=11)

Thank you! [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593) did the trick... It was a conflicting driver!!! :) :) :) :) :) Thanks!!!

---

### Post by Jeffreylb94 on 2010-10-08
> **Jeffreylb94 said:**
> I am new to linux, and I have the xp file for my wifi adapter. I went to [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and downloaded the file called "RT2870USB(RT2870/RT2770)" I go to my desktop, and I'm lost... How do I install? I have the wifi adapter plug in, but nothing happens... I have never used a linux os before, so I need help. Thank you for your help. I really want to use linux, but I can't find out how to install, and I don't have internet cause the desktop is to far to get internet by cable.
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593) I had a conflicting driver!

---

### Post by anewguy on 2010-10-08
Which driver??   Might help others who end up with the same problem.

Dave

---

### Post by Jeffreylb94 on 2010-10-08
> **anewguy said:**
> Which driver??   Might help others who end up with the same problem.

Dave

Wifi adapter Ralink RT2870

---

### Post by Malcolm Waterman on 2010-10-13
Hi,
       I was also having problems with my Ralink RT2870. After trying installing WICD, installing the drivers from the Ralink websight, I did find a method which seems to be working. This is what I did:

1) I installed ndiswrapper, using the following URLs to download:
[http://gb.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb)
[http://gb.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb)
[http://gb.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb)

Or you could make a script by typing in ndiswrapper and selecting ndiswrapper-common for installation. Then, once it's marked, File -> Generate package download script and then save. It will save as plain text and will be easy to get the URLs

2) I blacklisted the current drivers by:
[LIST=1]
[*]Opening Terminal
[*]Entering "gksu gedit /etc/modprobe.d/blacklist.conf"
[*]Once it had opened I added part way through the file "blacklist rt2800usb". Please note that it is possible on some systems, the device might not be called rt2800usb. If that happens you will need to install and run Device Manager (gnome-device-manager,) which will be available through Applications -> System Tools. The Adapter should be displayed as WLAN Interface. You will need to find the line under properties that says "info.linux.driver" and it might be in any of the mentioned devices that are higher up the thread in Device Manager. Though hopefully it will work just fine with the rt2800usb designation.
[*]I then saved the file and rebooted.
[/LIST]
3) You need to have the 2 or maybe 3 files in the archive. I know you need oem40.inf and rt2870.sys for this part. You need to run ndiswrapper by going to System -> Administration -> Windows Wireless Drivers. You then need to select the inf file and that should activate the wireless device. If it doesn't then e-mail me with the information [EMAIL="malcolmdw@hotmail.com"]malcolmdw@gmail.com[/EMAIL]

Addition: There has been some problems with the method I've outlined. It seems that there may be a slight incompatibility which means that if you connect and disconnect using this device after using my method, you might end up with Ubuntu crashing. I think though, if you wait for a few minutes *before unplugging after disconnecting *then that might stop the problem. Please e-mail me if this seems to work or if you see a crash anyway.

---

### Post by Malchuth on 2010-10-14
I just registered to say "thank you"!
Works for me!

I did the same (from the last post) back at the release of Lucid Lynx but had forgotten what exactly needed to be done, so now Maverick works just fine ;)
(Even though the drivers work out of the box in Maverick, I still suffered from connection drops and a bad connection which seems now solved)

Thx!

---

