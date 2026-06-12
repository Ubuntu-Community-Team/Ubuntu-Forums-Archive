---
title: "Samba gui?"
date: 2021-02-13
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2021-02-13
I am in the process of updating our Samba Servers to use AD-DC and would like to find a GUI that would make adding users and machines to the Domain easier.
Is there such a thing? if so what is it.

---

### Post by schragge on 2021-02-18
[gadmin-samba](https://manpages.debian.org/unstable/gadmin-samba/gadmin-samba.8.en.html) (GTK2)
 [shares-admin](https://manpages.debian.org/unstable/gnome-system-tools/shares-admin.1.en.html) (from **gnome-system-tools**, GTK3)

---

### Post by spamhog on 2021-05-24
I suggest you don't even try GUI tools as none seems reliable atm.

They used to be, but things have changed.

You risk ending up with nice config files that current samba packages can't understand.

**gadmin-samba** orphaned 10 years upstream
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=605306](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=605306) [B]

shares-admin[/B] hasn't worked properly in many years

**webmin** out of date, many consider it very poorly, not included in any distro, seems attractive because many *other* bits seem to work

**system-config-samba** was my favorite, not even included lately (it still works on some old LTS like 18.4).

**smb4k** ????

As far as I can tell there is NO (0) current and working GUI for administering samba shares.

I'd love to be proved wrong as I would like to use a GUI to manage SMB-CIFS.

So if I'm wrong **please anyone point me to a recent and relevant howto referencing a recent edition**, or at least someone willing to testify like "tool X works fine under Ubuntu <recent version>". Missing that, I wouldn't bother.

I bet there is some proprietary tool that works.

My reading is, the center of gravity is moving to internet-mediated-everything, the norm being local host talking to machines in the cloud, including when the task is sharing files or synching directories on machines in adjacent rooms. Everything is becoming a chromebook. :-P

---

