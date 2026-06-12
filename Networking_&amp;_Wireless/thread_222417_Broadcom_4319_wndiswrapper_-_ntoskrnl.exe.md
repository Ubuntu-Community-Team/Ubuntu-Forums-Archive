---
title: "Broadcom 4319 w/ndiswrapper - ntoskrnl.exe?"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by herrminer on 2006-07-25
I've been trying for weeks now to get my wireless working.  I have searched the forums and the net in general and found a lot of information on getting Broadcom chipsets to work with ndiswrapper.  I think I'm pretty close, but I can't get past this error!  Any help is greatly appreciated.

Here are the specs on my machine:

HP dv5000
AMD64 Turion
Dapper 6.06 (kernel 2.6.15-26)
Network controller: Broadcom Corporation: Unknown device 4319 (rev 02)

I am using ndiswrapper 1.8 with a 64bit driver--netbc564.inf (md5: f5ebb4643ba4aa0404afa4adc111b2df).

I have blacklisted the default driver (bcm43xx) in /etc/modprobe.d/blacklist, installed the updated driver via ndiswrapper -i and made a symlink from /etc/ndiswrapper/netbc564/14E4:4320.5.conf to /etc/ndiswrapper/netbc564/14E4:4319.5.conf

ndiswrapper -l results:
Installed ndis drivers:
netbc564                driver present, hardware present

I have also aliased the interfaces in /etc/modprobe.d/ndiswrapper:
alias eth1 ndiswrapper
alias wlan0 ndiswrapper

Upon boot (or modprobe ndiswrapper) I see the following in /var/log/syslog:

Jul 24 21:47:35 localhost loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver netbc564
Jul 24 21:47:35 localhost kernel: [  590.448677] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
Jul 24 21:47:35 localhost kernel: [  590.451620] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
Jul 24 21:47:35 localhost kernel: [  590.451636] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
Jul 24 21:47:35 localhost kernel: [  590.451642] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
Jul 24 21:47:35 localhost kernel: [  590.451646] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
Jul 24 21:47:35 localhost kernel: [  590.451731] ndiswrapper (load_sys_files:218): couldn't prepare driver 'netbc564'
Jul 24 21:47:35 localhost kernel: [  590.452239] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

So I have searched all over but can't seem to figure out what is causing this error.

Your help is _greatly_ appreciated!

---

### Post by dutchman25 on 2006-08-08
I never could get ndiswrapper to work with the 64-bit drivers on the same laptop.  I used bcm43xx-fwcutter and finally got it to work with the default bcm43xx driver.

---

