---
title: "Slow Samba Performance"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by Romanian on 2008-08-03
Hey all,

I'm using Ubuntu 8.04 Desktop edition on a small NAS of mine (I'm not proficient enough to use CLI), and I have it hooked up via Samba to my Windows laptop. They're both on 802.11, the server on G and the laptop on N, so I should theoretically be achieving speeds of 54mbps. That's not happening. I think I max out at about 65kBps. If you need any config settings to be posted or whatnot, I'd be glad to.

Anyone have any ideas?


Thanks,
Romanian

---

### Post by Romanian on 2008-08-05
Bump

---

### Post by dmizer on 2008-08-06
I suspect that you're getting average speeds. I'm not exactly sure how this is all calculated out, but bandwidth != file transfer speed.

Theoretical maximum bandwidth of 802.11b is 11 Mbps and that of 802.11g is 54 Mbps. In reality, the performance is usually 50 percent or even lower than the theoretical maximum.

Also, KBps (Kilobyte) != Kbps (kilobit)

According to Bandwith Place
> Bits per second: How communication devices (your wired network card) are measured. Kilo means 1000, and Mega means 1,000,000. Examples include a 56k modem and a 10Mbit ethernet.

Bytes per second: The way data is measured on your hard drive and how file sharing and FTP programs measure transfer speeds.  Kilo is 1024 and mega is 1,048,576.

So, when your bandwidth is 820.56 kilobits per second, your download will be 100.17 kilobytes per second.

---

### Post by cariboo on 2008-08-06
I have to say I find transfering files slower using samba shares than using ftp for the same server. Transfer via ftp run at approx 11000kbs as apposed to via samba 7600kbs.

Jim

---

