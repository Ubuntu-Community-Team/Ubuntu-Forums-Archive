---
title: "No boot without repeated enter key"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by gnuryder on 2009-11-17
[FONT=Comic Sans MS][SIZE=4][I]older toshiba laptop fails to boot 9.10 unless i hit enter key many times during boot?
any help would be appreciated.[/I][/SIZE][/FONT]

---

### Post by NickJones on 2009-11-18
Okay, I got the message... Are you trying to boot of the CD, or the HDD?

---

### Post by lidex on 2009-11-18
Check the output of dmesg
```
dmesg
```
and the content of /var/log/messages for clues to what is hanging up the boot process.

---

