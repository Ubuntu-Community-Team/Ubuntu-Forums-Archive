---
title: "ubuntu comes to a Standstill"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by rsiddharth on 2009-07-06
I recently installed ubuntu 9.04 side by side with Windows XP .  When I am working with ubuntu ,sometimes the Screen comes to a standstill and nothing works except my Mouse pointer , I also tried waiting for 1/2 hour hoping that it could recover but every time this happens I am finally forced to press the Power button for 5 -10 secs to switch off the PC and again restart .  It intuitively strikes me that the method I use to recover the system is not right , since  there may be a probability to lose data if I switch it off abruptly .  

Can any one help me in preventing this phenomenon ( as is described above ) and what I need to do if my computer comes to a standstill.

Thank you for your help.

---

### Post by nhasian on 2009-07-07
if your computer is freezing it may be either hardware or software related.  if both windows xp and ubuntu are freezing then we can begin looking at a hardware related problem.  if however only ubuntu freezes, then it may be your video driver or wifi driver causing the problem.

you can restart the ubuntu desktop with Control-Alt-Backspace but you have to enable this feature first:

[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

if that doesnt work you can use the magic sysreq keys:

[http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

---

### Post by rsiddharth on 2009-07-07
> **nhasian said:**
> if your computer is freezing it may be either hardware or software related.  if both windows xp and ubuntu are freezing then we can begin looking at a hardware related problem.  if however only ubuntu freezes, then it may be your video driver or wifi driver causing the problem.

you can restart the ubuntu desktop with Control-Alt-Backspace but you have to enable this feature first:

[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

if that doesnt work you can use the magic sysreq keys:

[http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/)

Thank you nhasian , I had installed the dontzap package and have disabled it in terminal and noted down peddicord's REISUB technique . 

My Windows Xp doesn't crash at all . I have choose " Normal " in the Visual effects tab in Appearance Preferences window . Do I have to choose " None " so as to stop this crashing  phenomenon ? .

---

### Post by mikechant on 2009-07-07
> I have choose " Normal " in the Visual effects tab in Appearance Preferences window . Do I have to choose " None " so as to stop this crashing phenomenon ? .

It's well worth trying this. If it solves the crashes, you can either manage without the visual effects, or see if you can get a more up to date video driver.

---

### Post by rsiddharth on 2009-07-07
> **mikechant said:**
> It's well worth trying this. If it solves the crashes, you can either manage without the visual effects, or see if you can get a more up to date video driver.

Do you really think its a video driver issue.

---

### Post by Yvan300 on 2009-07-07
Well jaunty uses a new video rendering engine and also ATI has stopped producing drivers for many cards. Mine was one of them and thus i was unable to use jaunty due to graphics problems. You should try intrepid Ibex, most likely there is a proper graphics driver for your card.

---

### Post by scrooge_74 on 2009-07-07
One more reason I use no visual effects, they are pretty and all, but they wont do any work for me. :D

---

### Post by rsiddharth on 2009-07-08
> **Yvan300 said:**
> Well jaunty uses a new video rendering engine and also ATI has stopped producing drivers for many cards. Mine was one of them and thus i was unable to use jaunty due to graphics problems. You should try intrepid Ibex, most likely there is a proper graphics driver for your card.
Is there a  video card at all which uses an Open source driver.

---

### Post by random turnip on 2009-07-08
90% of nVidia (probably the most common make) seem to be supported with ease.
Make sure you system is fully up to date by going:
System --> Administration --> Update manager

Also, what are your specs on the PC?
If it's old then it may be struggling to run Ubuntu, then you should try Xubuntu which is just a lighter version of Ubuntu.

---

### Post by change_mode on 2009-07-08
Take a look at the log files. I had the same system freezes because of PulseAudio. Disabling it (setting all sound options to ALSA) fixed it for me.

---

### Post by rsiddharth on 2009-07-08
> **mikechant said:**
> It's well worth trying this. If it solves the crashes, you can either manage without the visual effects, or see if you can get a more up to date video driver.


I completely switched off the visual effects and ran the system today and just few minutes a ago my system " came to a stanstill " again .  I used the magic key which  [ Jacob Peddicord]("http://fosswire.com/users/jacob/") described in [Fosswire]("http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/")  -- > Alt+printscr +REISUB  and the computer restarted instantly .     

I should thank nhasian , who was the one who linked me to Fosswire .

---

### Post by rsiddharth on 2009-07-08
> **random turnip said:**
> 90% of nVidia (probably the most common make) seem to be supported with ease.
Make sure you system is fully up to date by going:
System --> Administration --> Update manager

Also, what are your specs on the PC?
If it's old then it may be struggling to run Ubuntu, then you should try Xubuntu which is just a lighter version of Ubuntu.


Here are my System Specs :
 Intel Pentium 4 processor 512K 3.06 GHz , 1 MB L2 Cache 
I GB DDR RAM  400Mhz 
Integrated Intel GMA 900 Graphics 
CD-RW/DVD Combo Drive.

Is this configuration okay for ubuntu or should I upgrade . If I have to upgrade what are the components that should be upgraded ?

---

### Post by rsiddharth on 2009-07-08
> **change_mode said:**
> Take a look at the log files. I had the same system freezes because of PulseAudio. Disabling it (setting all sound options to ALSA) fixed it for me.

I am new to ubunu/Linux so is it possible for you to be more clear - What is Pulse Audio and ALSA ? and where should I look for the log files ? .

thank your help . :p

---

### Post by rsiddharth on 2009-07-08
As I was replying to all who have answered me , my system again "came to a Stanstill " . I did the REISUB magic and it restarted the system . 

Can anyone give me a concrete answer for it seems a mystery to me - this issue :-?

---

### Post by change_mode on 2009-07-08
You can access the log files via System -> Administration -> Log File Viewer. Just look for error messages at the time of the crash.

PulseAudio is the default sound system Ubuntu uses and it's quite famous for causing trouble. ALSA is an older sound driver you can use instead (Preferences -> Sound).

---

### Post by katzky on 2009-07-08
:guitar:&#9829;[SIZE=4]&#9829;[SIZE=5]&#9829;[/SIZE][/SIZE]`Ubuntu rocks![SIZE=5]&#9829;[SIZE=4]&#9829;[/SIZE][/SIZE]&#9829;):P


[RIGHT][[COLOR=#ffffff]_surendettement_[/COLOR]]("http://commissiondesurendettement.net")[/RIGHT]

---

### Post by scrooge_74 on 2009-07-08
> **rsiddharth said:**
> As I was replying to all who have answered me , my system again "came to a Stanstill " . I did the REISUB magic and it restarted the system . 

Can anyone give me a concrete answer for it seems a mystery to me - this issue :-?

From what I beeing seeing (and I will test that at some point today or tomorrow to help a friend). You should probably use the backports and downgrade your video drivers to previous version of Ubuntu.

---

### Post by rsiddharth on 2009-07-09
> **change_mode said:**
> You can access the log files via System -> Administration -> Log File Viewer. Just look for error messages at the time of the crash.

PulseAudio is the default sound system Ubuntu uses and it's quite famous for causing trouble. ALSA is an older sound driver you can use instead (Preferences -> Sound).
Thank you for your guidance change_mode . 

I opened  the log file viewer and wouldn't figure out what is what . I have attached an archive inside which is a .pdf file and has the log from 8:42 AM to 10:33 AM ( 9 July 2009)  , these messages in the file was under 'messages' heading in the Log file viewer . It will be great if you take pains to look into it . Between 8:42AM and 10:33AM , I had the system crash again and had to use REISUB keys to recover it , I was playing music while this crash happened . 

In the Archive attached is another file , which is a screen shot of the Sound Preferences dialog box , I request you to please view it and suggest what are the options which has to be changed . 

Thank you !

---

### Post by scrooge_74 on 2009-07-09
While the ability to reboot the Xserver is important, freezes and crashes are a no no on a production machine.

I tried my best but the damn ATI card was a pain. I have converted that laptop to Hardy, it has being on for the last 10 hours downloading updates and apps. I even have the desktops effects on and no freezes up to this point

---

### Post by change_mode on 2009-07-09
> **rsiddharth said:**
> 
In the Archive attached is another file , which is a screen shot of the Sound Preferences dialog box , I request you to please view it and suggest what are the options which has to be changed . 

Thank you !

I'm no expert with analyzing log files, but this should be the important part:

```
Jul 9 08:53:17 innov kernel: [ 118.268940] PM: Syncing filesystems ... done.
Jul 9 08:53:17 innov kernel: [ 118.273823] Freezing user space processes ... (elapsed 0.00 seconds)
done.
Jul 9 08:53:17 innov kernel: [ 118.274388] Freezing remaining freezable tasks ... (elapsed 0.00
seconds) done.
Jul 9 08:53:17 innov kernel: [ 118.274447] Suspending console(s) (use no_console_suspend to debug)
Jul 9 08:53:17 innov kernel: [ 118.275066] pci 0000:00:02.0: PCI INT A disabled
Jul 9 08:53:17 innov kernel: [ 119.028097] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Jul 9 08:53:17 innov kernel: [ 119.028240] sd 2:0:0:0: [sda] Stopping disk
Jul 9 08:53:17 innov kernel: [ 119.029023] parport_pc 00:06: disabled
Jul 9 08:53:17 innov kernel: [ 119.048130] ata_piix 0000:00:1f.2: PCI INT B disabled
Jul 9 08:53:17 innov kernel: [ 119.064109] ata_piix 0000:00:1f.1: PCI INT A disabled
Jul 9 08:53:17 innov kernel: [ 119.064209] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Jul 9 08:53:17 innov kernel: [ 119.080038] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Jul 9 08:53:17 innov kernel: [ 119.080067] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Jul 9 08:53:17 innov kernel: [ 119.080094] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Jul 9 08:53:17 innov kernel: [ 119.080122] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Jul 9 08:53:17 innov kernel: [ 119.096029] HDA Intel 0000:00:1b.0: PCI INT A disabled
Jul 9 08:53:17 innov kernel: [ 119.112065] PM: suspend devices took 0.840 seconds
Jul 9 08:53:17 innov kernel: [ 119.112231] ACPI: Preparing to enter system sleep state S3
Jul 9 08:53:17 innov kernel: [ 119.112803] Disabling non-boot CPUs ...
Jul 9 08:53:17 innov kernel: [ 119.112803] ACPI: Waking up from system sleep state S3
Jul 9 08:53:17 innov kernel: [ 119.132075] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -
> IRQ 16
Jul 9 08:53:17 innov kernel: [ 119.220199] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -
> IRQ 23
Jul 9 08:53:17 innov kernel: [ 119.220252] usb usb2: root hub lost power or was reset
Jul 9 08:53:17 innov kernel: [ 119.220275] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -
> IRQ 19
Jul 9 08:53:17 innov kernel: [ 119.220323] usb usb3: root hub lost power or was reset
Jul 9 08:53:17 innov kernel: [ 119.220343] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -
> IRQ 18
Jul 9 08:53:17 innov kernel: [ 119.220395] usb usb4: root hub lost power or was reset
Jul 9 08:53:17 innov kernel: [ 119.220414] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -
> IRQ 16
Jul 9 08:53:17 innov kernel: [ 119.220465] usb usb5: root hub lost power or was reset
Jul 9 08:53:17 innov kernel: [ 119.236012] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -
> IRQ 23
Jul 9 08:53:17 innov kernel: [ 119.236146] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -
> IRQ 18
Jul 9 08:53:17 innov kernel: [ 119.252040] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -
> IRQ 19
Jul 9 08:53:17 innov kernel: [ 119.320642] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20] MMIO=
[cffff800-cfffffff] Max Packet=[2048] IR/IT contexts=[4/8]
Jul 9 08:53:17 innov kernel: [ 119.329829] parport_pc 00:06: activated
Jul 9 08:53:17 innov kernel: [ 119.329893] sd 2:0:0:0: [sda] Starting disk
Jul 9 08:53:17 innov kernel: [ 123.360238] ata3.00: configured for UDMA/100
Jul 9 08:53:17 innov kernel: [ 123.372507] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors:
(80.0 GB/74.5 GiB)
Jul 9 08:53:17 innov kernel: [ 123.372530] sd 2:0:0:0: [sda] Write Protect is off
Jul 9 08:53:17 innov kernel: [ 123.372563] sd 2:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
Jul 9 08:53:17 innov kernel: [ 123.800013] usb 5-1: reset full speed USB device using uhci_hcd and
address 2
Jul 9 08:53:17 innov kernel: [ 123.972029] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ
16
Jul 9 08:53:17 innov kernel: [ 123.973357] PM: resume devices took 4.860 seconds
Jul 9 08:53:17 innov kernel: [ 123.973374] Restarting tasks ... done.
Jul 9 08:53:18 innov kernel: [ 124.098394] synaptics was reset on resume, see synaptics_resume_reset
if you have trouble on resume
Jul 9 08:53:18 innov kernel: [ 124.432017] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:53:24 innov kernel: [ 130.855280] eth0: link down
Jul 9 08:53:26 innov kernel: [ 132.505518] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 9 08:53:28 innov kernel: [ 134.464016] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:53:38 innov kernel: [ 144.476016] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:53:49 innov kernel: [ 155.916140] ata1.00: qc timeout (cmd 0xa1)
Jul 9 08:53:49 innov kernel: [ 155.916149] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
File: /home/siddharth/Desktop/logfile_messages_July 09_2009                              Page 10 of 18
Jul 9 08:53:54 innov kernel: [ 160.956015] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:53:59 innov kernel: [ 165.940016] ata1: device not ready (errno=-16), forcing hardreset
Jul 9 08:54:05 innov kernel: [ 171.136015] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:54:15 innov kernel: [ 181.196164] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:54:25 innov kernel: [ 191.924033] ata1.00: qc timeout (cmd 0xa1)
Jul 9 08:54:25 innov kernel: [ 191.924042] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jul 9 08:54:30 innov kernel: [ 196.980024] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:54:35 innov kernel: [ 201.964016] ata1: device not ready (errno=-16), forcing hardreset
Jul 9 08:54:41 innov kernel: [ 207.164017] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:54:59 innov kernel: [ 225.907530] eth0: link down
Jul 9 08:55:16 innov kernel: [ 242.932134] ata1.00: qc timeout (cmd 0xa1)
Jul 9 08:55:16 innov kernel: [ 242.932144] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Jul 9 08:55:16 innov kernel: [ 242.932151] ata1.00: disabled
Jul 9 08:55:17 innov kernel: [ 243.940019] ata1: soft resetting link
Jul 9 08:55:23 innov kernel: [ 249.136015] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:55:27 innov kernel: [ 253.952033] ata1: soft resetting link
Jul 9 08:55:33 innov kernel: [ 259.148015] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:55:37 innov kernel: [ 263.964029] ata1: soft resetting link
Jul 9 08:55:43 innov kernel: [ 269.160016] ata1: link is slow to respond, please be patient (ready=0)
Jul 9 08:55:48 innov kernel: [ 274.984077] ata1: EH complete
Jul 9 09:00:04 innov kernel: [ 530.648125] ACPI Error (psargs-0358): [\_TZ_.THRM] Namespace lookup
failure, AE_NOT_FOUND
Jul 9 09:00:04 innov kernel: [ 530.648134] ACPI Error (psparse-0524): Method parse/execution failed
[\_GPE._L1C] (Node f6c1f468), AE_NOT_FOUND
Jul 9 09:00:04 innov kernel: [ 530.648166] ACPI Exception (evgpe-0571): AE_NOT_FOUND, while
evaluating GPE method [_L1C] [20080926]
Jul 9 09:06:54 innov kernel: [ 940.398548] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 9 09:07:09 innov kernel: [ 955.033413] eth0: link down
Jul 9 09:07:10 innov kernel: [ 956.704281] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 9 09:31:26 innov -- MARK --
Jul 9 09:51:26 innov -- MARK --
Jul 9 10:07:06 innov kernel: [ 4552.318298] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 9 10:13:50 innov kernel: [ 4957.143400] SysRq : Keyboard mode set to system default
Jul 9 10:13:51 innov exiting on signal 15
Jul 9 10:14:23 innov syslogd 1.5.0#5ubuntu3: restart.

```

I don't see anything audio related, but it says that the PC was suspended and bringing it back obviously caused some error with the hard disk (ata1). Suspend and hibernation can be buggy, it's not unusual. Were you aware that the system was going into suspend mode?

> In the Archive attached is another file , which is a screen shot of the Sound Preferences dialog box , I request you to please view it and suggest what are the options which has to be changed .

Like I said I don't see anything related to pulseaudio errors in that log, but if you still wanna give it a try, you can change the first 3 options to ALSA (same as sound capture). After viewing the log, I don't think sound is the problem though.

Assuming you weren't aware that the PC went into suspend mode, you should try to find out what caused it to do that.


edit: I just discovered the second crash and there's an ACPI error too:

```
Jul 9 10:32:26 innov kernel: [ 1094.652342] ACPI Error (psargs-0358): [\_TZ_.THRM] Namespace lookup
failure, AE_NOT_FOUND
Jul 9 10:32:26 innov kernel: [ 1094.652353] ACPI Error (psparse-0524): Method parse/execution failed
[\_GPE._L1C] (Node f6c1f468), AE_NOT_FOUND
Jul 9 10:32:26 innov kernel: [ 1094.652383] ACPI Exception (evgpe-0571): AE_NOT_FOUND, while
evaluating GPE method [_L1C] [20080926]
Jul 9 10:32:57 innov syslogd 1.5.0#5ubuntu3: restart.

```

I can't say much about it, maybe someone else can. Looks like this error actually causes the crash.

---

### Post by rsiddharth on 2009-07-10
> don't see anything audio related, but it says that the PC was suspended and bringing it back obviously caused some error with the hard disk (ata1). Suspend and hibernation can be buggy, it's not unusual. Were you aware that the system was going into suspend mode?

No , I was indeed not aware about my System going to suspend mode ! . Its an habit that I put my system on suspend mode often when I am exhausted and need to take a break from the computer , Will reducing the times that I suspend my system solve the issue . 

Does 'Sleep '  mean ' Suspend ' ? . 

> edit: I just discovered the second crash and there's an ACPI error too:
 
  	Code:
 	Jul 9 10:32:26 innov kernel: [ 1094.652342] ACPI Error (psargs-0358): [\_TZ_.THRM] Namespace lookup
failure, AE_NOT_FOUND
Jul 9 10:32:26 innov kernel: [ 1094.652353] ACPI Error (psparse-0524): Method parse/execution failed
[\_GPE._L1C] (Node f6c1f468), AE_NOT_FOUND
Jul 9 10:32:26 innov kernel: [ 1094.652383] ACPI Exception (evgpe-0571): AE_NOT_FOUND, while
evaluating GPE method [_L1C] [20080926]
Jul 9 10:32:57 innov syslogd 1.5.0#5ubuntu3: restart. 
 I can't say much about it, maybe someone else can. Looks like this error actually causes the crash.



I  read a page about ACPI in Wikipedia and vaguely understood that its a some kind of standard which does some kind of power management irrespective of the hardware used and something like that . 

Thank you change_mode for your help and I am very grateful . 

What should be done next ? .Where should I go to get the ACPI issue  (as you found out ) resolved.
If my system crashes again ,  I will note down the exact time which will be helpful in pointing out the real issue ! .

---

### Post by change_mode on 2009-07-10
Yes, I think 'sleep' in windows is the same as 'suspend' in Ubuntu. It seems the suspend causes some hard drive error, but it's not what caused the crash so it should be fine. If you run into any problems after suspending the PC, you know where to look.

I don't really know enough about ACPI to be of any help. You can try to google the error message and find something there, or make a new topic in the General Help forum (ACPI issues have nothing to do with 'absolute beginner talk') and hope that people there know what to do.

---

### Post by scrooge_74 on 2009-07-10
Suspend mode has always being an issue for laptops, you may have to search for specific solutions for your particular brand and model

---

### Post by rsiddharth on 2009-07-10
> From what I beeing seeing (and I will test that at some point today or tomorrow to help a friend). You should probably use the backports and downgrade your video drivers to previous version of Ubuntu.

I seem to have resolution problems with the previous  versions of ubuntu , in v8.10 I was not able to go beyond a resolution of  600x800  , fortunately only 9.04 seem to work for me with regard to Resolution .

change_mode tells that it should be a ACPI problem - which has to do with power management I suppose .

---

### Post by rsiddharth on 2009-07-10
> **change_mode said:**
> Yes, I think 'sleep' in windows is the same as 'suspend' in Ubuntu. It seems the suspend causes some hard drive error, but it's not what caused the crash so it should be fine. If you run into any problems after suspending the PC, you know where to look.

I don't really know enough about ACPI to be of any help. You can try to google the error message and find something there, or make a new topic in the General Help forum (ACPI issues have nothing to do with 'absolute beginner talk') and hope that people there know what to do.
Thank you change_mode , I will start a thread in General Help section regarding the ACPI problem of mine.

---

