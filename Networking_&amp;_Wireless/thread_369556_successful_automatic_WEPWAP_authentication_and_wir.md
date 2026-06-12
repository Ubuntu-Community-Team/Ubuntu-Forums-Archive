---
title: "successful automatic WEP/WAP authentication and wireless access, but no internet"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by dominik.margraf on 2007-02-24
I have just helped my friend to install Ubuntu Feisty Herd-4 to his Fuijtsu Lifebook S7011 laptop, which has the IPW2200 driver (I think, since when I invoke lsmod, the ipw2200 module is shown to be loaded)

The installation went smoothly, it detects the WEP 64/128 bit encryption at his flat and correctly asks for the hex passphase.  We entered the passphase and everything went well.  We have successful web access to both the router and the ADSL modem before the router (and also successful ping).  This means successful wireless connection.

However internet access becomes a problem, although the ping program can figure out the IP address of most websites, such as:

[www.linux.org](www.linux.org)
[www.slashdot.org](www.slashdot.org)
[www.microsoft.com](www.microsoft.com)
[www.openoffice.org](www.openoffice.org)

etc.

but no packages went through.  Then I go to the firefox and tried, only a few websites ending with .org can be accessed (but unstable) and all other sites cannot be accessed.  Then I checked the network settings and it shows that the DNS are correctly detected (the wireless router and the ADSL modem). 

I am also sure that the MAC address would not be a issue and there are no soecific gateway settings or firewalls on the ADSL modem / wireless router because when I booted into the Windows XP installation in his laptop, the firefox browser can access to any website very quickly.

So what can go wrong here?  I haven't installed any extra package other than the automated installation by the Herd-4 live CD.  I can't anyway because the software update program (and/or synaptic) cannot get the repository information over the net and complains that there may be proxy problem.  Despite I am pretty sure that in both XP (which works) and Ubuntu installations, the proxy settings are correctly set to direct access to internet.  At the same time, computers of all of my friend's flatmate (who also use wireless network) have perfect wireless internet access.

Dominik

---

### Post by gradedcheese on 2007-02-24
sounds like a DNS problem, try replacing the contents of /etc/resolv.conf with:

```

search opendns.com
nameserver 208.67.222.222
nameserver 208.67.220.220

```

(ie: using opendns.org instead of the ISP)

---

### Post by dominik.margraf on 2007-02-24
I am going to ask my friend to change the DNS to the opendns.com ones.  However I remembered that when I tried to type in IP4 addresses directly to firefox, it still doesn't work.  So what else can you think of? (if I type in IP4 addresses directly, would DNS server matter any more?)

Thanks!

---

### Post by gradedcheese on 2007-02-24
yeah, if you know the IP address for a website, then it should have worked.  I'd turn off IPv6 (search the forum for instructions) in case that router handles it badly, but that shouldn't really be a problem.  If he can ping the router (and maybe access its web-based config page) then he should have access, as long as the router isn't stopping him.  On a side note, I have a problem with a certain Broadcom Ethernet card where unless I reload its module, I can ping and connect to anything on the LAN, but nothing beyond the router.  Very bizarre, but hopefully not similar to what he's dealing with.

---

