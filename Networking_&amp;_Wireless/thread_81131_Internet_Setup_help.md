---
title: "Internet Setup help"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by flux0 on 2005-10-23
I installed Ubuntu today.. so far so good, everything is good and whatever i had a problem with, i was able to fix through searching these forums! :KS 

Anyway, a problem i can't seem to fix is my internet.

I'm on a Toshiba Tecra 8000 Laptop (yes i know old) .. I have a 3com Megahertz PCMCIA Card (Megahertz 3CXEM556, LAN + 56K Modem (dual))

I have a computer which im using right now, my internet works fine, when i plug the cable into my laptop and try to configure it, it doesn't work.

Here is output from "cardctl ident" (it seems to recognise my card, and there IS a eth0 interface)

```

Socket 1:
    product info: "3Com", "Megahertz 3CXEM556", "LAN + 56k Modem", ""
    manfid: 0x0101, 0x0035
    function: 0 (multifunction)

```

this is my output for the eth0 section from ifconfig:

```

eth0	Link encap: Ethernet  HWaddr 00:00:86:36:7B:78
	inet6 addr: fe80:200:86ff:fe36:7v78/64 Scope: link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
	RX packets: 0 errors: 0 dropped: 0 overruns:0 frame:0
	TX packets:97  erros:0 dropped:0 overruns:0 carrier:44
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 b) TX bytes:15672 (15.3 KiB)
	Interrupt:3 Base address: 0x300

```

localhost ing works fine ..  output for ping yahoo.com:

```

ping: unknown host yahoo.com

```

i might be forgetting a few things.. but i have tried PPPoE with no success. 

I have entered the DNS addresses myself and configured eth0 to DHCP from the menus but still didn't seem to work.

any suggestions? 

I searched the forums but i couldn't find anything that really matched my problem.

Im going to carry on trying for myself tomorrow (sleep time now) .. but i'll appreciate any suggestions.

---

### Post by jasmuz on 2005-10-23
Did you notice in your output of ifconfig that your Eth0 dosent have an IP assigned,...dude, that is your issue.

---

### Post by flux0 on 2005-10-24
but it's supposed to be automatic (DHCP), when i plug my modem in (cable) .. nothing happens? 

eth0 seems active from the menu and it's set to DHCP,
 first i had 2 DNS servers manually entered then i removed them too because my windows setting for the connection showed that it should assign them automatically too.

:confused:

If anybody needs anymore info just ask.

---

### Post by flux0 on 2005-10-25
I tried the same connection on Windows and it worked.

I had to reset the modem though .. 

and this should be in the Ubuntu 5.10 forums

---

### Post by flux0 on 2006-07-26
Bump .. 

somebody please help me with this.. 

I started using my old laptop again today.. but i realised i can't use my PCMCIA ethernet .. :(

What do i need to do for it to work? 

I've tried many things.. i know the driver for this card is "3c589_cs.ko" .. which is loaded, but it's still not working!

---

