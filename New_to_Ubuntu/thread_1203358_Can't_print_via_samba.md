---
title: "Can't print via samba"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by canam101 on 2009-07-03
I am running ubuntu 8.04. It is on a lan with two windows pcs. We have an hp laserjet connected to one of the windows pcs.

If I try to set up a printer, it finds the computer that has the printer attached to it: smb://mshome/sms1/hplaserj, but it cannot 'verify' it. And I can't print to the printer. Samba is running.

If I re-boot my pc into mepis, I can print via the lan. If I print from the other windows computer, I can print via the lan.

If I attach the printer directly to my pc, I can set up the printer and print.

So I am guessing there is something mis-configured with my ubuntu pc as a far as connecting via samba.

Any suggestions? thanks.

---

### Post by oldsoundguy on 2009-07-03
have you gone to system> administration> printing and installed the printer via cups?

---

### Post by ukripper on 2009-07-03
> **canam101 said:**
> I am running ubuntu 8.04. It is on a lan with two windows pcs. We have an hp laserjet connected to one of the windows pcs.

If I try to set up a printer, it finds the computer that has the printer attached to it: smb://mshome/sms1/hplaserj, but it cannot 'verify' it. And I can't print to the printer. Samba is running.

If I re-boot my pc into mepis, I can print via the lan. If I print from the other windows computer, I can print via the lan.

If I attach the printer directly to my pc, I can set up the printer and print.

So I am guessing there is something mis-configured with my ubuntu pc as a far as connecting via samba.

Any suggestions? thanks.

What printer you got? - Model number?

---

### Post by canam101 on 2009-07-03
> **ukripper said:**
> What printer you got? - Model number?

It's an hp 2055, but I doubt that is the problem, since I can print if it is connected directly to my pc. Also, we have a second printer and the same problem exists with that one.

Yes, I went into system/admin/printing and did the installation there via 'windows printer via samba'.

Maybe samba has a problem, but I can see and edit files on the hard drives of the other two pcs. I am running gnome. Is there some gui interface for samba that I can use to see what it sees? Under kde, I used to use smb4k, but under gnome, it looks like you have to install half of kde to install it.

---

### Post by superprash2003 on 2009-07-03
did you uncomment the line
printing = cups 

in the smb.conf file? post your smb.conf file here

---

### Post by canam101 on 2009-07-03
I found the problem. Kind of an oddball thing, but maybe it will help others to know about it.

Under system/administration/network/general/host name
I had a host name like a.b.c.d, where c.d was a real domain name.

I had it that way because I needed to send emails to certain 'gateways' that required that kind of name - don't know why they do.

Well, I suspected that the host name has lots of consequences, so I decided to make it more normal and see what happened, and changed it to 'briggs'. As soon as I did that, the printer worked.

I don't think I can send messages to the gateways any more, but having the printer is more important.

Appreciate the replies. Great forum.

---

