---
title: "Wipe"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by rosswmcgee on 2010-01-01
If I do a clean install no partition/ and later wish to install via the recovery disc of win 7 will it do it?


I have used Ubuntu for years and just can not see Windows, the maintenance, the virus, etc.

---

### Post by sandyd on 2010-01-01
if you wipe everything from the computer and do that, yes, it will reinstall.
it also reinstalls if you have a ntfs volume somewhere on your drive.

---

### Post by rosswmcgee on 2010-01-01
What is an ntfs volume? Please and Thankyou.


Example win 7 takes 3 recovery discs. I made one and verified it.The second stalled on the verify so the whole process has to

be started over 1 2 3. The time I spent so far Ubuntu could have been burned, installed and up and running. Thats one reason why Ubuntu is so much easier.

---

### Post by rosswmcgee on 2010-01-03
So I installed Ubuntu inside Win 7 using that option. I find every thing works well

except the screen seems a wee blurry, and get this one, the mouse will not open

articles on the Drudge report, how wierd is that? Other sites no problem. 

Why blurry screen with Ubuntu, but when I use the Win 7 not blurry. Again I used the install Ubuntu within win 7 option.

---

### Post by Bartender on 2010-01-03
Your original question is one I wish I understood better.

I can tell you for sure that my Acer 5920 laptop (2006) came with 4 primary partitions.  Vista on one, and a confusing mish-mash of partitions that had something to do with recovery and the recovery utility.  I made the recovery discs, screwed up Vista, reinstalled, the discs deleted all the previous partitions and created just one partition with Vista.  It was simple to dual-boot Vista after that.

I know that HP (at least a year or two ago) said right in their user manual that after you made your recovery discs you could delete the recovery partition because the process of making the recovery discs somehow makes the recovery partition inaccessible from then on.

However, I've read posts on this forum from people stating that even if you make recovery discs, the discs still need to access the recovery partition.  That doesn't make much sense to me (if your HDD failed, where would that leave you?) but that's what they were saying.

In other words, it would seem there are several different schemes being implemented by different manufacturers.  So you need to find out for sure how yours works by visiting the manufacturer's website, joining a forum that's more specific to that manufacturer, googling, etc.

---

### Post by warfacegod on 2010-01-03
> What is an ntfs volume? Please and Thankyou.

NTFS is a Microsoft proprietary (they made it/own it) file system. If you go to Computer in Places look at the properties of your hard drive you will see somewhere it says ext3 or ext4. Those are file systems that linux uses.

So to answer your question. An NTFS volume is a way of saying: "I have a hard drive or a partition on a hard drive that is formated with NTFS.

FYI. NTFS stands for New Technology File System. It's been in use since the late '90s I believe (not very new any more) and I'm surprised Microsoft is still using it as their default file system.

---

### Post by Manyette on 2010-01-03
Just be sure that you know: The Win 7 DVD's will format your disk, and leave nothing on the disk but Win 7.  And do not depend on the "recovery" partition, because it cannot re-install win 7 after ubuntu has used it, because of the change of sector size on the disk, and it does NOT reformat the disk.

---

### Post by rosswmcgee on 2010-01-03
I have existed for years without windows/just linux/ the only reason to do it this

way is to not void the mgg warranty. Otherwise I would be 100% Linux. I think emachines has a recovery partition. However if for some reason the OS crashed I would just install Ubuntu.

So now for some reason after running the Live CD/ the Drudge page works again/ it was probably a left wing conspiracy.LOL

---

### Post by 3rdalbum on 2010-01-03
If the whole screen looks blurry, then you haven't selected your monitor's native resolution in Ubuntu's "Display Properties" program.

---

### Post by warfacegod on 2010-01-03
> **rosswmcgee said:**
> I have existed for years without windows/just linux/ the only reason to do it this

way is to not void the mgg warranty. Otherwise I would be 100% Linux. I think emachines has a recovery partition. However if for some reason the OS crashed I would just install Ubuntu.

So now for some reason after running the Live CD/ the Drudge page works again/ it was probably a left wing conspiracy.LOL

I don't think a manufacturer can void the warranty because you switched your OS from windows to linux. The operating system has nothing to do with with your hardware if it should fail. The manufacturer is responsible for replacing failing or defective hardware (under warranty time period) regardless of what you do software wise.

You should carefully read your entire warranty manual in case I'm wrong about something.

---

### Post by rosswmcgee on 2010-01-03
The display is fine. I just see a word with perhaps the last two letters faded. And now the Drudge articles won't open 

again. I may just do a complete clean install of Ubuntu because Ubuntu is not working as well as a shared computer.

---

### Post by rosswmcgee on 2010-01-03
Found blurry screen caused by graphic drivers that came installed/ went to applications/ removed them/ all is well. I am not really hep to all the nividia stuff.

---

### Post by Bartender on 2010-01-03
ross -
You see what I mean about recovery discs.  You got some conflicting information in the last few posts, such as the guy saying your recovery partition would be worthless.

I tell you what, I don't know for sure how your recovery discs work, but mine _didn't_ rely on the recovery partition.  The DVD's that were created from the Acer recovery utility erased the recovery partition and made one big Vista partition out of the four partitions.

I'll tell you something else that I know for a fact works on some machines, but can't tell you for sure it'll work on yours.  Some people have wiped their drives clean, created a primary NTFS partition out of part of the drive, leaving the rest of the drive unformatted or formatted as ext.  Then they tossed the Vista recovery partition in and re-booted.  The recovery DVD's installed Windows to the NTFS partition, leaving the rest of the drive free for Ubuntu.

So don't let anyone tell you what cannot be done with the recovery discs and recovery partition unless they have experience with the same PC (or at least from the same manufacturer and similar vintage) as yours.

---

### Post by rosswmcgee on 2010-01-03
Hey thanks! I did notice that. After cleaning up windows 7 into a way that I can tolerate, it's not so bad. I did install Ubuntu 9.10 again allowing Ubuntu to do the 
partion. The only problem I have now is that for some reason Opera is not working properly, when it comes to the Drudge website it will not open the articles, yet it works fine on other sites and in Win 7. How weird. At some point I will probably just do a complete HD
clean install of Ubuntu. I have not used Windows for years.

---

### Post by rosswmcgee on 2010-01-05
You are right as far as I can tell. I deleted ubuntu using win 7/ran recovery disks
using two different options. The tried to boot up and always got stuck with grub error and could not get past it to boot win 7. Oh well I am perfectly happy with an
ubuntu clean install and do not need the win 7 any way. I goofed though because I kept trying to fix the display in Ubuntu which was fuzzy in the dual boot, but not in Win 7. Now I know that I would have just needed to adjust the display when running
in Ubuntu. Lessons learned.

---

### Post by Bartender on 2010-01-05
Vista is different than 7.  I don't understand all the differences, nor how they interrelate, but reinstalling Vista would have wiped GRUB from the MBR and installed the Windows data in its place.  7, as far as I understand it, uses the MBR to place data essential for start-up too, so it's a mystery to me why reinstalling did not flush GRUB from the MBR.

Glad to hear that you got the display figured out in Ubuntu.

---

### Post by rosswmcgee on 2010-01-05
I think I read some where  that It is hard to get the grub off once Ubuntu is installed. Windows 7 is nice, but for me I had to clean it up get rid of all the installed garbage, install Open Office, AVG, FF Opera, you still are opening up the
virus opportunity, so at least I got to check it out. Ubuntu is simpler in my opinion
where Mossberg says its only for geeks is beyond me.

---

### Post by Bartender on 2010-01-05
It's not hard to get GRUB off.  GRUB Stage 1 tweaks or replaces the WIndows MBR, which is a dinky little packet of data at the very front of the HDD.  Windows is usually happy to overwrite GRUB when installed.  That's why I'm at a loss to explain why an installation of any Windows OS didn't overwrite the MBR.

Unless your GRUB Stage 1 wasn't installed to the MBR, but to some other partition??

I don't know who Mossberg is.  As far as I'm concerned, the only truth is this: don't believe anyone spouting generalities.  There are plenty of Ubuntu installs that went flawlessly, and plenty that didn't.  We have uber-geeks running Linux, and grandmas too.  Probly fair to say that the grandmas had the advantage of a geeky son or grandson to do the initial install, but still.

---

### Post by Son of William on 2010-01-05
"I don't know who Mossberg is."

Mossberg is a Wall Street Journal technology columnist.  His reputation is that of an unabashed lover of things made by Apple Computer.

"As far as I'm concerned, the only truth is this: don't believe anyone spouting generalities."

Very true.

I know from personal experience, however, that a Windows 7 install does not automatically wipe all other operating systems.  If you choose the wrong options it can -- but that is true of Ubuntu as well.

On the other hand, it is virtually certain that a Windows 7 recovery or install will foul up grub 2 and require a grub repair.

---

