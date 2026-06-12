---
title: "&quot;Too Much Work for IRQ10&quot;"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by Wraith's Hand on 2007-11-17
During the last couple of days I've been noticing a particular problem, namely, that I'm getting an error message when I start up that states something to the affect of "Too much work for IRQ10."  Ubuntu will load just fine, save that I cannot seem to connect to the network.  It will appear that I'm connected, for instance I can see the signal strength, but when I try to load a web page or connect to Pidgen, I will get error messages.  If I restart the computer sometimes it will go away; however, it seems to take more and more restarts to get it up and going.  Any suggestions on how to fix this problem?

My specs are: 

Intel Celeron Processor 2.60 gHz
1 Gig of RAM
Ubuntu 7.10
the device manager lists my wireless card as "AR2413 802.11bg NIC"

ETA: A friend of mine believes that the problem might be the wireless card is going bad.  How do I test this?

---

### Post by Wraith's Hand on 2007-11-24
A strange update.  Now my wireless card is still working and is no longer having problem that I mentioned; however, I am still getting that error message.  I looked up what IRQ 10 might mean, and it appears that IRQ10 is often used for networking and sound, but both of them seem to be working fine.  How do I tell what IRQ10 is set up for on my computer?

---

### Post by moshuptrail on 2008-02-08
I am getting this same error in Gutsty.  At first I suspect it may have something to do with the internal Broadcom wireless card.  But the message looks like:
serial8250: too much work for irq10
That looks like a serial port.  I can't disable serial ports in Bios.  
Anyone have any ideas on this?

---

