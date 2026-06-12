---
title: "No wlan0 with DWL-650 PCMCIA card"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by JonnyTrombone on 2007-02-24
I'm new to linux, so please bear with me. I've been trying to get my D-Link DWL-650 Revision P PCMCIA card to work with Ubuntu Edgy. I believe the card is either prism 2 or 3 (there are conflicting reports).

I downloaded the windows drivers, added the .inf in ndiswrapper and set the driver to work with my PCMCIA card. When I do "ndiswrapper -l" in terminal, it shows 'netprism    driver present, hardware present' and I get no errors with 'modprobe ndiswrapper.'

But when I check iwconfig, I only get lo, eth0 (my ethernet card) and sit0 (modem). 

I'm not sure if there is any other information I can add- I'm using a Dell Latitude C600...

Any help would be greatly appreciated.

---

### Post by rhum on 2007-02-24
why do use ndiwrapper ,  

normally this card is natively recognized by ubuntu ( it was like that with dapper  )

did u try iwconfig before using ndiswrapper?

---

### Post by JonnyTrombone on 2007-02-24
I started off by trying iwconfig. I didn't see a wireless device- there or on iwlist. I found a page through google that recommended trying ndiswrapper (with the DWL-650 Rev. P card). 

No luck, so far...

---

### Post by lorpi on 2007-03-03
I have the same problem, but I didn't try ndiswrapper yet. With Dapper (6.06.1) the DWL 650 works fine and is nativly recognized, but with my 6.10 nothing. I tried to bring up the wlan-device with following command:

[INDENT][FONT="Monospace"]**Code:**
sudo ifconfig ath0 up[/FONT][/INDENT]

But no luck. *:(* What happened with the kernel? What's up with these guys. Why they are removing stable drivers?

---

