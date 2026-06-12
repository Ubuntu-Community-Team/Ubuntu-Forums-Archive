---
title: "Getting files off an exernal hard drive with a backup of OSX on it"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by dragon2knight on 2010-04-02
Hi all,just reinstalled ubuntu after a few years absence.Im using 9.10 64 bit.I want to transfer my files(I have a ton of them)over from my external hard drive that has a full backup of OSX(mac)on it.It mounts,and I see the files,and thats where the trouble starts.Ubuntu wont let me transfer the files,saying that I'm not the owner,and dont have permission to do it.I have no idea at all on how to fix this,any help at all would be vastly appreciated,I need those files!1 Thanks ahead of time,Mike.:confused:

---

### Post by coffeecat on 2010-04-02
The external drive is probably formatted with the journalled version of hfs+, the MacOS, filesystem, which you can only read in Ubuntu. The permissions problem you are getting is because MacOS uses the same Unix permissions as Ubuntu and your UID (user identity number) will be different in MacOS. You can't change the files on the drive, but you can access them from a root Nautilus. Open a terminal, and...

```
gksudo nautilus
```Use the root Nautilus to browse the Mac drive and drag and drop into your home folder, or wherever you are going to transfer to.

---

### Post by Temposs on 2010-04-02
Shouldn't be too hard. One way to do it would be to change the permissions on the files. So, press Alt-F2. Now type:

```
gksudo nautilus
```

This gives you a file browser with root access. Navigate to the directory of your external hard drive, right click in a blank area, choose Properties, then click the Permissions tab.

Under the Others section, change the "Folder Access" to "Create and Delete Files". Then change "File access" to "Read and Write". Last, click the "Apply Permissions to Enclosed Files" button and wait for it to finish. It might take  while. 

Once this is done, close the root nautilus(File Browser) window and open one the normal way, through the Places menu. Now, you should be able to copy any files you want from your external hard drive.

---

### Post by dragon2knight on 2010-04-02
Thanks,I had a feeling the two were similar,just not THAT similar! You saved my bacon,I really do appreciate it!

---

### Post by dragon2knight on 2010-04-02
Ok,I tried this and I couldnt get past "change Folder Access to create and delete files",it wouldnt let me saying it is "read only"...right back where I started,no way to transfer files.Anyone else?

---

### Post by coffeecat on 2010-04-03
> **dragon2knight said:**
> Ok,I tried this and I couldnt get past "change Folder Access to create and delete files",it wouldnt let me saying it is "read only"...right back where I started,no way to transfer files.Anyone else?

The journalled MacOS filesystem is READ-ONLY in Ubuntu, so you can't change permissions on files which are still on the MacOS drive. I don't know why the other poster suggested this. Do what I suggest: open a root nautilus browser with 'gksudo nautilus' and use that to browse to your /User/Yourname/whatever folder on the MacOS drive. Then drag and drop whatever you need **from the root nautilus browser** to your home folder on your Ubuntu system. That will work. I've done it. You don't need to change permissions.

The only other way is to connect the hfs+ formatted drive to an Apple Mac and use that to change permissions of the files and folders you want to copy. But that's quite unnecessary. Use a gksudo nautilus in Ubuntu.

Let me say this one more time. The drive will be formatted with the Mac HFS+ filesystem. There are two versions: journalled and non-journalled. Ubuntu (Linux) can read and write to the non-journalled version, but it can mount the journalled version[SIZE=2]** READ ONLY**[/SIZE]. Hence no changing of permissions. When the Apple Mac that formatted that drive formatted it for backup purposes, it almost certainly did so with the journalled version of HFS+. The fact that you cannot change permissions makes it 100% certain that it did so.

---

### Post by Temposs on 2010-04-03
> **coffeecat said:**
> The journalled MacOS filesystem is READ-ONLY in Ubuntu, so you can't change permissions on files which are still on the MacOS drive. I don't know why the other poster suggested this. Do what I suggest: open a root nautilus browser with 'gksudo nautilus' and use that to browse to your /User/Yourname/whatever folder on the MacOS drive. Then drag and drop whatever you need **from the root nautilus browser** to your home folder on your Ubuntu system. That will work. I've done it. You don't need to change permissions.

The only other way is to connect the hfs+ formatted drive to an Apple Mac and use that to change permissions of the files and folders you want to copy. But that's quite unnecessary. Use a gksudo nautilus in Ubuntu.

Let me say this one more time. The drive will be formatted with the Mac HFS+ filesystem. There are two versions: journalled and non-journalled. Ubuntu (Linux) can read and write to the non-journalled version, but it can mount the journalled version[SIZE=2]** READ ONLY**[/SIZE]. Hence no changing of permissions. When the Apple Mac that formatted that drive formatted it for backup purposes, it almost certainly did so with the journalled version of HFS+. The fact that you cannot change permissions makes it 100% certain that it did so.

Yeah sorry, I should've deferred to coffeecat's explanation, since I obviously have never really used OSX and don't know much about it. I started writing my post before coffeecat posted his. In general my way would work on an external drive, but not in the case with an OSX filesystem.

So, do like coffeecat says. Disregard my instructions.

---

### Post by coffeecat on 2010-04-03
> **Temposs said:**
> In general my way would work on an external drive, but not in the case with an OSX filesystem.

Agreed, but no worries. :) It's mightily confusing with the Mac filesystem. It took me ages to work this one out by trial and error, not helped by the fact that there's a bug in Gparted such that when you create a (non-journalled) HFS+ filesystem with it with a MBR partition table, the partition table has the code for ext3 instead of hfs+. Which upsets MacOS. :|

---

### Post by dragon2knight on 2010-04-03
Well,I hate to tell both of you,but neither way worked.I explained the first way,but what coffeecat says didnt work either for me.It wouldnt let me transfer the files over,saying that I dont have the necessary permissions.I managed to get it to transfer by running the live cd,as it displays all available drives,including my home folder I was trying to transfer the files to.It worked when I opened two root nautilus windows and transfered the files that way.I still didnt have the permissions to modify them without first opening a root window,but at least I got them and can use them.I agree,macs are very much over protective of anything put on them,but at least there are work arounds if you have the patience to try try again ;) Thanks for all the suggestions,wouldnt have thought of the solution I came up with if it wasnt for them.

---

### Post by coffeecat on 2010-04-03
> **dragon2knight said:**
> what coffeecat says didnt work either for me.It wouldnt let me transfer the files over,saying that I dont have the necessary permissions.I managed to get it to transfer by running the live cd,as it displays all available drives,including my home folder I was trying to transfer the files to.It worked when I opened two root nautilus windows and transfered the files that way.I still didnt have the permissions to modify them without first opening a root window,but at least I got them and can use them.I agree,macs are very much over protective of anything put on them,but at least there are work arounds if you have the patience to try try again ;) Thanks for all the suggestions,wouldnt have thought of the solution I came up with if it wasnt for them.

It's not Macs being protective - it's all down to Unix permissions. :p

I have a HFS+ formatted drive which I use to do a complete MacOS system backup using Carbon Copy Cloner. I've just mounted it in Karmic and I was able to browse to most of my Mac home folders and copy files with an ordinary non-root Nautilus. This was because the permission for 'others' in them was set to 'read/write'. Which allowed me to read and copy even though my Ubuntu UID (1000) was different from my Mac UID (501). But some folders were - just as with you - inaccessible. They included the Desktop, Library, Movies, Music and Pictures folders - all ones already set up in a default Mac install. I guess they were the ones you were having trouble with. They were set for no access for 'others', which is why you get a permissions error when trying to open them.

The ones I was able to copy from were ones I had created myself in my Mac home folder, except, strangely, for two which had no access permission. Goodness knows why.

Anyway, as you discovered, the answer was to copy from a root nautilus to a root nautilus. The problem then being that the copied files on the Ubuntu machine become owned by root, which you discovered and found a way around.

I'm glad you've managed to copy your files. It's worth learning about the system of Unix permissions. Whether you use Ubuntu, MacOS or another Linux distro, you're going to encounter problems with them.

Good luck!

---

### Post by ugm6hr on 2010-04-04
> **coffeecat said:**
> Anyway, as you discovered, the answer was to copy from a root nautilus to a root nautilus. The problem then being that the copied files on the Ubuntu machine become owned by root, which you discovered and found a way around.

"gksudo nautilus" should allow access without needing to use the LiveCD.

As mentioned, permissions can subsequently be changed to allow access without root permissions in the future.

---

### Post by dragon2knight on 2010-04-05
> **coffeecat said:**
> It's not Macs being protective - it's all down to Unix permissions. :p

I have a HFS+ formatted drive which I use to do a complete MacOS system backup using Carbon Copy Cloner. I've just mounted it in Karmic and I was able to browse to most of my Mac home folders and copy files with an ordinary non-root Nautilus. This was because the permission for 'others' in them was set to 'read/write'. Which allowed me to read and copy even though my Ubuntu UID (1000) was different from my Mac UID (501). But some folders were - just as with you - inaccessible. They included the Desktop, Library, Movies, Music and Pictures folders - all ones already set up in a default Mac install. I guess they were the ones you were having trouble with. They were set for no access for 'others', which is why you get a permissions error when trying to open them.

The ones I was able to copy from were ones I had created myself in my Mac home folder, except, strangely, for two which had no access permission. Goodness knows why.

Anyway, as you discovered, the answer was to copy from a root nautilus to a root nautilus. The problem then being that the copied files on the Ubuntu machine become owned by root, which you discovered and found a way around.

I'm glad you've managed to copy your files. It's worth learning about the system of Unix permissions. Whether you use Ubuntu, MacOS or another Linux distro, you're going to encounter problems with them.

Good luck!

Thanks.This was the first time I ran into problems with transferring files from one OS to another,it was frustrating,but a good learning experience.Thanks again for all the help!

---

