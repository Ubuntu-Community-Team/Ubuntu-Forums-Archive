---
title: "Bart"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by SjurH on 2009-01-05
Hi I'm trying to make a BART (Bootable Antivirus and Repair Tool) with ubuntu 8.10 on a 32GB USB pen drive as the base.
I want to use this to remove viruses and other malware from windows computers. And also backup pictures, documents etc if a clean install should be needed.
Could you help me recommend an Antivirus, Antispyware and a Partition editor.
If someone can think of other useful tools to put on my pen-drive suggestions are more than welcome.

This is one of my first post's so feel free to move it..

---

### Post by northern lights on 2009-01-05
If the pendrive contains a bootable Linux distribution, you're choice of an antivirus app should be *[ClamAV]("http://www.clamav.net/")*.

You might want to consider using [Knoppix]("http://www.knoppix.net/wiki/USB_Based_FAQ") instead of Ubuntu, though. I would.

[EDIT]
If it's meant to work on broken Windows machines and they contain FAT filesystems, you will probably end up using *[dosfsck]("http://linux.die.net/man/8/dosfsck")* once in a while, but that works out of the box.
[/EDIT]

---

### Post by SjurH on 2009-01-05
Thanks, I'll try out knoppix

---

