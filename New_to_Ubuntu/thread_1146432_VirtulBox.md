---
title: "VirtulBox"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by augie2051 on 2009-05-02
When installing Vista in a Virtual box is it necessary to install an anti-virus on the virtual box as well if I will be using the virtual box to access the Internet?

---

### Post by Paqman on 2009-05-02
Treat your VM exactly like it's installed on real hardware. That means antivirus, firewall, etc.

---

### Post by Hospadar on 2009-05-02
It probably wouldn't hurt to scan it from time to time with clamwin or whatever.

It really all depends on what you're doing in the VM, if you're buying stuff on a credit card in internet explorer, than definately but if you're using office and occasionally looking something up, I'd say don't worry.

The VM itself is just as vulnerable as a normal windows installation, but it is extremely difficult to get access to data outside of the VM (this is the wet dream of a malware author as many important web services are hosted through vm's).

So if you're worried about your linux (host) installation, then I'd say stop worrying, but if you are worried about the windows (guest) installation being possibly infected, then you might want to install a scanner of the type that only scans when you tell it to (one that's always working in the background would probably grind your VM to a halt)

---

### Post by augie2051 on 2009-05-02
Thank you i wanted to be sure

---

### Post by swoody on 2009-05-02
Yup, as the others have said, your VM is basically a computer of it's own - which means AV, Firewall, etc. for Windows. My biggest reccomendation would be that if you are running Vista in a VM, to just use a browser in the Ubuntu host to surf the web, do online banking, etc. It'll be much safer than using the Windows VM. And if you do that, and you only use the Windows VM to lookup random little things now and again, I wouldn't be so much worried about an AV program.

---

### Post by augie2051 on 2009-05-02
Thanks for the advice everyone.  i only am using Vista as a VM because i have to use one program for school that requires Shockwave over the internet and to update my music for my zune.  Otherwise it wouldn't be necessary at all.  By the way dont bash me for the Zune it was a gift from my wife prior to my learning of ubuntu cant really get rid of now.

---

### Post by swoody on 2009-05-03
Sounds good! Since you're not going to be doing a lot of web surfing on the Windows VM, I would be a little more willing not too run an Anti-Virus/Anti-malware program at all. If you are downloading your music from a reliable source (i.e. cd's, iTunes) I wouldn't be worried at all. Your school program and a reliable music source aren't going to contain any viruses or malware. However, if you are downloading your music from a file sharing program (i.e. LimeWire, Shareaza, Napster, etc.) then I would be very concerned about viruses and malware as there are people out there who use those file sharing programs to distribute their crud to the world.

But that's just my $.02 - It's obviously up to you to make the final decisions about your personal computer :)

---

### Post by sneeks on 2009-05-03
as all have said,treat it as a pc on its own,unless it's just for testing the distro,and your not gonna be doing a lot or any web stuff.

---

