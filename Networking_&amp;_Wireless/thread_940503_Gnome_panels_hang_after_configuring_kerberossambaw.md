---
title: "Gnome panels hang after configuring kerberos/samba/winbind"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by jimofcheeni on 2008-10-07
Hello,

I have successfully added a 64 bit hardy client to a Windows 2003 AD Domain. However, when I login to gnome, the panels hang, rendering the system next to useless.

I get the same result when I use Likewise, or if I configure kerberos, samba and winbind manually.

This only seems to affect gnome. I can login to a terminal, or to KDE4 without any problems. I would switch to Kubuntu Intrepid when it comes out of beta, but I need an LTS product.

Has anybody got any idea what could be causing this?
Thanks.

---

### Post by jimofcheeni on 2008-10-07
OK, I think I have sorted this out myself.

I think it's the Quick User Switcher applet which is causing this. I have removed it from the top panel, and it appears that everything is working as it should.

---

### Post by jimofcheeni on 2008-10-07
Scrub that. It didn't solve it after all.

I just reinstalled and removed the Quick Switch applet, but I am now having the same issue.


IGNORE THIS. I FORGOT TO COPY THE PANEL SETTINGS INTO /ETC/SKEL. DUH.

---

