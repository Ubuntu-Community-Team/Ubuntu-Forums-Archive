---
title: "error message xsane"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by coolyus on 2010-04-20
Tried to open xsane, message read " invalid argument " need a specific fix.

---

### Post by polly1 on 2010-04-21
Hi coolyus

Not all Scanners work on Linux. Please see if your Scanner is listed on this link [http://www.sane-project.org/sane-mfgs.htm](http://www.sane-project.org/sane-mfgs.htm), and post the result together with full Model details to me, even if not listed.:guitar:

---

### Post by manoriax on 2010-04-21
Yes, it would be very nice to know, which scanner you are trying to use in particular.

---

### Post by dantalion23 on 2010-05-11
I'm having the same problem with an Epson Perfection V200 Photo. When I run xsane it starts okay but as soon as I press "acquire preview" it gives me the message:

Error: Failed to start scanner: Invalid argument.

I have been through all the steps I used to get the scanner working under 8.04 and 8.10 involving /etc/udev/rules.d/45-libsane.rules, /etc/sane.d/dll.conf, /etc/sane.d/epson.conf, epson2.conf and epkowa.conf.

One thing that does seem strange is that under User Privileges there is no reference to scanners and I had to add the scanner group manually.

---

### Post by dantalion23 on 2010-05-14
I have solved my problem. Several fora refer to downloading drivers from Avasys at:

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

I had already downloaded one driver but, since I don't usually scan from within GIMP, I assumed I didn't need the "plugin" driver. When I downloaded that driver iscan and xsane both started to work.

It's been a long and frustrating process but my scanner now works with 10.04.

---

