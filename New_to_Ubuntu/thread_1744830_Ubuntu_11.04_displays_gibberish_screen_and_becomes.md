---
title: "Ubuntu 11.04 displays gibberish screen and becomes unresponsive"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by beecheese on 2011-04-30
Dear Ubuntu folk,

I installed Ubuntu 11.04 on an older laptop last night and it has crashed 3 times in the last 24 hours. Each time this has happed, I have been in the middle of using either Chrome or Chromium and the screen becomes unreadable and covered in lots of grey and white horizontal lines. To get things back to normal, I have to force the machine to shut down.

It's an oldish laptop (Acer TravelMate 2420 - about 6 years old) but it has been running Ubuntu 10.10 without any hiccups for 6 months. After checking the FAQ, I thought the VGA card might be relevant and after checking in the Terminal I have found out these details about the VGA card:

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

I installed Narwhal from a bootable CD and completely deleted anything on the machine that existed previously. 

Has anyone got any suggestions of how to cope with this? Any suggestions would be much appreciated!

John

---

### Post by shahmish on 2011-04-30
A bit more info about the computer specifications would perhaps help.

---

### Post by beecheese on 2011-04-30
My laptop is an Acer Travelmate 2420 and has an Intel Celeron M chip apparently. From the terminal I have found this out:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

I have no idea what most of that means! Is there any other details I can find out that might help?

I really appreciate any suggestions!

---

### Post by ericthecat on 2011-05-01
Hi,

I think I'm getting the same problem - screen goes to narrow horizontal lines, and the mouse cursor still moves, but is otherwise unresponsive. Ctrl-Alt-F1 still switches virtual terminal, and I can restart from there. My lspci looks almost identical to the original poster's (this is an oldish Sony Vaio laptop).

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:05.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:05.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:08.0 Ethernet controller: Intel Corporation 82562EM/EX/GX - PRO/100 VM (LOM) Ethernet Controller Mobile (rev 03)
06:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


Just before the crash I got the following in dmesg/kern.log:

May  1 13:02:34 florence kernel: [  202.105730] exe (1771): /proc/1771/oom_adj is deprecated, please use /proc/1771/oom_score_adj instead.
May  1 13:02:35 florence kernel: [  203.308038] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May  1 13:02:35 florence kernel: [  203.310081] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 22691 at 22663, next 22692)
May  1 13:02:35 florence kernel: [  203.310481] [drm:i915_reset] *ERROR* Failed to reset chip.
May  1 13:02:34 florence kernel: [  202.105730] exe (1771): /proc/1771/oom_adj is deprecated, please use /proc/1771/oom_score_adj instead.
May  1 13:02:35 florence kernel: [  203.308038] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May  1 13:02:35 florence kernel: [  203.310081] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 22691 at 22663, next 22692)
May  1 13:02:35 florence kernel: [  203.310481] [drm:i915_reset] *ERROR* Failed to reset chip.

Which looks related. Strangely it seems quite stable using firefox, quite crashy using chrome, so perhaps chrome exercises more of the GPU

Anyone any thoughts?

Thanks

Chris

---

### Post by umarth on 2011-05-01
Same problem here. my computer also has 915gm graphics card. this seems to be an driver issue

---

### Post by cccc on 2011-05-22
I get same problems with my Intel 82845G/GL graphic card.
The Gnome Desktop is freezing completely:
```

May 23 02:38:09 ubuntu kernel: [ 1200.304006] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 23 02:38:09 ubuntu kernel: [ 1200.304017] render error detected, EIR: 0x00000000
May 23 02:38:09 ubuntu kernel: [ 1200.304778] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 17900 at 17899)
```

Pls let know if someone find a solution.

---

### Post by bkratz on 2011-05-22
Subscribing to this thread too to see if anything develops. I have the 915GM and have gone back to 10.04 for the same reason.

---

### Post by mgoldenbe on 2011-06-26
Does everyone in this thread also have/had the problem of black screen at boot up? (it seems to be related to the graphics driver as well). Has anyone solved it?

---

### Post by cccc on 2011-06-26
> **mgoldenbe said:**
> Does everyone in this thread also have/had the problem of black screen at boot up? (it seems to be related to the graphics driver as well). Has anyone solved it?


Which graphic card do you have?

You can try these solutions:

[http://ubuntuforums.org/showthread.php?t=1739646](http://ubuntuforums.org/showthread.php?t=1739646)

---

### Post by mgoldenbe on 2011-06-27
Thank you for the very prompt reply. I have Intel 915 (I think there was also a letter after the model number, could be "g", but I am not sure which command to use to show this info) graphics card. I got my computer with Ubuntu 9.10 installed and perfectly working (hence, I do not believe that the solutions from year 2006 that you refer to would be relevant). Once I upgraded to 10.04, I started getting black screen on boot up (after that, the system loaded and worked fine). So, I continued to upgrade to 10.10 and, finally to 11.04. The problem did not go away. With 11.04, the computer started to hang as well, which seems to be correlated with using Chrome (which I did not use with the previous distributions) as reported earlier in this thread.

---

### Post by cccc on 2011-06-27
> **mgoldenbe said:**
> Thank you for the very prompt reply. I have Intel 915 (I think there was also a letter after the model number, could be "g", but I am not sure which command to use to show this info) graphics card. I got my computer with Ubuntu 9.10 installed and perfectly working (hence, I do not believe that the solutions from year 2006 that you refer to would be relevant). Once I upgraded to 10.04, I started getting black screen on boot up (after that, the system loaded and worked fine). So, I continued to upgrade to 10.10 and, finally to 11.04. The problem did not go away. With 11.04, the computer started to hang as well, which seems to be correlated with using Chrome (which I did not use with the previous distributions) as reported earlier in this thread.

BTW this solution is not from 2006, the autor was joined into the forum in 2006.;)
First of all if this happens, pls try to change into Terminal using CTRL-ALT-F1 and pls post:```
**tail -f /var/log/syslog**
```

---

### Post by mgoldenbe on 2011-06-28
1) So, given all this information, which of the solutions (if any) there should I try? Is this particular solution dangerous (can destabilize the system)?

2) OK. When I get the gibberish screen again, I will try to redirect the output of tail into a file. Thanks!

---

### Post by mgoldenbe on 2011-07-26
OK. Now I got this hang even without running chrome. In fact it happened when I issued a "cd" command from the terminal (but that is probably just a coincidence). Here is what seems to be relevant from /var/log/syslog:

Jul 26 10:33:53 meir-OptiPlex-GX280 rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="395" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul 26 10:34:06 meir-OptiPlex-GX280 anacron[692]: Job `cron.daily' terminated
Jul 26 10:34:06 meir-OptiPlex-GX280 anacron[692]: Normal exit (1 job run)
Jul 26 10:54:30 meir-OptiPlex-GX280 kernel: [ 2746.732007] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jul 26 10:54:30 meir-OptiPlex-GX280 kernel: [ 2746.733806] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 349668 at 349665, next 349669)
Jul 26 10:54:30 meir-OptiPlex-GX280 kernel: [ 2746.734105] [drm:i915_reset] *ERROR* Failed to reset chip.
Jul 26 10:55:02 meir-OptiPlex-GX280 kernel: [ 2778.413095] show_signal_msg: 15 callbacks suppressed
Jul 26 10:55:02 meir-OptiPlex-GX280 kernel: [ 2778.413101] compiz[1278]: segfault at 0 ip 010445c6 sp bf8c34d8 error 6 in libc-2.13.so[fcf000+15a000]
Jul 26 10:58:56 meir-OptiPlex-GX280 acpid: client 955[0:0] has disconnected

Thank you!

---

### Post by cccc on 2011-07-26
> **mgoldenbe said:**
> OK. Now I got this hang even without running chrome. In fact it happened when I issued a "cd" command from the terminal (but that is probably just a coincidence). Here is what seems to be relevant from /var/log/syslog:

Jul 26 10:33:53 meir-OptiPlex-GX280 rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="395" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul 26 10:34:06 meir-OptiPlex-GX280 anacron[692]: Job `cron.daily' terminated
Jul 26 10:34:06 meir-OptiPlex-GX280 anacron[692]: Normal exit (1 job run)
Jul 26 10:54:30 meir-OptiPlex-GX280 kernel: [ 2746.732007] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jul 26 10:54:30 meir-OptiPlex-GX280 kernel: [ 2746.733806] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 349668 at 349665, next 349669)
Jul 26 10:54:30 meir-OptiPlex-GX280 kernel: [ 2746.734105] [drm:i915_reset] *ERROR* Failed to reset chip.
Jul 26 10:55:02 meir-OptiPlex-GX280 kernel: [ 2778.413095] show_signal_msg: 15 callbacks suppressed
Jul 26 10:55:02 meir-OptiPlex-GX280 kernel: [ 2778.413101] compiz[1278]: segfault at 0 ip 010445c6 sp bf8c34d8 error 6 in libc-2.13.so[fcf000+15a000]
Jul 26 10:58:56 meir-OptiPlex-GX280 acpid: client 955[0:0] has disconnected

Thank you!


Try these solutions:

[http://ubuntuforums.org/showthread.php?t=1739646](http://ubuntuforums.org/showthread.php?t=1739646)

---

### Post by mgoldenbe on 2011-07-26
This suggestion was offered before I posted my syslog. First, trying these solutions will take me hours and so is not worth avoiding the inconvenience of not using Chrome and rebooting once in a while. Second, some of these solutions may destabilize the system, which I do not want to risk. Shouldn't there be a way to diagnose the problem with better precision to know which solution will work? Thank you!

---

### Post by Steff@ on 2011-07-26
I had the same problem when I tried to install Ubuntu 11.04 on my Toshiba NB205.

I then tried Xubuntu 11.04 and for whatever reason I had no problem installing and running it whatsoever!

---

### Post by rawdmon on 2011-08-07
This sounds like it may be related to KMS (kernel managed video).  Try disabling KMS by issuing the following command:

echo options i915 modeset=0 > /etc/modprobe.d/i915-kms.conf

Reboot after you've issued the command and hopefully that will do the trick.

---

### Post by mgoldenbe on 2011-08-07
Now it says upon start-up that I do not have hardware to run unity and starts the standard interface.

---

### Post by cccc on 2011-08-14
> **mgoldenbe said:**
> Now it says upon start-up that I do not have hardware to run unity and starts the standard interface.

Try Ubuntu Classic Desktop:

[http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/](http://scottlinux.com/2011/03/05/ubuntu-11-04-change-from-unity-to-classic-gnome/)

---

