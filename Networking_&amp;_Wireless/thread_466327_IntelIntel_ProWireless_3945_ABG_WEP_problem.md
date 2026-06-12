---
title: "Intel
	

Intel Pro/Wireless 3945 ABG WEP problem"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by durrell on 2007-06-06
Yes I'm aware there have been several issues concerning this very network card, but I wasn't able to find anything concerning the WEP. Only people having issues with their card not being found. Well, my card is fine..it sees all the networks around me, but it won't connect to my wireless network using WEP. I did disable WEP to make sure it would connect without the key, and sure enough..it connects just fine without using WEP. Any ideas?

I'm sorry in advance if I overlooked any posts concerning the same subject. Any help would be greatly appreciated, as I don't want to leave our network unsecure for long..there are plenty of people around my house that would mooch off of it I'm sure.

Thanks!

---

### Post by DagMan on 2007-06-06
Have you tried clicking on the manual configuration option and then adding the wireless info there?  Don't forget to check that your DNS settings are filled in too.

---

### Post by durrell on 2007-06-06
Well I'd try that but for some reason now it won't even see the card anymore. It shows the restricted driver and even shows the card in the hardware list but Wireless isn't an option in the networks area.

Any ideas? :(

---

### Post by durrell on 2007-06-07
I did a fresh install, installed all of the updates and everything. The card was working at that point. I had no sound, though. I then went in and did the boot/grub/menu.lst change and added "acpi=off" in 2 seperate spots to fix my sound. That's when it hit me. My wireless stopped working when my sound started working. So, I edited the "acpi=off" back out of my menu.lst file and voila..card was back and it was working, although my WEP problem still stands.

With the fresh install, though..I got my sound and wireless to both work without the "acpi-off" entry, so I can deal with that. Still looking for an answer to my WEP problem, though.

---

### Post by dummy92 on 2007-06-13
Hi Durrell,

While I'm not certain if this will help, I just got my wireless connected. I have a Dell Inspiron e1505 with the pro/wireless card. When It tried connecting in the past it would take the password, try connecting, and keep asking again and again for the password. Well, as it turns out, I had the dropdown box set on "128 bit passphrase" - except I'm only using 128bix hex. So I changed the drop-down to 64/128 bit hex, entered my the 26 digits, and connected! I'm really not sure if your solution will be that simple, but maybe it's just that. Hope it helps!

-Jeff

---

### Post by Glennjamin on 2007-06-13
> **durrell said:**
> I did a fresh install, installed all of the updates and everything. The card was working at that point. I had no sound, though. I then went in and did the boot/grub/menu.lst change and added "acpi=off" in 2 seperate spots to fix my sound. That's when it hit me. My wireless stopped working when my sound started working. So, I edited the "acpi=off" back out of my menu.lst file and voila..card was back and it was working, although my WEP problem still stands.

With the fresh install, though..I got my sound and wireless to both work without the "acpi-off" entry, so I can deal with that. Still looking for an answer to my WEP problem, though.


wait can u talk me through that step? I'm having problems connecting here.:o

---

