---
title: "NIC removed caused problems."
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by gezerlis on 2006-11-20
I had for the last 4 months a **Realtek 8139** PCI NIC configured as **eth0** on my Dapper machine and no problem appeared. My machine has an on board NIC but I had it disabled from the BIOS. 

Three days ago, the administrator needed an extra card for another machine, so I removed my PCI card, I enabled the on board card, and booted Dapper. The network card was detected as **eth1** in the Networking tool (System => Administration => Networking), so I gave it the old IP address I had before. Everything worked just fine. 

When I rebooted the system problems started: no network interfaces where found so a lot of [COLOR="Red"][fail][/COLOR]s appeared in the boot sequence. So I struggled to find another NIC from old machines and found a **DEC 21140**. I disabled the on board NIC, booted Dapper, the Networking tool detected once again the DEC card with no problems as **eth2** this time, I configured it with ip/mask etc, but when I reboot the system it fails to load the card. I have to go to the Networking tool, choose the NIC and press on the Activate button every time I boot.

Thank you for your time, 
Spiros

---

### Post by dmizer on 2006-11-20
post the contents of /etc/network/interfaces and the contents of dmesg.

please contain dmesg inside [code] tags to make for a less cluttered thread.

---

### Post by FrodoB on 2006-11-20
Your original card's MAC identifier is tied to the device eth0 in:

/etc/iftab

You can edit this file and remove all of the references to any of the devices or you can tie one of the new cards to eth0 by editing this file.

I can't tell from your messages if this will resolve all of your concerns, but it will get things consistent again.

---

### Post by dmizer on 2006-11-20
> **FrodoB said:**
> Your original card's MAC identifier is tied to the device eth0 in:

/etc/iftab

thanks for that ... i've been looking for that one.

---

