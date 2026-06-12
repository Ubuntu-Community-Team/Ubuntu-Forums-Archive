---
title: "No Internet connection"
date: 2004-11-08
forum: Networking &amp; Wireless
---

### Post by Fintan on 2004-11-08
Hello out there.
I installed ubuntu after kanotix with the kanotix grub pointing to the ubuntu partition. It boots and looks really cool, except for the fact that i don't get any internet connection. I configed the card as DHCP and it found the card but will not let me surf.

Any ideas would be appreciated.

Thanks
Fintan

---

### Post by Rancoras on 2004-11-08
These are just some quick thoughts from the top of my tired brain.

I assume it's a network card.  Which one?  Can you ping your DHCP server?  If so, then your card is fine.  From there, I would check to see if you can ping the IP address of yahoo.  If you can do that, then the problem is probably DNS related.  What are you using for your DHCP server?  If it's the same machine that provides the internet access, do you have it set as the default gateway?

I moved this thread to the networking forum, better fit.

---

### Post by Fintan on 2004-11-09
Hi Rancoras,

Thanks for the quick reply. It is probably not quite that complicated. I am not sure of the card (I am not sitting at the box right now). 
Any way i installed ubuntu behind winxp first and put its grub in MBR. Everything was fine except i didn't quite like the grub (sorry). 
So i installed kanotix and put its grub on MBR and reinstalled ubuntu with its loader on hdax. Pointed grub (kanotix) to hdax and ubuntu loads fine except now there is no more internet connection. When i config. the netcard as DHCP it sees it and says ok. But i still cannot surf, read mails or do apt-get/synaptic.
I would not think that it has anything to do with where the loader is but that is the only difference in the installs.

Any ideas?
Fintan

---

### Post by ashley_v on 2004-11-10
[QUOTE=][/QUOTE]
 You might want to try checking your dns settings.

cat /etc/resolv.conf 

from a terminal and see what you get.

---

### Post by arctic on 2004-11-10
if you are using a dsl-router, a dns-server-bug in the 2.6 kernel is the most problable troublemaker (=constant flooding protection by kernel, although there is no flooding). i am suffering from it, too. you can do two three things:
1.) reprogram the kernel in order to fix the ipv6/dns-server blocking problem,
2.) enter more dns servers into the resolv.conf and  rewrite that file in a ten-minute time circle (eys, it gets automatically overwritten!!!)
3.) install a 2.4 kernel. the 2.4 series does not have this problem. i opted for this solution and currently use a 2.4.27 kernel

---

### Post by Fintan on 2004-11-10
Okay I will try all that but why did it work when the ubuntu Grub was in the MBR and refused to work when GRUB was not? That is my question.
I did NOT change anything on during install except the placement of GRUB.
I am missing something.

Thank you anyway for your quick responses
Fintan

---

