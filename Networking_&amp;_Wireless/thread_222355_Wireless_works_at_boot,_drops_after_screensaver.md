---
title: "Wireless works at boot, drops after screensaver"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by SishGupta on 2006-07-24
Hey I am new to ubuntu and I am having problems with my wireless.

This only started happening today.

I am using NetworkManager, my drivers are pci_ath for an atheros based wireless adapter that is built into my thinkpad, I have wpa supplicant installed and my router is encrypted with WPA2. Also i am running Ubuntu Dapper.

I start my laptop, login to linux. Then with nm-applet I connect to my AP. It asks for my key, and then I save it to keyring.
Wireless works.

Then I go away for a bit, screensaver is active, and the wireless drops and NetworkManager (or nm-applet) is asking for my wpa2 key again. I enter it and NM tries to connect again but it does not. I get one of the 2 green dots for nm-applet and then it just goes to a disconnected icon.

If I restart keyring asks me for the password, and nm-applet gets one icon but never gets to two and it disconnects again. 

To connect i must delete from ~/.gnome2/keyrings/keyrings.default and then reboot. From there the whole process beings again.

The odd part was this was not hapening yesterday (or since install) and AFAIK I have not made any wireless changes.

I dont think i am using madwifi drivers as I figure if its not broken don't fix it. Well its broken now, should I try switching? Does any one know how i can fix this?

Thanks.

The router is a D-link di-524 if it makes a difference.

---

