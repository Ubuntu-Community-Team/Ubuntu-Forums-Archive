---
title: "XP not showing in GRUB"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by DElliottJr on 2009-03-09
please help! i installed 8.10 with the alternate cd (and still wont run :() but thats not the problem. i explicitly used the external hdd to install saving my internal hddrunning xp. when it gets to the last setup sreen it says another os was detected would like to set GRUB as your master boot loader it may or may not recognise microsoft xp (last time it did).is there amy way to boot windows manually from GRUB? i know (hope) i didn't erase i saw the two OS with two different partition names(sda1,sda2, sdb1...etc) and two different memory values before i formatted it! please help get my os back!because as of yet ubuntu is absolutley useless!

---

### Post by mikewhatever on 2009-03-09
Post the output of <sudo fdisk -l>.

---

### Post by DElliottJr on 2009-03-09
look deededee sorry i didnt realize that the post below mine was about the same subject again i apologize. but at least this chap can get into ubuntu and configure from there i cant even get that far! i have no idea what to do! can i perform these edits from a bash in grub or a terminal somewhere? rightnow i am on a friends computer and wont have access to the web without xp running on my computer. please any and all is very appreciated!

---

### Post by DElliottJr on 2009-03-09
Re: XP not showing in GRUB 

--------------------------------------------------------------------------------

Post the output of <sudo fdisk -l>.



where do i enter this command! i really have no idea! nobody has told me where i am to enter these command and once i know i'll never need to ask again!thank you so much!

---

### Post by s.dalas on 2009-03-09
> **DElliottJr said:**
> Re: XP not showing in GRUB 

--------------------------------------------------------------------------------

Post the output of <sudo fdisk -l>.



where do i enter this command! i really have no idea! nobody has told me where i am to enter these command and once i know i'll never need to ask again!thank you so much!

You put this command on the Terminal (Applications - Accessories - Terminal)

---

### Post by DElliottJr on 2009-03-09
yea yea got it!! :D i was able to use the fail safe terminal in ubuntu and it read back my partitions and there it is reading both my hard drives and ntfs is there!! yay!! now how can i boot from this?

---

### Post by DElliottJr on 2009-03-09
You put this command on the Terminal (Applications - Accessories - Terminal)
__________________
if i could access any applications or accessories i'd be in heasven!!!

---

### Post by s.dalas on 2009-03-09
> **DElliottJr said:**
> You put this command on the Terminal (Applications - Accessories - Terminal)
__________________
if i could access any applications or accessories i'd be in heasven!!!

Ok if you could enter the terminal "in any way" post the output here!

---

### Post by DElliottJr on 2009-03-09
Disk /dev/sda:20.0 Gb "  alot of!       " bytes
255 heads,63 sectors/track,2432 cyliders
units = cylinders of 16065*512=8225280 bytes
disk identifier: 0xc8000000

    device boot        start     end       blocks   id    system
/dev/sda1                1         5        40131   de   dell uti
/dev/sda2    *           6      2431     19486685   7   hpfs/ntfs


disk/dev/sdb: 320.0 Gb "   alot   of!     " bytes
255 heads,63 cylinders/track,38913 cylinders
unitd=cylinders of 16065*512=8225280
disk identifier: 0x41ffc810

   device boot        start     end       blocks   id    system
/dev/sdb1    *          1       38489   309862861  83      linux
/dev/sdb2            38490      38913     3405780   5    extended
/dev/sdb5            38490      38913     3405748+ 82   linux swap/solaris





hand written! i am on two different computers!!!

---

### Post by DElliottJr on 2009-03-09
wow that got all crunched together and hard to read!! i had put alot of space in there but it didn't read out to well

---

### Post by ivanvajar on 2009-03-09
You have 2 HDDs? Maybe boot order in BIOS is wrong?

---

### Post by ivanvajar on 2009-03-09
Do you remember where you installed GRUB?

---

### Post by DElliottJr on 2009-03-09
no i don't

---

### Post by ivanvajar on 2009-03-09
I see that you have two boot loaders installed. I have 2 boot loaders installed myself. Do you know how BIOS functions?

---

### Post by DElliottJr on 2009-03-09
well the basics yea but to go in and edit it no... but hope you could tell me!!;)

---

### Post by jestinjoy on 2009-03-09
Add this to to /boot/grub/menu.lst file

title WindowsXP
root (hd0,1)
savedefault
makeactive
chainloader +1

---

### Post by ivanvajar on 2009-03-09
Yeah, type

sudo gedit /etc/grub/menu.lst

go to the end of page and add

title WindowsXP
root (hd0,1)
savedefault
makeactive
chainloader +1

You should see lines similar to the ones you are supposed to type in. Look closely. They are near the end of the file.

---

### Post by DElliottJr on 2009-03-09
/etc/grub/menu.lst


i want to write this in an open terminal as it is shown here.. no sudo in front or file name?

---

### Post by ivanvajar on 2009-03-09
sudo gedit /etc/grub/menu.lst

---

### Post by jestinjoy on 2009-03-09
no /boot/grub/menu.lst is the right one

---

### Post by ivanvajar on 2009-03-09
OOOPS! 

sudo gedit /boot/grub/menu.lst

What the hell was I thinking?!!!! This was on my mind from another topic. Won't happen again :-)

---

### Post by jestinjoy on 2009-03-09
Open the terminal and type 
```

sudo gedit /boot/grub/menu.lst
```

It will ask for the password and and after that.....gedit(the editor) will open in a new window....add the lines given below to the that file and save

```
title WindowsXP
root (hd0,1)
savedefault
makeactive
chainloader +1
```

REBOOT the system and tell what happens:)

---

### Post by ivanvajar on 2009-03-09
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a402acd6-2cd7-4913-8739-4a215009c413 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a402acd6-2cd7-4913-8739-4a215009c413 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet
[B]
THIS IS WHERE YOU ADD IT[/B]

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by DElliottJr on 2009-03-09
well i am currently re-installing using hardy heron in safe graphics mode someone pointed me to a bug in my graphics card that needs attention!! once this is de-bugged i can reset my boot order(or who knows maybe the new install with different version will auto fix it!) thank you again for all your help! i hope to one day be there on that end helpin out and givin it back!

---

### Post by ivanvajar on 2009-03-09
Ubuntu!

---

### Post by DElliottJr on 2009-03-09
it worked!!! i reinstalled hardy and xp is back in my boot order excellent!!!!!!!

---

### Post by mikewhatever on 2009-03-09
> **ivanvajar said:**
> ## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a402acd6-2cd7-4913-8739-4a215009c413 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a402acd6-2cd7-4913-8739-4a215009c413 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet
[B]
THIS IS WHERE YOU ADD IT[/B]

### END DEBIAN AUTOMAGIC KERNELS LIST

It's better to add the Windows entry after the ### EDN DEBIAN ..., because if it is inside, the entry gets deleted with every kernel update.

---

