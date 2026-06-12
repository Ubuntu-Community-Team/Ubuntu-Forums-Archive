---
title: "uninstall ubuntu"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by ravipanwar on 2010-08-23
i want to uninstall ubuntu and want to install windows xp in place of it..i had installed ubuntu onn the netbook..please help me..also in ubuntu i am not getting my other drives they are hidden...please help me to uninstall ubuntu .....please please:mad::mad::mad::mad::mad::mad::mad::mad:

---

### Post by silverglade00 on 2010-08-23
Just pop in your Windows XP CD and install. You do not need to uninstall Ubuntu first because XP will just write over it.

---

### Post by ravipanwar on 2010-08-23
but i have installed ubuntu on netbook and i dont know the procedurre to uninstall ubuntu.........and please tell me step by step procedure....i will be very thankful to u fr ur support...

---

### Post by Paul820 on 2010-08-23
You **can't** uninstall an operating system. silverglade00 has already told you what to do. Put your xp disc in and install windows.

---

### Post by Calash on 2010-08-23
If you have a CD drive then the process is exactly as was posted.  Boot from your Windows XP cd and tell it to use your entire hard drive.  Unless you used WUBI there is no uninstall process, just overwrite.

If you do not have a CD drive things get a lot more complicated.  Your best bet will be to find or borrow a USB CD drive and work from that.

---

### Post by ravipanwar on 2010-08-23
i have no usb cd drive..but i have heard abt the installation by making usb bootable..so pls tell me abt the procedure to install xp using usb pen drive...i m really frustrated...pls help me.........:(..

---

### Post by Calash on 2010-08-23
USB installing of Windows XP is out of scope for a Linux forum.

I found the following on Google.  It may be able to help you

[http://liliputing.com/2008/04/install-windows-xp-on-mini-note-usb.html](http://liliputing.com/2008/04/install-windows-xp-on-mini-note-usb.html)

Here is the link to the Google search, there are a ton of resources there.

[http://www.google.com/search?q=How+to+install+Windows+XP+via+USB](http://www.google.com/search?q=How+to+install+Windows+XP+via+USB)

---

### Post by ravipanwar on 2010-08-23
so if i cannot uninstall ubuntu then please how can i access my other drives ...i am not able to access the other partition after the unix install ....in disk utility it is showing they are unmounted and when i try to mount them it shows error...please help...otherwise tell me which other linux os can i install on my dell 1012 mini.

---

### Post by pricetech on 2010-08-23
Can you purchase or borrow a USB CD drive ??  That's your best way to install XP.

You won't actually be prompted to use the entire drive, it's just not worded that way.  The XP install is intuitive enough though, that if you follow instructions at all, you can install it just fine.

---

### Post by beew on 2010-08-23
Installing Windows XP with USB is tricky. There are many tutorials but if you read the comments it seem to be a hit and miss process. It seems that Windows is just not a very portable OS. Your best bet is to get a usb CD drive AND a windows XP disk somehow (I don't think you would have one if you buy a netbook). 

If your netbook supports booting from usb you should be able to access the hidden partition by booting to a live Ubuntu usb and then use gparted from there.

Why bother with XP? Ubuntu is much better. :)

---

### Post by uRock on 2010-08-23
Did you install via Wubi? How did you install Ubuntu?

---

### Post by ravipanwar on 2010-08-23
so if ubuntu is easy then why i am not able to access my other drives...in disk editor it shows they are unmounted so pls tell me hw to make them accessible....

---

### Post by beew on 2010-08-23
I just suggested one way. Use garted with a live usb.

---

### Post by uRock on 2010-08-23
What other drives do you have? We are under the impression that you wrote over Windows with Ubuntu. Do you have an external drive connected? Have you went into the Places menu and clicked on the other partitions, if they are listed? 

How did you install? Did you use Wubi or did you install into a partition?

---

### Post by ravipanwar on 2010-08-23
this was my first experience with any linux installation now i am stuck here and  i m frustrated...i hv heard lot abt ubuntu netbook and its easiness  but now i am not able to access my other drives so please help me to access my other drives...

---

### Post by Elfy on 2010-08-23
> **ravipanwar said:**
> so if ubuntu is easy then why i am not able to access my other drives...in disk editor it shows they are unmounted so pls tell me hw to make them accessible....

How about running this command from a terminal and then pasting it here so people can see what drives it is you are talking about.

```
sudo fdisk -l
```

---

### Post by uRock on 2010-08-23
> **beew said:**
> I just suggest one way. Use garted with a live usb.
How is Gparted going to help the OP to connect to his/her other drives? How will the OP run a LiveCD without a CD drive?

> **forestpiskie said:**
> How about running this command from a  terminal and then pasting it here so people can see what drives it is  you are talking about.

```
sudo fdisk -l
```
Thanks for posting that and "good now."

---

### Post by ravipanwar on 2010-08-23
these were my internal partitions ....in my previous window xp i had c, d and e drives....but i installed ubuntu netbook on c drive removing windows xp and now i am not able to access my other 2 drives (d and e in windows xp)..it shows unmounted in ubuntu disk utility...so what should i do to make them accessible even on ubuntu...i do n't care if even i have to format thos drrives because i have no important data onn those drives...but tell me how to make them accessible on ubuntu

---

### Post by ravipanwar on 2010-08-23
this is what ii got after typing in teerminal----




Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8924    71678976   83  Linux
/dev/sda2   *        8924        8937      102400   82  Linux swap / Solaris
/dev/sda3            8938       30401   172409580    b  W95 FAT32

Disk /dev/sdc: 4135 MB, 4135583744 bytes
128 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7936 * 512 = 4063232 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1017     4035425    c  W95 FAT32 (LBA)
ravi@ravi-laptop:~$

---

### Post by Elfy on 2010-08-23
You can install a couple of things to make it easy to mount them - pysdm is one.

[http://ubuntuforums.org/showpost.php?p=5470813&postcount=1](http://ubuntuforums.org/showpost.php?p=5470813&postcount=1)

Though what that has to do with removing ubuntu and installing I fail to see.

If you want help installing xp from a usb then you need to look elsewhere for help - this is not a windows  forum.

---

### Post by beew on 2010-08-23
URock

> How is Gparted going to help the OP to connect to his/her other drives? How will the OP run a LiveCD without a CD drive?Use a live usb. I think most newer netbooks do support booting from usb.  No, I never use a liveCD and I never told the OP to use one. Read my original post.  LiveCD  is obsolete technology man. :)

---

### Post by Elfy on 2010-08-23
> **beew said:**
> No, I never use liveCD, it is obsolete technology man. :)

Righto - that's me lost then ... 

The point urock was making was that using a live iso is not going to be of any use in mounting partitions in an install. All that needs to be done is some entries to fstab

---

### Post by Elfy on 2010-08-23
Stop all the back and forth now - it's not going to help the OP - it will just get confusing.

---

### Post by uRock on 2010-08-23
Have you tried going through the Places menu and clicking the file systems for those partitions? 

I realize that Ubuntu Netbook Edition has a different menu, but the file systems should be listed under the Places menu and once you click on them, then the system will mount them, unless these are supposed to be hidden partitions used by the manufacturer for booting and restoring the system.

---

### Post by beew on 2010-08-23
> The point urock was making was that using a live iso is not going to be  of any use in mounting partitions in an install. All that needs to be  done is some entries to fstab

 I have repartioned my installed Ubuntu systems using gparted with a liveusb. The OP doesn't say exactly what he meant by cannot access a partition. It maybe that it is not formatted or not formatted the right way.

---

### Post by ravipanwar on 2010-08-23
because of this drive problem i want to uninstall ubuntu.....i know this is nt a window forum....bt  u shud understand my problem....i m nt blaming ubuntu fr this....ubuntu is gud os and i wud even say that better than windows xp....but this drive problem has frustrated me thats why i want to uninstall ubuntu....
bt if my problem of drives is solved than i wud love to use ubuntu...
u shud understand that my hdd space of around 200 gb is not accessed by me now....so any person with some common sense wud do try to undo the step which has caused d problem (or it might b some bad luck ...not blaming ubuntu)....so i m in need of help ..thats why i have came to ubuntu nt window forum..

---

### Post by Elfy on 2010-08-23
read post #20 and follow it

---

### Post by Calash on 2010-08-23
> **ravipanwar said:**
> so if i cannot uninstall ubuntu then please how can i access my other drives ...i am not able to access the other partition after the unix install ....**in disk utility it is showing they are unmounted and when i try to mount them it shows error**...please help...otherwise tell me which other linux os can i install on my dell 1012 mini.


Follow the instructions linked in post #20 as suggested.  If they do not help you access the drive we need to know what the error is that you are getting so we can help.

---

### Post by ravipanwar on 2010-08-23
i have installed the s/w u mentioned n installed it nn followed the steps nw at last i am able to access the unmounted drive...
thanx frr ur help u rock men....thank u fr all the help at last my problem solved....thank u very much now i can fully enjoy ubuntu....

ubuntu rocks ..:)
ubuntu forum rocks.....:):):)<3

---

### Post by uRock on 2010-08-23
Awesome, glad you got it working, feel free to ask question about other stuff that you may need help with.

---

### Post by Elfy on 2010-08-23
> **ravipanwar said:**
> i have installed the s/w u mentioned n installed it nn followed the steps nw at last i am able to access the unmounted drive...
thanx frr ur help u rock men....thank u fr all the help at last my problem solved....thank u very much now i can fully enjoy ubuntu....

ubuntu rocks ..:)
ubuntu forum rocks.....:):):)<3

Excellent - have fun.

---

### Post by ravipanwar on 2010-08-23
guys a problem is still there iam getting icon of the partition but nw i cannot copy files in it ...please help me in this regard....

---

### Post by Elfy on 2010-08-23
Run this 

```
gksudo nautilus /media
```

Right click the partition - Properties - Permissions tab 

Change permission from Root ( a guess) to your user

---

### Post by ravipanwar on 2010-08-23
whenn i typed the same cmmand that u have written it open a window and says
' please check the location u typed correctly and try again'

---

### Post by Elfy on 2010-08-23
Sorry - been up for too long ... 

```
gksudo nautilus /media
```

---

### Post by ravipanwar on 2010-08-23
forestpiskie thank u very much.....:)
at last al things are working .....you are helpful friend thanx fr ur kind patience.....:)
three cheers for my frnd fforest :) :) :)

---

