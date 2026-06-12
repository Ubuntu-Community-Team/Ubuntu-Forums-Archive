---
title: "Conexant Modem or My Fault?"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by gros0350 on 2005-06-21
Hello,

Just finished a dual-boot install and...

I'm trying to get my dial-up connection in order.  Do I need to install some type of files so that my modem will be recognized?  I have a Conexant HSF.

I've set up the pppconfig and everything seems right, tried pon and nothing happens.  I've tried the modem tool in the toolbar but nothing dials-out

Now, I just read that you must pay for conexant drivers.

Did I set-up wrong or do I need a driver first and if I do, should I just buy a new, and cheaper than than a conextant driver modem?  Thanks!

---

### Post by GTvulse on 2005-06-21
No, you haven't done anything wrong. The quid of the matter is that those Conexant/Rockwell HCF/HSF thingies are WinModems[1] not the real thing. And as you already found out, the Linux kernel modules to control them are commercial products (see [http://www.linuxant.com/)](http://www.linuxant.com/)). *Sigh* I'm presently using my HCF card as a paperweight.... ;-) 

[1] Read [http://www.linmodems.org/](http://www.linmodems.org/) for authoritative information.

---

### Post by az on 2005-06-21
Many other winmodems work in Ubuntu for free

[https://wiki.ubuntu.com/forum/hardware](https://wiki.ubuntu.com/forum/hardware)

---

### Post by gros0350 on 2005-06-21
[QUOTE=azz]Many other winmodems work in Ubuntu for free

[https://wiki.ubuntu.com/forum/hardware](https://wiki.ubuntu.com/forum/hardware)[/QUOTE]
 Thanks for the quick reply and the information.  Are there any linmodems you can recommend?  I'll ask the local hardware supplier as well.  

I may try to keep my winmodem and install another linmodem.  2 total.

I have free dial-up through the local university and that's the only reason that I'm dealing with  a modem.

---

### Post by cwaldbieser on 2005-06-21
I had good results in Linux with an external Zoom 56K Fax modem before I got DSL.  In WinXP though, it gave me a hard time installing the drivers.

---

### Post by az on 2005-06-22
[QUOTE=gros0350]Thanks for the quick reply and the information.  Are there any linmodems you can recommend?  I'll ask the local hardware supplier as well.  

I may try to keep my winmodem and install another linmodem.  2 total.

I have free dial-up through the local university and that's the only reason that I'm dealing with  a modem.[/QUOTE]


Intel or lucent modems.  Ask your supplier about the chipset.  They should be able to find out for you.

---

