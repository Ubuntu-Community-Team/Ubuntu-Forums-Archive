---
title: "2 AR5005G, one works, one doesnt..."
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by weiln on 2007-02-15
I have a Acer Aspire 3680, 3 partitions: 1 Linux (Ubuntu 6.10), 1 Swap, 1 Windows (NTFS, XP Pro)

Until today, I had not installed Windows.  Everything was peachy including the built-in wireless card, AR5005G, according to Device Manager.  When I was installing Windows I popped in my PCMCIA card, it's an AirLink101, w/ AR5212 chip.  Installed Windows, updated Grub, all is good...not.

Now, whenever I try my built-in wireless card in Ubuntu, it doesn't work.  When I do "ifup ath0" it goes just fine, but never "finishes."  By that I mean it never gets back to the prompt, it stalls after "bound to 192.168.0.3 -- renewal in 285075 seconds".  Network manager shows it's working, but no websites ever resolve, just shows "Looking for www.google.com."

So I put the PCMCIA card, AR5212 in, and it works just fine.  Just for kicks, I throw in another PCMCIA card, a D-Link DWL-G630, and it works just fine too.  Then, I notice in Device Manager, its listed as the exact same chipset as built-in, AR5005G!  Now, what I don't understand is why the built-in was working fine until I installed Windows and used a PCMCIA card, and why it doesn't now. Also, why does the same chipset work just fine in the PCMCIA D-Link card, but not built-in?  What would cause the built-in to "stall" at ifup?

ath_pci is version 0.9.4.5 from dmesg.

Any ideas what would be causing this?

Thanks,
Nathan

---

### Post by weiln on 2007-02-15
Just to clarify, as I went to download and install the latest madwifi, this is what dmesg shows:

ath_pci: 0.9.4.5 (0.9.2.1)

As far as I can tell, this is the most updated version available.

Nathan

---

### Post by weiln on 2007-02-15
OK, nevermind.  I rebooted into Windows and then back to Ubuntu, and everything seems to be working just fine again.

Still, what would cause ifup to stall after "bound"?

---

