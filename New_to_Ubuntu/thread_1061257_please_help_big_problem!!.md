---
title: "please help big problem!!"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by matthewbrave on 2009-02-05
ok i have a laptop with a 40gb internal hdd in it. it has winxp home on it sp3.

i also have an external usb wd hard drive 250gb

i edited the partition on the external hdd to it was 150gb for windows files etc. and 100gb for ubuntu(2gb swap)


after the install i took the disc out as it directed and then it rebooted in to grub.

i elected windows xp. it loaded up all ok and i checked if all my origional files were there, which they were.

i then safley removed the ex-hdd and rebooted. i was expecting it to boot stright in to wondows and no grub, bt grub was there and it came up with error 21, which means squat to me.

i then switched off and pluged the hdd back in and it still says error 21.

when i installed ubuntu i was expecting to have to use my bios   (F12) to select either my internal hdd or usb device not grub.


how do i get back in to wndows and to remove grub so i can use the bios to select the boot.



thanks.

---

### Post by matthewbrave on 2009-02-05
ok this is really weird, i have just swiched it back on and grub was working, hooray! but is there a way to boot in to windows when the external hdd isnt pluged in?

---

### Post by 2hot6ft2 on 2009-02-05
You're wanting to restore the MBR so here's how.

> **Monotoko said:**
> Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

That will fix XP right up :)

You posted while I was getting that info for you.

Unless you have the option in your BIOS to where you can set it to boot the external first and just install the grub on the external so you'll get the grub when the external is set to boot first (and plugged in and turned on).

That would mean restoring the MBR on the internal so xp would start normally when the external isn't plugged in.

---

### Post by matthewbrave on 2009-02-05
so how would i go aout instaling the grub on the external.


recovering xp and then what?

---

### Post by matthewbrave on 2009-02-05
oh and i do have the option in my bios

---

### Post by 2hot6ft2 on 2009-02-05
First what do you get from
```
sudo grub
find /boot/grub/stage1
```
in a terminal?

So we can see how you partitioned it
```
grub> quit
```
when you're done

---

### Post by albinootje on 2009-02-05
> **2hot6ft2 said:**
> First what do you get from
```
sudo grub
find /boot/grub/stage1
```
in a terminal?

So we can see how you partitioned it


Please post the output of 
```

sudo fdisk -l

```
too.

---

### Post by matthewbrave on 2009-02-05
ok i am going to repare windows first

---

### Post by matthewbrave on 2009-02-05
ok xp is repared and boots fine now.

---

### Post by matthewbrave on 2009-02-05
the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd1,4)

grub>

---

### Post by matthewbrave on 2009-02-05
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x685e4495

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18237   146484544+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2           18238       30401    97707330    5  Extended
/dev/sdb5           18238       30151    95699173+  83  Linux
/dev/sdb6           30152       30401     2008093+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by 2hot6ft2 on 2009-02-05
Hi albinootje. Check this for mistakes before he does it please.

With the external hooked up and on
boot from the livecd, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit

```
And that's all it should take.

Make sure the drive and it's partitions are mounted before using the commands.

---

### Post by matthewbrave on 2009-02-05
so mount my xp one my xp things on the ex hdd and the ubuntu install on the external hdd

---

### Post by 2hot6ft2 on 2009-02-05
> **matthewbrave said:**
> so mount my xp one my xp things on the ex hdd and the ubuntu install on the external hdd
Just go to places and make sure the partitions on the external are mounted. It wont matter about mounting windows since it's the external we want to write the grub to.

---

### Post by matthewbrave on 2009-02-05
ok done that now

shall i reboot and use grub in to windows then unplug the hdd and reboot and not see grub and stright in to windows

---

### Post by 2hot6ft2 on 2009-02-05
Yes it should be all set now. Let me know if there's any problem.

---

### Post by matthewbrave on 2009-02-05
xp works perfectly as the internal hdd is set to boot first but when i press F12 to select boot device and i choose ubs mass storage grub loads and returnes error 22

---

### Post by matthewbrave on 2009-02-05
should i move the usb hdd up in the bios so it will auto boot first then the internal hdd

---

### Post by caljohnsmith on 2009-02-05
When you boot your USB drive, do you get the Grub menu, and then when you try to boot Ubuntu you get the Grub error 22? If so, most likely you just need to tweak your Grub's menu.lst file. So if you do get the Grub menu, how about trying this: select the Ubuntu entry you want to boot, press "e" to edit it, select the line that says "root (hd1,4)", press "e" to edit it, change it to "root (hd0,4)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hd1,4)" to use the (hd0,4) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by 2hot6ft2 on 2009-02-05
Yes, that's what I thought you did to get the error 22 in your previous post.

---

### Post by 2hot6ft2 on 2009-02-05
Thanks caljohnsmith. I keep getting "Database error" from the forum when trying to post. Connection must be messing up

---

### Post by matthewbrave on 2009-02-05
i solved the error by putting the usb drive first in the boot sequence, but i now have another problem when i am in ubuntu. when i log in it is all blured and i can see 3-4 mice moving in cordination to me moving the mouse.

is there a way to change the screen so i can see properly. also ubuntu thinks my screen is big when it isnt and the login screen(not blured) is in the bottom right hand side when t is supposed to be in the middle.

---

### Post by 2hot6ft2 on 2009-02-05
That's why I asked for someone to check the commands before he ran them. So does booting the external first make it hd0?
Whereas if booting the internal first would make the external hd1 and the internal hd0?

---

### Post by matthewbrave on 2009-02-05
everything works but ubuntu is blured thats all but only when i log in

---

### Post by 2hot6ft2 on 2009-02-05
> **matthewbrave said:**
> everything works but ubuntu is blured thats all but only when i log in
Just at the login screen? Or is it still messed up once you're at the desktop as you described a couple minutes ago too?

---

### Post by matthewbrave on 2009-02-05
the login screen isnt blured but it is in the bottom right of my screen not central, it is only blured when i have typed my password in

---

### Post by matthewbrave on 2009-02-05
i have to go off to my bed now it is getting late.


i will get back to it tomorrow, but thanks for your help so far.

please carry on leaving posts so i can pick up on them tomorrow

---

### Post by 2hot6ft2 on 2009-02-05
> **matthewbrave said:**
> the login screen isnt blured but it is in the bottom right of my screen not central, it is only blured when i have typed my password in
I'm not familiar with that happening. Sounds like a different issue.

I'm glad you got it booting up the way you were wanting. Did you have to change it to hd0 like caljohnsmith said or did it work after changing the boot order?

---

