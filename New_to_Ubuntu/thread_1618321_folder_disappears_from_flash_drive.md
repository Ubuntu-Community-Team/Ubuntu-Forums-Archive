---
title: "folder disappears from flash drive"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by sallam on 2010-11-10
Greetings

I've formatted a flash drive using Gparted, to NTFS.
It works fine. But just now I was trying to copy a folder from ubuntu into the flash rive. It was pasted OK. But when I take it out and re-insert it in USB, it disappears. I tried many times. I tried copy&paste, and I tried "send to.." typing my password and all, with no luck.


I browsed the flash drive in another machine, and the copied folder is not there!..Why it is not showing?

---

### Post by amjjawad on 2010-11-10
> **sallam said:**
> Greetings

I've formatted a flash drive using Gparted, to NTFS.
It works fine. But just now I was trying to copy a folder from ubuntu into the flash rive. It was pasted OK. But when I take it out and re-insert it in USB, it disappears. I tried many times. I tried copy&paste, and I tried "send to.." typing my password and all, with no luck.


I browsed the flash drive in another machine, and the copied folder is not there!..Why it is not showing?

Check the used space on your flash drive when you plug in in the other machine.

Perhaps it's hidden on the first machine and you need to "Show Hidden Files" on the other one?

---

### Post by sallam on 2010-11-10
I did press Ctrl+H to see if its hidden. Only the trash was hidden.

---

### Post by amjjawad on 2010-11-11
> **sallam said:**
> I did press Ctrl+H to see if its hidden. Only the trash was hidden.

What about the size? when you copy-paste a folder/file from your first PC, remove your USB drive, put it on the other PC and check the size of ***used space***. If it's zero used MB/KB then there's a problem. If your second PC could read the correct ***used space*** on your USB but couldn't show the files, I can only suggest to format your flash as FAT instead of NTFS.

Oh, there's another thing it might help. Try to format your USB flash from your 2nd PC, try to create new Partition Table, format it as FAT and then try to copy-paste a file/folder from your 2nd PC, remove your USB, put it in your 1st PC and see what will happen. In that case, you could make sure the PC is fine and it's your USB flash not the PC. 
I assume creating new Partition Table and Format it as FAT might solve the issue. Let's try everything and see what will happen.

Otherwise, I can't figure out what else to do?

---

### Post by toekneewood on 2010-11-11
I have seen this before. The paste looks like it has finishedan when actual fact it has not. Try it again and do a safe remove. You will find that a message will pop up telling you to wait. At that point if is finishing off the write from memory.

---

### Post by toekneewood on 2010-11-11
Just a bit of background info for you. In older versions of ubuntu if you pulled out a usb memory stick it would not auto mount. Especially if you did it on a windows machine and then inserted it into a ubuntu machine. As of ubuntu v9 this problem was sorted. I would still always do a safe remove, especially on a Linux system. If you look in nautilus you should see a eject icon next to your mounted usb device.

---

### Post by sallam on 2010-11-11
The weird thing is that even when I rename a file, that file, in other machines, still has its old name! as if I didn't change it.
when I pop in the usb drive in ubuntu again, the old name is showing too.

Before I use Gparted to format the usb drive to NTFS, it was behaving normally under FAT32. The problem with FAT32 is that it cannot handle any file larger than 4gb. But other than that, everything else was fine.

I'll try to reformat it again and let you know..

---

### Post by sallam on 2010-11-12
"Safely remove drive" did the trick. I just right-click the USB drive from he desktop and select "Safely remove drive", and everything is there later.
Its not required to do so in Win7, but ubuntu seems fuzzy about NTFS drives. No big deal. I just have to remember it each time. This is only related to NTFS. FAT32 USB drives can be removed without having to select the "Safely remove drive" step.

Many thanks for your great help.

---

### Post by amjjawad on 2010-11-12
> **sallam said:**
> **"Safely remove drive"** did the trick. I just right-click the USB drive from he desktop and select "Safely remove drive", and everything is there later.


I thought you were doing it already :)
For me, I never remove any USB unless I click[I] [B]Safely remove drive.

[/B][/I]:)

---

### Post by mcduck on 2010-11-12
> **sallam said:**
> "Safely remove drive" did the trick. I just right-click the USB drive from he desktop and select "Safely remove drive", and everything is there later.
Its not required to do so in Win7, but ubuntu seems fuzzy about NTFS drives. No big deal. I just have to remember it each time. This is only related to NTFS. FAT32 USB drives can be removed without having to select the "Safely remove drive" step.

Many thanks for your great help.

Actually yes, it *is* required even in Windows, and has always been. Every time you unplug a drive without removing it safely you risk loosing some data. And this isn't related to drive being FAT or NTFS or Ext2 or something else, it's just a question of how modern operating systems handle writes to disks.

Windows buffers writes to external drives just like Linux does, although it seems to keep a bit smaller buffer which is probably why you haven't broken your files in the Windowsland this far. :)

---

### Post by amjjawad on 2010-11-12
> > **mcduck said:**
> actually yes, it *is* required even in windows, and has always been. Every time you unplug a drive without removing it safely you risk loosing some data. And this isn't related to drive being fat or ntfs or ext2 or something else, it's just a question of how modern operating systems handle writes to disks.



+1

---

