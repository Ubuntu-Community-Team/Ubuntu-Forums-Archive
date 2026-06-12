---
title: "Problems with Samba and workgroups named in cyrillic."
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by ubumubumu on 2008-07-03
I have three problems, with workgorup names in cyrillic:
1. Those workgroup names, which are writen in cyrillic letters are not displayed correctly, i.e. they are probably converted improperly from ANSI to Unicode.
2. These workgroups are not browsable with Nautilus- no computers are diplayed inside them. When trying to browse such a workgroup with Gnome-commander I get message "List retriving is impossible.... " (I'm not sure what the exact English text is).
3. When I set my ownw workgroup with a name in cyrillic letters I cannot browse the samba network at all!

So I do not know if these problem are caused by any samba bugs, or ubuntu bugs, or hopefully I just have to do some more settings?

P.S. Ubuntu 8.04

---

### Post by superprash2003 on 2008-07-03
did you enter cyrillic in your smb.conf file?

---

### Post by ubumubumu on 2008-07-03
> **superprash2003 said:**
> did you enter cyrillic in your smb.conf file?
I only wrote *workgrop = &#1040;&#1041;&#1042;&#1043;&#1044;* i.e. I only wrote the name of the group with cyrillic letters in the smb.conf file, I did not set anything to
*something = cyrillic* or *something = 1251*

---

### Post by ubumubumu on 2008-07-07
I partially solved the problem adding

```
unix charset = UTF-8
display charset = UTF-8
dos charset = 866
```
in smb.conf
under ```
[global]
```
(adding these somewhere else does not work at all!!!)

No I can browse the workgrops with Gnome-Commander and I can browse the computer inside it.
But this des NOT work in Nautilus :(
At least the computers are accessible with *Go to address: smb://computername/*

The issue of clause 2 is completely okay.
The issue of clause 3 is completely okay.

Because Gnome-Commander is okay, then probably Samba is configured correctly, but Nautilus needs some more adjustment of bugfixing?

---

