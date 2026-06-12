---
title: "[SOLVED] No Sound Followed other instructions and nothing"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by dmatthys on 2008-12-04
i have followed several peoples instructions heres the problem i am absolutly new to linux ubuntu gnome everthing not windows so i managed to get my display working properly on my laptop and my desktop and my sound worked perfect on the laptop from the get go however my desktop does not have a built in sound card so i had to buy 1 and i installed it before i switched from windows and it was recognized and worked fine in windows i switched and had sound a couple of times but it has yet to work properly and i have absolutly no sound now so here is what i have seen in other posts people are asking for if any other information is needed please let me know i need help desperatly i dont have a radio for when friends are over its my computer with over 11,000 mp3's and now im without

lspci -v

derek@derek-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation E7230/3000/3010 Memory Controller Hub
	Subsystem: Dell PowerEdge SC440
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation E7230/3000/3010 PCI Express Root Port (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: efe00000-efefffff
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: efd00000-efdfffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: efc00000-efcfffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell PowerEdge SC440
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell PowerEdge SC440
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell PowerEdge SC440
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at ff40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell PowerEdge SC440
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Dell PowerEdge SC440
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: efa00000-efbfffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000e7ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell PowerEdge SC440
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Dell PowerEdge SC440
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at fe00 [size=8]
	I/O ports at fe10 [size=4]
	I/O ports at fe20 [size=8]
	I/O ports at fe30 [size=4]
	I/O ports at fec0 [size=16]
	Memory at effffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Dell PowerEdge SC440
	Flags: medium devsel, IRQ 10
	I/O ports at ece0 [size=32]

04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Dell PowerEdge SC440
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at efcf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

05:02.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at d800 [size=256]
	Capabilities: <access denied>

05:07.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Dell PowerEdge SC440
	Flags: bus master, stepping, medium devsel, latency 64, IRQ 9
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at dc00 [size=256]
	Memory at efaf0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at efa00000 [disabled] [size=128K]
	Capabilities: <access denied>




aplay -l

derek@derek-desktop:~$ aplay -l
aplay: device_list:205: no soundcards found...



i also tried instructions for using oss fromm the link below to no avail please please please help
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

and another that i followed was 

[http://ubuntuforums.org/showthread.php?t=205449&highlight=%2Fdev%2Foss%2Foss_cmpci0%2Fpcm1%3A+Device+OR+resource+busy](http://ubuntuforums.org/showthread.php?t=205449&highlight=%2Fdev%2Foss%2Foss_cmpci0%2Fpcm1%3A+Device+OR+resource+busy)

also with no success if any  further info is needed please just ask and be sure to include any commands i might need to use to get that info as i said completly new been using ubuntu for about two weeks and all i have been doing is making things work properly i almost went back to windows a couple of times but i decided im bettter off learning but finding help is hard so i may end up switching back if i cant get most of what i need running smooth thanks in advance for anyhelp that i hopefully get

---

### Post by abn91c on 2008-12-04
this is the best guide, I used it to install a really old ISA sound card om ny PC with ubuntu 8.10, make sure you do the "saving sound settings" step, it will be the most important one.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by dmatthys on 2008-12-04
I will give it a shot and see what happens and ill let ya know thanx for the tip

---

### Post by dmatthys on 2008-12-04
> **abn91c said:**
> this is the best guide, I used it to install a really old ISA sound card om ny PC with ubuntu 8.10, make sure you do the "saving sound settings" step, it will be the most important one.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

that appears to be the exact same instructions as this thread that i have already tried however i will follow it maby the one i have listed below is missing a step 

[http://ubuntuforums.org/showthread.p...+resource+busy](http://ubuntuforums.org/showthread.p...+resource+busy)

---

### Post by dmatthys on 2008-12-04
> **abn91c said:**
> this is the best guide, I used it to install a really old ISA sound card om ny PC with ubuntu 8.10, make sure you do the "saving sound settings" step, it will be the most important one.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I was able to get to step 4 when i got this error
    derek@derek-desktop:~$ sudo modprobe snd-
    [sudo] password for derek: 
    FATAL: Module snd_ not found.

following the next steps for getting the alsa drivers from a fresh kernel a from a fresh kernel

---

### Post by dmatthys on 2008-12-04
> **abn91c said:**
> this is the best guide, I used it to install a really old ISA sound card om ny PC with ubuntu 8.10, make sure you do the "saving sound settings" step, it will be the most important one.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

aplay: device_list:205: no soundcards found...
 after following getting alsa drivers from a fresh kernel and following alsa drive compilation no errors reported but its still giving me that output and the failure steps to that thread says post a new thread and include any errors that i received and that i was following that thread listed below again any ideas of what to try next

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by dmatthys on 2008-12-04
i think alsa has been black listed thoughout my ventures i had to blacklist somethings any ideas on how to unblacklist it

---

### Post by abn91c on 2008-12-04
> **dmatthys said:**
> I was able to get to step 4 when i got this error
    derek@derek-desktop:~$ sudo modprobe snd-
    [sudo] password for derek: 
    FATAL: Module snd_ not found.

following the next steps for getting the alsa drivers from a fresh kernel a from a fresh kernel
when you typed sudo modeprobe snd-, did you hit the TAB key before enter? that is a critical step then you do sudo modprobe snd-your-soundcard
example mine is sudo modprobe snd-opl3sa2

---

### Post by abn91c on 2008-12-04
> **dmatthys said:**
> i think alsa has been black listed thoughout my ventures i had to blacklist somethings any ideas on how to unblacklist it
go where you edited the file and remove the # before the blacklisted item

---

### Post by abn91c on 2008-12-04
your may be something like sudo modprobe snd-cmi8738

---

### Post by dmatthys on 2008-12-08
sorry took so long for a reply no i did not hit tab after that was probably why it wasnt working however i upgraded to 8.10 and it started working on its own after upgrading thank you for your help though it was much appreciated

---

