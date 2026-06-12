---
title: "file is not marked as exe..."
date: 2010-10-21
forum: New to Ubuntu
---

### Post by ppk on 2010-10-21
Trying to install Age of Empires 2 on my machine. The game installation went fine but I can't install the latest patch. It keeps telling me that the file is not marked as executable. I searched and read somewhere that I had to right click and go into 'permissions', and then change it through a box there. Thing is, I'm using xubuntu 10.04 and see no such option. What can I do?

---

### Post by ubudog on 2010-10-21
Open a terminal (however you do that in XFCE, I forgot) and type in the following and then try what you did in the beginning. 

```
chmod +x filename
```

(filename being the name of the file)

The above command will make the file executable, so everything should work now.  Good luck! :)

---

### Post by ppk on 2010-10-21
Thank! It worked!

---

### Post by trikster_x on 2010-10-21
> **ppk said:**
> Trying to install Age of Empires 2 on my machine. The game installation went fine but I can't install the latest patch. It keeps telling me that the file is not marked as executable. I searched and read somewhere that I had to right click and go into 'permissions', and then change it through a box there. Thing is, I'm using xubuntu 10.04 and see no such option. What can I do?

```
sudo chmod +ax /path/to/file
``` 

I believe this is the command you need to run in terminal to make the file executable.

---

### Post by ubudog on 2010-10-21
> **ppk said:**
> Thank! It worked!

No problem. :):)

---

### Post by ebruzzone on 2010-11-04
Hi everyone. I am experiencing the same problem after I upgraded to Maverick 10.10. The issue is that no matter how many times I tick the authorization box it does not stay. It just refuses to treat the .exe and .jar files as authorized by me!

thanks for your help

---

### Post by mcduck on 2010-11-04
> **ebruzzone said:**
> Hi everyone. I am experiencing the same problem after I upgraded to Maverick 10.10. The issue is that no matter how many times I tick the authorization box it does not stay. It just refuses to treat the .exe and .jar files as authorized by me!

thanks for your help

Make sure those files actually are on your Linux drive. You can't change permissions of files located on FAT/NTFS file systems, or read-only media like CD and DVD discs.

---

### Post by ebruzzone on 2010-11-04
> **mcduck said:**
> Make sure those files actually are on your Linux drive. You can't change permissions of files located on FAT/NTFS file systems, or read-only media like CD and DVD discs.

Hey! that worked out well. But may I ask why on 10.10 permissions are only allowed on the Linux drive? Until the last version I  used may .jar programs directly from my external hard drive. 

Thanks again!

---

### Post by DirtyPC on 2010-11-04
for future reference, if you dont have access to a certain .exe, so you cant mark it as executable, open terminal and type **gksu nautilus**

---

### Post by Morbius1 on 2010-11-04
> Hey! that worked out well. But may I ask why on 10.10 permissions are  only allowed on the Linux drive? Until the last version I  used may .jar  programs directly from my external hard drive. 
It's not that they are only allowed on the linux filesystem it's because of the change in how Debian automounts external ntfs drives thorough Places.

Before all directories and files where given permissions of 0700 which allowed the user to execute all contained files. Now directories are given 0700 and files are given 0600 - a "6" has the execute bit removed.

Although it's turned out to be very frustrating for most users it's more in line with how a linux filsysten handles file permissions by default.

---

### Post by mcduck on 2010-11-04
> **ebruzzone said:**
> Hey! that worked out well. But may I ask why on 10.10 permissions are only allowed on the Linux drive? Until the last version I  used may .jar programs directly from my external hard drive. 

Thanks again!

It's not a question of being allowed or not, but simply if the file system used is able to handle them or not. Nothing has changed.

NTFS and FAT file systems completely lack support for file ownerships/permissions as they are used in Linux/Unix.

..and filesystems used on CD's and DVD's are read-only by design.

So since these filesystems don't support the permissions, and can't store them in any way, you can't use chown/chmod on them. Instead the ownership & permissions are set for the whole disc/partition at the time it's mounted.

If you have any removable drive formatted in any Linux filesystem, you are of course able to change the permissions and ownerships on it.

If you were previously able to execute .jar files form your external partition,a nd it was a FAT/NTFS filesystem, you must have had it configured to mount with execute permissions. Meaning that every file on the drive was considered as executable. That sure hasn't been the default configuration in any Ubuntu release, but if you want to set such mount options yourself then read this fstab guide: [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by Morbius1 on 2010-11-04
> If you were previously able to execute .jar files form your external  partition,a nd it was a FAT/NTFS filesystem, you must have had it  configured to mount with execute permissions. Meaning that every file on  the drive was considered as executable. That sure hasn't been the  default configuration in any Ubuntu releaseThat's been the default on external NTFS formatted drives in Ubuntu until 10.10.

---

### Post by mcduck on 2010-11-04
> **Morbius1 said:**
> That's been the default on external drives in Ubuntu until 10.10.

if that's true, it definitely is strange since I for sure can't remember having default execute permissions on files, even on removable drives, on any of my past Ubuntu installs.

Doesn't sound like the most safe setup, really, so if it was like that then I can definitely see why it's been fixed now. :)

---

### Post by mc4man on 2010-11-04
If you go back in the changelog of udisks you can see the changes to the mount options for vfat, ntfs volumes and the reason for.
The issue with .exe and .jar is separate - they don't need to be set as executable to run, nor can they be set on vfat, ntfs volumes (& cd/dvd-roms

They aren't run because the default launch commands for wine (Wine Windows Program Loader) and java contain cautious-launcher in them. That script does look for the bit and prevents the execution if not found. (usr/bin/cautious-launcher

A simple 'workaround' for example on .exe's is to open directly with wine from cli, ie.
wine /path/to/whatever.exe
or to use the r. click open with - other application - custom command and just use wine as the command - in the future 'wine' will be a r. click option and an available default option for d. left click
 
A more direct solution is to edit the .desktop and set the Exec= back to the pre cautious launcher one.

What cannot be done any more (without altering the mount options in udisks), is run scripts from vfat/ntfs volumes, and if you do alter then all files will become executable which was the intent of the udisks change in preventing

---

### Post by abumaia on 2010-11-11
thanks for the "Open With" wine tip.  it works for me.  Now it at least appears to be working the way it used to.

---

### Post by wkhasintha on 2010-11-11
this should work now

---

### Post by ubudog on 2010-11-11
> **abumaia said:**
> thanks for the "Open With" wine tip.  it works for me.  Now it at least appears to be working the way it used to.

Cool. :)

---

### Post by ebruzzone on 2010-11-11
What about .jar files? Wine is not able to open them. btw if you tick open with jar it will not work. It gives me the message

The file '/media/ERIC/USB/DimSum.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by mcduck on 2010-11-11
> **ebruzzone said:**
> What about .jar files? Wine is not able to open them.
No, it's not. Java is. :)

"java /path/to/somefile.jar"

or right-click and select the option to run the file with whatever Java version you have installed.

The main point is that if you don't execute a file directly, but only pass it as an argument to some other program (wine, java, mono, sh, python, whatever) the file doesn't need to be executable.

---

### Post by lupulin on 2010-11-11
> **ubudog said:**
> Open a terminal (however you do that in XFCE, I forgot) and type in the following and then try what you did in the beginning. 

```
chmod +x filename
```(filename being the name of the file)

The above command will make the file executable, so everything should work now.  Good luck! :)

Amazing! that worked for me too. I had a java program (StrangeBrew) that would not execute. I had to install open jdk java and then I tried this and it's working now.

Thanks!

---

### Post by ebruzzone on 2010-11-11
> **mcduck said:**
> No, it's not. Java is. :)

"java /path/to/somefile.jar"

or right-click and select the option to run the file with whatever Java version you have installed.

The main point is that if you don't execute a file directly, but only pass it as an argument to some other program (wine, java, mono, sh, python, whatever) the file doesn't need to be executable.

Sorry guys. Not working for me. I even tried the gksudo trick but there is no way I can change the permissions.

---

### Post by mcduck on 2010-11-12
> **ebruzzone said:**
> Sorry guys. Not working for me. I even tried the gksudo trick but there is no way I can change the permissions.

If your file is on a FAT or NTFS partition, or on a optical media like CD or DVD, you are not going to be able to change it's permissions.

If it's on a Linux filesystem, and you can't change the permissions even with sudo, you are doing something wrong.

---

### Post by Morbius1 on 2010-11-12
I'm fairly certain it's not:
> "java /path/to/somefile.jar"It's:
```
java -jar /path/to/somefile.jar
```

---

### Post by XubuRoxMySox on 2010-11-12
This is a kinda-sorta GUI workaround that I use on lazy days when I don't remember the right commands...

Use Synaptic or Software Center to install a way-cool file manager called **PCManFM**.

PCManFM has a cool tool that lets you open a folder as root. Navigate to the folder that has the file you want to change/delete/edit/etc. Click on **Tool > Open Current Folder as Root** and when prompted, enter the root password.

A new window opens with the warning, "You are in Superuser Mode!"

Do your thing there from that Superuser window. When you close it, you are no longer root.

You can also use that "open as root" tool to change file permissions in that folder.

Hope that helps,
Robin

---

