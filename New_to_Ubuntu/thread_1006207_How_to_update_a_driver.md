---
title: "How to update a driver"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by Jon_Smith on 2008-12-09
Hi,

I have recently installed Ubuntu, I want to use the madwifi driver on my atheros wireless pci card but I am seriously struggling to do it,

I seem to be ok downloading the tarball, extracting it then doing the make, make install bit with no errors so I am fairly confident I have sucessfully installed the madwifi thing on it, I am stuck now when it comes to getting it onto my wireless card.

If I run iwconfig the card comes up as ath0 if that helps.

Jon Smith

---

### Post by igknighted on 2008-12-09
What atheros card do you have?  With 8.10, the handling of these chips changed rather dramatically, so make sure you have an up to date how-to.  If you are looking for an up to date how-to, see here: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros) ath5k wireless driver not enabled by default

---

### Post by Jon_Smith on 2008-12-09
I have a Netgear WG311T, it has an Atheros Chipset and was using an atheros driver under windows, but I want madwifi with Ubuntu.

Jon Smith

---

### Post by igknighted on 2008-12-09
> **Jon_Smith said:**
> I have a Netgear WG311T, it has an Atheros Chipset and was using an atheros driver under windows, but I want madwifi with Ubuntu.

Jon Smith

But why do you want MadWifi?  The driver Ubuntu uses is newer, and in most cases better.  Can you please post the result of 'lspci', and have you tried the solution in the link I posted?

---

### Post by Jon_Smith on 2008-12-09
I am interested in using it with the aircrack-ng suite, the madwifi drivers are the ones suggested on their site,

I think its to do with enabling monitor mode and packet injection.

I have not tried your solution yet as I am posting this at work, I will post the results of lspci when I have them


Jon Smith

---

### Post by Jon_Smith on 2008-12-10
Hi,

I couldn't get that help you directed me to, to work. I didn't really understand it.

my lspci was this
'01:01.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)'

---

