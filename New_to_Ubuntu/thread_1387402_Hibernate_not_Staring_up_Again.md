---
title: "Hibernate not Staring up Again"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by rbscairns on 2010-01-21
eee B202, Intel Atom N270 CPU, 160GB HDD, 2GB RAM, Ubuntu 9.10 clean install.

Here is what happens-[LIST=1]
[*]Select Myname
[*]Select Hibernate
[*]After some HDD activity, system powers off.
[*]Press the power button to reboot.
[*]System starts to reboot.
[*]The white Ubuntu logo appears for a short time then the screen goes black.
[*]Some text appears at the top of the screen for a very short time. This text includes the word "failed".
[*]The moving underlined word Ubuntu appears for a while.
[*]Logiun screen is displayed.
[*]Mouse and keyboard are frozen with NumLock light flashing.
[/LIST]
The only way I have found to get my system working again is to disconnect the power from the computer, reconnect and push the power button for a clean new boot.

I understand that I need a linux-swap partition for Hibernate to work. I have a 4GB linux-swap partition as part of the extended partition of my HDD. I have attached a Screenshot of my Gparted window showing the partitions that I have,

When I run free -m, I get the following results-```
             total       used       free     shared    buffers     cached
Mem:          2005        464       1541          0         42        229
-/+ buffers/cache:        192       1812
Swap:         4102          0       4102

```My swappiness=60

Hibernate is not a major requirement for me, however I would like to get it working if I could.

---

