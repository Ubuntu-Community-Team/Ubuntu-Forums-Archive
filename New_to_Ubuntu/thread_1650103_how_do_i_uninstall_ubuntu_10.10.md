---
title: "how do i uninstall ubuntu 10.10"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by shiftman on 2010-12-21
Hi All,

Could someone please tell me how I uninstall Ubuntu 10.10 and give the full hard drive back to Windows Vista. I installed it using the i386 iso disc and taking the option of splitting the hard drive 50:50 Vista/Ubuntu dual boot. 
I have come to the conclusion that I dont like it and just want the comp back to how it was.

Many thanks

Paul

---

### Post by mastablasta on 2010-12-21
boot to vista and then go to disk manager
 
delete ubuntu partition from disk and then add it to your vista partition.

---

### Post by Verbeck on 2010-12-21
that^ and you'll also need a vista installation/recovery disk to fix the mbr

in recovery options, choose command prompt
type *Bootrec.exe /FixMbr*

---

### Post by Megaptera on 2010-12-21
1. Put the Windows Vista or Windows 7 installation disc or recovery disc in the disc drive, and then start the computer.
   2. Press a key when you are prompted.
   3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
   4. Click Repair your computer.
   5. Click the operating system that you want to repair, and then click Next.
   6. In the System Recovery Options dialog box, click Command Prompt.
   7. Type Bootrec.exe, and then press ENTER.

Note To start the computer from the Windows Vista or Windows 7 DVD, the computer must be configured to start from the DVD drive. For more information about how to configure the computer to start from the DVD drive, see the documentation that is included with the computer or contact the computer manufacturer.

---

### Post by shiftman on 2010-12-21
Thanks for the replys folks, I have deleted the Ubuntu partition via the disc manager but how do I assign it back to Vista, I have the Vista disc and performed the Bootrec.exe/FixMbr but the drive is still missing the deleted ubuntu bit, have I missed something ?

---

### Post by amjjawad on 2010-12-21
> **shiftman said:**
> Thanks for the replys folks, I have deleted the Ubuntu partition via the disc manager but how do I assign it back to Vista, I have the Vista disc and performed the Bootrec.exe/FixMbr but the drive is still missing the deleted ubuntu bit, have I missed something ?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That was supposed to be your first step.
Please, post back the result and wrap up the text with "CODE" tags or click "#".

ALL the instructions are inside that link.

---

### Post by Elfy on 2010-12-21
Deleting the partition does just that. You'll need to resize the win partition or create a win partition to use.

---

### Post by Elfy on 2010-12-21
> **shiftman said:**
> Thanks for the replys folks, I have deleted the Ubuntu partition via the disc manager but how do I assign it back to Vista, I have the Vista disc and performed the Bootrec.exe/FixMbr but the drive is still missing the deleted ubuntu bit, have I missed something ?

> **amjjawad said:**
> [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That was supposed to be your first step.
Please, post back the result and wrap up the text with "CODE" tags or click "#".

ALL the instructions are inside that link.

What possible help would that be.

Deleting the partition and making sure that the win bootloader is reinstalled is needed.

---

### Post by amjjawad on 2010-12-21
> **forestpiskie said:**
> What possible help would that be.

Deleting the partition and making sure that the win bootloader is reinstalled is needed.

> Originally Posted by **shiftman** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10263667#post10263667") 				
 				*Thanks for the replys folks, I have  deleted the Ubuntu partition via the disc manager but how do I assign  it back to Vista, I have the Vista disc and performed the  Bootrec.exe/FixMbr **but the drive is still missing the deleted ubuntu  bit, have I missed something** ?*


I thought he can't boot into Vista, that's all.

---

### Post by Verbeck on 2010-12-21
> **shiftman said:**
> ...and performed the Bootrec.exe/FixMbr but the drive is still missing the deleted ubuntu bit, have I missed something ?

there should be a space between Bootrec.exe and /FixMbr 'case its an option [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
and after you've deleted the partition from disk management, right click the c: drive and select 'expand'

---

### Post by shiftman on 2010-12-21
Ok guys im at a loss here, in the picture you can see the current state of my hard drive. This is the state of the drive after I initially deleted the Ubuntu partition. If I right click on 279.72 GB NTFS section it wont allow me to expand partition and if I right click on the green free space bit I get a delete partition and New simple volume options. 

If I click on delete partition it says "This is an Extended Partition, the partition will become inaccessible if you delete it, are you sure you want to delete it" so I select yes, then I get a box with "There is not enough space available on the disc(s) to complete this operation"

I have tried the Bootrec.exe /FixMbr and am still in the same state as the photo, the comp boots up ok and runs vista ok but with a big bit of the drive missing

im no comp expert so any ideas will be most welcome




[IMG]http://i911.photobucket.com/albums/ac319/BLOBFUT/Discmanagement1.jpg[/IMG]

---

### Post by shiftman on 2010-12-21
Its Ok Guys, I have sorted it now, thanks again :o

---

### Post by Verbeck on 2010-12-21
[s]i  remember posting a while ago.... where did it go :-k[/s]<looks like i had the tab open and didn't submit  ](*,)
anyway, glad you fixed it. my method was to use the live cd to delete the partition and then again using disk management to merge it

and dont forget to mark the thread as solved (under thread tools at the top)

---

### Post by john77eipe on 2010-12-21
I thought this was very easy. I always though we could do it by booting from the CD and formating the disk as NTFS.

---

### Post by Megaptera on 2010-12-21
> **shiftman said:**
> Its Ok Guys, I have sorted it now, thanks again :o

Please share how you fixed it in case anyone else can benefit from your solution.

Thanks.

---

### Post by beew on 2010-12-21
Next time ask that kind of question in the Windows forums. :)

---

### Post by arpanaut on 2010-12-21
> **beew said:**
> Next time ask that kind of question in the Windows forums. :)

What?   How Rude!

If we are going to encourage people to install and use Ubuntu, we should at least offer help to get them back to normal if it does not work out for them.

Nuff said.

---

### Post by Megaptera on 2010-12-22
> **arpanaut said:**
> What?   How Rude!

If we are going to encourage people to install and use Ubuntu, we should at least offer help to get them back to normal if it does not work out for them.

Nuff said.

I agree.

---

