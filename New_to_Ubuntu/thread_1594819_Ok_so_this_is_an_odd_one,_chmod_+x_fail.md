---
title: "Ok so this is an odd one, chmod +x fail"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Binnyer on 2010-10-12
Ok so I have World of Warcraft installed on an NTFS partition that I use as an intermediary between Windows and Linux for programs/games/media I utilise on both. I was having WINE issues with a different game and so I uninstalled and reinstalled it, and after fixing the other game I came back and tried to play World of Warcraft only to get:
"The executable bit is not set" error
Puzzling since i know I set it, so I went in the properties and tried to click the box "Allow executing file as a program", but it instantly went from checked, to unchecked again.
I went into the terminal and chmod +x wow.exe, but I went and checked the properties again and the box had magically unchecked itself again.
So I sudo chmod +x wow.exe still nothing
sudo chmod a+x wow.exe still nothing
I can do wine wow.exe and it will load the program, but I cannot simply click the exe and load it. It's mildly annoying.

Note: chmod +x or the graphical check-box works for any file not within the WoW directory. However the WoW directory is owned by me and has executable bit enabled for the folder.
Note2: it isn't just wow.exe it is any executable file in the WoW directory, but all are owned by me. Also I cannot edit ANY other permissions, graphical or chmod for any file in the directory.

---

### Post by emoguitarist06 on 2010-10-12
Try right clicking the .exe and change the "Open With" from archive manager to Wine and then you should be able to double click and open???

If not... I tried :)

---

### Post by coffeecat on 2010-10-12
> **Binnyer said:**
> I cannot edit ANY other permissions, graphical or chmod for any file in the directory.

That's because:

> **Binnyer said:**
> installed on an NTFS partition

NTFS is a Microsoft filesystem and doesn't support Linux/Unix ownership and permissions. Ownership and permissions are set by the mount options. How are you mounting the partition, from the Places menu, or with a line in /etc/fstab? Most people have the exact opposite problem with **everything** being seen as executables on an NTFS partition. It's all down to mount options.

---

