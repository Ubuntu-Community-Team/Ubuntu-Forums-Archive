---
title: "Windows files share now asks for domain password"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by adriancollins on 2010-11-13
Hi,

I have been using Ubuntu 10.04 and had set up a file share to access files from my Windows 7 PC without problems. This had worked ok for weeks but now has stopped working and now asks for a password.

I had originally simply set up a bookmark from Nautilus to point to my Win7 PC, as below:

smb://(windows_username)/192.168.11.2/(windows_sharename)/

As I mentioned this worked fine for ages, but now I get a prompt for domain and password. I have tried every combination without success.

(I have double checked the share names on the Win7 PC etc)

Can anyone help me please?

Thanks - Adrian

---

### Post by coffeecat on 2010-11-13
> **adriancollins said:**
> smb://(windows_username)/192.168.11.2/(windows_sharename)/

Shouldn't 'windows_username' be 'windows_computername'? Also, if your Windows 7 machine is set up with the static address 192.168.11.2, then 'smb://192.168.11.2/sharename' should suffice. I know you said it worked before, but those are worth checking.

Also - try clicking on the Network icon in  the Places menu. Double-click on your W7 machine if it appears. If not, double-click on the Windows Network icon and see if it's inside there.

---

### Post by adriancollins on 2010-11-20
This is now solved. There was nothing incorrect in the Ubuntu settings I had been using. 

After much research I uninstalled Windows Live Mail from my Windows 7 PC - rebooted and I can now connect ok !

Appears to be a bug in Samba from what others are sayng - very difficult to find any info so I hope this post helps someone else. This has taken me for ever to solve!!

Amazing eh!!

---

### Post by bhb192 on 2010-12-08
It appears that ALL Windows Live products are causing this problem. Uninstall the entire "Windows Live Essentials" package and also "Windows Live Sign In Assistant" if you're having this problem.

---

