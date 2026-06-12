---
title: "Won't Suspend!"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by TheCosmicFrog on 2010-05-09
Hi guys,

MSI GX620 notebook. Computer suspended flawlessly in Karmic but ever since my upgrade to 10.04 Lucid it won't suspend. Screen fades to black, but backlight, power lights and fans etc. stay on. Computer is still clearly running. It hangs at this point and nothing will wake it up. Have to do a hard reset.

I've tried doing a fresh install but to no avail. Can someone help me? :)

Thanks,
Aaron.

---

### Post by TheCosmicFrog on 2010-05-10
Can anyone help?

---

### Post by sfarthing on 2010-05-10
I'm also encountering this sometimes on my desktop with U 10.04.  But if I boot up and then immediately do a suspend without starting any apps such as Firefox, etc. the system suspends just fine and quickly.  So something happens during a session that interferes with suspending.  Can you also suspend under that scenario?

---

### Post by HarrisonNapper on 2010-05-10
Firstly, if you get in to a situation where nothing will wake your computer up, use this to reboot:

Hold Alt-PrtScr and while holding both of those press these keys in this order: R, E, I, S, U, B

I remember it as BUSIER backwards.

Secondly, suspend the computer, do a reboot using the method I mentioned (write it down on paper, not on the laptop), open a terminal, and paste the output of the following commands:
```

uname -a
lsusb

```

To others: anyone know how to narrow syslog info down to suspend logs? When the system is booted up, that will push it back quite a bit. Can't think of it off of the top of my head right now (at work with doze and cygwin).

---

### Post by TheCosmicFrog on 2010-05-10
Thanks, here you go:

uname -a:
Linux aaron-notebook 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux


lsusb:
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by HarrisonNapper on 2010-05-12
Okay, well, that rules out 64-bit and lsusb was not as helpful as I'd hoped. Do you have a bluetooth and what happens if you disable the bluetooth (hardware disable on the keyboard) and then suspend?

---

### Post by kansasnoob on 2010-05-12
I wonder if SWAP is working as it should?

Maybe post the output of:

```
free -m
```

---

### Post by TheCosmicFrog on 2010-05-12
> **HarrisonNapper said:**
> Okay, well, that rules out 64-bit and lsusb was not as helpful as I'd hoped. Do you have a bluetooth and what happens if you disable the bluetooth (hardware disable on the keyboard) and then suspend?

I always leave Bluetooth off, so it must not be that.

and free -m outputs:
```

             total       used       free     shared    buffers     cached
Mem:          3023       1314       1708          0        200        534
-/+ buffers/cache:        580       2443
Swap:         3071          0       3071

```

---

### Post by kansasnoob on 2010-05-12
> **TheCosmicFrog said:**
> I always leave Bluetooth off, so it must not be that.

and free -m outputs:
```

             total       used       free     shared    buffers     cached
Mem:          3023       1314       1708          0        200        534
-/+ buffers/cache:        580       2443
Swap:         3071          0       3071

```

That looks alright to me so I'm puzzled :confused:

---

### Post by TheCosmicFrog on 2010-05-12
Well Suspend has nothing to do with Swap, only Hibernate, right?

---

### Post by HarrisonNapper on 2010-05-12
Hibernate stores to disk and assuming that disk is the swap partition, that would make sense. Suspend stores to memory, so if the saved state exceeded memory, it could use swap.

I think primarily we need to get the system messages generated during the suspend process, which should be in /var/log/messages, but I can't think for the life of me how to narrow it down. dmesg might also have useful output, but don't know if that's only for hibernate and shutdown/startup.


That being said, Suspend it, shut it down, start it back up (or however you have to do it; remember to alt-prtscr REISUB) and then cat -f /var/log/messages, G to go to the end of the file and then scroll up and look for errors. Jot down anything you notice and let us know. You can theoretically cat it out to a file and post it on the forums, but apart from being rather long, I don't know how secure that would be.

---

### Post by TheCosmicFrog on 2010-05-12
I'm not really sure what to deduce from the /var/log/messages file, but if somebody can tell me what to look for I'll check!

One interesting thing, after I click Suspend, using the Alt-PrtScr REISUB command doesn't do anything. It works when Ubuntu is running normally of course, it just reboots.

---

### Post by jojubees on 2010-05-12
My HP 9812us Notebook was suspending perfectly until I did an update this morning.  Now when I select lock screen my system locks up requiring a hard reboot.  I'm using Ubuntu 10 64bit.

---

### Post by TheCosmicFrog on 2010-05-13
> **jojubees said:**
> My HP 9812us Notebook was suspending perfectly until I did an update this morning.  Now when I select lock screen my system locks up requiring a hard reboot.  I'm using Ubuntu 10 64bit.

Strange, my lock screen works fine, but it seems to be the same sort of problem you're having. I'm using Ubuntu 10.04 32-bit, though.

---

### Post by QLee on 2010-05-13
[QUOTE=HarrisonNapper]... Suspend stores to memory, so if the saved state exceeded memory, it could use swap...[/QUOTE]

There is a mis-conception here:

Suspend does not "save" anything to memory, it keeps the voltage on for memory while shutting down the rest of the power supply (other than SBY). This is not going to "use" swap. The saved state will not exceed RAM.

---

### Post by QLee on 2010-05-13
[QUOTE=HarrisonNapper]
That being said, Suspend it, shut it down, start it back up (or however you have to do it; remember to alt-prtscr REISUB) and then cat -f /var/log/messages, G to go to the end of the file and then scroll up and look for errors. Jot down anything you notice and let us know. You can theoretically cat it out to a file and post it on the forums, but apart from being rather long, I don't know how secure that would be.[/QUOTE]

When one is interested in something like this it is usually sufficient to issue the command tail (i.e. tail /var/log/messages) the default is last ten lines (used with the -n switch you can specify the number of last lines).

Please don't post your whole file for a troubleshooting situation like this.

---

### Post by TheCosmicFrog on 2010-05-13
Thanks QLee. In that case, does this mean anything to anyone?:

```

May 13 15:54:14 aaron-notebook kernel: [ 1890.662879] [UFW ALLOW] IN= OUT=wlan0 SRC=140.203.215.76 DST=128.242.240.20 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=53897 DF PROTO=TCP SPT=55898 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
May 13 15:54:17 aaron-notebook kernel: [ 1893.700339] [UFW ALLOW] IN= OUT=wlan0 SRC=140.203.215.76 DST=172.16.7.141 LEN=57 TOS=0x00 PREC=0x00 TTL=64 ID=5209 DF PROTO=UDP SPT=60507 DPT=53 LEN=37 
May 13 15:54:17 aaron-notebook kernel: [ 1893.703106] [UFW ALLOW] IN= OUT=wlan0 SRC=140.203.215.76 DST=172.16.7.141 LEN=79 TOS=0x00 PREC=0x00 TTL=64 ID=5209 DF PROTO=UDP SPT=52636 DPT=53 LEN=59 
May 13 15:54:17 aaron-notebook kernel: [ 1893.707337] [UFW ALLOW] IN= OUT=wlan0 SRC=140.203.215.76 DST=172.16.7.141 LEN=57 TOS=0x00 PREC=0x00 TTL=64 ID=5210 DF PROTO=UDP SPT=34198 DPT=53 LEN=37 
May 13 15:54:17 aaron-notebook kernel: [ 1893.711898] [UFW ALLOW] IN= OUT=wlan0 SRC=140.203.215.76 DST=128.242.240.20 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=10122 DF PROTO=TCP SPT=55903 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
May 13 15:54:27 aaron-notebook kernel: [ 1903.367574] [UFW ALLOW] IN= OUT=wlan0 SRC=140.203.215.76 DST=172.16.7.141 LEN=59 TOS=0x00 PREC=0x00 TTL=64 ID=7625 DF PROTO=UDP SPT=59022 DPT=53 LEN=39 
May 13 15:54:27 aaron-notebook kernel: [ 1903.388777] [UFW ALLOW] IN= OUT=wlan0 SRC=140.203.215.76 DST=172.16.7.141 LEN=59 TOS=0x00 PREC=0x00 TTL=64 ID=7631 DF PROTO=UDP SPT=34828 DPT=53 LEN=39 
May 13 15:54:27 aaron-notebook kernel: [ 1903.413086] [UFW ALLOW] IN= OUT=wlan0 SRC=140.203.215.76 DST=65.55.172.253 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=43480 DF PROTO=TCP SPT=40229 DPT=995 WINDOW=5840 RES=0x00 SYN URGP=0 
May 13 15:54:27 aaron-notebook kernel: [ 1903.944585] [UFW AUDIT] IN= OUT=wlan0 SRC=140.203.215.76 DST=65.55.172.253 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=43489 DF PROTO=TCP SPT=40229 DPT=995 WINDOW=263 RES=0x00 ACK URGP=0 
May 13 15:54:28 aaron-notebook kernel: [ 1904.002356] [UFW AUDIT] IN=wlan0 OUT= MAC=01:22:fb:81:ad:42:FA:18:19:ad:83:c7:08:00 SRC=207.46.125.33 DST=140.203.215.76 LEN=178 TOS=0x00 PREC=0x00 TTL=118 ID=22198 DF PROTO=TCP SPT=80 DPT=51727 WINDOW=65224 RES=0x00 ACK PSH URGP=0 

```

---

### Post by QLee on 2010-05-13
Yeah, those are hits on your firewall. 

You probably want to look right after trying to suspend, if you wait until too long other messages will take up the "last" 10 lines.

try cat /var/log/messages | grep PM since it is likely PM statement you are looking for.

...or read the whole thing yourself but post only the last relevant lines

---

### Post by TheCosmicFrog on 2010-05-13
> **QLee said:**
> Yeah, those are hits on your firewall. 

You probably want to look right after trying to suspend, if you wait until too long other messages will take up the "last" 10 lines.

try cat /var/log/messages | grep PM since it is likely PM statement you are looking for.

...or read the whole thing yourself but post only the last relevant lines

The following was taken from $cat /var/log/messages | grep PM, right after hard-rebooting after a failed suspend attempt:

```

May 13 17:15:26 aaron-notebook kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
May 13 17:15:26 aaron-notebook kernel: [    0.000000] PM: Registered nosave memory: 0000000000099000 - 00000000000a0000
May 13 17:15:26 aaron-notebook kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
May 13 17:15:26 aaron-notebook kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
May 13 17:15:26 aaron-notebook kernel: [    0.004235] Performance Events: Core2 events, Intel PMU driver.
May 13 17:15:26 aaron-notebook kernel: [    0.216633] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.216637] pci 0000:00:01.0: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.216991] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.216996] pci 0000:00:1a.7: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.217082] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.217086] pci 0000:00:1b.0: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.217151] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.217155] pci 0000:00:1c.0: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.217223] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.217226] pci 0000:00:1c.1: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.217296] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.217300] pci 0000:00:1c.2: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.217367] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.217371] pci 0000:00:1c.3: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.217439] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.217443] pci 0000:00:1c.5: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.217780] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.217784] pci 0000:00:1d.7: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.218036] pci 0000:00:1f.2: PME# supported from D3hot
May 13 17:15:26 aaron-notebook kernel: [    0.218040] pci 0000:00:1f.2: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.218434] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.218439] pci 0000:02:00.0: PME# disabled
May 13 17:15:26 aaron-notebook kernel: [    0.218775] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
May 13 17:15:26 aaron-notebook kernel: [    0.218782] pci 0000:06:00.0: PME# disabled

```

---

### Post by HarrisonNapper on 2010-05-14
> **QLee said:**
> There is a mis-conception here:

Suspend does not "save" anything to memory, it keeps the voltage on for memory while shutting down the rest of the power supply (other than SBY). This is not going to "use" swap. The saved state will not exceed RAM.

Thank you for the info; much appreciated. The reason I had suggested just working from the end of the file was for the reason that if one were to boot up and have a lot of programs at startup, there would be lots of things on the logs.

TheCosmicFrog: lspci, lscpu, and cat /proc/ioports

(I realize that's more info than necessary, just want to cover all bases)

---

### Post by QLee on 2010-05-14
Don't know if the OP is coming back or not but:

In the output from the messages log I don't see any indication of the system trying to go into standby (which is what the OP is saying, eh?)

I'd expect the system to try and sync the drives, then try and go into mem sleep and it doesn't show that in the log.

Shotgun approach (just a bunch of stuff I thought of since I can't stay around today):
Does this system have 4G memory, if so should it use the pae kernel? Has the kernel been tried with any of the "tricks" like pci=off or acpi=off or any of that? Is it possible that whichever video driver is being used is having an effect? The kernel mentioned is the newest avail for Lucid, is it the first one you were offered or do you have a previous kernel on the system?

Good luck!

---

### Post by TheCosmicFrog on 2010-05-15
> **QLee said:**
> Don't know if the OP is coming back or not but:

In the output from the messages log I don't see any indication of the system trying to go into standby (which is what the OP is saying, eh?)

I'd expect the system to try and sync the drives, then try and go into mem sleep and it doesn't show that in the log.

Shotgun approach (just a bunch of stuff I thought of since I can't stay around today):
Does this system have 4G memory, if so should it use the pae kernel? Has the kernel been tried with any of the "tricks" like pci=off or acpi=off or any of that? Is it possible that whichever video driver is being used is having an effect? The kernel mentioned is the newest avail for Lucid, is it the first one you were offered or do you have a previous kernel on the system?

Good luck!

I'm still here, I have a subscription to this thread :)

So you're saying the system isn't apparently attempting to sleep? That's odd. I will try and disable the video driver (Nvidia proprietary) and see what happens. I haven't tried any of the "tricks" you mentioned. Are they safe to attempt and, if so, how do I test them?

And this is a clean install of Lucid, so it's the kernel that came with Lucid (updated once since Lucid become available).

---

### Post by slibuntu on 2010-05-15
Are you running 64 or 32 bit?

---

### Post by slibuntu on 2010-05-15
> **HarrisonNapper said:**
> 

TheCosmicFrog: lspci, lscpu, and cat /proc/ioports

(I realize that's more info than necessary, just want to cover all bases)

Post these outputs and lets get as much info as we can about the problem

---

### Post by TheCosmicFrog on 2010-05-15
> **slibuntu said:**
> Are you running 64 or 32 bit?

32-bit. 

> **slibuntu said:**
> Post these outputs and lets get as much info as we can about the problem

$lspci:
```

aaron@aaron-notebook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
07:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
07:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
07:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
08:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)

```$lscpu:
```

aaron@aaron-notebook:~$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              6
CPU MHz:              2000.000
L1d cache:             32K
L1i cache:             32K
L2 cache:              3072K

```$cat /proc/ioports:
```

aaron@aaron-notebook:~$ cat /proc/ioports
0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
004c-004f : enecir
0050-0053 : timer1
0060-0060 : keyboard
0064-0064 : keyboard
0070-0071 : rtc0
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
03c0-03df : vga+
  03c0-03df : uvesafb
0400-041f : 0000:00:1f.3
0480-04bf : pnp 00:08
04c0-04cf : pnp 00:08
04d0-04d1 : pnp 00:08
04d2-04ff : pnp 00:08
0800-087f : pnp 00:08
  0800-0803 : ACPI PM1a_EVT_BLK
  0804-0805 : ACPI PM1a_CNT_BLK
  0808-080b : ACPI PM_TMR
  0810-0815 : ACPI CPU throttle
  0820-082f : ACPI GPE0_BLK
  0850-0850 : ACPI PM2_CNT_BLK
0cf8-0cff : PCI conf1
1000-1fff : PCI Bus 0000:05
2000-2fff : PCI Bus 0000:06
3000-3fff : PCI Bus 0000:07
a400-a41f : 0000:00:1a.2
  a400-a41f : uhci_hcd
a480-a49f : 0000:00:1a.1
  a480-a49f : uhci_hcd
a800-a81f : 0000:00:1a.0
  a800-a81f : uhci_hcd
a880-a89f : 0000:00:1d.2
  a880-a89f : uhci_hcd
ac00-ac1f : 0000:00:1d.1
  ac00-ac1f : uhci_hcd
b000-b01f : 0000:00:1d.0
  b000-b01f : uhci_hcd
b400-b41f : 0000:00:1f.2
  b400-b41f : ahci
b480-b483 : 0000:00:1f.2
  b480-b483 : ahci
b800-b807 : 0000:00:1f.2
  b800-b807 : ahci
b880-b883 : 0000:00:1f.2
  b880-b883 : ahci
bc00-bc07 : 0000:00:1f.2
  bc00-bc07 : ahci
c000-cfff : PCI Bus 0000:02
  c800-c8ff : 0000:02:00.0
    c800-c8ff : r8169
d000-dfff : PCI Bus 0000:03
e000-efff : PCI Bus 0000:08
  ec00-ec7f : 0000:08:00.0

```Also, you know who this is, right Shane? :cool:

---

### Post by frznchckn on 2010-05-17
I'm having an identical issue that started with a round of updates on Friday.  After the problem started, I tried upgrading to 10.04 thinking it would magically fix it but to no avail.

For me, it seems the THIRD attempt to suspend since I had a hard reboot hangs the system every time whether or not I've been running wireless/firefox/anything else.

I've been forcing suspends with "s2ram -f" but I don't know the long term consequences of doing this.

Please let me know what info would be helpful in debugging this.

Any solution is desperately needed.

---

### Post by TheCosmicFrog on 2010-05-18
> **frznchckn said:**
> I'm having an identical issue that started with a round of updates on Friday.  After the problem started, I tried upgrading to 10.04 thinking it would magically fix it but to no avail.

For me, it seems the THIRD attempt to suspend since I had a hard reboot hangs the system every time whether or not I've been running wireless/firefox/anything else.

I've been forcing suspends with "s2ram -f" but I don't know the long term consequences of doing this.

Please let me know what info would be helpful in debugging this.

Any solution is desperately needed.

You're lucky s2ram works. It doesn't seem to work for my laptop :(

---

### Post by HarrisonNapper on 2010-05-19
Even with the -f option? Does it give you any output? If so, paste it here.

---

### Post by TheCosmicFrog on 2010-05-19
> **HarrisonNapper said:**
> Even with the -f option? Does it give you any output? If so, paste it here.

-f causes X to terminate and it just gives me a screen with:
```

login aaron-notebook:

```

The system is locked up though so no input is accepted.

When I use it without -f:

```

aaron@aaron-notebook:~$ sudo s2ram
[sudo] password for aaron: 
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Micro-Star International"
    sys_product  = "GX620      "
    sys_version  = "Ver 1.000"
    bios_version = "A1651IMS.10V"
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.

```

---

### Post by HarrisonNapper on 2010-05-20
> **TheCosmicFrog said:**
> -f causes X to terminate and it just gives me a screen with:
```

login aaron-notebook:

```The system is locked up though so no input is accepted.

When I use it without -f:

```

aaron@aaron-notebook:~$ sudo s2ram
[sudo] password for aaron: 
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Micro-Star International"
    sys_product  = "GX620      "
    sys_version  = "Ver 1.000"
    bios_version = "A1651IMS.10V"
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.

```


Firstly, try out that web address (and/or google for the Machine unknown error). Secondly, when it takes you to that login prompt, log in and do  sudo s2ram -f again. That should give you some output.

---

