---
title: "Netgear Wireless USB Adapter in Ubuntu 14.04?"
date: 2014-06-06
forum: Networking &amp; Wireless
---

### Post by s.prough93 on 2014-06-06
I can't seem to get my adapter to work. I am new to Ubuntu and would rather enjoy getting to learn it but I can't figure out how to get this to work. I do not have access to a wired connection. Please help!

It's a Netgear N300

---

### Post by Andrew F in Australia on 2014-06-06
I can't help with detail but open up a terminal window (ctrl+alt+T)and type in the following commands (one at a time) then post the output here.

uname -a
 lsusb 
iwconfig 
ifconfig 
lsmod 
lsb_release -a

This'll help out others that are very familiar with the system architecture

edit: the adapter needs to be plugged in when you do this.

---

### Post by s.prough93 on 2014-06-06
Here you go:
```

main@main-TA890GXB-HD:~$ uname -a
Linux steven-TA890GXB-HD 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


main@main-TA890GXB-HD:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


main@main-TA890GXB-HD:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


main@main-TA890GXB-HD:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:67:6c:e2:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11505 (11.5 KB)  TX bytes:11505 (11.5 KB)


main@main-TA890GXB-HD:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
udf                    89723  1 
crc_itu_t              12707  1 udf
snd_hda_codec_hdmi     46207  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
joydev                 17381  0 
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm_amd                59987  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm                   451511  1 kvm_amd
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
psmouse               102222  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13462  0 
k10temp                13126  0 
snd_timer              29482  2 snd_pcm,snd_seq
ppdev                  17671  0 
edac_core              62291  0 
edac_mce_amd           22617  0 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
radeon               1514165  3 
sp5100_tco             13979  0 
lp                     17759  0 
i2c_piix4              22155  0 
parport_pc             32701  1 
parport                42348  3 lp,ppdev,parport_pc
ttm                    85115  1 radeon
drm_kms_helper         52758  1 radeon
mac_hid                13205  0 
drm                   302817  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
soundcore              12680  1 snd
pata_acpi              13038  0 
r8169                  67581  0 
ahci                   25819  3 
mii                    13934  1 r8169
pata_atiixp            13271  0 
libahci                32168  1 ahci


main@main-TA890GXB-HD:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

```

---

### Post by Andrew F in Australia on 2014-06-07
HI Steve,

Since no-one else has answered, you've got the Broadcom BCM43231 Chipset - that's the driver you need.

A quick search found this:

[https://www.google.com.au/search?client=ubuntu&channel=fs&q=BCM43231+linux](https://www.google.com.au/search?client=ubuntu&channel=fs&q=BCM43231+linux)

Regards,

AF

---

### Post by s.prough93 on 2014-06-07
Okay, I only have found one spot where I can still find the drivers.

But I can't get ndiswrapper to install. I've downloaded .deb files and the .tar.gz but everytime the installation fails.

---

### Post by Andrew F in Australia on 2014-06-07
Hi,

I've never had to install ndiswrapper, so hopefully someone else can jump in.

Looks as though you've got a bit of a task ahead of you.
[https://www.google.com.au/search?client=ubuntu&channel=fs&q=0846:9020](https://www.google.com.au/search?client=ubuntu&channel=fs&q=0846:9020)
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)
[http://matthew-4gl.wikispaces.com/wna3100_ubuntu_linux](http://matthew-4gl.wikispaces.com/wna3100_ubuntu_linux)

[http://ubuntuforums.org/showthread.php?t=2174748](http://ubuntuforums.org/showthread.php?t=2174748)
[http://ubuntuforums.org/showthread.php?t=1965989&p=11876626](http://ubuntuforums.org/showthread.php?t=1965989&p=11876626)


Good luck with it from here, I'm away from computer for next few hours -> Can someone help s.prough out with ndiswrapper??

---

### Post by Andrew F in Australia on 2014-06-08
*bump* on s.prough's behalf

Ndiswrapper help (I've never had to deal with it,) and;
help with compilation perhaps.  Links above, script needs adding to the driver file before it's compiled.

AF

---

### Post by Andrew F in Australia on 2014-06-13
[http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)

---

