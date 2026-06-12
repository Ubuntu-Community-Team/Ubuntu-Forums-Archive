---
title: "I messed up my install...No Grub2"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by Jeffster999 on 2010-04-02
**Hosed Install??** 			
 			 			 		   		 		 		Hello all, Here is what I have done...

I successfully set-up a dual bot system on my laptop and feeling a bit confident I decided to do the same my desktop. I installed a 1 TB WDC drive in the machine, partitioned it to 3 partitions ( M:,P:, L: ) formatted the partitions to NTFS and thought I was ready...Keep in mind there is another HDD ( C: ) on which Win XP is installed.

Initially, I installed wubi (before reading about it enough) and realized I did not want that type of install. I then installed from the CD (btw ver 9.10) and went through the steps installing to the L: drive on the 2nd HDD theinstall looked to be successful until I rebooted the computer.
My boot screen shows:

     Windows XP Media Center Edition
     Windows XP Media Center Edition SP2
     Ubuntu
When I choose Ubuntu, I get a terminal screen and when I type BOOT it get back 'no kernel loaded'

Now you know the setup and here is what I have done thus far:


I googled and found this page: 
[https://help.ubuntu.com/community/Re...tallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

followed the directions closely until I get to this portion and am a little confused

sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda

[FONT=Verdana]One question I have is which drive do I list in the above string? The drive with the MBR or the
drive that Ubuntu is on?

Also if you guys can tell me what I could have done differently.

Thank You in advance [/FONT]
 		                   		  		  		 		 			 				__________________

---

### Post by undecim on 2010-04-02
The driver string after --root-directory should be wherever you have the drive mounted.

The last part should be /dev/sda

---

### Post by Jeffster999 on 2010-04-02
OK one more question...
did I mess up by not uninstalling wubi before performing the install from CD?

---

### Post by undecim on 2010-04-02
> **Jeffster999 said:**
> OK one more question...
did I mess up by not uninstalling wubi before performing the install from CD?

No, Wubi won't mess anything up.

---

### Post by Jeffster999 on 2010-04-02
Thank You but still no love on my end, I can't get it to boot even with Super Grub

I think what I am going to do is start all over...

Like I said I have been successful on a single HDD dual boot but I think I may me over my head on a 2 HDD dual boot scenario

---

### Post by oldfred on 2010-04-02
If you want to see all the UUIDs:

```
sudo blkid
```

An alternative set of instructions:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you are still having issues we can review your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by Jeffster999 on 2010-04-02
Thank You for your replies...

Here is what I did...out of sheer frustration I loaded windows, went into control panel---> computer management--->storage and reformatted the L: partition (which btw would not show b/c is was not NTFS. Side note...I f I would have read more thoroughly, I would have realized that the later versions of Ubuntu do in fact recognize NTFS partitions). Once done I inserted the Ubuntu disk and did an install from inside windows. Everything seemed to go well , the install completed I was able to boot into windows to make sure that it still worked. I rebooted again this time choosing Ubuntu and got this:

                                      GNU GRUB    version 1.97~beta4


   [Minimal BASH-like line editing is supported. For the first word, TAB
     lists possible command completions. Anywhere else TAB lists possible
     device/file completions. ]
     
    sh:grub>



this is a recreation of the other screen

What did I do wrong now?

---

### Post by Jeffster999 on 2010-04-02
BTW from the sh:grub prompt i cannot run the above mentioned sudo blkid command

---

### Post by oldfred on 2010-04-02
So are you in wubi again?

The sudo blkid can be run from the liveCD that you have to use to reinstall grub.

If wubi this is often the problem:
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Jeffster999 on 2010-04-02
oldfred...YOU ARE THE BEST....

Finally, it is fixed and booting


Thank You

---

