---
title: "Maybe have to fix BIOS, no idea how?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by comethalley on 2010-02-11
So I've downloaded ubuntu netbook remix twice onto my usb - once through pendrive linux, once through unetbootin - all normal.  But I can't get my eeepc 1005HA to recognize the usb!  When I set it to boot from removable device, it just... doesn't - goes straight to windows.  I think my computer should support it, because I haven't heard of anyone else with an eee 1005 having these problems.  My computer definitely recognizes the usb.  How do I get it to boot from it?  I have no knowledge of terminal at all.

---

### Post by audiomick on 2010-02-11
Hi,
I haven't done this but:
I assume you have read this
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Does your BIOS have the option to boot from a USB device rather that "removeable device"?

---

### Post by SlugSlug on 2010-02-11
google shed this when seaching for 

eee 1005 boot from usb



Booting into the Crunchbang live environment.
By default the 1005HA has something called 'Boot Booster' enabled which might prevent you from booting using a USB-Stick. To disable this go into the BIOS by repeatedly pressing F2 after turning on the Eee PC. Don't change anything and just press F10 to save and exit from the BIOS. After having exited repeatedly press ESC to get into the boot device selection screen. Once there just select your USB-Stick. When the UNetBootin menu pops up you should choose 'Default' and then wait untill crunchbang has started up.

---

### Post by comethalley on 2010-02-11
Thanks!  I tried hitting the escape button a few times after going to BIOS page, and after that I got it to load!  Now I just need to find a way to get it to recognize my internet...

---

