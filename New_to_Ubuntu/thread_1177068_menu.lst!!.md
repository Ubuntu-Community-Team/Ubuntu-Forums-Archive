---
title: "menu.lst!!"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-06-03
Please configure my menu.lst, I lost link to windows 7 after installing XP

In SS:-
sda1 --> ubuntu 9.04(working)
sda3 -->  Windows 7
sda8 --> win xp pro

I have attached my menu.lst also.

When i boot using windows 7 option then it boots xp.

---

### Post by labinnsw on 2009-06-03
> **eshant_engineer said:**
> Please configure my menu.lst, I lost link to windows 7 after installing XP

In SS:-
sda1 --> ubuntu 9.04(working)
sda3 -->  Windows 7
sda8 --> win xp pro

I have attached my menu.lst also.

When i boot using windows 7 option then it boots xp.

Could you also post the device map? The menu list looks OK.

---

### Post by eshant_engineer on 2009-06-03
I am sorry..i don't know what is device map. some explanation please!

---

### Post by labinnsw on 2009-06-03
It should be located at /boot/grub/device.map, same location as the menu list.

---

### Post by eshant_engineer on 2009-06-03
It is showing following statements:-

> (hd0)	/dev/sda
(hd1)	/dev/sdb

---

### Post by labinnsw on 2009-06-03
That looks correct as well. When you select Windows 7 option, don't you get another option to select one or the other of the windows systems?

---

### Post by eshant_engineer on 2009-06-03
No, when i select option of windows 7 then it start booting XP and when i choose XP then it show error

---

### Post by eshant_engineer on 2009-06-03
I have tried a lot but not succeded...please if anybody can help.

---

### Post by SOULRiDER on 2009-06-03
Its not a problem with Linux or with GRUB, its a problemn with windows. I believe you ahve to edit the boot.ini file in windows or something.....

---

### Post by Nythain on 2009-06-03
definately sounds like a windows bootloader problem, probably the windows 7 bootloader... i know vista was a pita

---

### Post by ptsubin on 2009-06-03
It seems to me that you have first installed windows 7 and then windowx XP which could have normally owerwritten the boot info for windows 7. There might be workarounds for this problem, bu copying some boot files. Just see if your windows 7 partition containd ntldr . if so , just google this problem.

---

### Post by QIII on 2009-06-03
When you say "when i choose XP then it show error", what is the text of the error?

---

### Post by eshant_engineer on 2009-06-03
sorry, i am posting.

---

### Post by eshant_engineer on 2009-06-03
> **ptsubin said:**
> It seems to me that you have first installed windows 7 and then windowx XP which could have normally owerwritten the boot info for windows 7. There might be workarounds for this problem, bu copying some boot files. Just see if your windows 7 partition containd ntldr . if so , just google this problem.

Where would i find it, in XP or in Win 7 because i have searched all hidden files and folder in Windows 7 partition but nothing like ntldr is there.

> **QIII said:**
> When you say "when i choose XP then it show error", what is the text of the error?

Error 12: Invalid device requested

press any key to continue...

---

### Post by labinnsw on 2009-06-04
> **eshant_engineer said:**
> Please configure my menu.lst, I lost link to windows 7 after installing XP

In SS:-
sda1 --> ubuntu 9.04(working)
sda3 -->  Windows 7
sda8 --> win xp pro

I have attached my menu.lst also.

When i boot using windows 7 option then it boots xp.

I had another look at your partitions. It is very unlikely that XP is at sda8 since the size of that partition is only 4.92 GB. 

If sda3 is Windows 7, then XP is either on sda5 or sda7.
In the menu list it should either be hd0,4 or hd0,6.

Please edit the menu list and try again.

Or use those that I have edited.

[ATTACH]116379[/ATTACH]

[ATTACH]116380[/ATTACH]

Your original is here so you can forego backing up.

---

