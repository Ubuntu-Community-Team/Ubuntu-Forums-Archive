---
title: "Networked printer not printing"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by nicstevens42 on 2008-08-28
I have ubuntu 7.10 and am trying to use a printer connected via smb to a windows machine. My old printer died this morning and I bought a new one but unlike the old I cannot print to the new. 

The job spools and on the windows machine both the print manager and HP's software says its printing but the printer does nothing. I could leave the job for hours and it wont print.

The windows machine is vista basic and the printer can print when directly connected to the ubuntu box. 

HP says this is a linux problem but I think its an issue with their driver but because linux is involved they wont support it without my paying $65 (I paid $60 for the printer)

Ideas? 

TIA,
Nic

---

### Post by dmizer on 2008-08-28
Does the printer work on the 7.10 machine?

If so, try sharing the printer through cups instead of through smb.  Any firewalls?

---

### Post by nicstevens42 on 2008-08-28
> **dmizer said:**
> Does the printer work on the 7.10 machine?

If so, try sharing the printer through cups instead of through smb.  Any firewalls?

Because I have UAC disabled (it breaks some things) on the vista machine I cant print to a shared printer on the linux machine (which is really preferred)

I think this is really a windows issue but intelligent windows support along with interoperability with linux is hard to come by

---

### Post by dmizer on 2008-08-28
I'm not suggesting that this is a Linux or a Vista issue.  It is simply someplace to start looking for a problem.  If the problem is in how Vista communicates with Ubuntu via the smb daemon, trying another protocol (cups) would shed light on that.

---

### Post by drifter2502 on 2008-09-15
I do not know if Vista has the same or similar but I resolved my proble with this suggestion.
[http://ubuntuforums.org/showthread.php?t=917991&highlight=printer+problem](http://ubuntuforums.org/showthread.php?t=917991&highlight=printer+problem)

---

