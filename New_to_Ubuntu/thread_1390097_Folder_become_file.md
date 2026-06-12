---
title: "Folder become file"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by ZuLuuuuuu on 2010-01-25
Hello,

Yesterday I created a folder on my NTFS partition and put a few files in it. I used it for a while and it was working fine but after I restarted my system today I saw that the folder looks like a file when I apply "ls" command in terminal. The output for "ls -l" command looks like this:

```
-rwxrwx--- 1 root plugdev      360 2010-01-25 14:08 scooter
```

As you can see there is - instead of d. And the size is smaller than other folders (which is 4096). Do you have any idea what might have happened to the folder? I have created several folders and files before on my NTFS partition with no problem, this is happening for the first time.

I'm using Ubuntu 9.10, 64-Bit.

---

### Post by phillw on 2010-01-25
Hi,

if you haven't been doing other work on the computer, I'd run an fsck on the disk & see if the errant files appear in lost+found.

Pop over to post#2 at [http://ubuntuforums.org/showthread.php?t=546258](http://ubuntuforums.org/showthread.php?t=546258)  For a 'How-To' on fsck. (The commands work with ext4, also)

Regards,

Phill.

---

### Post by halitech on 2010-01-25
did you remount the partition after you rebooted?

---

