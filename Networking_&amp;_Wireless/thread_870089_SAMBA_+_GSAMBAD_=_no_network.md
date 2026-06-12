---
title: "SAMBA + GSAMBAD = no network"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by scartmell on 2008-07-25
Okay, so I'm a noob in the Linux/Unix/Ubuntu community. (2 days experience)

My job is to make this new Ubuntu box into a file server for all the other computers in the network, which are running on windows.

Earlier this morning, on my windows machine I was able to go "Run > \\Ubuntu's IP" and it would show the test folder I had set to be shared. 

After that, I installed GSAMBA for all the extra server options it has. However, when I went to share a folder using GSAMBA, the folders I right-clicked > sharing options, it told me 
I needed to add this line (usershare owner only =false) to the smb.conf in the [global] section, so  did, and it fixed that. So I had the shared folders being shared using GSAMBA.

However. When I went back to my windows machine, did the "Run > ubuntus IP", it would not connect. 


I also have this error on the Ubuntu box when I open up SAMBA now:

"

Some lines couldn't be understood while reading the configuration file /etc/samba/smb.conf. These may be unknown configuration directives for Samba plugins but could also be configuration errors.

show details...

38: enable spoolss = yes

"


I never messed with enable spoolss, so I'm totally confused and now the network can't connect to the ubuntu box. 


Anyone have ANY idea of what's going on here?

---

### Post by scartmell on 2008-07-25
bump...

---

### Post by Iowan on 2008-07-25
Lacking better advice, I might suggest you look through smb.conf to see if it has a **enable spoolss = yes** line (perhaps line #38?).  Try "commenting it out" with a leading semicolon (;) or hash (#).  If it messes up something else (NT printing), you can put it back.

---

### Post by cariboo on 2008-07-25
After modifying your smb.conf test it in a terminal using:

```
testparm
```

This should show any errors in your smb.conf file.

Jim

---

