---
title: "SMC Wireless Card causes hang at boot"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by SmileyMike on 2007-02-10
Hi,

I'm new to Ubuntu. Just installed 6.10 on P3-550. Runs fine with my wired network card. When I add my SMC EZ Connect Turbo 22Mbps Wireless PCI Card (SMC2402W) to the hardware configuration it causes the system to hang during boot (after 3 bars of progress). Removing my wired network card and trying with only the wireless card installed did not resolve the problem. I got the same results when trying to boot from the Live 6.10 installation CD. Trying to boot from the 6.06 Live CD also hung. When I removed the wireless card the system booted without any problem. 

Can anyone suggest how to get my wireless card working with Ubuntu? 

Thanks,
Mike

---

### Post by gradedcheese on 2007-02-10
That sounds like a hardware problem to me.  You might find some information as follows: try to boot with that card in and fail, power off, remove the card, and boot properly.  Now check your dmesg log files.  They are named like this:

/var/log/dmesg
/var/log/dmesg.0
/var/log/dmesg.1
(and so on)

Basically the last few boots should be there.  dmesg starts with really basic stuff (finding how much RAM there is, asking the BIOS basic hardware questions, etc).  Compare the 'good' boot with a 'bad' one (I think they are numbered newest to oldest, ie dmesg is newer than dmesg0 and so on).  The later logs are compressed (dmesg.2.gz) and you can uncompress the log before viewing it ("sudo gunzip /var/log/dmesg.2.gz") if needed.

Basically you're looking for some error message that will hopefully shine some light on the situation.

---

