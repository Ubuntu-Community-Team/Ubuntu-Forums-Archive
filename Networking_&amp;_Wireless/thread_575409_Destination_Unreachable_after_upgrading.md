---
title: "Destination Unreachable after upgrading"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by chamonix on 2007-10-14
Hi,
I'm having a problem similar to this one:
[http://ubuntuforums.org/showthread.php?t=34290]("http://ubuntuforums.org/showthread.php?t=34290")

In brutal detail, here's what I did:
1. upgraded system to Ubuntu 7.04
2. seemed to be working fine, was on the 'net
3. moved the PCMCIA (3com 3c574) ethernet card to the other PC card slot
4. networking died with problems reported below
5. rebooted; no changes
6. moved back to original PC card slot; still failed.

Basically, I'm seeing transmit but no receive packets when I view "ifconfig".  ARP does not seem to be working reliably. I'm getting destination unreachable from the NIC for my gateway, but I can successfully ping the NIC address.  There are "carrier: " errors at the end of the transmit line, but they don't seem to be growing at an alarming rate (substantially less than # of packets) and may be related to cable plugs/unplugs. 

To my eyes, mii-diag looks okay. I'm getting an error "interrupt(s) dropped" occasionally.  I checked /proc/interrupts (IRQ 3, pcmcia 0.0) and /proc/ioports (0x300, pcmcia_socket0) and they look fine. 

I also tried the following:
1. PC card in Windows laptop (works)
2. Cable in Windows laptop (works)
3. rebooting multiple times, ejecting the card, starting/stopping the /etc/init.d/networking
4. Viewing the arp table from my Windows laptop; one in a blue moon it has the arp entry for the offending NIC, but 90% of the time it doesn't.  Weird. 

The IP address is statically configured (I didn't touch that stuff).  I'm sure I may be missing something else obvious. Interestingly enough, when I run "tcpdump" I can see arp who-has requests going out, but I cannot see ICMP pings (maybe I'm not running tcpdump correctly?). 

This is an old computer so it's *possible* it's a hardware failure, but that's extremely odd timing, and it doesn't seem to be the card or cable since they worked on the Windows PC. I'd be more likely to guess the driver, but ethtool doesn't appear to work on this card. (Should it?)

Any suggestions? 

Thanks in advance.

---

