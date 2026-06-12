---
title: "backup with dd"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-07-19
hi, i just installed a fresh copy of vista ultimate, and it was such a pain i would hate to do it again. so, i want to use dd to backup this partition, but i don't know how. 

firstly, i only want to backup my vista partition (/dev/hda1). i have ubuntu on my hdd as well, so i can't use dd on the entire hdd.

i wasn't too sure as to what the "bs" and "count" and "skip" (and etc.) options do. could someone provide some explanation & advice as to these options?

i presume **"dd if=/dev/hda1 of=~/Desktop/vista.bkup"** to backup and **"dd if=~/Desktop/vista.bkup of=dd if=/dev/hda1"** to restore is too simplistic?

thanks

---

### Post by mikewhatever on 2009-07-19
Edit: never mind

---

### Post by Paddy Landau on 2009-07-19
I recommend [PartImage]("http://www.partimage.org/") to back up your partition.

PartImage will back up only the used parts of your partition, and compress the result, thereby using as little space as possible.

Either you can install PartImage through Synaptic Package Manager and run it from your Ubuntu login, or you can use [SysRescCD]("http://www.sysresccd.org/") (which includes PartImage) and boot from the CD.

Warning: You cannot safely use PartImage to back up a partition that you have mounted (so you would have to use SysRescCD to back up your Ubuntu partition).

---

### Post by Cheesemill on 2009-07-19
Or you could use [CloneZilla]("http://clonezilla.org").

---

### Post by akimatsu123 on 2009-07-19
thanks, partimage looks great. i also made a dd image just in case, with:

dd if=/dev/sda1 of = ~/Desktop/Vista.img bs=4096 conv=notrunc

would that work if i restored the image?

i will definitely give partimage a try

---

### Post by VastOne on 2009-07-19
> **Paddy Landau said:**
> I recommend [PartImage]("http://www.partimage.org/") to back up your partition.

PartImage will back up only the used parts of your partition, and compress the result, thereby using as little space as possible.

Either you can install PartImage through Synaptic Package Manager and run it from your Ubuntu login, or you can use [SysRescCD]("http://www.sysresccd.org/") (which includes PartImage) and boot from the CD.

Warning: You cannot safely use PartImage to back up a partition that you have mounted (so you would have to use SysRescCD to back up your Ubuntu partition).

Does PartImage now handle ext4?

I have checked the PartImage site and it does not

---

### Post by Paddy Landau on 2009-07-19
> **VastOne said:**
> Does PartImage now handle ext4?

I have checked the PartImage site and it does not
Good point. Thanks for bringing it up!

Does anyone know of an alternative for ext4? [FSArchiver]("http://www.fsarchiver.org/") is still under development and cannot be considered reliable.

---

### Post by VastOne on 2009-07-19
> **Paddy Landau said:**
> Good point. Thanks for bringing it up!

Does anyone know of an alternative for ext4? [FSArchiver]("http://www.fsarchiver.org/") is still under development and cannot be considered reliable.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by lavinog on 2009-07-19
> **akimatsu123 said:**
> hi, i just installed a fresh copy of vista ultimate, and it was such a pain i would hate to do it again. so, i want to use dd to backup this partition, but i don't know how. 


Vista is really weird when it comes to partition manipulation.
There is a chance that if you don't restore the vista partition in the same order, it wont work.
I moved my vista partition once and had to reinstall, because  vista relabeled the partition as a new drive letter, and the uac doesn't work if it doesn't have the correct drive letter. Since UAC wasn't working I couldn't edit the registry to fix the one registry key causing the issue. And Vista's recovery disk doesn't have a registry editor like XP's had.

I downloaded all the programs I had to install afterwards and archived them, so that if I have to reinstall again, I just run everything in that folder.

---

### Post by akimatsu123 on 2009-07-20
> **lavinog said:**
> Vista is really weird when it comes to partition manipulation.
There is a chance that if you don't restore the vista partition in the same order, it wont work.
I moved my vista partition once and had to reinstall, because  vista relabeled the partition as a new drive letter, and the uac doesn't work if it doesn't have the correct drive letter. Since UAC wasn't working I couldn't edit the registry to fix the one registry key causing the issue. And Vista's recovery disk doesn't have a registry editor like XP's had.

I downloaded all the programs I had to install afterwards and archived them, so that if I have to reinstall again, I just run everything in that folder.

But otherwise it worked? I have UAC disabled, so hopefully that won't be a problem. Another thing that worries me, what about windows activation? is there any problems with that? it seems to me like if it doesn't have protection against people duplicating HDDs then someone can just buy 50 of the same computers, buy one valid vista license, install and activate on one computer, then after its activated duplicate the hdd on all the other 49 computers...

---

### Post by lavinog on 2009-07-20
> **akimatsu123 said:**
>  what about windows activation? is there any problems with that? it seems to me like if it doesn't have protection against people duplicating HDDs then someone can just buy 50 of the same computers, buy one valid vista license, install and activate on one computer, then after its activated duplicate the hdd on all the other 49 computers...
Windows activation will know if it is a different computer. If you make a copy of a hd install and put that copy in the same physical machine, it will know it was the same machine you originally activated with...if you put it in another machine, or replace a couple of parts in the original machine, it will require re-activation.

There are many parts that have unique ids like your network card, your processor, hd...etc

---

### Post by decoherence on 2009-07-20
> **akimatsu123 said:**
> i presume **"dd if=/dev/hda1 of=~/Desktop/vista.bkup"** to backup and **"dd if=~/Desktop/vista.bkup of=dd if=/dev/hda1"** to restore is too simplistic?

thanks

Not too simplistic... the commands you list will probably work fine unless the disks you are using are very, very different.

Clonezilla is great, though.

---

