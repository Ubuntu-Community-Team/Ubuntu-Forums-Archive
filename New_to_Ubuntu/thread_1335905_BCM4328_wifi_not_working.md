---
title: "BCM4328 wifi not working"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by chris tallman on 2009-11-23
I have an HP TouchSmart tx2-1025dx Notebook PC with BCM4328 802.11 a/b/g/n wireless chipset. I cannot get Ubuntu to recognize it. I have never seen Karmic Koala and the [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) toutourial didnt help much, I got lost after installing the *ndisgtk* package. Can anyone help me, I'm running Ubuntu 9.10, thanks.

---

### Post by anewguy on 2009-11-23
Do you have the ability to hard-wire to a network connection temporarily?  If so, I'd install the fw-cutter, then restart your computer and see if anything shows in restricted drivers and if not enabled then enable it.

If not, at what point are you getting stuck with the ndiswrapper stuff?  If you have the Windows driver files for your wireless card (the .inf and .sys file(s) ), just put them on your desktop, start ndisgtk (there should be a menu entry saying either ndisgtk, windows wireless installation, or some such thing).  If you can't find the menu entry, try opening a terminal and typing:

sudo ndisgtk <press enter>

This should start up ndisgtk.  Select install new driver, then point it to your files on the desktop - it should install fine then.


Dave :)

---

### Post by Ostrava on 2009-12-06
Does this also work if you're on a MBP?

---

### Post by boby.maggorr on 2010-02-01
This thread looks abandoned, but when I was searching for a solution for the same problem, it poped up on google as one of the first and because I found a possible solution, I want it to be solved ;) 
I have a tx2-1050eo notebook but I'm not sure whether it has the same Broadcom wifi, but I hope it'll work...

I simply forgot about that "Jockey" application, which can be run via 
menu ->system -> administration -> hardware drivers
and there I found what I was looking for: option to install proprietary drivers, easily, just a few clicks.

I don't know if the method discussed above is necessary for making the wifi to work, but this jockey thing is worth a try :)

---

### Post by samantha_ on 2010-02-01
jockey installs bcmwl-kernel-source, which may work for the card.
You can just install it manually from the repos if you want ;)

---

