---
title: "Trash question"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by dyecide on 2009-10-28
Hey,

Yesterday I made Ubuntu a bit more 'Windows-like' by deleting the upper panel and adding the components I need to the bottom one. I also deleted the trash icon from the taskbar, and added it to the desktop by using Gnome Configuration Editor.

Since then I cannot move files to the trash from other partitions (NTFS ones), only from Ubuntu's own one (ext4). If I press delete on a file on an NTFS system, it asks 'Cannot move file to trash, do you want to delete immediately?' . How could I solve the problem?

I'm using Ubuntu 9.10RC

Thx in advance!

---

### Post by SunnyRabbiera on 2009-10-28
Actually you better not delete/add files to NTFS while in Ubuntu, it can cause Windows to have a major conniption.

---

### Post by corncob on 2009-10-28
Are you duel booting to Windows or do you just have a partition formated to NTFS?  I use pen drives and SD cards formated to NTFS or FAT32 and they have their own .Trash folders (they're hidden).  When I get
> Cannot move file to trash, do you want to delete immediately?
its usually because its too big.  I think the capacity of the trash is 10% of the partition but there may be a way to reset it.
If you're running Windows, why not just boot into that and delete the files there?
I still have XP but I'm running it in Sun VirtualBox, not duel boot.  I guess if I wanted to put a Windows file into my Ubuntu trash I'd first move it to the shared folder and go from there.

---

### Post by ajgreeny on 2009-10-28
Any file you delete from any partition will go to that partitions own trash, not to trash in your home folder or partition, so anything in an ntfs partition will go to a hidden folder in that partition.  How windows deals with that I have no idea, but you can find it in nautilus by making sure hidden files are visible, then going to /.local/share/Trash/files on that partition.  The same is true for usb flash drives and all drives/partitions.

I always add a delete option to the right click context menu in nautilus preferences to get rid of things straight away.  Use carefully, however, as once it's gone it's gone for good.

---

### Post by nakama85 on 2009-10-28
Just curious. If you wanted ubuntu to feel more like windows why did you not just install Kubuntu??

---

### Post by community nerd on 2009-10-28
Why do you want to make ubuntu look like windows?

---

### Post by dyecide on 2009-10-29
> **nakama85 said:**
> Just curious. If you wanted ubuntu to feel more like windows why did you not just install Kubuntu??
I've tried Kubuntu, but KDE looked like a mess to me. I prefer Gnome + Ubuntu.

[quote=community nerd]Why do you want to make ubuntu look like windows?     [/quote]
I'm new to Linux and I find having 2 'taskbars' (panels) unnecessary. Takes up screen space.


And yes I got a dual boot system. Ofc I can delete files from windows aswell, I don't store any personal stuff on windows' partition (I got 3 NTFS ones), for example my pictures are on an NTFS onel, and rebooting to windows just to do file operations there would be silly. File size doesn't matter at deleting, it always says that when I try to delete something from an NTFS partition.

---

### Post by corncob on 2009-10-29
> I'm new to Linux and I find having 2 'taskbars' (panels) unnecessary. Takes up screen space.

You might want to try [Linux Mint]("http://www.linuxmint.com").  Its Ubuntu but looks like Windows in my opinion -- no upper taskbar and everything comes up on the "start button".  Also it plays videos right out of the box.  I used it for a while but I'm back to plain old Ubuntu mainly because I like the two taskbars lol.

---

### Post by dyecide on 2009-10-29
Thx, but I will stay with Ubuntu :D I like it a lot. Imo if you have a big enough monitor (22" in my case) 1 taskbar is enough. But ofc it's personal preference.

Btw, before i removed Trash from the taskbar and put it on the desktop, trash worked on NTFS partitions aswell. I find it a bit hilarious that deleting an icon prevents Trash from working on the other partitions :\

Any idea how could I fix this?

PS: tried putting trash back on the panel, didn't work.

---

### Post by karimruan on 2009-10-29
> **dyecide said:**
> 

PS: tried putting trash back on the panel, didn't work.

I was just going to suggest that. Google it, see what you come up with. That is how I fix a lot of my configuration problems!

---

### Post by dyecide on 2009-10-29
Yes I always Google before asking something on a forum :) But results are about 'trash stopped working from a moment to another', and not my specific case.

---

