---
title: "[SOLVED] Linksys WRT54G not allowing 3 computers (Ubuntu, Mac, and Windows) to connec"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by bmeyer on 2008-07-25
We have a run-of-the-mill Linksys WRT54G wireless router.  My Ubuntu box never has any trouble connecting to it, regardless of how many other computers in the house are connected.

But, my sister just bought a Macbook Pro.  Whenever she is connected, another computer's (WinXP)internet will not work.  It establishes a connection with the router, but cannot load web pages.  When she's disconnected, the WinXP box works just fine.

Is there some incompatibility occurring when both the WinXP box and Macbook are connected at the same time?  Why doesn't the issue occur with my Ubuntu box?  I've tried various settings on the router the last few days and nothing works.

---

### Post by caljohnsmith on 2008-07-25
Is either the Macbook Pro or the Windows computer configured to use a static IP address (vs. using DHCP)? That could possibly cause a conflict like you describe. And when the Win XP computer does not work, can you ping the router from that computer?

---

### Post by bmeyer on 2008-07-25
> **caljohnsmith said:**
> Is either the Macbook Pro or the Windows computer configured to use a static IP address (vs. using DHCP)? That could possibly cause a conflict like you describe. And when the Win XP computer does not work, can you ping the router from that computer?

No, all the computers (& the router) are using DHCP -- I tried using static and assigned each one a unique IP, but that didn't work either.

I'll try pinging...

---

### Post by ModelM on 2008-07-25
Check the range of DHCP addresses the router has been told to assign. It may have been given an address range of only two addresses.

---

### Post by bmeyer on 2008-07-25
> **ModelM said:**
> Check the range of DHCP addresses the router has been told to assign. It may have been given an address range of only two addresses.

No, it has the full range of 192.168.1.100 and up.  Maximum connections is set to the default 50.

---

### Post by caljohnsmith on 2008-07-25
Try turning on "AP Isolation" in the router setup--that will prevent computers on the WLAN from communicating with each other; they will be able to communicate with the router/internet fine but they won't be able to "see" each other. I have a WRT54G too, and to do this go into your router's setup, hit the "Wireless" tab at the top of the web configuration screen, then select "advanced wireless settings" below that. You'll see "AP isolation" there. That will give a useful clue as to your problem I think.

---

### Post by ModelM on 2008-07-25
Have you tried swapping the cables between ports. I have a router here in a drawer which works fine, but has a bad switch. In mine, only one port is hot & the others are dead. Yours may have different symptoms, tho.

---

### Post by Jimbro727 on 2008-07-25
Are all three machines connecting wirelessly?

Perhaps it's an issue relating to the router scaling back to 802.11b when an 802.11b device connects, and the 802.11g devices aren't configured to connect to 802.11b networks?  It's somewhat far fetched, since this should all be transparent, but it's worth looking in to if nothing else mentioned works.

---

### Post by bmeyer on 2008-08-02
Thanks for all the suggestions.  I think I solved the issue...

The Windows box is still using DHCP while my Ubuntu box and the Macbook use static IPs outside of the DHCP block.  I had tried this earlier and it didn't seem to work at first, but all's well now.  I've read other sources stating that OSX seems to have issues with DHCP, attempting to use multiple IPs.

---

