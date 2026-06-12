---
title: "I have to disable and then re-enable wireless drivers after every reboot?"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2008-05-13
On my computer, I have a wireless card with an Atheros chipset (it's a D-Link DWL-G510).  When I start my computer up, I have to go into System>Administration>Hardware Drivers to get my card working.  When I first open Hardware Drivers up, it lists:

Atheros Hardware Access Layer (HAL)  (Checked Enabled, but "Not in Use")
Support for Atheros 802.11 wireless LAN card (Checked Enabled, but "Not in Use")

To get my card to work, I have to uncheck (disable) the second item listed, and then check it back off to re-enable it.  When I do this, the status of both items changes from "Not in use" to "In Use" and within a few seconds, the card works again and connects to my wireless router.

I have to do this every time I restart or turn the computer on after shut down.  I'd like to fix this so I don't have to do this every time I want my drivers to be used by the card.  Any ideas on how to fix this?

---

### Post by nixscripter on 2008-05-14
It sounds like the proprietary driver (which is probably a kernel module) is not being loaded at boot. If you can figure out which one it is, you can make it load at boot with a simple edit.

I don't know what it's called, and if you don't here's how you can figure it out. Before and after you enable the card, get a listing of drivers currently loaded in the kernel and see what was added. The command is: ```
lsmod
``` You will probably find drivers like **ieee80211** were also added, but they should all have dependencies on the Atheros driver.

Once you figure it out, you can add its name to the list of modules in **/etc/modules**. Hopefully, that will do it.

---

### Post by H2CO3 on 2009-01-27
Thanks! It worked for me... :)

-SMCWCB-G EZ Wlan Cardbus (Atheros 2413)-

---

