---
title: "Help with drive sharing"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by iceclimber1973 on 2009-11-05
I have just installed Ubuntu 9.1 and have VERY limited knowledge of Linux.  I got SAMBA installed and set my workgroup correctly but have a problem sharing ext hard drives formatted NTFS.  I plug the drive up and it automounts fine.  Using the GUI I navigate to /media/mcp_backup and right click on my drive.  Under sharing options I share the drive across my network.  From my windows box I can see the drive but when i click on it i don't have permission to view the contents.  It seems as though the automount is setting permissions incorrectly.  If I unmount the drive and the mount in manually, I have no issues sharing with my windows box.  I have tried fstab with no luck but that could be that I don't know what i am doing.  The manual workaround works but is a pain and i would like for the automount to allow me to share the drive across the network.  Thanks for the help!

---

### Post by iceclimber1973 on 2009-11-05
did i post this in the wrong spot?

---

### Post by iceclimber1973 on 2009-11-08
anybody?

---

### Post by yanceypd on 2009-11-08
Try installing ssh  see if that helps.

---

### Post by iceclimber1973 on 2009-11-09
How would installing SSH help with sharing on my local network?

---

### Post by alphaniner on 2009-11-09
Well, what are the permissions when auto-mounted, and what are the permissions when manually mounted?  Post the output of
**ls -l /media** in each case.  Also, how is your share set up ('Allow Others...', 'Guest Access...') and what is the output of
**cat /var/lib/samba/usershares/mcp_backup**?

I doubt I have a solution for you, but getting more info out into the open can't hurt.

---

