---
title: "Realtek rtl8723bs sdio adapter"
date: 2014-10-25
forum: Networking &amp; Wireless
---

### Post by stridast76 on 2014-10-25
Ok, I'm expecting a reply along the lines of "um have fun, and good luck, you'll need it"

I've installed ubuntu 14.04.1 on my Pipo W2.  It's a windows 8.1 bay trail tablet, the wifi chip in it is a realtek 8723bs wifi/bt chip.  This is not supported of course by ubuntu. so no wifi right now.  Ubuntu boots with no problem, and I've got grub2 configured now for the stupid 32 bit uefi setup.  I've found the following info to build a driver for the wifi:   [https://github.com/hadess/rtl8723as](https://github.com/hadess/rtl8723as)

This is from someone who's doing similar work on a different bay trail tablet with the same wifi chip.  

Other problems with this tablet that might be relevant to answers:  It boots 14.04 ubuntu just fine. but wont boot 14.10 at all. the screen goes weird even with video=VGA-1:800x1280e reboot=pci,force in the command line, and no quiet or splash.  Hard to troubleshoot what's going on with 14.10 when I cant even read any text to post,  so I'm stuck working with the older kernel in 14.04 

The problem is, while I've been using lubuntu for a couple years, I don't know anything about how to turn this into a working wifi driver to get it working.  More to the point, I don't know enough to really be sure of what questions to ask, which really makes it harder to just google the information and research it.  I am not looking for someone to spoon feed me step by step instructions,  just for someone to point me in the right direction, so I can try to work this out.  Even if it takes a couple months of reading and experimenting to get it to work, I want to get this working and learn as much as I can in the process. Anyone help me with what I should be looking up?

---

### Post by chili555 on 2014-10-25
Ohhh, sorry! I can't give you the answer you expect.

The process is usually something like this, with a temporary working internet connection:```
sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/hadess/rtl8723as.git
cd rtl8723as
make
sudo make install
sudo depmod -a
sudo modprobe 8723bs
```It 'makes' with one warning but no errors on my 14.10 system. It doesn't call for firmware, so, assuming your device is covered, it ought to spring to life.

I await your report of success.

---

### Post by stridast76 on 2014-10-26
ok, thank you thank you. everything went fine, until the end, when i just get the following:

stridast@stridast-Vega-8008W:~/rtl8723as$ sudo make install
make -C /lib/modules/3.13.0-37-generic/build SUBDIRS=/home/stridast/rtl8723as modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-37-generic'
  INSTALL /home/stridast/rtl8723as/8723bs.ko
Can't read private key
  DEPMOD  3.13.0-37-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-37-generic'
stridast@stridast-Vega-8008W:~/rtl8723as$ sudo modprobe 8723bs
modprobe: FATAL: Module 8723bs not found.

---

### Post by chili555 on 2014-10-26
Please try:```
cd ~/rtl8723as
sudo depmod -a
sudo modprobe 8723bs
```It worked for me.

Does it drive your device?

---

### Post by stridast76 on 2014-10-26
well, it worked, at least in the fact that it didn't have the error that showed up last time.  however, no luck with wifi working =/

---

### Post by chili555 on 2014-10-26
I'll amend my instructions above for the benefit of the searchers.

Let's see some diagnostics:```
dmesg | grep -e 8723 -e RTL
lspci -nn | grep 0280
```What is your reference that suggests this is the correct driver so I may study the prior art?

---

### Post by stridast76 on 2014-10-26
references that it's the right chip is, with my windows installation the wifi/bluetooth shows up as realtek rtl8723bs sdio  (sorry no screenshot handy atm)

googling info on the realtek  rtl8723bs I found multiple references to the Onda v975w windows tablet, and threads asking for help regarding it's wifi.

[http://thread.gmane.org/gmane.linux.kernel.wireless.general/127706/focus=127896](http://thread.gmane.org/gmane.linux.kernel.wireless.general/127706/focus=127896)

and the website the person who is working on porting linux to the onda v975w is here
[https://wiki.gnome.org/BastienNocera/Ondav975w](https://wiki.gnome.org/BastienNocera/Ondav975w)

(the link I posted earlier to the driver is from his website)

---

### Post by chili555 on 2014-10-26
How about the diagnostics I requested?

If you are having trouble finding the pipe symbol | just post the wireless part of:```
lspci -nn
``` And also the parts of:```
tail -n20 /var/log/dmesg
```...that relate to RTL or 8723. Thanks.

---

### Post by stridast76 on 2014-10-26
Sorry, I had to get home to run the diagnostics.  here's the end of the dnesg.  not sure where to look to post lspci though

tail -n20 /var/log/dmesg
[   71.913518] NET: Registered protocol family 31
[   71.913524] Bluetooth: HCI device and connection manager initialized
[   71.913537] Bluetooth: HCI socket layer initialized
[   71.913544] Bluetooth: L2CAP socket layer initialized
[   71.913556] Bluetooth: SCO socket layer initialized
[   71.927969] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   71.927977] Bluetooth: BNEP filters: protocol multicast
[   71.927992] Bluetooth: BNEP socket layer initialized
[   71.947071] Bluetooth: RFCOMM TTY layer initialized
[   71.947090] Bluetooth: RFCOMM socket layer initialized
[   71.947106] Bluetooth: RFCOMM ver 1.11
[   72.024742] type=1400 audit(1414358187.700:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=683 comm="apparmor_parser"
[   72.024761] type=1400 audit(1414358187.700:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=683 comm="apparmor_parser"
[   72.026128] type=1400 audit(1414358187.704:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=683 comm="apparmor_parser"
[   72.142804] type=1400 audit(1414358187.820:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=738 comm="apparmor_parser"
[   72.142824] type=1400 audit(1414358187.820:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=738 comm="apparmor_parser"
[   72.142836] type=1400 audit(1414358187.820:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=738 comm="apparmor_parser"
[   72.143902] type=1400 audit(1414358187.820:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=738 comm="apparmor_parser"
[   72.143918] type=1400 audit(1414358187.820:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=738 comm="apparmor_parser"
[   72.221772] cfg80211: Calling CRDA to update world regulatory domain


00:00.0 Host bridge [0600]: Intel Corporation ValleyView SSA-CUnit [8086:0f00] (rev 0d)
    Subsystem: Intel Corporation Device [8086:0f31]
    Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller [0300]: Intel Corporation ValleyView Gen7 [8086:0f31] (rev 0d) (prog-if 00 [VGA controller])
    Subsystem: Intel Corporation ValleyView Gen7 [8086:0f31]
    Flags: bus master, fast devsel, latency 0, IRQ 104
    Memory at 88000000 (32-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 1000 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:14.0 USB controller [0c03]: Intel Corporation ValleyView USB xHCI Host Controller [8086:0f35] (rev 0d) (prog-if 30 [XHCI])
    Subsystem: Intel Corporation ValleyView USB xHCI Host Controller [8086:0f35]
    Flags: bus master, medium devsel, latency 0, IRQ 103
    Memory at 88800000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:1a.0 Encryption controller [1080]: Intel Corporation ValleyView SEC [8086:0f18] (rev 0d)
    Subsystem: Intel Corporation ValleyView SEC [8086:0f18]
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at 88700000 (32-bit, non-prefetchable) [size=1M]
    Memory at 88600000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation ValleyView Power Control Unit [8086:0f1c] (rev 0d)
    Subsystem: Intel Corporation ValleyView Power Control Unit [8086:0f1c]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

---

### Post by chili555 on 2014-10-26
I see nothing remotely helpful there. Let's look at:```
lsusb
sudo lshw -C network
```Your dmesg looks like the bluetooth is working!

---

### Post by stridast76 on 2014-10-26
using lspci -nnv worked to bring it up.  I dont see it listed at all.

00:00.0 Host bridge [0600]: Intel Corporation ValleyView SSA-CUnit [8086:0f00] (rev 0d)
    Subsystem: Intel Corporation Device [8086:0f31]
    Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller [0300]: Intel Corporation ValleyView Gen7 [8086:0f31] (rev 0d) (prog-if 00 [VGA controller])
    Subsystem: Intel Corporation ValleyView Gen7 [8086:0f31]
    Flags: bus master, fast devsel, latency 0, IRQ 104
    Memory at 88000000 (32-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 1000 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:14.0 USB controller [0c03]: Intel Corporation ValleyView USB xHCI Host Controller [8086:0f35] (rev 0d) (prog-if 30 [XHCI])
    Subsystem: Intel Corporation ValleyView USB xHCI Host Controller [8086:0f35]
    Flags: bus master, medium devsel, latency 0, IRQ 103
    Memory at 88800000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:1a.0 Encryption controller [1080]: Intel Corporation ValleyView SEC [8086:0f18] (rev 0d)
    Subsystem: Intel Corporation ValleyView SEC [8086:0f18]
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at 88700000 (32-bit, non-prefetchable) [size=1M]
    Memory at 88600000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation ValleyView Power Control Unit [8086:0f1c] (rev 0d)
    Subsystem: Intel Corporation ValleyView Power Control Unit [8086:0f1c]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

---

### Post by stridast76 on 2014-10-26
lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 046e:5542 Behavior Tech. Computer Corp. 
Bus 001 Device 004: ID 050d:845a Belkin Components F7D2101 802.11n Surf & Share Wireless Adapter v1000 [Realtek RTL8192SU]
Bus 001 Device 003: ID 1d57:0005 Xenta Wireless Receiver (Keyboard and Mouse)
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2.3
       logical name: wlan0
       serial: b4:75:0e:24:ea:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.0.102 multicast=yes wireless=IEEE 802.11bg
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2.3
       logical name: wlan0
       serial: b4:75:0e:24:ea:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.0.102 multicast=yes wireless=IEEE 802.11bg

EDIT: looks like only the USB wireless adapter that I am using temporarily is showing up

---

### Post by chili555 on 2014-10-26
I see nothing useful. I suggest you email this guy and ask him about it: [https://wiki.gnome.org/BastienNocera/Ondav975w](https://wiki.gnome.org/BastienNocera/Ondav975w)

I notice he says it's working with:> Using Adam Williamson's 3.16.0-0.rc5.git0.1.1awb fedlet kernel.Perhaps you need to find and install it and use it instead of the Ubuntu generic kernel.

---

### Post by stridast76 on 2014-10-26
will do.  seriously thanks for the help so far!

---

### Post by chili555 on 2014-10-26
> **stridast76 said:**
> will do.  seriously thanks for the help so far!C'mon back when you have some additional information and you'd like to continue. I love coaxing new devices to life!

---

### Post by stridast76 on 2014-10-27
[COLOR=#500050][FONT=arial]I got a reply: potentially useful


>> Hello there, I was wondering if you would mind sharing how you got
>> your onda to show up the realtek 8723bs wifi chip.
>
[/FONT][/COLOR][FONT=arial]>I looked inside the decompiled DSDT. See my incorrect guesses on the[/FONT]
[FONT=arial]>"Realtek GPIO chipset, for Baytrail?" thread:[/FONT]
>[http://www.spinics.net/lists/linux-wireless/thrd3.html](http://www.spinics.net/lists/linux-wireless/thrd3.html)
[COLOR=#500050][FONT=arial]>
>>   I'm working on trying to get ubuntu working well on a Pipo W2
>> windows tablet,  The two tablets share the same wifi/bluetooth chip
>> (realtek rtl8723bs)   I've installed the driver you put up on github,
>> but I cant seem to get ubuntu to recognize the realtek chip in the
>> first place.  It doesnt show up anywhere that I can find.  Any tips
>> you could share?
>
[/FONT][/COLOR][FONT=arial]>It's actually SDIO, so should show up somewhere[/FONT]
[FONT=arial]>in /sys/bus/sdio/devices/. If it doesn't, it probably means that it's[/FONT]
[FONT=arial]>either not this device, or there's a bug enumerating the SDIO bus.

however sys/bus/sdio/devices/ is empty. which gives a direction to go with.  I can experiment more tonight when I get home from work.  [/FONT]

---

### Post by stridast76 on 2014-10-27
Ok, I think my problem at this point is the same bug people came across here [https://bugzilla.kernel.org/show_bug.cgi?id=67921](https://bugzilla.kernel.org/show_bug.cgi?id=67921)

sadly, reading though, the solution they came up with seems to be using a newer kernel.  which might, or might not, prevent me from booting since this tablet doesnt like the newer kernel, at least it wont boot on the kernel in 14.10 release.  (I did get ubuntu mate beta 2 to boot once and that was running [COLOR=#333333][FONT=Helvetica Neue]Kernel 3.16.2

[/FONT][/COLOR]"with a 3.16 rc2 kernel, even without any version of Doug's patch, the SDIO device enumerates:"

I assume this is the same as 3.16.2

How would I go about trying to install kernel 3.16.2?  Worth a shot.  if it breaks my installation, then I have to reinstall.  I'll live.

---

### Post by Hadaka on 2014-10-28
[http://ubuntuforums.org/showthread.php?t=2190930](http://ubuntuforums.org/showthread.php?t=2190930)
post #4

---

### Post by chili555 on 2014-10-28
> **Hadaka said:**
> [http://ubuntuforums.org/showthread.php?t=2190930](http://ubuntuforums.org/showthread.php?t=2190930)
post #4I don't think this is the best solution. He is already running a 3.13-xx kernel.

Typically, you can download the linux-image and -headers and install the .deb files. The install process rewrites GRUB so that upon reboot, you boot into the latest kernel. By the same token, if there is a glitch, you can interrupt the boot process at the GRUB menu and select the earlier, glitch-free kernel. If all else fails, once booted into the earlier kernel, you can uninstall the later kernel. Ideally, no harm, no foul.

In an ordinary desktop or laptop running an x86 or x86_64 processor, we'd go here and get all the 3.16.2 (or even newer) pieces: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.2-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.2-utopic/)

I assume your tablet runs what is quoted here: [http://www.pompmall.com/pipo-w2-windows-8-1-intel-quad-core-tablet-pc-2gb-32gb-8-inch.html](http://www.pompmall.com/pipo-w2-windows-8-1-intel-quad-core-tablet-pc-2gb-32gb-8-inch.html)> Intel Quad-core 1.8GHz processorYou can probably verify with:```
cat /proc/cpuinfo
```The next step is to verify that you have a 32-bit install:```
arch
```Is your kernel low-latency?```
uname -a
```If so, I'd go ahead and download the i386 image and headers as appropriate and install them:```
cd Desktop  [COLOR="#FF0000"]<--or wherever you downloaded the .deb files[/COLOR]
sudo dpkg -i linux*.deb
```Reboot. Is all well??

If so, recompile the wireless driver:```
cd ~/rtl8723as
make clean
make
sudo make install
sudo depmod -a
sudo modprobe 8723bs
```Fingers crossed!

---

### Post by stridast76 on 2014-10-28
ok will try to install that.  TBH I'm not certain how to tell what the responses with arch and uname -a mean. so I'll post them in case.  as for the processer, that's easy enough to confirm what it is.  it is more or less as quoted.  technically the clock speed is 1.33Ghz but it can go up to 1.8Ghz for short periods apparently.  I get the 1.33Ghz listed with cpuinfo and it confirms thats its the Z3735D SoC 

as for the others
stridast@stridast-Pipo-W2:~$ arch
i686
stridast@stridast-Pipo-W2:~$ uname -a
Linux stridast-Pipo-W2 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014 i686 i686 i686 GNU/Linux
stridast@stridast-Pipo-W2:~$ 


going to install now and hope for the best.

EDIT:  just realised that since it lists the generic kernel on uname that thats the one I need not the low latency :D  is it just the linux image and headers I need?

ok, missed the headers all.deb file at first, and got the obvious error,  downloaded that, ran dpkg again and I think all is well.  rebooting now  *crosses fingers*

---

### Post by stridast76 on 2014-10-28
ok, no luck booting.  I get the following right off:

..MP-BIOS bug 8254 timer not connected to IO-APIC
pnp 00:03: can't evaluate_CRS:  1
I8042 no controller found


now to try to boot from the older kernel
followed by the usual rpmb timeout problems that all these bay trail tablets get.  (not certain how to add this code to a kernel to fix it)
[https://dev-nell.com/rpmb-emmc-errors-under-linux.html](https://dev-nell.com/rpmb-emmc-errors-under-linux.html)

then my screen goes funny, it becomes impossible to see what's going on.  Same bug that all the newer kernels seem to cause.   its like it forgets what the resolution is, since I get a bunch of horizontal white lines, on a black screen. I had a similar issue when I tried to figure out the resolution on boot. working from the asus t100 tutorials which used video=VGA-1:1368x768e reboot=pci,force   to boot.  I initially tried video=VGA-1:1280x800e  when I needed 800x1280  instead.  and the screen went all funny similar to this.  thing is, with the messed up resolution, I could tell it still booted to desktop eventually, since moving the mouse changed the pattern on the display, and the colors changed from white, to colors that matched the ubuntu desktop background.  With this, it never boots up to desktop, the white lines displayed eventually fade to black. so it's something more then just resolution issues

removed the 3.16.2 kernel with

sudo apt-get purge linux-image-3.16.2*
sudo update-grub

and now it's not booting *sigh*  trying to boot from ubuntu advanced options in grub freezes at: 
Loading linux-image-3.13.0-37 
loading initial ramdisk.

trying recovery mode boots to the prompt at least.  any way to fix it?

---

### Post by chili555 on 2014-10-28
> trying recovery mode boots to the prompt at least. any way to fix it?Usually, when it boots to the prompt, it is a problem with the graphics driver or configuration. You can log in to the system and check:```
dmesg
tail -n 20 /var/log/Xorg.0.log
```> ..MP-BIOS bug 8254 timer not connected to IO-APIC
pnp 00:03: can't evaluate_CRS: 1
I8042 no controller foundI suspect that the customized kernel mentioned above, Adam Williamson's 3.16.0-0.rc5.git0.1.1awb fedlet kernel, overcomes this. Can you find and install it?

---

### Post by stridast76 on 2014-10-29
Reply I got from Adam Williamson was this:


[LIST]
[*]
[LIST]
[*][COLOR=#555555]Fedlet uses a slightly patched Fedora kernel, it has nothing at all to do with any Ubuntu kernel. The changes are fairly clearly marked out in the kernel.spec file in the kernel .src.rpm &#8211; [https://www.happyassassin.net/fedlet/repo/SRPMS/kernel-3.17.0-0.rc6.git2.1.2awb.src.rpm](https://www.happyassassin.net/fedlet/repo/SRPMS/kernel-3.17.0-0.rc6.git2.1.2awb.src.rpm) . Searching for &#8216;awb&#8217; within the spec should find most of the fedlet-specific changes.
[/COLOR]


[*]
so I don't think the fedlet kernel will work for this.  Fedlet boots on my tablet, so yes somethings fixed, but the touchscreen doesn't work, and everything is insanely laggy to the point of uselessness.  the lag can be anywhere from a second or two, up to  5 min or so.   Interestingly. after playing around with boot attempts quite a few times, I got the 3.16.2 kernel to boot.  once  the touchscreen didnt work in that either,  but this time, I got what I believe is the wifi chip to show up.  under /sys/bus/sdio/devices there is now a folder where there wasnt one before. labeled mmc1:0001:1  So it would seem the problem I am running into is that the sdio bus isn't loading on the 3.13 kernels.  I also got a system program detected window to show up on 3.16.2  (ok 3 of them)  I added the driver for the wifi,  but I can't comfirm if it works or not, since I havn't gotten lucky enough for it to boot a second time.  On my 6th attempt now since it booted up last,  and out of time to work on it. will try more tonight.  if I can get through to desktop again I can at least confirm if the driver works, which changes this entire issue into a sdio bus problem, instead of a wifi problem.




[/LIST]
[/LIST]

---

### Post by stridast76 on 2014-10-29
ok, First off, I was able to get it to boot to desktop again on the 3.16.2 kernel. had to use recovery option for the kernel then complete the boot from recovery.

  the wifi works with the driver. on the tablet now, without a wifi adapter as I type this!

 so I'm going to update the initial post.  the wifi does indeed work.  my problem now that the driver is solved is more of one of working out how to get the sdio bus to load up without needing one of these glitchy, problematic on the touchy tablet, kernels. (quite certain its the tablets fault not the kernels, but that doesnt make much difference)

I'm going to start a new thread about that in a different section of the forums since it seems to not be a wifi issue at this point.  but I'm posting the output from the : tail -n 20 /var/log/Xorg.0.log

[   170.268] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.4/1-2.4:1.0/0003:046E:5542.0005/input/input7/event1"
[   170.268] (II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD, id 7)
[   170.268] (**) Option "xkb_rules" "evdev"
[   170.268] (**) Option "xkb_model" "pc105"
[   170.268] (**) Option "xkb_layout" "us"
[   170.270] (II) config/udev: Adding input device BTC USB Multimedia Keyboard (/dev/input/event5)
[   170.270] (**) BTC USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[   170.270] (II) Using input driver 'evdev' for 'BTC USB Multimedia Keyboard'
[   170.270] (**) BTC USB Multimedia Keyboard: always reports core events
[   170.270] (**) evdev: BTC USB Multimedia Keyboard: Device: "/dev/input/event5"
[   170.270] (--) evdev: BTC USB Multimedia Keyboard: Vendor 0x46e Product 0x5542
[   170.270] (--) evdev: BTC USB Multimedia Keyboard: Found keys
[   170.270] (II) evdev: BTC USB Multimedia Keyboard: Configuring as keyboard
[   170.270] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.4/1-2.4:1.1/0003:046E:5542.0006/input/input8/event5"
[   170.270] (II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD, id 11)
[   170.271] (**) Option "xkb_rules" "evdev"
[   170.271] (**) Option "xkb_model" "pc105"
[   170.271] (**) Option "xkb_layout" "us"
[   170.290] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   170.315] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm

and dmesg

pasting parts that jump out at me, first, related to wifi i got this error

[   46.589898] 8723bs: module verification failed: signature and/or  required key missing - tainting kernel
[   46.604071] RTL871X: module init start version:v4.1.3_8883.20130902_v2
[   46.964685] RTL871X: module init ret=0
[   47.019286] sst-acpi 80860F28:00: Cannot load firmware intel/fw_sst_0f28.bin-i2s_master


[   37.289285] random: nonblocking pool is initialized
[   37.308637] EXT4-fs (mmcblk0p5): mounted filesystem with ordered data mode. Opts: (null)
[   37.805342] systemd-udevd[221]: starting version 204
[   37.981944] 80860F0A:00: ttyS4 at MMIO 0x8894d000 (irq = 39, base_baud = 16020) is a 16550A
[   37.988555] 80860F0A:01: ttyS5 at MMIO 0x88953000 (irq = 40, base_baud = 16020) is a 16550A
[   38.064777] mei_txe 0000:00:1a.0: can't derive routing for PCI INT A
[   38.070669] sst-acpi 80860F28:00: Direct firmware load failed with error -2
[   38.070672] sst-acpi 80860F28:00: Falling back to user helper
[   38.085445] mei_txe 0000:00:1a.0: PCI INT A: no GSI
[   38.092525] mei_txe 0000:00:1a.0: irq 106 for MSI/MSI-X
[   38.096560] INT3403: probe of INT3403:04 failed with error -22
[   38.144488] [drm] Initialized drm 1.1.0 20060810
[   38.178863] dw_dmac INTL9C60:00: DesignWare DMA Controller, 8 channels
[   38.189530] mei_txe 0000:00:1a.0: NFC MEI VERSION: IVN 0x1 Vendor ID 0x1 Type 0x1
[   38.193594] dw_dmac INTL9C60:01: DesignWare DMA Controller, 8 channels



anyways, thats what I have at the moment.thanks again for the help,.  it DID at least get the wifi up and running, just requires a kernel that doesnt like my tablet to boot up the device in the first place. then installing the drivers

Now to test things before I start a new thread. now that I know how to install new kernels, I'm going to test every kernel version that's newer than 3.13 to see if any of them are both boot friendly on this tablet, and SDIO friendly on this tablet.

---

### Post by chili555 on 2014-10-30
Before you close the door entirely, I do see one thing in dmesg that we can probably fix:> sst-acpi 80860F28:00: Cannot load firmware intel/fw_sst_0f28.bin-i2s_master...which leads to:> sst-acpi 80860F28:00: Direct firmware load failed with error -2Let's grab the firmware and solve that issue:```
cd /lib/firmware/intel
sudo wget https://chromium.googlesource.com/chromiumos/third_party/linux-firmware/+/refs/heads/stabilize-5339.B/intel/fw_sst_0f28.bin-i2s_master
```I understand that sst-acpi has to do with the sound system, so, upon reboot, you might find some things working better now.

I see nothing remarkable (read: fixable) in the Xorg log.

After a reboot, you might search dmesg again for issues:```
dmesg | grep -i error
```I think in any trailblazing project, part of the process is to look for leaks in the hull and seal them one-by-one.

---

### Post by stridast76 on 2014-10-30
ok tried that :D it's applied, no sound yet on this tablet,  posting the dmesg error list at the bottom of this post

intel released graphics drivers for these bay trail tablets I think, which might help my graphics problem booting these later kernels.  how do I install it?

[https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.6-0intel1_i386.deb](https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.6-0intel1_i386.deb)

I've got a fair idea how to do so, but I I would rather make certain before I try, since there's a lot of work now involved in my latest installation of ubuntu that I really really don't want to have to reinstall again.

and last but not least, every boot is plagued with rpmb timeout errors (on all of the various bay trail tablets AFAIK)  I've found this patch to fix it

[https://dev-nell.com/rpmb-emmc-errors-under-linux.html](https://dev-nell.com/rpmb-emmc-errors-under-linux.html)

but I haven't the faintest idea how to apply it.  any tips on that?  (relevent to the long list of errors in this dmesg list)


stridast@stridast-Pipo-W2:~$ dmesg | grep -i error
[    0.459191] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[   12.295520] mmcblk0rpmb: error -110 transferring data, sector 8064, nr 8, cmd response 0x900, card status 0xb00
[   12.356620] end_request: I/O error, dev mmcblk0rpmb, sector 8064
[   12.362002] Buffer I/O error on device mmcblk0rpmb, logical block 1008
[   20.600319] mmcblk0rpmb: error -110 transferring data, sector 8064, nr 8, cmd response 0x900, card status 0xb00
[   20.662219] end_request: I/O error, dev mmcblk0rpmb, sector 8064
[   20.667584] Buffer I/O error on device mmcblk0rpmb, logical block 1008
[   28.885055] mmcblk0rpmb: error -110 transferring data, sector 8176, nr 8, cmd response 0x900, card status 0xb00
[   28.964829] end_request: I/O error, dev mmcblk0rpmb, sector 8176
[   28.971861] Buffer I/O error on device mmcblk0rpmb, logical block 1022
[   37.207887] mmcblk0rpmb: error -110 transferring data, sector 8176, nr 8, cmd response 0x900, card status 0xb00
[   37.267427] end_request: I/O error, dev mmcblk0rpmb, sector 8176
[   37.272465] Buffer I/O error on device mmcblk0rpmb, logical block 1022
[   38.272578] sst-acpi 80860F28:00: Direct firmware load for intel/fw_sst_0f28.bin-48kHz_i2s_master failed with error -2
[   38.354195] INT3403: probe of INT3403:04 failed with error -22
[   47.121170] mmcblk0rpmb: error -110 transferring data, sector 8064, nr 8, cmd response 0x900, card status 0xb00
[   47.192654] end_request: I/O error, dev mmcblk0rpmb, sector 8064
[   47.198642] Buffer I/O error on device mmcblk0rpmb, logical block 1008
[   55.416536] mmcblk0rpmb: error -110 transferring data, sector 8064, nr 8, cmd response 0x900, card status 0xb00
[   55.483105] end_request: I/O error, dev mmcblk0rpmb, sector 8064
[   55.488780] Buffer I/O error on device mmcblk0rpmb, logical block 1008
[   63.705537] mmcblk0rpmb: error -110 transferring data, sector 8176, nr 8, cmd response 0x900, card status 0xb00
[   63.771293] end_request: I/O error, dev mmcblk0rpmb, sector 8176
[   63.777060] Buffer I/O error on device mmcblk0rpmb, logical block 1022
[   71.994245] mmcblk0rpmb: error -110 transferring data, sector 8176, nr 8, cmd response 0x900, card status 0xb00
[   72.072469] end_request: I/O error, dev mmcblk0rpmb, sector 8176
[   72.079648] Buffer I/O error on device mmcblk0rpmb, logical block 1022
[  258.944609] EXT4-fs (mmcblk0p5): re-mounted. Opts: errors=remount-ro
[  267.769017] mmcblk0rpmb: error -110 transferring data, sector 8064, nr 8, cmd response 0x900, card status 0xb00
[  267.784617] end_request: I/O error, dev mmcblk0rpmb, sector 8064
[  267.784747] Buffer I/O error on device mmcblk0rpmb, logical block 1008
[  276.002406] mmcblk0rpmb: error -110 transferring data, sector 8064, nr 8, cmd response 0x900, card status 0xb00
[  276.018659] end_request: I/O error, dev mmcblk0rpmb, sector 8064
[  276.018789] Buffer I/O error on device mmcblk0rpmb, logical block 1008
[  284.237736] mmcblk0rpmb: error -110 transferring data, sector 8176, nr 8, cmd response 0x900, card status 0xb00
[  284.253520] end_request: I/O error, dev mmcblk0rpmb, sector 8176
[  284.253651] Buffer I/O error on device mmcblk0rpmb, logical block 1022
[  292.589337] mmcblk0rpmb: error -110 transferring data, sector 8176, nr 8, cmd response 0x900, card status 0xb00
[  292.604895] end_request: I/O error, dev mmcblk0rpmb, sector 8176
[  292.604990] Buffer I/O error on device mmcblk0rpmb, logical block 1022
[  494.679849] RTL871X: ERROR psta->ieee8021x_blocked == _TRUE,  pattrib->ether_type(86dd) != 0x888e |n0x88B4

---

### Post by chili555 on 2014-10-30
> [https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.6-0intel1_i386.deb](https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.6-0intel1_i386.deb)The usual way is:```
sudo dpkg -i some_package.deb
```However, I notice this is from the 14.04 directory; your kernel is 3.16.2, approximately the 14.10 kernel. Therefor, I suggest you do:```
sudo dpkg --dry-run -i intel*.deb
```See if there are any obvious errors, etc. If not, install the usual way. Logging out and back in should restart the graphics system but, if in doubt, reboot.

If it all goes terribly wrong, remove:```
sudo apt-get purge intel-linux-graphics-installer
```'Purge' will uninstall the package and remove the configuration files it created.> [https://dev-nell.com/rpmb-emmc-errors-under-linux.html](https://dev-nell.com/rpmb-emmc-errors-under-linux.html)I regret this is beyond my experience. Modifying the .c code is quite easy, but I assume you then need to recompile the kernel (YIKES!) for it to apply. I never have done so, nor have I extracted my own tooth!

I recommend you follow the first reply:> For anyone interested in the details, they can check out my recent posts on backing up the T100, updating the BIOS, and installing Ubuntu Linux (a pre-release of Version 14.10) at: [http://linuxnorth.wordpress.com/2014/08/23/installing-linux-on-the-asus-transformer-book-t100/](http://linuxnorth.wordpress.com/2014/08/23/installing-linux-on-the-asus-transformer-book-t100/).... (I will add a post soon about your wonderful patch!)I'm sorry I can't advise you on the dark art of kernel compilation.

---

### Post by stridast76 on 2014-11-02
ok, this is in reply to someones question from the comments on the fedlet website. (Dosfish was the username)

xinput from the pipo w2:
xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; FTSC1000:00 2808:5056                       id=9    [slave  pointer  (2)]
&#9116;   &#8627; HID-compliant Mouse HID-compliant Mouse     id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=7    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=8    [slave  keyboard (3)]


not certain what you ment by syslog, so i can run that if you explain more.

---

### Post by mtndrgon on 2015-02-04
This thread is closed, however seems unresolved and there are several thousand hits.. this adapter seems to rely on a twist of M$ enumeration and a bit of linux knowhow. got mine to work fully with fedlet on the 3.19 rc5 kernel w/ a module compiled with [https://github.com/hadess/rtl8723bs](https://github.com/hadess/rtl8723bs) against the kernel-devel. Wifi only as the BT looks for the microsoft enumerator but loads at boot for keyboard and mouse. I haven't even started on the FM capabilities.

[atlis@round5 ~] $ dmesg | grep -e 8723 -e RTL
[    7.767817] r8723bs: module verification failed: signature and/or  required key missing - tainting kernel
[    7.770794] RTL871X: module init start
[    7.770801] RTL871X: rtl8723bs v4.3.5.5_12290.20140916_BTCOEX20140507-4E40
[    7.770804] RTL871X: rtl8723bs BT-Coex version = BTCOEX20140507-4E40
[    8.009873] RTL871X: rtw_ndev_init(wlan0)
[    8.010547] RTL871X: module init ret=0
[   16.336105] RTL871X: rtw_set_802_11_connect(wlan0)  fw_state=0x00000008
[   16.542934] RTL871X: SetHwReg(wlan0) variable(76) not defined!
[   16.550218] RTL871X: start auth
[   16.552129] RTL871X: auth success, start assoc
[   16.557764] RTL871X: assoc success
[   16.558150] RTL871X: SetHwReg(wlan0) variable(37) not defined!
[   16.571827] RTL871X: send eapol packet
[   16.578552] RTL871X: send eapol packet
[   16.581888] RTL871X: set pairwise key camid:4, addr:78:24:af:ed:0a:68, kid:0, type:AES
[   16.584314] RTL871X: set group key camid:5, addr:78:24:af:ed:0a:68, kid:1, type:AES

also:
[    0.049061] mce: CPU supports 6 MCE banks
[    0.049075] CPU0: Thermal monitoring enabled (TM1)
[    0.049089] Last level iTLB entries: 4KB 48, 2MB 0, 4MB 0
Last level dTLB entries: 4KB 128, 2MB 16, 4MB 16, 1GB 0
[    0.049286] Freeing SMP alternatives memory: 24K (c0e5f000 - c0e65000)
[COLOR=#ff0000][    0.050886] **Ignoring BGRT: invalid status 0 (expected 1)**[/COLOR]
[    0.055622] ftrace: allocating 26670 entries in 53 pages
[    0.078267] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.079294] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[COLOR=#ff0000]**[    0.089309] ..MP-BIOS bug: 8254 timer not connected to IO-APIC**[/COLOR]
[    0.089319] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.089323] ..... (found apic 0 pin 2) ...
[    0.099329] ....... works.
[    0.099334] smpboot: CPU0: Intel(R) Atom(TM) CPU  Z3735D @ 1.33GHz (fam: 06, model: 37, stepping: 08)
[    0.099365] TSC deadline timer enabled
~
[    7.285194] ACPI: Battery Slot [BAT1] (battery present)
[    7.391844] i2c_hid i2c-GDIX1001:00: unexpected HID descriptor bcdVersion (0x0000)
[    7.406191] dw_dmac INTL9C60:00: Missing DT data
[    7.406727] dw_dmac INTL9C60:00: DesignWare DMA Controller, 8 channels
[    7.406982] dw_dmac INTL9C60:01: Missing DT data
[    7.407553] dw_dmac INTL9C60:01: DesignWare DMA Controller, 8 channels
[    7.530293] Goodix-TS i2c-GDIX1001:00: IC VERSION: 39 32 37 31 40 10
[    7.538433] input: Goodix Capacitive TouchScreen as /devices/platform/80860F41:05/i2c-13/i2c-GDIX1001:00/input/input3
[    7.651520] alg: No test for crc32 (crc32-pclmul)
[    7.659275] cfg80211: Calling CRDA to update world regulatory domain
[    7.767817] r8723bs: module verification failed: signature and/or  required key missing - tainting kernel
[    7.770794] RTL871X: module init start
[    7.770801] RTL871X: rtl8723bs v4.3.5.5_12290.20140916_BTCOEX20140507-4E40
[    7.770804] RTL871X: rtl8723bs BT-Coex version = BTCOEX20140507-4E40
[    7.855137] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[    7.855191] SELinux: initialized (dev mmcblk0p1, type vfat), uses genfs_contexts
[    7.885455] iTCO_vendor_support: vendor-support=0
[    7.894888] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.11
[    7.894979] iTCO_wdt: Found a Bay Trail SoC TCO device (Version=3, TCOBASE=0x0460)
[    7.895680] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    7.906273] byt-rt5640 byt-rt5640: ASoC: CPU DAI baytrail-pcm-audio not registered
[    7.906304] platform byt-rt5640: Driver byt-rt5640 requests probe deferral
[    7.913308] baytrail-pcm-audio baytrail-pcm-audio: error: invalid DMA engine 0
[    7.913318] baytrail-pcm-audio baytrail-pcm-audio: sst_dma_new failed -22
[    7.949803] baytrail-pcm-audio baytrail-pcm-audio: FW version: 04.05.13.a0
[    7.949811] baytrail-pcm-audio baytrail-pcm-audio: Build type: a0
[    7.949817] baytrail-pcm-audio baytrail-pcm-audio: Build date: Apr  2 2014 14:14:39
[    7.952750] random: nonblocking pool is initialized
[    7.971542] intel_rapl: Found RAPL domain package
[    7.971549] intel_rapl: Found RAPL domain core
[    7.984197] input: gpio-keys as /devices/platform/gpio-keys.0.auto/input/input4
[    7.986780] input: gpio-keys as /devices/platform/gpio-keys.1.auto/input/input5
[    7.992351] byt-rt5640 byt-rt5640: rt5640-aif1 <-> baytrail-pcm-audio mapping ok
[    8.009873] RTL871X: rtw_ndev_init(wlan0)
[    8.010547] RTL871X: module init ret=0
[    8.221658] cfg80211: World regulatory domain updated:
[    8.221668] cfg80211:  DFS Master region: unset
[    8.221673] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    8.221682] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    8.221689] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    8.221695] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    8.221703] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    8.221710] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    8.221717] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    8.221724] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    8.221730] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    8.423441] cfg80211: Calling CRDA for country: US
[    8.443287] cfg80211: Regulatory domain changed to country: US
[    8.443306] cfg80211:  DFS Master region: FCC
[    8.443317] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    8.443337] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
[    8.443354] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
[    8.443373] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
[    8.443388] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
[    8.443403] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[    9.073115] audit: type=1305 audit(1423109696.436:4): audit_pid=506 old=0 auid=4294967295 ses=4294967295 subj=system_u:system_r:auditd_t:s0 res=1
[   10.604233] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   10.678434] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   10.921992] Ebtables v2.0 registered
[   11.026087] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[   14.466704] SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs
[   16.336105] RTL871X: rtw_set_802_11_connect(wlan0)  fw_state=0x00000008
[   16.542934] RTL871X: SetHwReg(wlan0) variable(76) not defined!
[   16.550218] RTL871X: start auth
[   16.552129] RTL871X: auth success, start assoc
[   16.557764] RTL871X: assoc success
[   16.558150] RTL871X: SetHwReg(wlan0) variable(37) not defined!
[   16.571827] RTL871X: send eapol packet
[   16.578552] RTL871X: send eapol packet
[   16.581888] RTL871X: set pairwise key camid:4, addr:78:24:af:ed:0a:68, kid:0, type:AES
[   16.584314] RTL871X: set group key camid:5, addr:78:24:af:ed:0a:68, kid:1, type:AES
[   16.584798] SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs
[   52.554641] SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs
[   54.387194] fuse init (API version 7.23)
[   54.405007] SELinux: initialized (dev fuse, type fuse), uses genfs_contexts
[   54.435330] SELinux: initialized (dev fusectl, type fusectl), uses genfs_contexts
[   54.907969] SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs
[   55.611820] Bluetooth: Core ver 2.20
[   55.612116] NET: Registered protocol family 31
[   55.612122] Bluetooth: HCI device and connection manager initialized
[   55.612137] Bluetooth: HCI socket layer initialized
[   55.612144] Bluetooth: L2CAP socket layer initialized
[   55.612162] Bluetooth: SCO socket layer initialized
[   55.636453] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   55.636461] Bluetooth: BNEP filters: protocol multicast
[   55.636472] Bluetooth: BNEP socket layer initialized
[   55.854312] SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs
[   61.251740] FAT-fs (mmcblk1p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[   61.251760] SELinux: initialized (dev mmcblk1p1, type vfat), uses genfs_contexts
[   61.270786] SELinux: initialized (dev mmcblk0p3, type fuseblk), uses genfs_contexts
[   61.326683] SELinux: initialized (dev mmcblk0p6, type fuseblk), uses genfs_contexts
[COLOR=#ff0000]**[   87.619178] byt_gpio INT33FC:02: Gpio 18 interrupt flood, disabling**[/COLOR]

Now trying to insert the fedlet kernel into a 14.10 ubuntu, but still needed to sort some errors first. Fedlet works amazingly well. Getting that kernel and Ubuntu to play nice will make this a powerhouse.

---

