---
title: "Dell XPS M1530 wireless problems"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by slyhne on 2008-02-25
When I first installed Ubuntu 7.10 on my new Dell XPS M1530, the wireless was working good - but at some point I think an update to Ubuntu broke the driver for my wireless adapter.

I can only make it work if I add noapic in grub (and  nmi_watchdog=0, otherwise VirtualBox wont work) - but thats hardly a solution more like a nasty hack.

I see the following with dmesg | grep ipw3945: 
ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
ipw3945: Copyright(c) 2003-2006 Intel Corporation
ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
ipw3945: MAC is in deep sleep!
ipw3945: Unable to int nic

And this with dmesg | grep 80211:
ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stack, git-1.1.13
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>

I have tried using iwl3945 instead, but could never get it going, it doesn't work at all:

I see the following with dmesg | grep iwl3945: 
iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.1.0
iwl3945: Copyright(c) 2003-2007 Intel Corporation
ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:0b:00.0 to 64
wl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
iwl3945: MAC is in deep sleep!
iwl3945: Unable to int nic
iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff
 iwl3945: HARDWARE GONE?? INTA == 0x000000000000000000000000000000000000000000000000000000000000000000000000ffffffff

Does anyone know how to wake up the NIC?
I have tried unloading/loading the modules without any effect.

Relevant lspci output:

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


Regards

slyhne

---

### Post by simonl2009 on 2008-02-26
Hi,
I have the same computer, same problem. I'd *really* like to see a solution to this, since I've fallen in love with ubuntu and don't want to deal with windows anymore. I tried using iwl3945 to no avail. My current way of dealing with the problem is to keep rebooting until the wireless does work: it usually takes about four tries. 

If anyone has any suggestions, please feel free to PM me or post here.
I've tried installing ndiswrapper, but I think I must be configuring it wrong since once it's installed ubuntu ceases to boot, it gets stuck on the load screen.

---

### Post by slyhne on 2008-02-26
Hi Simon

You can add **noapic** to /boot/grub/menu.lst

My entry for starting ubuntu in menu.lst looks like this:

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root       (hd0,5)
kernel   /boot/vmlinuz-2.6.22-14-generic root=UUID=10cad5a0-5f15-4f99-b08f-455d46fbd882 ro quiet splash** noapic** nmi_watchdog=0
initrd     /boot/initrd.img-2.6.22-14-generic
quiet

This solves the problem for now, hopefully they will solve the problem in version 8.04.

Regards

slyhne

---

### Post by simonl2009 on 2008-02-26
Thanks for the advice.
That will leave me running on a single core, right? I guess I can live with that for a while...

---

### Post by uberlube on 2008-02-26
Why not try to reinstall your wireless driver? This is a very good howto: to use the ndiswrapper

[http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper)

---

### Post by sgt.peppa on 2008-02-27
I am having the very same problem with the same laptop.

Noapic works for me. 

What exactly are the conquences of using noapic? Is it true that i am down to one core with noapic?
 I still see two cpus, allthough i am not sure wether the process scheduling is still sane...

---

### Post by shemapi on 2008-04-10
noapic works really well for me too. Thank you.

---

### Post by royfeldman on 2008-05-26
I have a Dell XPS 1530 and have been experiencing the same problems with Gutsy.  noapic works for me, but I also would like to know if noapic deprives me use of both cores.

thanks in advance,

roy

---

### Post by Lacrimstein on 2008-06-08
On Gutsy noapic didn't deprive me of anything, except boot time was perhaps about 5 seconds slower. On Hardy, however, only 1 core is visible.

---

### Post by tasos044 on 2008-06-10
Ok guys. I think i have a clue why this is happening. The problem seems to be Wi-Fi Catcher button  provided by Dell. I don't know how it messes up wireless (intel 3945) but when I disabled it, wireless network in ubuntu (hardy 8.04) seems to work like a charm. Go to bios (F2 at Dell splash screen) on 'Wireless' go to 'Wi-Fi Catcher' and switch it to 'OFF'. After that, using no other workarounds (not even 'noapic' kernel boot option) I am able to connect to any Wireless network using the iwl3945 driver. 


I use Dell XPS M1530 with A08 bios

---

### Post by simonl2009 on 2008-06-17
I can confirm that turning the wi-fi catcher off works in ubuntu 8.04 running bios A07. I've been running with no problems without bothering with noapic or any of the other proposed solutions for a couple of days now, so I think it's fixed.

Thanks a million mate, I owe you one.

---

### Post by AndrewTheArt on 2008-06-19
I can also confirm that the following settings fix wireless on the Dell XPS M1530 with Ubuntu 8.04 Hardy Heron 

***** Downgrade to bios A07 from this website -  

[http://support.dell.com/support/downloads/previousversions.aspx?c=us&l=en&s=gen&SystemID=XPS_M1530&releaseid=R182442&vercnt=3&deviceid=14338&formatcnt=1&releasetype=BIOS&servicetag=&catid=-1&libid=1&impid=-1&osl=en&os=BIOSA](http://support.dell.com/support/downloads/previousversions.aspx?c=us&l=en&s=gen&SystemID=XPS_M1530&releaseid=R182442&vercnt=3&deviceid=14338&formatcnt=1&releasetype=BIOS&servicetag=&catid=-1&libid=1&impid=-1&osl=en&os=BIOSA)

(This requires you to boot into your Windows Vista install, however. Otherwise you need a DOS Boot floppy)

***** The Wifi-Catcher switched ON (turning it off may work for you, though)

If you're still using bios A08, adding **noapic **to the kernel boot entry of your choice may allow you to connect, but that's not  a guarantee. It seemed to work intermittently when I was still using that bios.

The big report for this issue is here - 

[https://bugs.launchpad.net/dell/+bug/190664](https://bugs.launchpad.net/dell/+bug/190664)

On an unrelated but important note, downgrading to bios A07 also fixes the jumpy touchpad issue.

---

### Post by AndrewTheArt on 2008-06-19
Can someone open a new page in the Community Docs for this laptop and post this there? It would help a lot of people.

(I need to create a Launchpad account)

---

### Post by simonl2009 on 2008-06-20
Looks like I jumped the gun a bit when I posted about the wi-fi catcher. I'm still getting the bug, but it seems less common now.

---

### Post by joatmon on 2008-07-03
Has anyone found a permanent solution to this?  My wireless was working flawlessly on 8.04 until the latest set of updates.

Thanks!

---

