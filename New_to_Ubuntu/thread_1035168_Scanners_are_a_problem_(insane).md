---
title: "Scanners are a problem (insane)"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by MickAld on 2009-01-09
Back again following a few days fiddling with the system and I now have two more related problems.

The first is I have an Epson Stylus Photo RX560 connected to one of my usb inputs and the printer is recognised but the scanner portion is not. When I run sane it looks for a scanner but reports no scanner found.

So I thought about it for a while and then decided to connect a dedicated scanner that was sat in my 'reserves' which is also an Epson but Perfection 2580 Photo. Now sane says 'cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin. Edit the firmware file entry in snapscan.conf.

Sounds straightforward enough until one looks for /snapscan and you find it doesn't exist. Clearly I need to get some drivers and config stuff downloaded and installed but going to the sane website is a nightmare. Despite finding that both devices are supported at 'good' level, any attempt to click in the links produces a website written in Chinese and a lower message written in English stating that the URL is not recognised. 

Even the information provided by Sane is confusing as it says in one place the support is good and elsewhere it says basic. 

What I really need is a simple step by step procedure to obtain the correct files for my computer to recognise and access the scanner features. Can anyone help?

---

### Post by richg on 2009-01-09
Spend some time searching the Beginners, Hardware, maybe Community for scanners, Epson scanner etc. I and others have done that and found a solution. I did that for my HP 2210 all in one. Consider it a learning experience or OJT, On The Job Training.

Rich

---

### Post by MickAld on 2009-01-09
As I understand it, HP scanners are well supported in Linux but I am not so sure that Epson have the same committment. I did find some stuff about directly downloading drivers but the link went off to AVASYS and then I got lost again. I really am a bit tentative about doing some of the things, being a newby at all this and really need some simple step-by-step guidelines. However thx for the idea, I will pursue it.

---

### Post by MickAld on 2009-01-10
Well I have fiddled about, and found some stuff, and now my Sane recognises my scanner (the combo one in my RX560) but I get a message saying Error during CMS conversion: Could not open scanner ICM profile.

It seems to get more cryptic but I went into Xsane preferences and disabled colour management. Now I don't get the warning, However at one point last night I also had displayed another three windows, one of which gave me a preview of the item to be scanned. Now it has disappeared. 

Does anyone know what I need to do to sort this out?

---

### Post by MickAld on 2009-01-10
You have to laugh don't you? :o I have been neroing away and suddenly was inspired to see if a later version of Xsane was available and going into synaptic I noticed that sane was not installed. So I installed it and now I get the colour (I am ENGLISH) business, Now, apart from a minor issue, I need to learn how to use sane to its potential.

The minor issue is that I tried to access the items under help labelled backend.doc and available backends and get a message that says

file:///usr/share/doc/xsane-common/html/sane-backends-doc.html (or similar) does not exist.

Can anyone enlighten me?

Oh and one minor item, According to sane website it says there is a version update 0.996 but mine is 0.995. How do I get the latest version?

---

