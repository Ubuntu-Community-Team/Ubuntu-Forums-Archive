---
title: "Mounting Windows Share on Ubuntu"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by vasiauvi on 2009-10-11
Hello all,
I know that this subject is very talked on this forum and also on other forums and sites but I really don't manage to make it work.
Because of that I've made this new thread and I have the hope that somebody to help me.

I want to make regular backups on other PC with Windows installed. I've done it until now but now it's not working anymore. 
To open the Windows share I press ALT+F2 and write 
```
smb://192.168.2.101/FILME
``` and it worked very well.
After some time I don't know why (maybe because of some updates) but this was not working, the error:"Failed to mount Windows share".
I've installed samba and also smbfs from here [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba") and I can enter from Network/Windows Network/MSHOME/USER/FILME(E)/ .

Can anyone tell me how to mount this share?I've tried some ideas ([http://industriousone.com/mounting-windows-shares-linux](http://industriousone.com/mounting-windows-shares-linux)) but I can't manage it!

Thanks and again sorry because I've started a new thread with this subject.

---

### Post by Boondoklife on 2009-10-11
What happens if you goto Places -> Network -> SERVERNAME, Can you browse the files that way? if you can and you are getting a folder on your desktop that takes you to the share then it IS mounted (look in ~/.gvfs).

---

### Post by vasiauvi on 2009-10-11
Yes, I can browse the files from Places -> Network ->Windows Network ->MSHOME ->USER -> ...
and also with ```
cd ~/.gvfs
``` and here I have "filme %28e%29 on user".
Hmm...then is mounted?
Thanks!I will try to make the backup and if I don't manage I will be back with other questions!

Thanks again!

---

### Post by Boondoklife on 2009-10-11
no worries, i made a link to that folder in my home dir and named it "mounted-drives" this way I can get to it quickly and didnt have to remember the .gvfs stuff

---

### Post by vasiauvi on 2009-10-11
> **Boondoklife said:**
> no worries, i made a link to that folder in my home dir and named it "mounted-drives" this way I can get to it quickly and didnt have to remember the .gvfs stuff
The problem is that when I want to choose the folder on Simple Backup Config (the backup program) it's not appearing the folder .gvfs in my /home directory, but in the root it's appearing but is empty. :(
I really don't understand and it's frustrating that it's so hard in Linux to share some folders.

---

### Post by Boondoklife on 2009-10-11
Well that would completely make sense as it is on a per user basis =P. Since you browsed to the share as XYZ user it put it in XYZ's gvfs folder, wouldnt make sense to just randomly mount it under some other users home dir now would it.

*nix is a lil bit of a curve but once you get it youll see that really this makes sense and wonder what in the world the other OS's were thinking.

---

### Post by vasiauvi on 2009-10-11
> **Boondoklife said:**
> Well that would completely make sense as it is on a per user basis =P. Since you browsed to the share as XYZ user it put it in XYZ's gvfs folder, wouldnt make sense to just randomly mount it under some other users home dir now would it.

*nix is a lil bit of a curve but once you get it youll see that really this makes sense and wonder what in the world the other OS's were thinking.
Yes, I understand this!
But how can I mount the shared folder like on this site [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) because I need to put a backup there and when I put in the backup program the path:
~/.gvfs/filme\ %28e%29\ on\ user/ is not working.
Some days ago worked with just only:
smb://192.168.2.101/FILME but now it's not working anymore and I don't know why!

I've tried the steps from here [http://industriousone.com/mounting-windows-shares-linux](http://industriousone.com/mounting-windows-shares-linux) and didn't worked.

Finally, I will see what I will do.

If you have other suggestions please tell me and also for the ideas from above thank you. It helped me because I didn't know before of the ./gvfs folder.

---

### Post by Boondoklife on 2009-10-11
The only other option I could suggest would be to mount it manually by putting it in the fstab like that second site said. If that is not working then you might not have the proper packages installed to do what you need.

A quick look in the ubuntu packages tells me you might need smbfs to do as the site mentioned.

---

### Post by Alex566 on 2009-10-11
If you still can't get it to work, I would try taking a look at [http://ubuntuforums.org/showthread.php?p=1440697.]("http://ubuntuforums.org/showthread.php?p=1440697") It's what got me connected to my share. Hope this helps.

---

### Post by oldfred on 2009-10-11
Another howto
**[SIZE=1][FONT=Arial][B]*Ubuntu Jaunty file and public folder sharing tutorial by Powel212 ***[/FONT] 
[B][FONT=Georgia]
[http://ubuntuforums.org/showthread.php?t=1233071](http://ubuntuforums.org/showthread.php?t=1233071)
[/FONT][/B][/SIZE] [/B]

---

### Post by vasiauvi on 2009-10-12
Thanks all for your support!
I didn't managed to mount the share folder from Windows with the above tutorials but finally I can backup my data on that folder using rsync like this [http://www.ghacks.net/2009/10/11/backup-your-linux-box-with-rsync/](http://www.ghacks.net/2009/10/11/backup-your-linux-box-with-rsync/) and I've excluded some folders and files with this tutorial:[http://articles.slicehost.com/2007/10/10/rsync-exclude-files-and-folders](http://articles.slicehost.com/2007/10/10/rsync-exclude-files-and-folders).

Thanks for your help!

---

