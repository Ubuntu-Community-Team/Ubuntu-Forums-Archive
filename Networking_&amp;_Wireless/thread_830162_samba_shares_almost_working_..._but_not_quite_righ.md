---
title: "samba shares almost working ... but not quite right"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by gopher38 on 2008-06-15
Hello, I'm trying to permanently connect to an NAS server with a vfat drive.  I'm almost there, I think, but a couple of annoying things:

1) Mount command works, but not at boot.

I put my mounting command in fstab (last line):

//192.168.1.100/wdhd    /media/wdhd   cifs    credentials=/root/.smbcredentials,uid=gopher38,gid=users,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

When I boot, the disk isn't visible.  But if I run "sudo mount -a" (which runs fstab, right?), it pops up and works just about perfectly.  Anyone have an idea why?  The command would work when I run it from a terminal, but not at startup?

2) Can't create a link
I said that the disk works almost perfectly.  Why do I say "almost"?  I can create and delete files, create and delete folders, rename, basically do everything EXCEPT create links to folders on the remote disk.  It says that I don't have permission. But like I said, I can delete the whole disk if I try.  Why are links different?

Thanks in advance for any assistance.

---

### Post by gopher38 on 2008-06-15
Well, for anyone else who has these issues, I didn't really find the answer, but I did find work arounds.

1) fstab mount doesn't work but command line mount does

This seems to be a timing issue.  I found another thread that treats this issue, and some people were able to fix it be adding "auto" or "user" to the fstab mount line.  This didn't work for me, nor for most people on that thread.  Someone did post a bit ugly workaround, which was to put the lines:

sleep 30
/bin/mount -a -t cifs

In the rc.local file.  This seemed to fix the issue for everyone else, including me.  I tried eliminating the sleep line, and it didn't work.  I did reduce it down to 5 though, and it still worked.  So: no sleep = doesn't work; sleep of 5 or 10 = does work.

Whatever.

2) Can't create links to my Samba share (don't have permissions), even though I can delete every file on the disk.  

Well, I just went in and created the symbolic links from the terminal, and that worked.  I didn't have to use "sudo", just a normal "ln" command, so I don't see why that had more permissions than nautilis, but so it is.

Ciao.

---

