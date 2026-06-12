---
title: "more ndiswrapper woes"
date: 2005-07-03
forum: Networking &amp; Wireless
---

### Post by hack_benjamin on 2005-07-03
output of dmesg

Modules linked in: ndiswrapper tsdev sr_mod sbp2 evdev scsi_mod ieee1394 rtc psmouse mousedev parport_pc lp parport ide_cd cdrom reiserfs ide_generic ide_disk via82cxxx ide_core unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
Pid: 2382, comm: loadndisdriver Not tainted 2.6.10-5-amd64-generic
RIP: 0010:[<ffffffffa0146537>] <ffffffffa0146537>{:ndiswrapper:unload_ndis_driver+128}
RSP: 0018:000001001e003eb8  EFLAGS: 00010246
RAX: 0000000000000040 RBX: 0000010001779418 RCX: ffffffff802f1ac0
RDX: 0000010001000000 RSI: 0000000000000000 RDI: 0000000000000000
RBP: 0000000000000000 R08: 0000000000000000 R09: 000000000000000d
R10: 0000000000000000 R11: ffffffffffffd674 R12: 000001001f8c6600
R13: 00000000ffffffe7 R14: 0000000000000000 R15: 0000000000000000
FS:  0000002a9556c250(0000) GS:ffffffff803d1800(0000) knlGS:0000000000000000
CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
CR2: 0000000000000050 CR3: 0000000000101000 CR4: 00000000000006e0
Process loadndisdriver (pid: 2382, threadinfo 000001001e002000, task 000001001e683690)
Stack: 000001001f8c6600 ffffff000021a000 ffffffffffffffff ffffffffa01469da
       000001001f8c6988 0000010001779418 0000002a00040004 ffffffffa015d493
       0000000000000000 ffffff000021a000
Call Trace:<ffffffffa01469da>{:ndiswrapper:load_ndis_driver+434}
       <ffffffffa0146f1d>{:ndiswrapper:wrapper_ioctl+116}
       <ffffffff801711e6>{sys_ioctl+483} <ffffffff8010ddd6>{system_call+126}
Code: 48 8b 78 10 e8 83 c0 00 00 49 8d 7c 24 38 e8 19 24 00 00 49
RIP <ffffffffa0146537>{:ndiswrapper:unload_ndis_driver+128} RSP <000001001e003eb8>
CR2: 0000000000000050
 <3>ndiswrapper (ndiswrapper_load_driver:93): loadndiswrapper failed (9); check
system log for messages from 'loadndisdriver'

this is lspci

0000:00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

and this is a verbose modprobe and the output of lsmod

ndiswrapper           188360  1

so as far as i can tell it should all work.

alias wlan0 ndiswrapper is set up in /etc/modules/ndiswrapper

but when i run ifup wlan0 it tells me it is ignoring unknown interface wlan0.

I thought at first (after reading the forums that it was the two gig of ram and the broadcom chip that were at fault but i have removed one gig and it still says the same

HELP!

cheers

---

### Post by spd106 on 2005-07-03
Hi, which version of Ndiswrapper are you using?
I have the same chipset on my belkin cardbus and i found it wouldn't work with version 0.12 ie the one in the repo. So I had to compile v1.1 from source. I updated to v1.2 recently though and that's ok too. According to the wiki this isn't the right way, but they haven't updated the page yet and it works for me.

Also check the /etc/network/interfaces file. 

Incidentally it works with Xandros 3.0 and that uses v0.12. It also works on warty with v0.12 although I think I might have used a dell driver. Mandriva2005 uses v1.0 and it works from there too, as that's how i'm writing this. 

Dual boot with ubuntu, honest!

---

