---
title: "Help uninstalling Ubuntu"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by letters on 2008-12-26
Hello

I was recently running Windows Vista, but decided to download Ubuntu LiveCd and Install Ubuntu. I would like to go back to Windows Vista. I was wondering how I would uninstall Ubuntu. Ive tried to insert my Windows recovery cd, but once it loads.. it says Error there is no partition. Can someone please help me. Thank you very much.

:confused:

---

### Post by oilchangeguy on 2008-12-26
> **letters said:**
> Hello

I was recently running Windows Vista, but decided to download Ubuntu LiveCd and Install Ubuntu. I would like to go back to Windows Vista. I was wondering how I would uninstall Ubuntu. Ive tried to insert my Windows recovery cd, but once it loads.. it says Error there is no partition. Can someone please help me. Thank you very much.

:confused:

boot from the live cd. go to system, admin, partition manager. then delete all ubuntu partitions. then you'll have a hard drive with unallocated space. windows should see it just as a new hard drive, blank.

---

### Post by letters on 2008-12-26
> **oilchangeguy said:**
> boot from the live cd. go to system, admin, partition manager. then delete all ubuntu partitions. then you'll have a hard drive with unallocated space. windows should see it just as a new hard drive, blank.


in gparted there are 3 partition my harddrive and 2 others... swap.. just delete all partitions ok.

---

### Post by swoody on 2008-12-26
Do you still have Windows installed on your computer? Or did you do a clean install of Ubuntu taking up the entire disk? When you start your computer, does it still give you the option to boot into Windows, or does it just give you the option to boot into Ubuntu? 

Start Ubuntu, and open a terminal (On main menu click on Applications > Accessories > Terminal)

Then type in to the terminal: 
```
sudo fdisk -l
``` 
and paste the results here.

---

### Post by oilchangeguy on 2008-12-26
> **letters said:**
> in gparted there are 3 partition my harddrive and 2 others... swap.. just delete all partitions ok.

yes, you want a blank hard drive.

---

### Post by oilchangeguy on 2008-12-26
> **woody86 said:**
> What option did you select when you installed Ubuntu? It sounds like you may have selected "Use entire Disk" and it may have completely ovoerwritten your Windows installation. 

Start Ubuntu, and open a terminal (On main menu click on Applications > Accessories > Terminal)

Then type in to the terminal: 
```
sudo fdisk -l
``` 
and paste the results here.

why would the op need to do this. they've already stated they want to uninstall ubuntu, and install windows again. so it does not matter how ubuntu was installed.

---

### Post by kansasnoob on 2008-12-26
> **letters said:**
> in gparted there are 3 partition my harddrive and 2 others... swap.. just delete all partitions ok.

If you can still boot Ubuntu post the output from terminal of:

```
sudo fdisk -l
```

I have a notion that you're mad because you lost Win!

I'm curious why you're leaving, and more curious why you jumped in with both feet!

It's much better to start with Wubi or a dual-boot!

---

### Post by swoody on 2008-12-26
> **oilchangeguy said:**
> why would the op need to do this. they've already stated they want to uninstall ubuntu, and install windows again. so it does not matter how ubuntu was installed.

Well, technically he didn't say he wanted to 'reinstall' Windows, he may be dual-booting Windows/Ubuntu. If that's the case, then he needs to delete his Ubuntu partitions, and repair his MBR. He said in gparted it shows 3 partitions, these could be his Ubuntu partition, swap, and his Windows partition.

If he just installed Ubuntu and completely erased his hard drive of Windows, then yes, he would just need to delete his partitions and reinstall. By running the sudo fdisk -l command I was going to see whether his Windows partition still exists (dual-booting), and if it does then we need to find out why his Restore Disk is not recognizing it.

---

### Post by oilchangeguy on 2008-12-26
> **woody86 said:**
> Well, technically he didn't say he wanted to 'reinstall' Windows, he may be dual-booting Windows/Ubuntu. If that's the case, then he needs to delete his Ubuntu partitions, and repair his MBR. If he just installed Ubuntu and completely erased his hard drive of Windows, then yes, he would just need to delete his partitions and reinstall. By running the sudo fdisk -l command I was going to see whether his Windows partition still exists (dual-booting), and if it does then we need to find out why his Restore Disk is not recognizing it.

it's a safe bet, that if the windows cd is not finding a partiton. then there is no ntfs partition, meaning windows is gone.

---

### Post by letters on 2008-12-26
Ive booted with the livecd. in gparted ive deleted the ubuntu partition.. but there are 2 other with key symbols beside them which i cant delete. i can boot the recovery cd. but it still says there is no partition. i think when i was installing ubuntu it installed over windows vista.

---

### Post by oilchangeguy on 2008-12-26
> **letters said:**
> Ive booted with the livecd. in gparted ive deleted the ubuntu partition.. but there are 2 other with key symbols beside them which i cant delete. i can boot the recovery cd. but it still says there is no partition. i think when i was installing ubuntu it installed over windows vista.

you need to unmount the hard drive. right click on the drive and select unmount.

---

### Post by letters on 2008-12-26
> **oilchangeguy said:**
> you need to unmount the hard drive. right click on the drive and select unmount.

i cannot unmount ive deleted the partition. here is a screenshot  after i deleted the 1st partition.

[IMG]http://img19.picoodle.com/img/img19/3/12/26/f_gpartedm_49012db.png[/IMG]

---

### Post by oilchangeguy on 2008-12-26
try this ( i don't know if it's the same in vista) boot from the windows cd, once it loads press r to enter the repair console. then at the prompt type diskpart and press enter. from there you can delete any partitons, and create a new one. then format the drive, and install windows.

---

### Post by swoody on 2008-12-27
If you're having problems with gparted, you could always try to Nuke it!
[http://www.dban.org/](http://www.dban.org/)
This will remove the partitions, and leave your drive squeaky clean ;)

---

### Post by letters on 2008-12-27
Ive installed winxp... now windows vista is installing. thank you for all the help. :popcorn:

---

