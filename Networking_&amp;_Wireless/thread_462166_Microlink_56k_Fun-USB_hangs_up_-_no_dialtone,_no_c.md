---
title: "Microlink 56k Fun-USB hangs up - no dialtone, no carrier, trying again - Kubuntu edgy"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by yollywau on 2007-06-02
My Acer Aspire 5100 Notebook with AMD 64 Turion CPU and snd-hda-intel sound fails with the PCI conexant Modem and with Microlink 56k Fun-USB. Kernel 2.6.17-10-generic.
This no dialtone-problem is posted in this forum for some times, but I am still offline until now.

In XP, Microlink 56k Fun USB is listed as smartlink. The USB-Modem works on another laptop with the smartlink driver.
I tried the newer slmodemd*tar.gz  of linmodems.technion.ac.il/packages/smartlink/ and the newest smartlink package, section ubuntu. I can dial with wvdial or kppp, but I get no connection or the modem hangs up after a minute.  
After the command:sudo mknod -m 600 /dev/slusb0 c 243 0 and
sudo slmodemd -c GERMANY /dev/slusb0, the query in kppp works, and the modem dials.
I wrote Carrier Check=no and stupid Mode=yes in wvdial.conf. I tried something in /etc/ppp/options.
I forgot in the end, what I did in the beginning...I tried with sl-modem-daemon, sl-modem source, module assistant of ubuntu.packages.com. Make and make install for slmodemd...tar.gz and sudo dpkg -i sl-modem-daemon.
The end: no carrier, no dialtone, no internet...

SLMODEMD.gcc4.1 of linmodems and then that...

sudo slmodemd --alsa -c YOUR_COUNTRY modem:1
error: mixer setup: attach hw:1 error: No such device
ALSA lib confmisc.c:670snd_func_card_driver) cannot find card '1'
ALSA lib conf.c:3479_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391snd_func_concat) error evaluating strings
ALSA lib conf.c:3479_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070snd_func_refer) error evaluating name
ALSA lib conf.c:3479_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline:CARD=1,DEV=0
error: alsa setup: cannot open playback device 'modem:1': No such device
error: cannot setup device `modem:1'

In the end, I tried the hsf-conexant driver of linuxant for the PCI-modem. No modem was found, and there was no sound any more. I am out of ideas, what I can do. Must I write the driver for my own and tell the kernel to load the module. I hope not...

Can you help me?





The ModemData of ./scanMode

 Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org .
 Local Linux experts can be found through: http://www.linux.org/groups/index.html
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
 scanModem update of:  2007_May_11
The modem symbolic link is /dev/modem -> ttySL0

ALSAversion 1.0.11
Bus 001 Device 005: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem
  idVendor           0x0483 SGS Thomson Microelectronics
  idProduct          0x7554 56k SoftModem
  idVendor           0x1267 Logic3 / SpectraVideo plc
  idProduct          0x0210 
  idVendor           0x045e Microsoft Corp.
  idProduct          0x008a Wireless Keyboard and Mouse

Modem or host audio card candidates have firmware information:

 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 00:14.2    1002:437b    1025:009f    Audio device: ATI Technologies Inc Unknown device 437b 

 Modem interrupt assignment and sharing: 
209:       4118   IO-APIC-level  HDA Intel

 --- Bootup diagnositcs for card in PCI slot 00:14.2 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

1002:437b is a High Definition Audio card, possibly hosting a soft modem.
 For candidate modem in PCI bus:  00:14.2
   Class 0403: 1002:437b Audio device: ATI Technologies Inc Unknown device 437b
      Primary PCI_id  1002:437b
    Subsystem PCI_id  1025:009f 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: 14f1, a Conexant type,
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:    hsfmodem

 Already loaded into the kernel is snd-intel8x0m and audio drivers it depends on,
 displayed by:    lsmod | grep snd_intel8x0m
Module                  Size  Used by
-------------------------------------
snd_intel8x0m          18956  0 
snd_ac97_codec         97696  1 snd_intel8x0m
snd_pcm                84612  5 snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    58372  8 snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11400  3 snd_intel8x0m,snd_hda_intel,snd_pcm


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
    /proc/asound/pcm
-------------------------------
00-01: ALC883 Analog : ALC883 Analog : capture 2
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 2

    /proc/asound/modules
-------------------------------
 0 snd_hda_intel
and from the command:
    aplay -l | grep -i modem


----------------end Softmodem section --------------

 Formal support for Conexant chipset modems are available ONLY through 
 http://www.linuxant.com/drivers.  Read Conexant.txt for details.
 and Modem/YourSystem.txt for follow through guidance.  Driver speed is limited to
 14,400 until a key is purchased.  There is NO freeware alternative.
 There are two support package types: hsfmodem  and hcflinmodem.
 http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B reports a
 problem and solution in stalling a key, after testing of the free low
 speed download.

 The hsfmodem package serves a great variety of Conexant chipset modems. 
 From  http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php
 download hsfmodem_VersionSpec_k2.6.17_10_generic_ubuntu_i386.deb.zip 
                           with 2.6.17_10_generic equivalent to 2.6.17-10-generic, your kernel version.
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See Testing.txt  for details.
 
 Read Conexant.txt

Writing Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
    -rwsr-xr-- 1 root dip 260920 2006-07-10 21:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html

To enable dialout without Root permission do:
    $ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
    sudo chmod a+x /usr/sbin/pppd

Checking settings of:    /etc/ppp/options
asyncmap 0
noauth
defaultroute
crtscts
lock
hide-password
modem
noipdefault
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx
idle 300

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html


 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2007-05-30 07:55 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",            SYMLINK+="modem"
/etc/udev/rules.d/030_sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/rules.d/030_sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-baseptions snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-baseptions snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

