---
title: "HELP! Kubuntu Edgy, Asus A8Js, can't establish wireless connections"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by meldroc on 2006-12-28
HELP!!! ](*,) 

I cannot get any wireless connectivity in Kubuntu!  I tried firing up the wireless connectivity GUI tool that comes stock with Kubuntu (I haven't had connectivity, so the system's very much stock off the install CD,) and it will see nearby access points, but when I try to connect to any of them, even those that are completely open (like those at coffee shops), it says "Connection failed."  It's constantly bitching about not having root permissions, even though I run it from a shell prompt with sudo.  It's bitching about not being able to write to /etc/resolv.conf, and last time I checked, there is no such file (why doesn't this file exist?)

I started off attempting to connect at home, and theorized that it was because I had locked down my router, and haven't figured out the incantations required to get WEP working.  So I tried it in a coffee shop with open wi-fi, and can't connect there either.  My computer's pretty much crippled if I can't find net access.  I may have to resort to plugging it into the router with a CAT5 cable (how quaint.)

I'm running pretty much a stock kubuntu install, using the AMD64 install CD (whee, 64-bits! 8)  ) and haven't had the chance to do much of anything at all with it.

HOW DO I MAKE WIRELESS WORK???  It's an Intel chipset inside this laptop (Asus A8Js with 2GB RAM, 100GB 7200RPM hard drive, Bluetooth, 2GHz Core 2 Duo,) and it sees the adapter, and the wireless tool can see access points, so I don't think it's a compatibility problem.  It also isn't bad hardware, because it works in Windows (I'm dual-booting.)

What am I doing wrong?  Maybe there's a better wireless GUI tool that I can use?

Gotta love new computers - it takes me a couple of weeks of tinkering before I'm happy with it...

---

### Post by meldroc on 2006-12-28
Bump...

Turns out I'm using WPA, which is making things into a total god-forsaken pain in the ***.

I googled a few places, and as it turns out, none of the GUI tools work.  All of the sudden, I'm editing twenty different config files in /etc, have to edit twenty different config files, generate long strings of license plate numbers using wpa_passphrase.

What a nightmare!!!!  I was able to get this exact same wifi card working with this exact same router, with WPA, in 30 seconds in Windows.  I clicked on my access point, typed in the pass phrase, and it Just Works.

How do you do the same in Linux?

---

### Post by meldroc on 2006-12-28
OK, I finally found that kwlan speaks WPA, and once I installed and configured that & rebooted, it Just Worked.  Yay!!!

Edit.  OK, I discovered knetworkmanager.  USE THIS PROGRAM.  It does a far better job of setting up your wlan in a way that Just Works than anything else.

---

