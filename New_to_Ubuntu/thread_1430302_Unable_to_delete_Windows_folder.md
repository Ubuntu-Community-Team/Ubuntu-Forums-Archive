---
title: "Unable to delete Windows folder"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2010-03-15
Without thinking I copied a WindowsXP folder to Ubuntu on my dual boot PC and now I find that although I can move it to trash I cannot delete because I do not have permission even by using sudo nautilus . I have read previous threads and this appears to be because although Ubuntu can read XP files you can't alter the permissions , is this correct ?

---

### Post by caravel on 2010-03-15
Where did you copy the directory to?  If you copied it as root, it's probably inherited root permissions.  You need to take ownership of the directory.

---

### Post by halitech on 2010-03-15
you shouldn't use sudo nautilus, it should be gksudo for graphical apps. When you say you can move it to the trash but can't delete it, can you explain what you mean?

---

### Post by ex-wirecutter on 2010-03-15
> **halitech said:**
> you shouldn't use sudo nautilus, it should be gksudo for graphical apps. When you say you can move it to the trash but can't delete it, can you explain what you mean?

Thanks for the replies , what I mean is , when I click on " empty trash "  it doesn't because of the permissions problem .

---

### Post by halitech on 2010-03-15
Go into the trash folder and right click the file and go to permissions. Who is the owner of the file?

---

### Post by ex-wirecutter on 2010-03-15
It just says there is a problem because " you are not the owner " but since there  is only me I can only assume it's because its a WindowsXP folder . I suppose I could just leave it there , it's not doing any harm , just taking up space .

---

### Post by mcduck on 2010-03-15
> **ex-wirecutter said:**
> It just says there is a problem because " you are not the owner " but since there  is only me I can only assume it's because its a WindowsXP folder . I suppose I could just leave it there , it's not doing any harm , just taking up space .

Even if you are the only *human* user on the computer, any Linux/Unix system will have *way more* users than just you. Since the directory was copied from a Windows drive it's most likely owned by root instead of your own user.

You should check the owner & permissions just like suggested above.

..and to actually remove the directory, you will _definitely_ be able to do that if you start the file manager as root (by running "gksudo nautilus"). Select the directory, hold down Shift and then press Delete to delete the directory immediately instead of sending it to root user's trash.

---

### Post by sebastianabate on 2010-03-15
> **ex-wirecutter said:**
> Thanks for the replies , what I mean is , when I click on " empty trash "  it doesn't because of the permissions problem .

The problem here is that you moved the folder to the trash with nautilus as root, but when you empty the trash, you do that as a normal user. Try deleting the folder from nautilus as root pressing SHIFT+DEL, this way the folder is deleted inmediately (without going to the trash).

---

### Post by Steven_S on 2010-03-15
If I may, I have a related problem. 

I have 3 disks that were created with XP. Now I want to use them on a dual-boot system. Does that mean I have to change the owner for all 3? 

And will Win Xp still be able to access them when I boot into that?

---

### Post by ex-wirecutter on 2010-03-15
Thanks everyone .

---

### Post by mcduck on 2010-03-15
> **Steven_S said:**
> If I may, I have a related problem. 

I have 3 disks that were created with XP. Now I want to use them on a dual-boot system. Does that mean I have to change the owner for all 3? 

And will Win Xp still be able to access them when I boot into that?

Depends on what you want to do. The default setup leaves their owner as root but gives all users full access to files. 

And yes, whatever ownership & permissions you define to those drives in Ubuntu won't affect Windows in any way. The settings are not actually set on the file system itself (Windows filesystems don't even support such file ownerships and permissions as are used on Linux/Unix systems) but simply in the configuration file inside Ubuntu that tells what options to use when accessing the drive.

---

