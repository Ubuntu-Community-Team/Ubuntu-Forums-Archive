---
title: "Continued sound issues in Jaunty"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by cguwilliams on 2009-09-12
Hi all,

I'd first off like the thank those who have helped me with my sound issues so far. I thought I'd start a new post, as my current sound problems are pretty different than the ones I [previously]("http://ubuntuforums.org/showthread.php?t=1263445") had encountered before.

When I run sound, either through Rythmbox or through a website (I've tried Pandora and YouTube), I get an indication that there is sound in my Volume Control (the meter moves up and down to the unheard rhythm of the unheard music). So, something is not working between my computer and my speakers. I am sure the speakers work, because they work on my Mac laptop, and because they worked when I was briefly running Fedora 11. Here is a comprehensive look at my system's information (at least, as much as I know how to gather). I am using Pulseaudio, and have gone through [this tutorial]("http://ubuntuforums.org/showthread.php?t=1130384") to get to where I am now.

:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
-------------------------------

:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe7f8000 irq 2297
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe8ec000 irq 2297
-------------------------------

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
-------------------------------

:~$ pulseaudio -vvv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is df48647235a35018e08eca404aaa7857.
I: main.c: Using runtime directory /home/patrick/.pulse/df48647235a35018e08eca404aaa7857:runtime.
I: main.c: Using state directory /home/patrick/.pulse.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
-------------------------------

Thank you for any help that you may be able to provide.

-Patrick

---

### Post by Wataru8675 on 2009-09-12
So I'll see if I can give you one of those uneducated, stupid-enough-to-work suggestions, since I don't understand any of the lingo in that huge long list. xD

Have you tried anything with JACK Audio?  I don't know what the program does or why it's needed...but it's required for some programs (the reason I have it is Musescore) to be able to produce sound to the speakers (external or not).

---

### Post by cguwilliams on 2009-09-12
I just solved the problem. I can say, after this past week of troubleshooting, few things in my long use of computers (going back to the AppleIIe) has made me more satisfied than hearing the Ubuntu startup sound.

The solution was to add the line:

options snd-hda-intel probe_mask=1 model=6stack-dell

to:

/etc/modprobe.d/alsa-base.conf
-------------------------------

And the worst thing of all is that I found the solution on the Dell Linux forums :confused: haha.

So anyway, if anyone else has a Dell Studio Desktop 540, that is the solution.

How do you add [solved] to a thread?

---

