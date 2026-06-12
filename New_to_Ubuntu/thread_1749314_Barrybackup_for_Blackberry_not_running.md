---
title: "Barrybackup for Blackberry not running"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by bthomson100 on 2011-05-04
My son has given me an older Blackberry 8320 and I've installed barrybackup. I can read the contents of the mini-SD card with a USB cable and work with files (copy, paste, etc.), but when I try to run barrybackup in terminal mode, I get the following error message
[INDENT]*Usb::Error caught in main:*
*(-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed*
[/INDENT]Can anyone help me resolve this? I'm a complete Linux newbie so very simple, step-by-step instructions, tips, etc. would be appreciated.

Bob Thomson, Ottawa, Canada

---

### Post by wolfen69 on 2011-05-04
Try running it as superuser
```
sudo barrybackup
```

---

### Post by bthomson100 on 2011-05-04
Many thanks. Running with sudo worked.

---

### Post by bthomson100 on 2011-05-04
While I can backup the Blackberry now, I also tried installing barry-utils but can't run it. When I type sudo barry-utils as root, I get the message "command not found". So what's the name for the programme since no icon nor name got installed that I can see with Nautilus.

I can see a directory .barry in root from a terminal window, but can't get to it using Nautilus. Nautilus tells me I don't have  the permissions necessary to view the contents of "root". How do I get them?

Bob Thomson

---

