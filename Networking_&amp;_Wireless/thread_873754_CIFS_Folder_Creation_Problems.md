---
title: "CIFS Folder Creation Problems"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by ReverendJ1 on 2008-07-29
I am having trouble with CIFS. I have a Windows box that I regularly transfer files and folders to, but if I copy a folder to it with subfolders it always says:
> The folder "subfolder" cannot be copied because you do not have permissions to create it in the destination.
If I hit retry, it will create the subfolder and then fail on the first file, which gives me:
> There was an error copying the file into /media/windowsshare/folder/subfolder/file.
and
> Error opening file '/media/windowsshare/folder/subfolder/file': permission denied.
If I hit cancel here and try again it will copy the files flawlessly. Below is my fstab entry for the Windows share:
```
//windowspc/folder   /media/windowsshare/folder   cifs  guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777   0
```
Does anyone have an idea of why this happens?

---

### Post by ReverendJ1 on 2008-08-14
*Bump* I was just wondering if anyone else has this problem or knows what's wrong.

---

### Post by Iowan on 2008-08-14
One thing I noticed in [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To is ```
sudo mount [COLOR="Red"]-t[/COLOR] cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777
```

---

