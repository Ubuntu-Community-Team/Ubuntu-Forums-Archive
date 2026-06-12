---
title: "ubuntu doesn't detect built-in bluetooth"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by currupipi on 2009-02-19
I've got a built-in bluetooth with that linux doesn't recognize and its led doesn't work. what should i do?that's what the terminal says:
jose@pepito:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jose@pepito:~$ hcitool dev
Devices:
jose@pepito:~$ hcitool scan
Device is not available: No such device
Thank you

---

### Post by egalvan on 2009-02-19
> **currupipi said:**
> I've got a **built-in bluetooth** with that linux doesn't recognize and its led doesn't work. what should i do?

Thank you

Some computers have a physical switch for built-in wireless network cards (Wi-Fi).

Perhaps yours has a switch for the Bluetooth?

Check the documentation.

---

### Post by currupipi on 2009-02-19
Yes. It has a switch next to the wifi one, but its led doesn't work, nad switching it doesn't change anything,what would you do next?tx

---

### Post by Fire_Chief on 2009-02-19
What kind of laptop do you have? (I'm guessing it's a laptop since BT is built-in.)
Also, what version of Ubuntu please?

---

### Post by currupipi on 2009-02-19
My laptop is an acer aspire1640z model zl9 and my ubuntu version is 8.10.

---

### Post by Jake24 on 2009-07-26
i have the same problem on a acer aspire 5720 have you resolved your problem yet?

---

### Post by currupipi on 2009-07-28
Sorry.I can't help you. Fact is that after spending like a week searching for solutions, I decided to open up the laptop only to find out that there was no bluetooth card whatsoever!Seems that bluetooth is optional on my model, and I bought it on sale, so...I printed the list of ubuntu's compatible-bluetooth models and took it to the store..It was cheaper than what I'd spent on coffee.(or a new logical problem-solving brain)

---

### Post by PhoHammer on 2009-07-28
> **currupipi said:**
> Sorry.I can't help you. Fact is that after spending like a week searching for solutions, I decided to open up the laptop only to find out that there was no bluetooth card whatsoever!Seems that bluetooth is optional on my model, and I bought it on sale, so...I printed the list of ubuntu's compatible-bluetooth models and took it to the store..It was cheaper than what I'd spent on coffee.(or a new logical problem-solving brain)

My USB bluetooth dongle was about $5 shipped. Works like a charm in all GNU/Linux 
distros I've tried it with.

---

### Post by brawd on 2009-07-29
I've recently had huge problems with similar laptops and have found out that Acer have had a recall out for these machines because the built-in BT and wireless link fails.

Check the website for further information,  but unfortunately I think the recall time might have expired.

regards,

brawd.

---

