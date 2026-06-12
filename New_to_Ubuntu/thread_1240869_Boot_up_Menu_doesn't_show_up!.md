---
title: "Boot up Menu doesn't show up!"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Darklaguna on 2009-08-15
Hi there,

So this maybe a very old question, but I need tsomeone o guide me to the right direction. Basically I have two HDDs; 

[LIST]
[*]A 300 GB IDE set as a Master drive, containing WinXP (with C, D and E partitions)
[*]A 1 TB SATA (with I and K partitions)
[/LIST]
And I wanted to install Ubuntu on the I partition of the second HDD, So I used the Live CD, and created out of the I drive 3 drives (/ , /home and swap) and installed Ubuntu on / .

Everything went fine till the system restart, where the GRUB didn't show up, **and the booting continued to WinXp.**

So, as a total noob, what went wrong, and how can I fix this?

Thanks for the help. Great community indeed.

---

### Post by Sidewinder1 on 2009-08-15
First, **Welcome **to Ubuntu Forums!!!
Looks like you did everything right. Did you, from the Live-CD menu "Check for Errors"? Perhaps the live cd needs to be burned at a slower speed (4X or less). Did you do an MD5SUM check on the version of Ubuntu that you downloaded?
There are any number of minor things that may have gone wrong, perhaps your burner had some dust in it?...
HTH,
Side

---

### Post by plucky on 2009-08-15
> **Darklaguna said:**
> Hi there,

So this maybe a very old question, but I need tsomeone o guide me to the right direction. Basically I have two HDDs; 

[LIST]
[*]A 300 GB IDE set as a Master drive, containing WinXP (with C, D and E partitions)
[*]A 1 TB SATA (with I and K partitions)
[/LIST]
And I wanted to install Ubuntu on the I partition of the second HDD, So I used the Live CD, and created out of the I drive 3 drives (/ , /home and swap) and installed Ubuntu on / .

Everything went fine till the system restart, where the GRUB didn't show up, **and the booting continued to WinXp.**

So, as a total noob, what went wrong, and how can I fix this?

Thanks for the help. Great community indeed.

It is possible the Grub boot has been written to the MBR of the SATA drive instead if the MBR of the IDE drive.

Go in to your bios and change the boot order to boot from the sata drive first and see if the GRUB boot menu now shows up.

Good Luck

---

### Post by Darklaguna on 2009-08-15
Thank you both Sidewinder1 & plucky for the prompt reply. :)  plucky's comment was the right one. Changing the boot order to the SATA's MBR from within the BIOS did solve it. 

Thank you again for your help!  ;)

---

