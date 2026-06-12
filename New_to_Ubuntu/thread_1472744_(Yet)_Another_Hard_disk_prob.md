---
title: "(Yet) Another Hard disk prob"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Wungle on 2010-05-04
Can anyone shed light on this? Am currently migrating from Vista and was importing a load of files from Thunderbird into Evolution - I had previously been using Outlook for email, but read on another post that this was best way of migrating to Evolution.  The Thunderbird files are on an old-ish 500GB Seagate drive.  All was going as planned.
But when I rebooted, the external drive wasn't recognised let alone mounted.
Anyone have any ideas as to why it would be recognised and mounted and then not?
Thanks

---

### Post by tgalati4 on 2010-05-04
Well, disks do fail right after moving lots of files.  They get hot and refuse to read properly.

Let it cool down for a while then come back to it to investigate.

Install smartmontools.

Open a terminal:

sudo apt-get install smartmontools

sudo smartctl -a /dev/sda

Take note of any strange issues, power-on hours, and temperature.

---

### Post by ScottinSoCal on 2010-05-04
If the HD works after cooling down, but won't let you get the rest of your files off, put it in an ESD bag and put it in the freezer overnight. You should have enough operating time to get your data off before it craps out again.

---

### Post by Wungle on 2010-05-04
Thanks for the help guys.  I'll try again in the morning.

---

### Post by Wungle on 2010-05-05
Right - got the problem sorted in the end.  Not a problem with overheating as it turns out, but somehow the system type on the MBR had been changed.  Had to work through on Vista on my laptop as I am slightly less nooby on Windows than Ubuntu.  
Downloaded Partition Wizard, which enabled me to change the system type back to FAT32 and allocate a drive letter, which had been missing.
Connected it back to the my desktop (Ubuntu 10.04) and hey presto it mounted straight up!

---

### Post by tgalati4 on 2010-05-05
sudo gparted /dev/sda

This would probably allow you do to do the same.  Already included in the base Ubuntu.

Good luck with the rest of your migration adventure.

---

### Post by Wungle on 2010-05-06
Thanks!

---

