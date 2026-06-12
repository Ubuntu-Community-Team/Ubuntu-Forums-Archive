---
title: "LinuxDC++ connects to ADC hub but doesn't download"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by Arathon on 2008-03-31
I'm running 7.10.  I installed LinuxDC++ from a .deb, and it connects to any hub I want it to connect to.  However, while it would allow me to get file lists and download files from users on a campus hub which ran on the old NMDC protocol, it won't allow me to do either on the new ADC hub. 

LinuxDC++ uses the core of DC++, and my version should support ADC (and obviously allows me to connect just fine). 

Booting into Windows and trying it there - it works perfectly.  I should be able to connect as "Active" without inputting any settings.  As I understand it, Ubuntu doesn't have a firewall, so I don't understand why this won't work.  However, given that LinuxDC++ connects just fine, this seems like an Ubuntu issue more than an application problem.  Please help.

---

### Post by stevensheehy on 2008-04-02
> **Arathon said:**
> I'm running 7.10.  I installed LinuxDC++ from a .deb, and it connects to any hub I want it to connect to.  However, while it would allow me to get file lists and download files from users on a campus hub which ran on the old NMDC protocol, it won't allow me to do either on the new ADC hub. 

LinuxDC++ uses the core of DC++, and my version should support ADC (and obviously allows me to connect just fine). 

Booting into Windows and trying it there - it works perfectly.  I should be able to connect as "Active" without inputting any settings.  As I understand it, Ubuntu doesn't have a firewall, so I don't understand why this won't work.  However, given that LinuxDC++ connects just fine, this seems like an Ubuntu issue more than an application problem.  Please help.

Try it in passive mode and see if you can download from other active users. If you can, then you need to configure LinuxDC++ as active manually. If you are behind a router, then you have to configure the active settings on Windows or Linux regardless. Even if you're not behind a router or firewall, there's no guarantee that LinuxDC++ will automatically configure itself as active.

---

### Post by Arathon on 2008-04-02
No, passive doesn't work either.  Active and passive both work fine under Windows.  =(

---

