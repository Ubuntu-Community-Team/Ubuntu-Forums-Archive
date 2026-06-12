---
title: "Intel Pro 2100 Wireless problems"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by dcushion on 2006-11-13
I'm having some problems getting my wireless card working.  It seems like the card is not turned on (see screenshot below).  When I issue the "iwconfig eth1 txpower on" command I get "operation not permitted".  Any help anyone can provide will be greatly appreciated!

Dave

---

### Post by Stealth on 2006-11-13
Sorry for the obvious question but, did you run "iwconfig eth1 txpower on" with sudo?

---

### Post by dcushion on 2006-11-13
Hey Stealth,

Just tried that and I get "invalid argument" when I run the command.

sudo iwconfig eth1 txpower on

---

### Post by Stealth on 2006-11-14
You might want to try iwconfig --help to see how they want you to use the command.

But the Intel 2100 is suppose to be quite an easy wireless to get working. Do you have the actual hardware switch on? For instance, on my laptop (with a Intel 2200) I fold Fn+F2 and turn it off and on. Then checking iwconfig I can see the power off and on too. So make sure the hardware switch is on.

---

### Post by dcushion on 2006-11-16
Hi Stealth,

Just tried the hardwar power (FYI... this is a Dell Latitude D505 - toggle Wifi power is FN-F2).  No good.  Same thing.  ](*,) 

Dave

---

### Post by jsares on 2006-11-21
I'm having the same problem on a T41p with Intel Pro 2100. I think the problem is the system defaults to having the wifi and bluetooth turned off. I tried:

sudo iwconfig eth1 txpower on

but that didn't give any output and didn't turn the wifi on.

Any help?

---

### Post by jsares on 2006-11-23
Not sure what I did but after a reboot its working. I'm connected right now to a neighbors wifi. I'll have to get WPA support to connect to my network.

---

### Post by ingo on 2007-01-26
Hi dcushion,

sorry about late reply :)

Your card appears to be on as the system can see it. I have the same card on an IBM T41 and it runs successfully using knetworkmanager with wpa encryption.

Have you made any inroads yet?

---

### Post by dcushion on 2007-02-01
Well, I don't know what happened, but I installed Ubuntu 6.10 and my wireless problem disappeared!  I was so close to abandoning LINUX because of the problems I was having, but this has saved it from the recycle bin!

Thanks to everyone for their suggestions on getting this fixed!

Dave

:guitar:

---

