---
title: "need my brown ubuntu go wireless, here the details!!"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by Arijua on 2006-07-25
I have a Belkin router and a usb adapter netgear, what do I need to do to connect on my net and go internet?

I do not find any driver on the web for linux

---

### Post by tturrisi on 2006-07-25
What model adapter?

---

### Post by Arijua on 2006-07-25
WG111T by NETGEAR

---

### Post by tturrisi on 2006-07-26
Do you know the version # of the wg111t?  Apparantly Netgear made several versions of that adapter using 3 different chipsets, and knowing which chipset determines which drivers must be used.

---

### Post by ORF1000 on 2006-07-27
I got mine to work, but it wasn't that easy.  Needed to download and compile the latest version of ndiswrapper (the 1.8 in the Ubunt repositiories isn't good enough).  [Go here for instructions to download and install the latest ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

Dave

---

### Post by ORF1000 on 2006-07-29
One more thing about the WG111T -- you need to install both Windows drivers -- athfmwdl.inf and netwg11t.inf.

---

