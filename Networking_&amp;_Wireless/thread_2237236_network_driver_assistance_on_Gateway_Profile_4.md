---
title: "network driver assistance on Gateway_Profile_4"
date: 2014-07-31
forum: Networking &amp; Wireless
---

### Post by barclay.mcdaniel on 2014-07-31
am unable to get network working, network driver help for Lubunto_14.04 on Gateway_Profile_4, it works for WindowsXP though.

---

### Post by ajgreeny on 2014-07-31
Wireless or cable?

We need much more info please, so open a terminal, type **lspci**, hit enter and copy back here the output you get from that command.

---

### Post by barclay.mcdaniel on 2014-08-01
per below*, i just copied this one line with ethernet info from lspci results to paper and typed here for you to read...

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev81)

* = i cannot seem to copy text from terminal.  might you know how?  ctrl+insert does not seem to work.  i searched several times and cannot seem to come up w/ lubuntu copy/past keyboard shortcuts

---

### Post by ajgreeny on 2014-08-01
I am very surprised that your Intel network card does not work as Intel is normally very well supported.
I have found one case where a BIOS update solved a similar problem, but I can not assist with how you might do that, I'm afraid.

To copy from a GUI terminal I usually highlight text and right-click > Copy, but to use the keyboard it is **Shift+Ctrl+C**.

This because **Ctrl+C** cancels any current running command.  For just about every other application it is Ctrl+C to copy and Ctrl+V to paste, as per default in that other OS.

---

### Post by barclay.mcdaniel on 2014-08-01
ah, nice idea (bios update).  will try that.  tks.  i should get that from "gateway".  correct?

---

### Post by ajgreeny on 2014-08-02
Possibly, but I have never updated a BIOS so I am the wrong person to tell you how to do it.

Try the Gateway website or Award or Phoenix site, or whatever BIOS it uses, which you should see quickly at power-on.

---

