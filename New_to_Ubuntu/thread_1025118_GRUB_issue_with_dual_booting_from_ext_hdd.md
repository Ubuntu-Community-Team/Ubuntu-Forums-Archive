---
title: "GRUB issue with dual booting from ext hdd"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by barfobulator on 2008-12-29
I have Ubuntu 8.10 installed on an external USB hard drive. After installation, I notice that the computer will not automatically boot Windows from the internal hard drive when the USB drive is unattached. It tries to use GRUB, and won't let me boot anything until I plug in the USB and tell it which OS I want.

In BIOS, the computer is set to boot from CD, Removable Devices (the USB drive), and the internal hard drive, in that order. I would prefer that the machine boot Windows automatically if the USB drive is not present. Does anyone know how to fix this? 

If necessary, I would be perfectly willing to remove the GRUB system.

---

### Post by caljohnsmith on 2008-12-29
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by OldDogNewTricks on 2008-12-31
This thread should give you your fix.
[http://ubuntuforums.org/showthread.php?t=1018493](http://ubuntuforums.org/showthread.php?t=1018493)

Same problem is happening to many persons.  IMO, GRUB needs to be on the same disk as the MBR (master boot record), to avoid this issue.  I have WinXP on my main drive, and I'd like it to be able to boot without having to attach the second drive.

Perhaps someone who knows how could file a bug report on this?

---

### Post by handydan918 on 2008-12-31
I agree. I think the best fix for this is a BIG sticky saying "Don't do that!"
Seems to me that most of the problems are suffered by noobs who are afraid to install to the same hard drive, and are inwilling to add an internal. 
It's not a good combination. 
Sure, if you are slightly competent with partitioning, grub can be deciphered. caljohnsmith is a god, for sure. 

I wish it were possible to just tell people this is not a good solution, in most cases.


#-o

---

### Post by caljohnsmith on 2008-12-31
> **OldDogNewTricks said:**
>  I have WinXP on my main drive, and I'd like it to be able to boot without having to attach the second drive.

Perhaps someone who knows how could file a bug report on this?
If you want to post the output of that script I linked to in my previous post, I can help you set up your system so that your drives are independent of each other, and then you won't have to have your 2nd drive attached in order to boot. There are many different ways of accomplishing that, but the easiest is if you can change your BIOS so that your 2nd drive boots before the Windows internal drive. If you can do that, the solution to your problem could be really simple, because you would just need to install Grub to your 2nd drive's MBR in order to make it bootable (and tweak your menu.lst too maybe). Let me know if you would like a hand, but please post the output of the script first so I can get a clear picture of your setup.

---

