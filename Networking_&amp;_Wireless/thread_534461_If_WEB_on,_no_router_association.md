---
title: "If WEB on, no router association"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by carusoswi on 2007-08-25
Ok, I run a dual boot system, 7.04 and XP Pro.  I can configure my Belkin wireless adapter with XP to work with my router with WEP enabled or disabled.  In Ubuntu, if I enable WEP, the association is lost.  Please don't bother suggesting that I double check my security key, I have checked and rechecked it.  It is the same key I use to connect to the router through XP, so the key is definitely not the problem.

I have this same problem in ubuntu on two differenct computers using different adapters but accessing the same router.

Both computers dual boot, the other one uses XP Home instead of pro, and the router is a Linksys.

The exact same problem affects both computers in exactly the same way.  No security and accessing the router is consistently successful in either OS.  Enable WEP and ubuntu, while it detects the router under NETWORK, and allows you to configure it using the WEP key, no association is present when you open up a terminal and run iwconfig.

Can anyone help?

Caruso

---

### Post by Darkhack on 2007-08-25
Go into your router's administration page and change the encryption key from "shared" to "open".  It should continue to work on XP as well without needing any additional configuration on the Windows side.

---

### Post by carusoswi on 2007-08-25
> **Darkhack said:**
> Go into your router's administration page and change the encryption key from "shared" to "open".  It should continue to work on XP as well without needing any additional configuration on the Windows side.

Well, when I went into my router's settings page, the encryption key was already set to open.  There were two additional choices, shared and both.  I set it for both, and now Ubuntu is working fine on the net with WEP (not WEB as I typed it in my topic heading) enabled.

I've been living with this for so long, you simply cannot imagine . . . and I've posted more than once for help.  Thank you for sharing a suggestion that solved my problem.

Caruso

---

