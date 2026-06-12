---
title: "Tripple Boot Grub2 Ubuntu Karmic 9.10, XP, and Windows 7"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by boytoreckonwith on 2009-12-19
I looked all over for this solution, and couldn't find it anywhere. Sorry if this is a repost. 

I found a solution to get XP and Windows 7 both into Grub menu by trial and error.  I started with Grub only showing Windows 7 boot loader, so I had to go there and then choose legacy OS to get to XP. The boot loader was actually on the XP partition since I had installed XP first. To fix it, all you do is (in ubuntu)
1) *move* (delete after copying) "bootmgr" and the "boot" folder to the Windows 7 patition from the XP partition. 
2) sudo update-grub - it should find both the Windows 7 boot loader and winXP
3) Restart and choose Windows7 boot loader and start Windows 7
4) Right click [I]My Computer -> Manage -> Disk Management
[/I]5) Make the Vista Partition Active (if you don't, you can't edit the boot manager)
6) start menu, right click on *command promp* and run as Administrator
7) starting in c:\windows\system32 type bcdedit.exe, then *bcdedit /time 0 - this will make it boot almost directly to Windows 7 so you don't have to hit enter every time (0 seconds to choose default) - WARNING - if you have edited this before to make default XP, then make sure you edit it back.*

You could also to try delete the xp entry, you can do this by typing* bcdedit  /delete <xp name> /f* (usually it's bcdedit /delete /{ntldr} /f) .To be safe, read details by typing bcdedit /?  - this will give instructions about your options. Get all the boot options like the xp name by just typing *bcdedit.exe*

Now you can choose Ubuntu (or your flavour), XP, or Windows 7 right from Grub2. Enjoy

As always, if you don't back up first....keep your install discs handy :)

---

### Post by mrkazoodle on 2009-12-31
WOW, this thread can save lives! 	:D
Thank you very much for posting it, I'll check it out later.

---

### Post by gymophett on 2010-02-12
It DID save my life.

---

### Post by fedejofa on 2010-05-01
Mine too!!!!!! :-D

---

