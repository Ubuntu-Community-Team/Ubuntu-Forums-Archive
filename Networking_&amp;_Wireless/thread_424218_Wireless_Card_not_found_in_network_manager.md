---
title: "Wireless Card not found in network manager"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by SwaroopKunduru on 2007-04-26
Hi All,

Please see the attachments. I cannot see the wireless network card in the applet. I tried installing windows drivers and ndiswrapper but no luck. I request you to please help.

When I try to run Network manager with command I got the error. I included that in the attachments.

Please help me installing wirless on my Dell Inspiron laptop with NetGear card.

Regards,

Swaroop Kunduru.

---

### Post by stchman on 2007-04-26
> **SwaroopKunduru said:**
> Hi All,

Please see the attachments. I cannot see the wireless network card in the applet. I tried installing windows drivers and ndiswrapper but no luck. I request you to please help.

When I try to run Network manager with command I got the error. I included that in the attachments.

Please help me installing wirless on my Dell Inspiron laptop with NetGear card.

Regards,

Swaroop Kunduru.

I see your Broadcom card is a 44xx series.  I have a procedure for the 43xx series.

[http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)

If you have the Broadcom 44xx series .inf files you could modify the procedure for that family of chipsets.  I would substitute the .inf drivers in the scripts.

---

### Post by SwaroopKunduru on 2007-04-26
> **stchman said:**
> I see your Broadcom card is a 44xx series.  I have a procedure for the 43xx series.

[http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)

If you have the Broadcom 44xx series .inf files you could modify the procedure for that family of chipsets.  I would substitute the .inf drivers in the scripts.

stchman,

When I was working on 6.04 for some time(9Months) I installed ndiswrapper and was no problem in connecting wireless.

Brodcom card I have is for ethernet card right? I can work in wired network. My only problem is wireless.

I'll go through the link in your messages. Will it work for 44XXXX ?


Thanks and regards,

Swaroop Kunduru.

---

### Post by SwaroopKunduru on 2007-04-26
Hi All,

Somebody? Any body? help needed. Is there any help with **[COLOR="Red"]wifi-radar [/COLOR]**can I get any help?

Regards,

Swaroop Kunduru.

---

### Post by stchman on 2007-04-26
> **SwaroopKunduru said:**
> Hi All,

Somebody? Any body? help needed. Is there any help with **[COLOR="Red"]wifi-radar [/COLOR]**can I get any help?

Regards,

Swaroop Kunduru.

Gnome network manager will show you available wireless networks if that is what you are looking for.

---

### Post by stchman on 2007-04-26
> **SwaroopKunduru said:**
> stchman,

When I was working on 6.04 for some time(9Months) I installed ndiswrapper and was no problem in connecting wireless.

Brodcom card I have is for ethernet card right? I can work in wired network. My only problem is wireless.

I'll go through the link in your messages. Will it work for 44XXXX ?


Thanks and regards,

Swaroop Kunduru.

As I said my procedure is for Broadcom 43xx cards.  It is possible to modify the scripts for the 44xx series cards seeing as you already have the Windows drivers.

---

### Post by SwaroopKunduru on 2007-04-26
> **stchman said:**
> Gnome network manager will show you available wireless networks if that is what you are looking for.

Yes, But it dosen't show the wireless in network manager  aplet.

Regards,

Swaroop kunduru.

---

### Post by dolphin_oracle on 2007-04-26
This may be relevant to your RTL8180L card.  Apprarently the module is disabled by default due to a bug.

[http://ubuntuforums.org/showthread.php?t=422198](http://ubuntuforums.org/showthread.php?t=422198)

the author also points to this tutorial to get the card working.  There are some unintuitive steps.

[https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L?highlight=%28WifiDocs%2FDevice%29)

good luck.

---

