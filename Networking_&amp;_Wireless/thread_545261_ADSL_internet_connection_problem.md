---
title: "ADSL internet connection problem"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by PabloG on 2007-09-07
Hello,
I am running Kubuntu Dapper on an IBM netvista machine, which dual boots with Windows XP.
When I run XP, I can access the internet using my ethernet connected Netopia 2240N ADSL modem.
I have tried to connect in Kubuntu, but have not had any success.
The ethernet card is recognized and is active, I have all green lights on the modem, (ethernet, dsl sync, internet, power), but I cant get online. When I try to run pppoeconf, it times out while waiting for my ISP's access concentrator.
I have pinged 127.0.0.1 and that seems to work, (although there seems to be no way of stopping this process once it has started. maybe I need to set a limit on how many tries it does, but I don't know how, and have had to resort to exiting the terminal to stop it), but when attempting to ping any other IP address, it says that it cannot connect.
I don't know if I'm missing something obvious, but I would love to get this machine online.
Please advise if I can  provide any more specific info that would help.

Thanks

---

### Post by ddrichardson on 2007-09-08
Pinging localhost isn't really helpful - BTW CTRL-C cancels ping or ping -c3 hostname pings it three times.

I'd look at the pppoe scripts and change the timeout value to something higher.

---

### Post by PabloG on 2007-09-11
Thanks for the help.
I can't figure out how to modify the timeout settings in the pppoeconf file. Can you advise me what I need to modify there?
When the pppoe process times out the message is "Timeout waiting for PADO packets", any idea what this means?

---

### Post by ddrichardson on 2007-09-11
Yes, its often cleared by a hard reset - find the little button on the back of the modem, you know the kind you need a paperclip to depress?

---

### Post by PabloG on 2007-09-13
I have tried the hard reset on the modem and still no change. Is there a specific way to do this? I tried pressing the button while on and while off as well as pressing and holding it in for a few seconds. The lights didn't blink or do anything to indicate that it had reset though. Is there anything else I can try?

---

### Post by ddrichardson on 2007-09-13
The manual for it says to hold down for 3 seconds to reset, there should be a change in lights, as the boot sequence for it shows a sequence of lights.

I would suspect though in this case that the modem is not being communicated with correctly by Ubuntu or at least the pppoeconf is not allowing enough time for a response. PADO is PPPoE Active Discovery Offer, and works much like DHCPOFFER/DHCPDISCOVER does with Ethernet modems.


The options should be in /etc/ppp/options

---

