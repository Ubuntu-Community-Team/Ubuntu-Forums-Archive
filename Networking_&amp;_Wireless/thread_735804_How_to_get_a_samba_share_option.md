---
title: "How to get a samba share option"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by antmenj on 2008-03-26
I want to copy files form Dapper box to a Gutsy box on the same router.  I went to system -> administration -> shared forlders and there was a box for NFS and samba.  I only ticked NFS as it was linux to linux.  Seemed that was a bad idea as I havn't done any good with NFS and now I don't have a samba option.

I tryed installing samba form the add/remove section but still no joy.  I also tryed to disable NFS form system -> administraton -> services to see if the option to install both would come back - no joy.

How can I get the samba option to be available or is there a better option?

---

### Post by dmizer on 2008-03-26
nfs is the better option.  faster and tuned to linux.  it is easily configured via the command line with only one small line to be added to a .conf file.

see the 4th link in my sig for a detailed howto.

---

### Post by antmenj on 2008-03-26
Thanks for that.  I'll see if I can get my head around it.

---

