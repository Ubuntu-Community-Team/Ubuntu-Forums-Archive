---
title: "Printer problems"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by Mick1d on 2009-11-01
Since upgrading to 9.10 I can't get my Brother DCP 115c printer to work.  When I first changed to Ubuntu it was 9.04 and I followed a thread, downloaded drivers from the Brother Solutions Centre and my printer worked.  I have tried to do the same in 9.10 but when I try to unpackage the drivers I get a red error message which says incorrect architecture i386.  Any help would be appreciated.  I don't want to go back to Windows!

---

### Post by Temposs on 2009-11-01
I assume you're running 64-bit Ubuntu. You have two options.

1) Find a 64-bit version of the printer driver

2) Install 32-bit Ubuntu instead of 64-bit

maybe 3) Use a --force option on dpkg to make the driver package install, ignoring the architecture conflict.

---

### Post by Mick1d on 2009-11-01
Thanks for the response. Since posting, looking about the threads, I realised the drivers that I needed and had downloaded from Brother were available in Synaptic Package Manager. I downloaded and installed them through Synaptic and the printer now works fine. Problem solved, happy and relieved.:p

---

### Post by Oropher8598 on 2009-11-01
**Edit:** not quick enough... ;)
[s]From [http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#115](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#115):
> [s]
**I'm using an AMD64 bit version of Linux. Can I use the Brother Linux printer drivers?**

Yes. Our drivers are created and optimized for 32 bit version of Linux,
but those can be used for 64 bit Linux also. Some additional steps are required.

For dpkg users:
1. Install lib32stdc++6(Debian) or ia32-libs(Ubuntu)
2. Restart the system
3. Use "--force-architecture" option when you install the drivers.
4. After the driver installation, and if there is "/usr/lib64/filter/", copy the file which name starts with "brlpdwrapper" ( in the "/usr/lib/cups/filter/" ) to "/usr/lib64/cups/filter/".
Or confirm there are symbolic links between "/usr/lib/" and "/usr/lib64/".
[/s]
There are a few other solutions on that page to other possible issues on 64-bit.[/s]

---

### Post by yeats on 2009-11-01
You've *probably* already tried this, but have you gone through the "add a printer" dialog to see if any of the on-board printer drivers work?

---

