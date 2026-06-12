---
title: "How to use Ubuntu LiveCD to get Windows Product Key from hosed system"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by sugardaddy_mrbig on 2009-08-25
I'm trying to get my windows product key from my existing installation of Windows.  I have a LiveCD (I can put it on a USB drive if needed) of Ubuntu 9.  

My Windows allows me to log in, but then immediately logs me out again.  Even does same in Safe Mode.  I tried a Windows repair, but no dice.

I'd like to get my product key so I can have an easier time reformatting.

Any tips?

---

### Post by lkraemer on 2009-08-25
How/Why does this post belong in the Linux UBUNTU FORUM?

Call DADDY GATES, and ask for help with the recovery of your key.
Heck they probably even have you as a REGISTERED USER in their
Datadase and can tell you how to recover the key.

Good Luck.

lkraemer

---

### Post by juanoleso on 2009-08-25
Your product key is in the windows registry:

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion]
"ProductKey"="XXXXX-XXXXX-XXXXX-XXXXX-XXXXX" or
"ProductId"="XXXXX-XXXXX-XXXXX-XXXXX-XXXXX"

And the HKLM registry section is found at:

```
%SystemRoot%\System32\config
```
(e.g. C:\WINDOWS\system32\config\)

and you want the file "software"

From what I've seen, though, there is not an easy way to read a windows registry from Ubuntu.

From [[COLOR="BLUE"]Wikipedia[/COLOR]]("http://en.wikipedia.org/wiki/Windows_Registry"):
> It also possible to edit the registry under Linux using the opensource [[COLOR="BLUE"]Offline NT Password & Registry Editor[/COLOR]]("http://home.eunet.no/pnordahl/ntpasswd/") to edit the files.

Or another website I found suggested using wine to run a 3rd party registry editor to access the registry:

[[COLOR="BLUE"]http://thelinuxgirl.blogspot.com/2009/01/editing-windows-registry-through-linux.html[/COLOR]]("http://thelinuxgirl.blogspot.com/2009/01/editing-windows-registry-through-linux.html")

> Windows stores registry files in the "C:\Windows\System32\config" directory. While there do not seem to be any Linux utilities to open/edit these hives, there is still a solution. Of course -- using 3rd party Windows registry viewers/editors through WINE. There are many 3rd party programs that work similar to regedit, usually only allowing you to view registry hives and export them to REGEDIT4 format (.reg files used to modify the registry.) An example of one of these would be [[COLOR="BLUE"]Regworks[/COLOR]]("http://www.regwrks.com/"). These programs can be used very easily to do many tasks.

So, you could mount your windows partition and try one of these ideas.  Someone else might have other ideas though...

good luck

---

### Post by jaqrah on 2009-08-25
[http://ubuntuforums.org/showthread.php?t=858456](http://ubuntuforums.org/showthread.php?t=858456)

But really, those product keys are like GOLD.. you should be more careful.:lolflag:

And quite frankly, I googled your question and the first hit was the above link.  Google is your friend.

---

### Post by RedRat on 2009-08-25
Well I just checked my XP installation and regedit did not show anything like:

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Curr entVersion]
"ProductKey"="XXXXX-XXXXX-XXXXX-XXXXX-XXXXX" or
"ProductId"="XXXXX-XXXXX-XXXXX-XXXXX-XXXXX"

The Product ID was there, but no ProductKey entry. Down below under WindowsNT, there was a binary number for the Product Key but unless you have the hash code for that it will not do you much good. If you can get into the registry and find that entry, you might be able to copy the binary and put it into a reinstallation. But I doubt that will work either. 

Better find your original disks.

---

### Post by juanoleso on 2009-08-25
ah, yes, my bad.  It is not human readable and it could be in multiple places.  That magical jelly bean program that jaqrah linked works well.  It might work under wine.

---

### Post by sugardaddy_mrbig on 2009-10-21
@lkraemer, I posted it here because lots of people use the Ubuntu LiveCD to troubleshoot Windows problems.  I thought I could get help here... and I was right.  :-)   However, *your* response was very Microsoftian: lots of talk, but nothing useful.

@juanoleso, et al...

Because of your help, I was able to learnthe location of the Windows Registry files:
([FONT=Courier New]C:\WINDOWS\system32\config\[/FONT])

I also had found Magic Jellybean KeyFinder (MJBKF) in my searching previously, but was unaware that it would work on a hive that was not the current one, like some other programs of similar purpose.  With information from you folks, I made some attempts.  Here's what worked...

[LIST=1]
[*]I copied the [FONT=Courier New]config [/FONT]folder (mentioned above) to my USB drive using Ubuntu to get access to the hard drive.
[*]On another Windows machine, I installed MJBKF and plugged in the USB drive.
[*]MJBKF didn't work if I pointed it to the [FONT=Courier New]config [/FONT]folder.  So I thought to duplicate the directory structure it might normally see in Windows.
[*]I created a [FONT=Courier New]windows [/FONT]folder, and then created a [FONT=Courier New]system32 [/FONT]folder in it.
[*]I then moved the [FONT=Courier New]config [/FONT]folder into the [FONT=Courier New]system32 [/FONT]folder.
[*]MJBKF worked fine when I pointed it to the newly-created [FONT=Courier New]windows [/FONT]folder.  I was able to get my Windows XP Key!
[/LIST]

---

### Post by philinux on 2009-10-21
Excellent info. Could prove useful in future.

---

### Post by gbold on 2009-10-21
Can you get into Windows using the Administrator account from Safe Mode?  Is there another account you can use from Safe Mode?  If you suspect a virus etc., I find pulling the drive and scanning it in another computer works well (just fixed one of my wife's friends computer this way... found 12 instances of viruses... McAfee sux!).
Greg

---

### Post by sugardaddy_mrbig on 2009-10-21
> **gbold said:**
> Can you get into Windows using the Administrator account from Safe Mode?  Is there another account you can use from Safe Mode?  If you suspect a virus etc., 
Greg, when it wasn't working, I couldn't log in at all, not even as the admin, nor under Safe Mode.  I had installed IE 8, and then my virus software had some sort of issue with it, and blammo, I could no longer log in.

---

### Post by tommy2k10 on 2010-08-05
> **sugardaddy_mrbig said:**
> @lkraemer, I posted it here because lots of people use the Ubuntu LiveCD to troubleshoot Windows problems.  I thought I could get help here... and I was right.  :-)   However, *your* response was very Microsoftian: lots of talk, but nothing useful.

@juanoleso, et al...

Because of your help, I was able to learnthe location of the Windows Registry files:
([FONT=Courier New]C:\WINDOWS\system32\config\[/FONT])

I also had found Magic Jellybean KeyFinder (MJBKF) in my searching previously, but was unaware that it would work on a hive that was not the current one, like some other programs of similar purpose.  With information from you folks, I made some attempts.  Here's what worked...

[LIST=1]
[*]I copied the [FONT=Courier New]config [/FONT]folder (mentioned above) to my USB drive using Ubuntu to get access to the hard drive.
[*]On another Windows machine, I installed MJBKF and plugged in the USB drive.
[*]MJBKF didn't work if I pointed it to the [FONT=Courier New]config [/FONT]folder.  So I thought to duplicate the directory structure it might normally see in Windows.
[*]I created a [FONT=Courier New]windows [/FONT]folder, and then created a [FONT=Courier New]system32 [/FONT]folder in it.
[*]I then moved the [FONT=Courier New]config [/FONT]folder into the [FONT=Courier New]system32 [/FONT]folder.
[*]MJBKF worked fine when I pointed it to the newly-created [FONT=Courier New]windows [/FONT]folder.  I was able to get my Windows XP Key!
[/LIST]



I am trying to locate a product key from a Windows installation that will not boot.  (Windows cannot even detect the drive, but Linux can see it and mount it!
I am using Ubuntu System Rescue 1.5.5 to try and do it, together with MJBKF.  I followed the above procedure, tried to load the hive, and it says, 'Can't load Registry Hive. A required privilege is not held by the client.'  Why does this error message appear?
I don't know what the Windows OS is.
And can I find the product code by booting it with a usb flash drive?

---

### Post by tommy2k10 on 2010-08-05
> **tommy2k10 said:**
> I am trying to locate a product key from a Windows installation that will not boot.  (Windows cannot even detect the drive, but Linux can see it and mount it!
I am using Ubuntu System Rescue 1.5.5 to try and do it, together with MJBKF.  I followed the above procedure, tried to load the hive, and it says, 'Can't load Registry Hive. A required privilege is not held by the client.'  Why does this error message appear?
I don't know what the Windows OS is.
And can I find the product code by booting it with a usb flash drive?

Correction - I am using Gentoo Linux System Rescue 1.5.8

---

### Post by thatguymark on 2010-08-05
Magical Jellybean Keyfinder does come as a Bart's PE plug-in - except it didn't work when I tried the boot disc I made. It's there in the menu but for some reason grayed out and I didn't find any special instruction on other configuration and since I wasn't doing it out of necessity I gave up. I did find that there is another program that does the same thing, I'm sure a google will pull up those posts.

---

### Post by viditgoyal3009 on 2010-08-05
> **sugardaddy_mrbig said:**
> I'm trying to get my windows product key from my existing installation of Windows.  I have a LiveCD (I can put it on a USB drive if needed) of Ubuntu 9.  

My Windows allows me to log in, but then immediately logs me out again.  Even does same in Safe Mode.  I tried a Windows repair, but no dice.

I'd like to get my product key so I can have an easier time reformatting.

Any tips?
might be there is a virus running at the startup...as soon as you login keep the shift button pressed which prevents startup programs...if every thing goes perfectly after that release the shift key, right click on my computer and go to properties, there you might see your windows key. hope this will help

---

### Post by tommy2k10 on 2010-08-05
Where exactly in the Registry is the key for Windows Vista?  JBKF keeps saying it can't find the specified file, not that it can't read the specified file.

---

