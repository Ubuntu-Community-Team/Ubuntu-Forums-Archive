---
title: "No sound on Ubuntu 9.1"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by inggiulietta on 2009-11-23
Hi everyone!

I'm absolutely desperate because I have upgraded to Ubuntu 9.1 but now have no sound at all.
When I first did it I had sound on skype but, because I couldn't listen to music, I tried to switch from alsa to oss.... It's been a complete disaster!!!
Now the system doesn't even recognize the sound card.
Please help me....:confused:

Thanks!

Giulia

---

### Post by Sealbhach on 2009-11-23
Did you uninstall a lot of stuff? Perhaps you could go into Synaptic, look at the history, and reinstall what you removed.

.

---

### Post by inggiulietta on 2009-11-24
I guess you're right but to be honest I've tried to fix the problem so many times and made loads of changes so now I don't know what I need to reinstall!
 
Isn't there a procedure to make my system detect the sound card (or a list of things I need to install in order ot do it)?
 
Thank you!

---

### Post by Julita on 2009-11-24
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) there is a great problems' guide! It solved everything for me!

---

### Post by epicoder on 2009-11-24
In case that doesn't work, you could use [this guide]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/") to upgrade alsa. This works on Jaunty and Karmic.

---

### Post by inggiulietta on 2009-11-25
I'm trying to follow the procedure that is on 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
but I can't find the driver that matches my sound card (step 3).
Can someone help me???

My sound card is Intel Corporation 82801H (ICH8 Family) USB UHCI controller 
(this is the output from lspci command

Thank you!

---

### Post by pi.boy.travis on 2009-11-25
Did you remove pulseaudio?  I am guessing you did, since skype doesn't have support for it yet.

---

### Post by inggiulietta on 2009-12-04
I removed pulseaudio but i still don't know what to do...
Can someone tell me how to find the driver that matches my sound card? I wrote down the name of my sound card in an earlier post...

---

### Post by ndo on 2009-12-05
You should really consider using this one here that the other dude posted:

[http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)

It worked for me - kind of. Out of the box UBU was pure sound failure, but after following this tutorial this "marvel" of an OS at least detected my sound card. VLC is still silent, but at least streaming video and system dings are working...christ, basic sound doesn't work on their freaking update and still they wonder why the majority of mainstreamers won't touch Linux with a 20 ft pole...

---

### Post by lloyd_b on 2009-12-05
> **inggiulietta said:**
> I'm trying to follow the procedure that is on 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
but I can't find the driver that matches my sound card (step 3).
Can someone help me???

My sound card is Intel Corporation 82801H (ICH8 Family) USB UHCI controller 
(this is the output from lspci command

Thank you!

Could you please post the output of 'lspci'?  The 82801H is NOT a sound device, but a bridge device that could actually be connected to one of a number of different sound devices.  The full output from 'lscpi' should include info to identify the actual sound device.

Lloyd B.

---

### Post by inggiulietta on 2009-12-07
I hope this will help...

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by lloyd_b on 2009-12-07
Okay, that clarifies the situation.  You have what's known as an Intel HDA sound device (you had me confused with your reference to "USB UHCI Controller").

Next step - determine if it's loading a driver for the device.  In a terminal window, please run the following and post the results:```
lshw -c Multimedia
```, the command ```
cat /proc/modules | grep snd
``` and the command ```
sudo aplay -l
``` and finally the command ```
aplay -l
``` (don't bother posting this if it's the same as the results from the previous command).

Sorry about all the "could you please post ..." requests, but the more info you can give us, the better the chance of us figuring this out.

Lloyd B.

---

### Post by Julita on 2009-12-08
HDA Intel has issues with Ubuntu. The solution explained here: [help.ubuntu.com/community/HdaIntelSoundHowto](help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by inggiulietta on 2009-12-09
I hope this will help! I really need this problem to be sort out!
Thank you very much!

giuseppe@giuseppe-laptop:~$ lshw -c Multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=oss_hdaudio latency=0
       resources: irq:22 memory:92400000-92403fff
giuseppe@giuseppe-laptop:~$ cat /proc/modules | grep snd
giuseppe@giuseppe-laptop:~$ sudo aplay -l
aplay: device_list:223: no soundcards found...
giuseppe@giuseppe-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
giuseppe@giuseppe-laptop:~$

---

### Post by lloyd_b on 2009-12-09
It doesn't appear to be loading the sound drivers for that chip.

In a terminal window```
sudo modprobe snd-intel-hda
```If this generates an error, please post the error.

If no error, type ```
aplay -l
``` again, and see if it shows your sound card.

(note: if it does show up, but you get no sound in your applications, check the mixer and make sure that the channels are unmuted).

If this *does* restore your sound, then you need to edit a file to make it permanent```
sudo nano /etc/modules
``` and add a line "snd-intel-hda" to the end of the file.

Lloyd B.

---

### Post by inggiulietta on 2009-12-09
I think this is bad....let's see what you think...

giuseppe@giuseppe-laptop:~$ sudo modprobe snd-intel-hda
[sudo] password for giuseppe: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module snd_intel_hda not found.
giuseppe@giuseppe-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
giuseppe@giuseppe-laptop:~$

---

### Post by lloyd_b on 2009-12-11
> **inggiulietta said:**
> I think this is bad....let's see what you think...

giuseppe@giuseppe-laptop:~$ sudo modprobe snd-intel-hda
[sudo] password for giuseppe: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module snd_intel_hda not found.
giuseppe@giuseppe-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
giuseppe@giuseppe-laptop:~$

I think it was just a typo on my part.  Try "sudo modprobe snd-hda-intel" instead.:oops:

Lloyd B.

---

### Post by k3liutZu on 2009-12-12
Sorry to barge in on this thread.

I had the exact problems as the thread initiator.
I managed to reinstall my alsa drivers, and install the intel hds sound card follosing all these steps.

I still don't get any sound, but at least I have now a device in my Sound Preferences > Hardware tab.

Any clues on what to do next? I had a similar problem in 8.x, after I did an upgrade, and it was a kernel bug back then. And the issue got fixed with a new kernel version.

---

### Post by inggiulietta on 2009-12-14
No good news again...

giuseppe@giuseppe-laptop:~$ sudo modprobe snd-hda-intel
[sudo] password for giuseppe: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module snd_hda_intel not found.
giuseppe@giuseppe-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
giuseppe@giuseppe-laptop:~$

---

### Post by k3liutZu on 2009-12-14
Well, I have reinstalled ubuntu, and have it working now :)

Alsa drivers work just fine now.

---

### Post by lloyd_b on 2009-12-14
> **inggiulietta said:**
> No good news again...

giuseppe@giuseppe-laptop:~$ sudo modprobe snd-hda-intel
[sudo] password for giuseppe: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module snd_hda_intel not found.
giuseppe@giuseppe-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...
giuseppe@giuseppe-laptop:~$

That is really weird.

Here's another terminal command to run:```
find /lib/modules -name "snd-hda*" -print
```  On my machine, I get the following:```

lloyd@dell:~$ find /lib/modules -name "snd-hda*" -print
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
**/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko**
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
```with the one in bold being the critical one.

Please check and see if you get the same results...

Lloyd B.

---

### Post by inggiulietta on 2009-12-16
I think it's the same as yours.

find /lib/modules -name "snd-hda*" -print
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.31-16-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.28-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.31-15-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-15-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.31-15-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-15-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.31-15-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.31-15-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.31-15-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-15-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.31-15-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.31-15-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko

---

### Post by rosswmcgee on 2009-12-18
See my post "Helping a Friend"

---

### Post by inggiulietta on 2009-12-18
I've seen your post but I have a laptop and so the cable problem doesn't apply to me.
Moreover, the sound was perfect with the previous version of ubuntu (and my computer is always the same...).
Thank you anyway!
I really hope someone will help me because I can't believe an operative system has a huge problem like this!

---

### Post by madman559 on 2009-12-18
I had a similar problem before I re-installed. I had to run 
this code every time I rebooted.
I just wrote a shell script that did it for me.

```
sudo alsa force-reload
```

---

### Post by ericpvk on 2009-12-24
hello,

After reading about 20 posts and not getting anywhere, I finally found a driver for my via chipset sound card. Here's the link to the site.

[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

It supports quite a few sound cards and distros, just check the list and see if your card is there then pick the type of package you need. I'm a total nubie and got it to work the first time. Hope this helps.

---

### Post by inggiulietta on 2009-12-29
Unfortunately nothing works on my computer....
I've tried everything and still have no audio.
Unless someone helps me in the next few days, I'll switch back to XP because I need my computer to work properly.
Thank you anyway!

---

### Post by magump on 2010-01-30
Did you ever resolve your audio (no sound) problem?  I thought I had a problem with sound also and found that my volume control was set to 0.  (dumb me!)  I have used Ubuntu '2005 and now run ubuntu on my old system and Mint on my new system.  I love both systems but tend to favor Mint because more of the restricted codecs, etc. are pre-installed.  I originally went to Mint because I couldn't play video on CNN.  However, that has been corrected.

---

### Post by chill3570 on 2010-02-01
I am having the same issue. Seems same hardware as the first user.
Was there ever a solution.  All was fine before upgrade to 9.10

       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:21 memory:f6afc000-f6afffff
chill3570@dell-desktop:~$

---

### Post by cicciopapero on 2010-02-15
PROBLEM: No sound using alsa AS A NORMAL USER from the command line.
I use Ubuntu with a window manager but no desktop.
Starting with 9.04, I was only able to use sound from root, but there
I fixed the problem by giving user permissions to /dev/snd.
Starting with 9.10, user cannot get sound even after adding user to
the audio group and giving user permissions to /dev/snd; sound still works
well for root.

Most of the questions in this thread seem to imply problems with alsa/pulse or with not using the right device. My problem is simple, more fundamental, but CHRONIC---and I'm sure a lot of other people must have the same problem. I'm tired of trying a lot of "solutions" given by people that are well-intentioned but apparently groping in the dark themselves. If the problem were clear, the solution would probably be obvious and it would actually work. IS IT POSSIBLE THAT NO ONE KNOWS WHAT THE PROBLEM MIGHT BE? I've been using Linux as a power user for over ten years, and I usually end up solving my problems without having to scream. But this problem makes me doubt the wisdom of giving more and more power to the desktop (why not?) but without checking that things don't get broken at the command-line level. 

Sincere thanks for any help in this!

---

### Post by Julita on 2010-02-15
chill3570, did you use the command
```
 sudo adduser yourusername audio
```?

Create another user to see if it is a global problem.

---

### Post by Krishna C. Addanki on 2010-02-19
> **lloyd_b said:**
> It doesn't appear to be loading the sound drivers for that chip.

In a terminal window```
sudo modprobe snd-intel-hda
```If this generates an error, please post the error.

If no error, type ```
aplay -l
``` again, and see if it shows your sound card.

(note: if it does show up, but you get no sound in your applications, check the mixer and make sure that the channels are unmuted).

If this *does* restore your sound, then you need to edit a file to make it permanent```
sudo nano /etc/modules
``` and add a line "snd-intel-hda" to the end of the file.

Lloyd B.


Hi Lloyd, I am totally new to Ubuntu and have been facing the problem of no audio in this OS. I was following your instructions and when I typed in the commands, it was shown in the terminal that the sound card is detected but still I cannot play the audio in the system. I checked the audio preferences and other things with the little knowledge I have but was not successful. Could you please guide me through this? Thanks a lot.

I am pasting below the commands and the results from the terminal for your reference:

chaitanya@chaitanya-laptop:~$ sudo modprobe snd-intel-hda
FATAL: Module snd_intel_hda not found.
chaitanya@chaitanya-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Julita on 2010-02-19
Please install this (works both for alsa and pulseaudio): linux-backports-modules-alsa-your_kernel-generic (if unsure, go to Synaptics and in search field just type linux-backports-modules-alsa) and linux-backports-modules-alsa-karmic-generic. Then add to /etc/modprobe.d/alsa-base in the Option sections the following line: snd-hda-intel model=auto Then reboot.

---

