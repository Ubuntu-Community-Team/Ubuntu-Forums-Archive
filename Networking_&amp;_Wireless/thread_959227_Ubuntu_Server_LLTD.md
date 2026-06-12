---
title: "Ubuntu Server LLTD"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by slong501 on 2008-10-26
I've got an Ubuntu Server setup and running smoothly now and I was wondering if there is a compiled LLTD out there or a guide on how to compile the source code. I have some knowledge of Linux and Unix commands etc. but I'm no pro

Thank You :)

---

### Post by cabbiinc on 2009-01-01
> **slong501 said:**
> I've got an Ubuntu Server setup and running smoothly now and I was wondering if there is a compiled LLTD out there or a guide on how to compile the source code. I have some knowledge of Linux and Unix commands etc. but I'm no pro

Thank You :)

I just ran across this [http://www.howtoforge.com/installing-the-lltd-protocol-responder-for-linux-on-debian-lenny](http://www.howtoforge.com/installing-the-lltd-protocol-responder-for-linux-on-debian-lenny)

I don't know code at all. I was just googling LLTD for Ubuntu and this seamed pretty close to a fix from what I see. I have the same problem.

---

### Post by bcschmerker on 2012-01-09
As of 9 January 2012, there is apparently no ready-to-install Debian package for the Microsoft® Link Layer Topology Discovery™ Library; and even were there, Canonical® would only be able to place it either as part of a Lauchpad™ PPA or (and I consider this the practical approach) in the Ubuntu® Restricted repository due to rather restrictive licence terms (including nondisclosure of source code) from Microsoft Corporation.  LLTD™ was engineered as part of the TCP/IP backend for Windows® 6-up (e.g., Windows® Vista™ 6.0.60xx; Windows® Se7en™ 7.0.80xx; and Windows® Server 2008™ 6.0.60xx and Release 2 6.1.76xx), remember.

I already knew about the [HOWTO article](http://www.howtoforge.com/installing-the-lltd-protocol-responder-for-linux-on-debian-lenny) at HowToForge.net and the feedback on errors found and bugs encountered.

---

### Post by AOINEKO on 2012-03-03
Using the original code provided by Microsoft and with the modifications indicated here:
[http://www.veerkade.com/lld2d/](http://www.veerkade.com/lld2d/), I've got the daemon working properly:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213646&stc=1&d=1330808929[/IMG]

I've made another modification, I've added to the list of functions that return the constant "TLV_GET_FAILED" in the file "osl-linux.c", the function "get_net_flags", this prevent the property page to show a "management web page" for the device. I wrote a simple upstart script to start the daemon and a configuration file for the icons, they are attached to the comment.
I don't know if we can share the modified source, you can ask me to [EMAIL="diegorluna@gmail.com"]diegorluna@gmail.com[/EMAIL].


The file "lld2d.conf" goes in "/etc" and the file "lltd.conf" (upstart job) in "/etc/init", you should modify the network card eth2 in the upstart job to the corresponding value, probably eth0 for a machine with only one network card, and point the "jumbo-icon" and "icon" in the "lld2d.conf" file to the desired icons paths. The executable file "lld2d" goes in "/usr/bin" (or you should modify the upstart job accordingly).


Sorry for my English.

---

