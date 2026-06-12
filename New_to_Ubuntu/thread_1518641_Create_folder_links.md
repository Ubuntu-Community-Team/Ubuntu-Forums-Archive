---
title: "Create folder links"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by kkj.droid on 2010-06-26
I have an awesome setup in Windows 7, where I have a second partition mounted to C:\Users. Because C:\Users is basically /home, I thought I'd mount the same partition to /home in my Ubuntu install. That way, I could save a document as a .docx in Ubuntu, and it would show up in C:\Users\Me\Documents in Windows. Or, I could download a picture in Windows, and it would show up in /home/me/downloads in Ubuntu. Thing is, Windows can't read EXT4, and Ubuntu won't mount NTFS as /home. So, I thought I'd create a shortcut to /media/dev/sda3, named "home" under /, a technique I have used in Windows before to have things link. For example, C:\Documents and Settings is linked to C:\Users in Windows Vista and 7, so that programs that want to stick stuff in your documents but haven't amended the filepath from 2K/XP can do so. How can I achieve this in Ubuntu 10.04 LTS 32-bit?

---

### Post by khelben1979 on 2010-06-27
To create soft/hard links you can use the ln command. ```
man ln
``` for more information.

To mount your NTFS partition, you can mount it directly at the /mnt catalog by using the mount command. ```
man mount
``` for more information.

---

### Post by oldfred on 2010-06-27
You can do the linking, but I prefer not to directly write into a system partition with a different system unless it is for repairs. I create a shared NTFS partition and write any data that I might need in both like firefox & thunderbird profiles and all photos. Since I am mostly in Ubuntu now I also have a /data partition in Ubuntu just for all the data I know I will never want in windows.

---

