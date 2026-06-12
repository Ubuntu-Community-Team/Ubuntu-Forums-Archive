---
title: "Dell inspiron 1545 wireless driver issue"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by kletops on 2010-06-01
Hello I just installed ubuntu 10.04 amd 64, the proprietary graphics driver and the wireless one. But I can not use the wireless option in network manager!I attached some pictures to prove the drivers are installed. What can I do to fix this?
If i go to the network manager I can use wired networks but not wireless. The wireless is with gray and it says "disconnected". I pressed f2 for wireless and bluetooth appeared. So wireless is enabled.

[IMG]http://img413.imageshack.us/img413/1783/hardwaredrivers.png[/IMG]
Please help me out!

---

### Post by dhirendra1 on 2010-06-01
Try disabling Broadcom driver and stick to ATI proprietory one.  Restart the system.  It might work.

---

### Post by kletops on 2010-06-01
I think you didn't understood me. I have problems with my wireless card.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Tried this link but nothin, does not work.

Ati drivers are for one thing and broadcom for another. There is no link between them.

---

### Post by creativedave1977 on 2010-06-13
I installed Ubuntu 10.04 on June 6 and I have been having the same issues.  I have a Broadcom 4312 card and cannot get wireless to work on it.  I have tried just about every workaround.

---

### Post by bkratz on 2010-06-13
> **creativedave1977 said:**
> I installed Ubuntu 10.04 on June 6 and I have been having the same issues.  I have a Broadcom 4312 card and cannot get wireless to work on it.  I have tried just about every workaround.

Found this one earlier, checked the link today and it is still active.

[http://ubuntuforums.org/showpost.php?p=9134672&postcount=6](http://ubuntuforums.org/showpost.php?p=9134672&postcount=6)

---

### Post by sille777 on 2010-06-13
have you tried doing what this site says?

It worked for my wife's Dell with the same broadcom wireless chipset:

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

If I remember right its still the STA driver, but need the b43-fwcutter installed as well.

---

### Post by creativedave1977 on 2010-06-13
I followed the instructions at [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) and I was able to connect to my wireless router until I rebooted.  On reboot I get the same problem again.

---

### Post by sandyd on 2010-06-13
try
```

sudo modprobe wl

```
Ive found that ubuntu sometimes doesn't load the driver at first, you have to load it once manually before it will automatically load

```


iwconfig
ifconfig
lsmod

```

---

### Post by creativedave1977 on 2010-06-13
This is what I got when I typed in the commands:

david@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

david@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:ae:2e:82:38  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe2e:8238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5950125 (5.9 MB)  TX bytes:753839 (753.8 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4856685 (4.8 MB)  TX bytes:4856685 (4.8 MB)

david@ubuntu:~$ lsmod
Module                  Size  Used by
snd_hda_codec_idt      61418  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
ndiswrapper           244768  0 
lib80211_crypt_tkip     8676  0 
i915                  317872  3 
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wl                   1964968  0 
dell_wmi                2177  0 
snd                    70978  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211                6119  2 lib80211_crypt_tkip,wl
joydev                 11072  0 
dell_laptop             7941  0 
dcdbas                  6886  1 dell_laptop
psmouse                64608  0 
serio_raw               4918  0 
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
drm_kms_helper         30742  1 i915
intel_agp              29225  2 i915
drm                   198770  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  1 lp
usbhid                 40988  0 
hid                    83376  1 usbhid
usb_storage            49833  2 
ahci                   37646  1 
sky2                   48803  0 
david@ubuntu:~$

---

### Post by creativedave1977 on 2010-06-13
Also...I keep getting this error:

david@ubuntu:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

---

### Post by sandyd on 2010-06-14
try
```

sudo apt-get remove ndiswrapper
```

---

### Post by ddrichardson on 2010-06-14
I have a 1545 with Intel graphics, when installing 10.04 I had an issue with wireless where I selected the Broadcom driver from the Live CD and then installed. After installation I couldn't get the proprietry driver up and it wouldn't detect it.

To cut a long story short, I purged:
```
sudo apt-get purge linux-modules-backport-wireless-*
```Then rebooted, it was detected and off I went.

PS. Your warnings are because filenames in that folder need to end in .conf now - i.e. sound.conf. That said I'd check them because it might have the kernel module you need blacklisted.

---

### Post by creativedave1977 on 2010-06-14
I get this message when I try to remove the ndiswrapper:

david@ubuntu:~$ sudo apt-get remove ndiswrapper
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper

---

### Post by creativedave1977 on 2010-06-14
As you can tell, I am very new to linux...once I get this figured out, I will be in business and can start to learn this system more so I can help others.  I appreciated your replies!

---

### Post by ddrichardson on 2010-06-14
> **creativedave1977 said:**
> As you can tell, I am very new to linux...once I get this figured out, I will be in business and can start to learn this system more so I can help others.  I appreciated your replies!
OK but did you try purging backports?

---

### Post by creativedave1977 on 2010-06-14
Yes I did.  Keeps telling me that it could not find the package.

david@ubuntu:~$ sudo apt-get purge linux-modules-backport-wireless-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-modules-backport-wireless-*

---

### Post by ddrichardson on 2010-06-14
Sorry I mistyped it:
```
sudo apt-get purge linux-backports-modules-wireless-*
```

---

### Post by creativedave1977 on 2010-06-14
Thanks, now I get this message...still cannot find package

david@ubuntu:~$ sudo apt-get purge linux-backports-modules-wireless-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting linux-backports-modules-wireless-2.6.32-22-server for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-2.6.32-22-preempt for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-lucid-server for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-lucid-preempt for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-2.6.32-23-server for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-2.6.32-22-generic for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-2.6.32-23-preempt for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-lucid-generic for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-2.6.32-23-generic for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-2.6.32-21-preempt for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-2.6.32-21-server for regex 'linux-backports-modules-wireless-*'
Note, selecting linux-backports-modules-wireless-2.6.32-21-generic for regex 'linux-backports-modules-wireless-*'
E: Couldn't find package linux-backports-modules-wireless-*

---

### Post by ddrichardson on 2010-06-14
Yes it can, it's the ones above, there isn't one ending in * is what it's telling you. Have you rebooted too?

---

### Post by creativedave1977 on 2010-06-14
I just rebooted.  I still get the grayed out "wireless is disabled" message.

---

### Post by ddrichardson on 2010-06-14
Can you post a screen cap of the message?

---

### Post by sandyd on 2010-06-14
> **creativedave1977 said:**
> I get this message when I try to remove the ndiswrapper:

david@ubuntu:~$ sudo apt-get remove ndiswrapper
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper

oops.
typo
```

sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
```

---

