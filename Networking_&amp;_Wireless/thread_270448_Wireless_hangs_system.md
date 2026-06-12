---
title: "Wireless hangs system"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by dnel on 2006-10-03
Hi, I'm looking for a bit of a direction in resolving this problem.

I have 2 usb wlan cards, a Gigabyte which I think uses an RT25 chipset and a newer Edimax which has an RT73 chipset.

The RT25 did work for a short while while testing but I wasn't intending on using this with the system. The RT73 wasn't supported out-of-the-box like the RT25 and I had to compile the driver from Ralink which I did sucessfully. Now both card detect and the driver claims them ok but when I try to change my wireless network settings like SSID and WAP key (I changed my router), the computer will hang dead requiring a hard reset.

Because of the hang I am unable to find any diagnostic information in logs that I've found. What puzzles me is what might be causing it as it is with two completely different wlan cards, two different drivers, the first being supplied with the standard kernel image. So I assume the problem must be to do with the common wireless subsystem.

Can anyone suggest a cause or resolution?

Thanks,
d.

---

