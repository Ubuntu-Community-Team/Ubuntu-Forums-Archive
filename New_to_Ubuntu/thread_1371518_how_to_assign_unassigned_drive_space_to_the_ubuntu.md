---
title: "how to assign unassigned drive space to the ubuntu partition?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by totoff on 2010-01-03
dear forum members,

i installed ubn together with win xp dividing hd 50:50. now i've been fallen in love with ubuntu and want to give it more hd space. i resized my 160 gb hd with gpart giving the win xp partition 40 gb. unfortunately i didn't find out how to assign the free space now to the ubuntu hd. whenever i mark sda3 or sda 5 in gpart i'm only offered the disk size i had before resizing the ntfs partition. note that i didn't unswap the swap partition so far because i'm afraid of destroying something....
here is my hd structure

/dev/
/dev/sda1 ntfs (win xp) 29,43 gb
not assigned 65,5 gb
/dev/sda3 extended 50,56 gb
/dev/sda5 ext4 48,54 gb
/dev/sda6 linux-swap 2,11 gb
not assigned 4,25 mb
dev/sda2 fat32 (win xp recovery)

any clue how to assign the free 65,5 gb to sda3 is much appreciated. thanks for your help.

---

### Post by Mahngiel on 2010-01-03
it looks like your ubuntu is part of an extended partition. once inside an extended partition, you're not going to be able to assign it space from the logical area. you're going to have to look into moving partitions around using a liveCD. look at gparted's help menu.

mind posting a pic?

---

### Post by Paqman on 2010-01-03
> **totoff said:**
> note that i didn't unswap the swap partition so far because i'm afraid of destroying something....


You can go ahead and swapoff, it won't break anything.

---

### Post by bodhi.zazen on 2010-01-03
Also, when resizing partitions, you need to do it from a live CD, or in your case boot from the USB.

Turn swap off.

Then , last, you may need to move things in steps. So resize your NTFS -> apply changes
move partitions -> apply changes -> add to Ubuntu -> apply changes. 

You will have to move/ resize partitions such that the free space is adjacent to your ubuntu partition.

---

### Post by totoff on 2010-01-03
hi manghiel and bohdi.zazen,

thanks for your replies. i booted from usb, sure. so far i understand that i will have to turn swap off in order to make the drive accessible. however, i didn't understand the problem with the extended partition and in which order i have to move/rearrange. before i go agead with swapoff i post a picture. maybe i can get even more specific advise. thank you very much.
[IMG]file:///tmp/moz-screenshot.png[/IMG] [IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

