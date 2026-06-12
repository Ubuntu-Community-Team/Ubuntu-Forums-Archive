---
title: "Sudden System Hang when using Ubuntu 10.10"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by cheepan28 on 2011-04-28
Hi,

I just installed Ubuntu 10.10 on my PC yesterday. I observed that the screen, mouse and the keyboard (both PS/2) would hang after a while when I was installing Ubuntu. I had to reboot the PC a few times before getting the Ubuntu installed.

After installation, I still observed similar problem when I start using Ubuntu. I had tried to disabled Ubuntuone process from loading at startup but still unable to resolve the issue. I was prompted to upgrade to Ubuntu 11.04 but unable to complete the upgrade due to this problem.

I am new to Linux and Ubuntu. Can someone advise me on this? 

Thank you.

Regards,
cheepan28

---

### Post by mörgæs on 2011-04-29
Have you checked that you are using the newest BIOS? 

A memory test is also worth trying. Can be done from the Ubuntu CD.

---

### Post by cheepan28 on 2011-04-29
Hi mörgæs,

Thank you for the advise. Earlier before your reply, I had tried updating the ATI graphic card driver thru the Administrator -> Additional Driver menu. The driver recommended was [fglrx-amdcccle_8.840-0ubuntu4_i386.deb]("http://my.archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.840-0ubuntu4_i386.deb") . After I had downloaded and upgraded the driver, the system prompted for reboot. I rebooted but now, I can't log in. When the log in page is reached, the mouse will hang and will not respond. I had rebooted > 5 times and it is still the same.

As what you have advised, I also ran the Memtest86+ v4.10 and it passed. I also flashed my Asus P7P55D motherboard to the latest BIOS P7P55D-ASUS-2003 but still does not resolve the problem.

Is there anything else that I can do?

Thank you.

---

### Post by mörgæs on 2011-04-29
Try a fresh install of either 10.10 or 11.04 with only the open source drivers. Don't add anything for the graphics card, even if Ubuntu suggests it.

---

### Post by cheepan28 on 2011-04-30
Hi mörgæs,

After my last message, I went into Recovery Mode and selected Repair Package. The system ran the whole night until this morning. After that (still within the command prompt recovery mode), it prompted to download and upgrade on certain packages. I went ahead with it and rebooted the PC after it finished. It got worse, my PC won't even boot until the login screen. It showed a black screen with many error messages.

So, I had no choice but to reinstall Ubuntu 10.10 fresh this morning. Again, the mouse and the keyboard (both PS/2) would hang after a while. I was thinking whether would it be better to use the USB port for the mouse and keyboard instead of PS/2. So, I got a PS/2 to USB converter for them. As of now, my mouse and keyboard are still functioning after 30 minutes of usage. I will continue to monitor a little while more before I jump to any conclusion.

Thank you for the advise. I really appreciate it.

Regards,
cheepan28

---

### Post by mörgæs on 2011-04-30
You are welcome. Write again, if the system shows problems.

---

### Post by cheepan28 on 2011-04-30
Hi mörgæs,

The mouse and keyboard froze again after about 1.5 hours. I disconnected the keyboard & mouse USB connector and reconnect it again. The keyboard and mouse are functioning again.

I guess I will live with this problem for a while. But it is still better when I was using PS/2. I will continue to search for the solution. If you think of any idea, do let me know.

Thank you.

Regards,
cheepan28

---

