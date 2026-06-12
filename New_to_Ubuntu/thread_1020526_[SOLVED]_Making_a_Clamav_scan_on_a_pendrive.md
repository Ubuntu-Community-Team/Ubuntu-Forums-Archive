---
title: "[SOLVED] Making a Clamav scan on a pendrive"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Azanatos on 2008-12-24
Hi! I'm a very new user of Ubuntu. Since I have also Windows Xp installed on my laptop, I decided to get an antivirus also for Linux.
I have installed ClamAV, and I would like to scan my pendrive and my portable USB device, but I don't know what is the command that identifies these devices to put in the terminal after *clamscan*.
Thanks a lot for your help!

---

### Post by oilchangeguy on 2008-12-24
you don't need anti-virus software with linux. read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Azanatos on 2008-12-24
> **oilchangeguy said:**
> you don't need anti-virus software with linux. read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

I know, I have read all the threads, Linux supersafe and so on :) ; but I still need an antivirus in order to check my usb devices before using windows on my laptop or in the one of my parents. But I'm not able to find how can I scan external devices.

---

### Post by LowSky on 2008-12-24
use the mount point usually something like

 /media/*name_of_pendrive* (you can alwsys find its name from what it mounts to as on your desktop or in Nautilis and going to the /media folder)

Using antivirus on linux mayu not be really needed but if he is downloading files from his ubuntu machine and then using them on the windows machine, then I understand why he may want the ability to scan a pendrive

---

### Post by oilchangeguy on 2008-12-24
> **Azanatos said:**
> I know, I have read all the threads, Linux supersafe and so on :) ; but I still need an antivirus in order to check my usb devices before using windows on my laptop or in the one of my parents. But I'm not able to find how can I scan external devices.
when you plug the usb device into a windows computer (before you open it), from my computer, right click on the device, and select scan using windows a/v software. there's no need for a/v on linux.

---

### Post by LowSky on 2008-12-24
> **oilchangeguy said:**
> when you plug the usb device into a windows computer (before you open it), from my computer, right click on the device, and select scan using windows a/v software. there's no need for a/v on linux.

Some viruses can autorun right from mount, so scanning them in Linux is a decent idea. Linux geeks need to get off there high horse with statement like "linux doesn't ever need antivirus"

Well it does if its a gateway to the internet PC for Windows machines, or in this case a person want to scan a pendrive for viruses before he hands them over to Windows users.

---

### Post by oilchangeguy on 2008-12-24
> **LowSky said:**
> Some viruses can autorun right from mount, so scanning them in Linux is a decent idea. Linux geeks need to get off there high horse with statement like "linux doesn't ever need antivirus"

Well it does if its a gateway to the internet PC for Windows machines, or in this case a person want to scan a pendrive for viruses before he hands them over to Windows users.

if one stays off the porn sites, and other places where the wicked virus' can be obtained, they won't be a problem. I've never had a problem with any of my windows boxes. that's not to say it's not possible. i'm just careful.

---

### Post by Azanatos on 2008-12-24
It works fine!
Thanks really a lot LowSky, I forgot the */media* thing. :)

P.S. Yesterday I got the virus Kamsoft.exe from the computer of my university (without antivirus). I just would like to avoid to infect mine too :) .

---

### Post by LowSky on 2008-12-24
No problem dont forget mark the thread solved

---

