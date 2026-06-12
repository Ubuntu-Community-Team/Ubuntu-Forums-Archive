---
title: "bash command has invalid option"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-17
Hi,

I'm trying to run a command from an ubuntu howto page, but there's something wrong with it that i dont understand?

Can you point it out please?

Thanks


root@nnjond-desktop:/# tar -cvpzf backup.tar.gz -–exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev /
tar: invalid option -- 
Try `tar --help' or `tar --usage' for more information.
root@nnjond-desktop:/#

---

### Post by albandy on 2010-07-17
[FONT="Courier New"]this is wrong "[SIZE="5"]-–exclude=/backup.tar.gz[/SIZE]" it should be "[SIZE="5"]--exclude=/backup.tar.gz[/SIZE]"
[/FONT]

Look at the diference in "[FONT="Courier New"][SIZE="5"]--[/SIZE][/FONT]" you writed "[FONT="Courier New"][SIZE="5"]-–[/SIZE][/FONT]" and it should be "[SIZE="5"][FONT="Courier New"]--[/FONT][/SIZE]"

---

### Post by nnjond on 2010-07-17
Many thx

---

