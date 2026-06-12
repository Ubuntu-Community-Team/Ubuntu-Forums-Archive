---
title: "HP nc6230 embedded and wireless"
date: 2005-04-20
forum: Networking &amp; Wireless
---

### Post by Crimson Tide on 2005-04-20
I have new HP nc6230 laptop with Broadcom NetXtreme and Intel Wireless.  I am not concered with the wireless at this point.  However its causing me trouble, I suspect.  I have had good luck installing Debian 3.1 from the netinstall CD so I know the tg3 driver works and I know the card is good.

I am still running the installed 2.6.10-5-386 kernel.

During the install the installer asked me about my primary interface being down, the wireless, I told it to use eth1 my Broadcom and use the tg3 driver. Soooo everything appeared to go great from that point on. Upon boot my broadcom does not have a link light, making me think its diabled.  I review the BIOS and its not, boot into XP and  it works.  If I do a System > Admin > Network settings it tells me that eth1 is active.  Since the link light is out I did not holding my breath.

I have disabled bluetooth and the wirelss nic in the bios with hopes to resolve this, but nothing has worked.  

Not sure where to go from here.

Thanks in advance.

---

### Post by Crimson Tide on 2005-04-20
Freaking cable came also.

Colour me a dummy.  I checked that earlier but missed it.

 ](*,)

---

### Post by Psyklops on 2006-06-26
Have a look at the sofpaq update from HP listed here:
[ftp://ftp.compaq.com/pub/softpaq/sp30001-30500/SP30429.txt](ftp://ftp.compaq.com/pub/softpaq/sp30001-30500/SP30429.txt)

You'll note that the new SoftPaq address intermittent issues with the Broadcom NIC under linux:
> 
FIXES:
- Provides solution for intermittent issue where the integrated NIC is not
  listed in the Device Manager.


The SoftPaq can be downloaded from here:
[ftp://ftp.compaq.com/pub/softpaq/sp30001-30500/SP30429.tar](ftp://ftp.compaq.com/pub/softpaq/sp30001-30500/SP30429.tar)

---

