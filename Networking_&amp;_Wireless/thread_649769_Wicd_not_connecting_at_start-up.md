---
title: "Wicd not connecting at start-up"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by AndyC_772 on 2007-12-25
Hi all,

I have a new Acer laptop which has an Atheros AR5006EG wi-fi card, which I'm using via ndiswrapper, with Wicd 1.3.1 as connection manager.

My wireless network has a hidden SSID and uses WPA-PSK encryption. I can connect manually to the wireless LAN and it works fine - the only problem is that when I reboot the PC, it doesn't reconnect automatically.

To reconnect, all I have to do is click the Wicd tray icon, click 'hidden network' and fill in the SSID of my network. My WPA password and IP settings are retained.

I have another laptop with a Broadcom wireless card (Dell Inspiron 8200) and the same version of Wicd, and that works fine.

Any ideas why the Acer doesn't connect automatically at start-up?

Ta,
Andy.

---

### Post by chalewa on 2007-12-25
im guessing it is because the network essid is hidden and wicd isn't scanning for networks that are hidden to connect to...

---

### Post by AndyC_772 on 2007-12-26
It sounds plausible, except for the fact that I have another laptop running the same version of Wicd which does connect reliably to the same network at start-up. So, either they're configured slightly differently somewhere, or it's a difference relating to the network card (Atheros vs Broadcom).

---

### Post by trooperchix on 2007-12-26
...it's a card issue...

---

### Post by imdano on 2007-12-26
I believe this is an ndiswrapper problem.  Hidden networks don't show up in iwlist scan until the essid of the network is entered manually.  It's sort of on the back burner right now, as there are other bug fixes and features that are a little more pressing, but I've been working on a workaround that might allow wicd to connect automatically even though the network doesn't show up.  Basically It'd make wicd go through all the networks listed checked as "connect automatically" enter that essid into iwconfig, then scan and see if the network appears.  It'll be a little bit difficult to get working since I can't actually test it myself, so it may be a while before it gets released.

---

### Post by AndyC_772 on 2007-12-27
So, is it worth trying to install and use madwifi instead?

---

### Post by imdano on 2007-12-28
> **AndyC_772 said:**
> So, is it worth trying to install and use madwifi instead?
If you want to give it a shot,  and think you won't have a problem uninstalling and reverting back to ndiswrapper without working wireless, go for it.

---

### Post by AndyC_772 on 2008-01-22
Any update on this please?

It seems the card might actually be a 5007, not a 5006 - which means madwifi won't currently work without a rather cumbersome and unsupported patch.

---

### Post by AndyC_772 on 2008-01-26
I just bought a new laptop for myself too, an Asus G1S with Intel 4965AGN, and that has exactly the same issue. I've not touched the driver itself, which worked straight out of the box. Any ideas?

---

