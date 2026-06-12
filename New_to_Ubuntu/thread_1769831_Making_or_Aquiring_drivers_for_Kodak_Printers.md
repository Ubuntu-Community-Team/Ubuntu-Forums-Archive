---
title: "Making or Aquiring drivers for Kodak Printers"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by LinuxLearner123 on 2011-05-28
Hello all,
I have finally convinced my Windows-only family to switch from Windows XP to Ubuntu Linux. Everything is working great, except for one [major] problem; my Kodak printer just won't work.
Now, I'm very tech-savy, although I can't say I know too much, but I'm willing to try anything-using an open-source driver, running an emulator just for a driver, connecting the printer to some Internet service, or even building the driver myself, as long as it works. I don't mind if the answer is not a solution but a workaround, but this printer NEEDS to work.
BTW, it's a Kodak 5 AiO All-In-One, connected by USB.
Thanks!

UPDATE: I've seen lots of people in other threads saying that you simply should not buy Kodak printers and focusing on the fact that they will lose customers. However, although I do agree, I already have the printer and need it to work, right now.
Thanks!

UPDATE: I guess the installation is 64-bit, anything with i386 architecture won't work.

---

### Post by bodhi.zazen on 2011-05-28
In my experience Kodak support for Linux is poor at best and it is highly likely your printer will not work at all.

Your options are to :

1. google search your printer and see if there is a working solution.

2. Contact Kodak and complain. Last time I did this Kodak could frankly care less about Linux, good luck on this one.

3. In the future, do not buy Kodak products.

In the mean time , I suggest probably the best solution is to dual boot, using Windows as you and your family learns linux, and for the (occasional) printing.

You could try using your printer in Virtualbox, it may or may not work.

---

### Post by HermanAB on 2011-05-28
Howdy,

My solution for obstreperous printers, is to make a WindowsXP virtual machine using Vmware Player or Virtualbox and install the printer in that, then share it on the LAN.

---

### Post by philinux on 2011-05-28
Bodhi is correct,

[https://answers.launchpad.net/ubuntu/+source/cups/+question/20496](https://answers.launchpad.net/ubuntu/+source/cups/+question/20496)

There is a workaround driver but it's only available in 32 bit.

[http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)

Not sure how to get this working in 64 bit, but someone on here will. :P

---

### Post by oldsoundguy on 2011-05-28
Or you could sell that Kodak on eBay or at a flea market or in your local Craig's List and purchase a new photo printer.  
For the best quality photos, I chose an Epson .. I have an R-1800 and it really can not be beaten for quality of print (one of the few printers that print archival prints.)

---

### Post by DavePlummer on 2011-05-29
The link provided by philinux, also gives you access to the driver's source code. Try compileing and installing on your 64-bit system using the included instructions.

---

