---
title: "Novatel XU870 doesnt work after using in Windows"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by dymo0815 on 2008-03-22
Hi Forum!

I need some help. I've used a Novatel XU870 without any problems on my DELL Noebook with Ubuntu 7.10 running on it. After some weeks a good friend has buyed also an XU870 and runns with Windows. He got some trouble so I have helped him. After some configuration poblems with vodafone mobile connect and mwconn I found the problem and correct it. Sadly I've checked his installation also with my XU870. Now both cards runns with Windows perfectly but none with ubuntu. 
I've tryed kppp and umtsmon but no chance to connect to internet.
My provider is "blau" (same settings like e-plus) 
The Firmware on the card is 101.9 like before as it works fine.
The issue is: On plug, the card flashes red, after at+cpin=xxx it lit steadly red. So it don't log in to the provider. 
When Windows is running with VMC9.24: after at+pin=xxx it lit for a view seconds red and the flash blue for two times. 
What can be wrong? What is the AT- command to tell the card for login to the provider? 
I know it must be only a small thing using an similar AT command but i did'nt find it.
The command at+cops=? for searching will freeze the card.
Please help.

Best whishes and happy easter.

dymo

---

### Post by dymo0815 on 2008-03-23
Hi Forum,

I've got a workaround in my case.
I've installed VMware Server on my LT an setting up a Windows XP installation.
On that virtual Windows I've installed the Vodafone Software cause I was able to route the XU870 through the USB connector to my virtual Windows.
Now I was able to initialize the card and connect to the Internet. 
If I close the Software, the card will be disabled. If I pull out the card after disconnect and close the software after, it will be belive activated. Then I'm able to use the card in Ubuntu with kppp. I can live with it, but I'm always interested about the AT-command for activate / deactivate the card and setting up the hardware compression rate I can setup in the vodafone software.
I will happy if anyone know about of it. 

Thanks in advance,

Dymo0815

---

