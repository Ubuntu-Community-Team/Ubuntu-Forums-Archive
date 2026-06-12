---
title: "evolution smtp error"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by fishfinder on 2009-05-12
I installed Ubuntu for the first time about 4 days ago. I set up Evolution as per ISP instructions but I am unable to receive mail. I get the message "Error while performing operation - Host lookup failed:smpt.xnet.co.nz:Name or service not known".
I rechecked my setup for the obvious typo but I had actually typed it correctly smtp.xnet.co.nz and not as it stated in the error message.
I have tested the same setup information using outlook on XP and I can send and receive with no problem.

Help would be greatly appreciated.

---

### Post by Ericyzfr1 on 2009-05-12
Whatever you used in XP should work with Evolution.

---

### Post by lisati on 2009-05-12
> **fishfinder said:**
> I installed Ubuntu for the first time about 4 days ago. I set up Evolution as per ISP instructions but I am unable to receive mail. I get the message "Error while performing operation - Host lookup failed:[COLOR="Red"]**smpt**.xnet.co.nz[/COLOR]:Name or service not known".
I rechecked my setup for the obvious typo but I had actually typed it correctly smtp.xnet.co.nz and not as it stated in the error message.
I have tested the same setup information using outlook on XP and I can send and receive with no problem.

Help would be greatly appreciated.

Kia ora! Shouldn't it be **smtp.xnet.co.nz**? Odd, isn't it?

EDIT: Have you tried using IMAP instead of POP? According to XNET's website the IMAP server is imap.xnet.co.nz

---

### Post by fishfinder on 2009-05-12
> **lisati said:**
> Kia ora! Shouldn't it be **smtp.xnet.co.nz**? Odd, isn't it?

EDIT: Have you tried using IMAP instead of POP? According to XNET's website the IMAP server is imap.xnet.co.nz



Hi, thanks for your inputs. My problem is with outgoing mail, incoming is fine. See Xnet email settings shown below:

Incoming Mail Server: pop3.xnet.co.nz
                      Incoming Mail Server: imap.xnet.co.nz
                     Outgoing Mail Server: smtp.xnet.co.nz
                     Webmail URL:webmail.xnet.co.nz


I don't understand why the error message comes up as it does. There's nothing to mess up in the settings really. I'll probably remove the Ubuntu package application, then reinstall Evolution from the Evolution site. Failing that, I'll look for alternative email application.


Thanks for the help people.

---

