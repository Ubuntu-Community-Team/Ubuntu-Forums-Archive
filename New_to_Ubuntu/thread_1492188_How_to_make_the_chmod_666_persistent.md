---
title: "How to make the chmod 666 persistent"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-05-24
After upgrading to Lucid Lynx ver. 10.04, my Brother MFC-240C (printer, FAX, Scanner, Copier) would NOT scan.

Netsearching I found a post about a different scanner (HP) and although this command works, I cannot make it persistent.

[http://ubuntuforums.org/showthread.php?t=1484372](http://ubuntuforums.org/showthread.php?t=1484372)

I had to change the original poster's command a little. To get the scanner working, I had to;

1 - Turn the device on

2 - in a terminal, type: lsusb

3 - record the usb information for the Brother product (this will change with every boot, or re-boot, at least that is what I have noticed)

4 in a terminal, type

sudo chmod 666 /dev/bus/usb/00*/00*

where /usb/00*/00* are the numbers given in lsusb at the Brother MFC-240C line. For example, today, my lsusb reads:

Bus **002** Device **004**: ID 04f9:01ab Brother Industries, Ltd MFC-240C

Once that is accomplished, both Simple Scan and XSane scan as usual.

My question is:

How do make this persistent so that I'm not running terminal commands to make devices work properly?

---

### Post by roger_1960 on 2010-05-24
Hi

See this page

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

The brother site has good instructions for installation

---

### Post by Mark_in_Hollywood on 2010-05-24
> **roger_1960 said:**
> Hi

See this page

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

The brother site has good instructions for installation

This has solved my problem with both Simple Scan and XSane.

---

