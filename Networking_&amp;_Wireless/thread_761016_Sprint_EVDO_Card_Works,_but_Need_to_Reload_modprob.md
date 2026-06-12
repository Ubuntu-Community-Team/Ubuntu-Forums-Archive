---
title: "Sprint EVDO Card Works, but Need to Reload modprobe?"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by jbentham on 2008-04-20
Hi all,

I've got a Sprint Pantech PX-500 that works great on my Gutsy installation of Kubuntu, but I'm having just one problem with it:

Here's where I'm at.  I followed the Sprint Mobile Broadband guide for Linux at [http://support.sprint.com/doc/sp10782.xml?id16=evdo_linux#2](http://support.sprint.com/doc/sp10782.xml?id16=evdo_linux#2).  Since it's written with Ubuntu as an example, it was very easy to follow and my card worked the first time.  Per the guide, I did the following:

sudo modprobe -r usbserial

sudo modprobe usbserial vender=0x106c product=0x3702

Then inserted the card, configured kppp as indicated in the guide and it connected perfectly.

The only problem I have is when I reboot - I need to redo the modprobe commands to get it working again.  When I run kppp and 'connect' after a reboot, kppp says it is "Initializing modem..." and the log window reports "Expecting: OK".

I've read several posts that suggest adding 'usbserial' in the /etc/modules so that it loads at boot time; i've done this, but the modem still hangs in the same place.

I've also run 'depmod -a' after the modprobe commands to rebuild the dependency table, but still no permanent fix.

Any ideas would be greatly appreciated!

---

