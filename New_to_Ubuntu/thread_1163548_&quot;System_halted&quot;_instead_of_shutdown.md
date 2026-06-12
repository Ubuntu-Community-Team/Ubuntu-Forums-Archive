---
title: "&quot;System halted&quot; instead of shutdown"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by don_diego on 2009-05-18
Having to power down manually is a minor annoyance but since my laptop used to power down automatically when ending a session, I assume this is something that can be fixed. 

My question is HOW to fix it?

TIA for any help.

---

### Post by nandemonai on 2009-05-19
> **don_diego said:**
> Having to power down manually is a minor annoyance but since my laptop used to power down automatically when ending a session, I assume this is something that can be fixed. 

My question is HOW to fix it?

TIA for any help.

Have you disabled ACPI?

---

### Post by don_diego on 2009-05-19
> **nandemonai said:**
> Have you disabled ACPI?

No, at least not knowingly. But now that you mentioned it, I checked this old laptop's (Dell Inspiron 2650) BIOS and can't find anything in it that allows me control the ACPI setting.

Guess I'll have to be content  with the way things are. 

Thank you nevertheless.

---

### Post by don_diego on 2009-05-19
After seeing mention of the shutdown problem in another thread I checked my menu.list and found the following:

```
/boot/vmlinuz-2.6.28-11-generic root=UUID=90dfdb52-87e2-4602-bf42-8db3e40e19c1 ro acpi=off noapic nolapic edd=on quiet
```I changed acpi from off to force, did the sudo update-grub but the result was not what I hoped for: the system would not boot!

Used recovery mode to restore things back the way they were and was able to boot. I have no idea what  "noapic" and  "nolapic" mean/do. Should I perhaps have removed them also?

---

### Post by cariboo on 2009-05-19
Maybe this [article]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture") will help answer your questions.

---

### Post by timzak on 2009-06-27
Found this solution that worked for me:


```
gksudo gedit /etc/modules

```
Add the following line to the bottom of the file, save, and reboot:

> apm power_off=1 

---

