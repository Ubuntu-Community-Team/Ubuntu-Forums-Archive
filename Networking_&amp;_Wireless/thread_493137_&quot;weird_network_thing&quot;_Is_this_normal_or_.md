---
title: "&quot;weird network thing&quot; Is this normal or not?"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by fuzzybunny on 2007-07-05
I have a 755Mhz iMac that is running Feisty PPC and I am sharing it to XP using Samba 3.0.24

I can see the ubuntu computer fine in workgroup computers, but if I open it it takes about five minutes to bring up the login box, then about five again to open the shared folders and printers window. 

After that point it flies along, browsing with no trouble whatsoever.

Copying generally goes quickly, but sometimes it gets stuck in one place, also for a good couple of minutes....

Any ideas?

---

### Post by sfarber53 on 2007-07-05
Streater,

Take a look at your /etc/samba/smb.conf file.  It needs a "netbios name" to easily find the share you want to connect to and "wins" should be checked as on in the share configuration.

I went through this recently and got it fixed by making those corrections.  Now the thing fairly screams.

Good luck!

Steve

---

### Post by fuzzybunny on 2007-07-06
I was under the impression that wins should be "no" as Samba is not a WINS server?

I did try it and same result.

If I set user to share, it goes fine, with no hang time, but I don't really want to do that.
Is the issue somewher on the authentication side maybe?

---

### Post by fuzzybunny on 2007-07-11
Guys? can anyone help here?
I need to get this sorted ASAP

---

