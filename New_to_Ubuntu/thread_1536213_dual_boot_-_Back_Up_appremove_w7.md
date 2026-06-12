---
title: "dual boot - Back Up app/remove w7"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by TimEnid on 2010-07-21
so i am currently running w7 and ubuntu in dual boot. I want to get rid of w7. But, i will also be getting a new motherboard. So my question is, can i back up my ubuntu OS and reinstall when my new mobo arrives. I dont want to have to reinstall my apps again. But first, i want to completely wipe out w7. They are not installed on the same hd. I have ubuntu on one, and w7 on another. any suggestions?

---

### Post by ubunterooster on 2010-07-21
Put grub on the Ubuntu drive and format the Windows one. And why would you need to reinstall because of a new mobo?

---

### Post by Zeike on 2010-07-21
While a Windows installation would probably probably fail to boot if you switched out your mobo/cpu, Ubuntu should boot fine if it supports the new hardware.

---

### Post by TimEnid on 2010-07-21
> **ubunterooster said:**
> Put grub on the Ubuntu drive and format the Windows one. And why would you need to reinstall because of a new mobo?

> **Zeike said:**
> While a Windows installation would probably probably fail to boot if you switched out your mobo/cpu, Ubuntu should boot fine if it supports the new hardware.

yeah, im still in a windows state of mind. this is great news. i can swap mobo without having to reinstall. just the news i wanted. now, how should i go about putting grub on the ubuntu drive? i believe it is currently installed on the windows drive.

---

### Post by ubunterooster on 2010-07-21
The following shows how to reinstall grub
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by TimEnid on 2010-07-22
thanks for the directions. so should i remove the hd with windows on it from my pc, before installing grub to the ubuntu hd?

---

### Post by ubunterooster on 2010-07-22
> **TimEnid said:**
> thanks for the directions. so should i remove the hd with windows on it from my pc, before installing grub to the ubuntu hd?
Yes

---

### Post by TimEnid on 2010-08-03
> **TimEnid said:**
> thanks for the directions. so should i remove the hd with windows on it from my pc, before installing grub to the ubuntu hd?

> **ubunterooster said:**
> Yes
so if i remove the w7 hd, and add grub to the ubuntu hd, when i put my w7 drive back into my pc, will the grub on w7 hd not be detected?

while in ubuntu, can i format the w7 hd and then place grub on the ubuntu drive? if so, when i open gparted and try to format the w7 hd, the option for format is greyed out.

---

### Post by Keen101 on 2010-08-03
> **TimEnid said:**
> so if i remove the w7 hd, and add grub to the ubuntu hd, when i put my w7 drive back into my pc, will the grub on w7 hd not be detected?

while in ubuntu, can i format the w7 hd and then place grub on the ubuntu drive? if so, when i open gparted and try to format the w7 hd, the option for format is greyed out.

Thats a bit confusing the way you phrased that. But, yeah i think if you put the win7 drive back in after installing grub to the other drive, they should both work. It depends on which drive is Master and which is Slave. At that point they both should have Grub on them.

If you set your "new" ubuntu drive as master, then it wont prompt to boot win7, but if you mark win7 as master, you should be able to boot both like before.

I haven't needed gparted to format a drive in a while, but i think it might be greyed out either because you have the win7 drive still mounted, or you need to install some extra NTFS stuff, but you should be able to delete the win7 partition, or reformat as a linux format without that NTFS stuff. ...so try unmounting your win7 drive when booted into ubuntu.

---

### Post by TimEnid on 2010-08-03
> **Keen101 said:**
> Thats a bit confusing the way you phrased that. But, yeah i think if you put the win7 drive back in after installing grub to the other drive, they should both work. It depends on which drive is Master and which is Slave. At that point they both should have Grub on them.

If you set your "new" ubuntu drive as master, then it wont prompt to boot win7, but if you mark win7 as master, you should be able to boot both like before.

I haven't needed gparted to format a drive in a while, but i think it might be greyed out either because you have the win7 drive still mounted, or you need to install some extra NTFS stuff, but you should be able to delete the win7 partition, or reformat as a linux format without that NTFS stuff. ...so try unmounting your win7 drive when booted into ubuntu.

thanks. so how can i set my ubuntu hd as the master?

this is what i plan to do tonight:
install grub to my ubuntu hd - set it as master
remove thw w7 hd and boot the pc to make sure my ubuntu loads up properly
place the w7 drive back in and reformat it, somehow. 
Now heres the tricky part. After i have confirmed that ubuntu boots properly, and my w7 hd is blank and usable, i am going to replace my motherboard. from what is said above, i can just plug my ubuntu hd into the mobo, and all should be fine. 

how does this sound?

---

### Post by ubunterooster on 2010-08-03
All correct. :D

---

### Post by TimEnid on 2010-08-03
> **ubunterooster said:**
> All correct. :D
great, so last two questions:

how do i set my ubuntu hd as the master?

how do i format the w7 hd?

---

### Post by ubunterooster on 2010-08-03
I would just take out the w7 drive before reinstalling grub so there is no confusion. Often the motherboard decides which drive to boot from; often it has  labeled sata ports to simplify which has a higher priority.

In ubuntu go to system>administration>disk utility. The disk utility allows you to reformat a drive

---

### Post by TimEnid on 2010-08-03
> **ubunterooster said:**
> All correct. :D

> **ubunterooster said:**
> I would just take out the w7 drive before reinstalling grub so there is no confusion. Often the motherboard decides which drive to boot from; often it has  labeled sata ports to simplify which has a higher priority.

In ubuntu go to system>administration>disk utility. The disk utility allows you to reformat a drive
so if i remove the w7 drive, which has grub installed on it, how would the pc boot into ubunutu?

---

### Post by ubunterooster on 2010-08-03
> **TimEnid said:**
> so if i remove the w7 drive, which has grub installed on it, how would the pc boot into ubunutu?
I was thinking you would use the live CD to restore grub as in the following instructions (yes, they still apply even though you are not reinstalling windows): 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by TimEnid on 2010-08-03
> **ubunterooster said:**
> I was thinking you would use the live CD to restore grub as in the following instructions (yes, they still apply even though you are not reinstalling windows): 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


got it, thanks for all the help.

---

### Post by ubunterooster on 2010-08-03
You are welcome :)

---

