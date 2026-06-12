---
title: "Windows drive access (same ssd drive as Ubuntu is installed on)"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by 6rom on 2011-03-14
Hello

First of all, I know this kind of question has been asked and answered countless of times and am therefore feeling bad about making a new thread to ask it, in stead of putting the energy into looking for an answer elsewhere. The problem is, that I don't have the first clue about linux file systems and syntax used in solutions based on terminal entries neither. All I know is that i have tried a few and none have proved to be working for me.

Anyway, the problem is, that I have a ssd drive (don't know if it matters, I just though that it might on the account of before mentioned syntax), on which I have installed win7 os I use. I have installed Ubuntu on the same drive with "Wubi windows installer". Now, ubuntu is working perfectly for all I can see, and can also see the other 2 partitions of another hard drive I have, and can access the files on them without problems. I just cant figure out how, for the love of the holy penguin, can I access the files on the drive on which has the os's installed.

Thanks for help in advance ^^

P.S.: since i'm already asking things, can someone point me in the right direction of adding pooloads of repositories to my ubuntu, as i know i'll have to do this, as my searches for software via synaptic packet manager are somehow dry so far...

---

### Post by Mark Phelps on 2011-03-14
If you're asking about accessing the MS Windows files from inside the Ubuntu install, I believe the Windows filesystem is mounted at /host.  Look for that in the Places menu.

However, I would strongly suggest that you do NOT make changes to Windows files from inside Ubuntu.  Win7 is especially touchy about changes being made from outside, and such can result in filesystem corruption.  And then, since the Win7 OS partition won't boot, it's a very difficult problem to fix.

If you really want to share files, a better approach is to create a shared NTFS data partition.

Also, if you can boot from CD, suggest you utilize the Backup feature to create and burn a Win7 Repair CD.  That could come in handy later if you need to repair the Win7 boot loader.

---

### Post by 6rom on 2011-03-14
The place i was looking for was indeed /host, thank you for that :)

Also since you mentioned it, how would i "go about" ruining the win boot, what exactly would i have to alter to mess that up?

I had boot problems in the past, as GRUB took over the boot, and after removing the ubuntu, i had to manualy repair master boot record in order to boot windows properly, but i dont understand what exactly would i have to alter in order to mess boot up, apart from system and other registry connected files.

---

