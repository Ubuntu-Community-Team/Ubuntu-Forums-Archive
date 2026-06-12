---
title: "grub error: &quot;unknown filesystem&quot; after deleted partition"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by mrbiscuits on 2011-08-10
Hey all,

Recently dual booted windows xp sp3 with ubuntu 10.10. I later, realizing i was running out of hard drive space, I deleted the partition which had ubuntu on it while running windows. Later windows auto rebooted my computer (AAAHHHH.) and, where grub usually popped up, it said:

error: unknown filesystem.
grub rescue>

I checked on another thread but it was a different scenario, they hadn't deleted the ubuntu partition.

Anyway can I delete grub to boot windows through a live cd? or is there something in grub rescue I can do to fix? I have command line experience (though not in grub).

Thanks everyone.

---

### Post by jtarin on 2011-08-10
You have no Grub files to boot as you deleted them when you deleted the Ubuntu partition. You will need to repair your Windows MBR using a Windows install disk or the XP recovery console if you have it installed.

---

### Post by Gone fishing on 2011-08-10
Here's a link on how to do it:

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

However, I think you made a mistake surely you should have deleted the Windows partition? ;)

---

### Post by mrbiscuits on 2011-08-10
Its a family computer so no general happiness on deleting windows :p

thanks for the help! I ended up misplacing the windows disk so i found someone who posted a thread on how to fix the mbr in an ubuntu live cd. Thanks for leading me in the right direction.

---

### Post by RDLP715 on 2011-08-19
My issue must be in some related to the OP, so I reckon I should seek help here instead of opening a whole new thread.

When I boot my laptop(dell inspiron from 2006, ubuntu 10.04) it goes directly to 

> error: unknown filesystem
grub rescue>

I tried 
> grub rescue> set prefix=(hd0,5)boot/grub
grub rescue> set root=(hd0,5)
grub rescue> insmod normal
but its reply to that..
> error: unknown filesystem

There was another solution I saw elsewhere that involved something along the lines of "~sudo mount ...." , but my grub rescue keyboard layout does not have the "~" symbol.

Any assistance would be greatly appreciated.

---

### Post by oldfred on 2011-08-19
@RDLP715 
Even though it is the same error, boot issues often are unique as everyone's system is different. Start a new thread and post this from a liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

You can also do it from this and it may make the repairs for you.
Yanni has created a easy way to download boot repair & run script Maverick:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)

---

### Post by harry_r_s on 2011-10-15
I had the same problem of filesystem error
and i tried reloading the ubuntu within windows and guess wat my problem is solved...

---

### Post by subinthegladiator on 2012-03-25
@mrbiscuits: How do you fix MBR using ubuntu live  CD. I  am in the same situation. Please guide me. I just want my windows 7 back. I deleted linux partition from windows. Thanks in advance

---

### Post by gajjar8055 on 2013-01-07
Use Super Grub Disk . Its Better Option Solve This Kind Of grub Problem [http://www.supergrubdisk.org/super-grub-disk/](http://www.supergrubdisk.org/super-grub-disk/):D

---

### Post by oldos2er on 2013-01-07
Old thread closed.

---

