---
title: "Is there repair option in ubuntu like windows?"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-13
In windows if system files were deleted,by using the Windows bootable cd we can repair our system..It will bring back all the missing system files and there will be no loss in our datas and preinstalled softwares..Like that is there any option in ubuntu?So that i can repair my system if something goes wrong...

---

### Post by Sef on 2010-03-13
> In windows if system files were deleted,by using the Windows bootable cd  we can repair our system..It will bring back all the missing system  files and there will be no loss in our datas and preinstalled  softwares..Like that is there any option in ubuntu?So that i can repair  my system if something goes wrong...

The chance of that happening in Ubuntu (or Linux in general) is rather remote as long as you run as user and not root.   In Windows, since one generally runs as root, it is much more common.

---

### Post by yeats on 2010-03-13
I would say that backing up your /home (where your files and settings live) and /etc (where system settings live) directories to external media would allow you to restore your environment after a reinstall (if your system breaks for whatever reason).

---

### Post by karthick87 on 2010-03-13
How to backup /home and /etc directories?and how to restore it back..Can you give me some detailed information on this?

---

### Post by Chris_cur on 2010-03-13
A live CD can be used to access your files. In case of an emergency.

I don't know about a "repair system" option. openSuse has that option, perhaps we should recommend this to the powers-that-be.

---

### Post by Tikkyca on 2010-03-13
Best thing is to backup your files,and then reinstall the system which is also great thing on windows,and also you will know that your system is without any issue.

---

### Post by Mark Phelps on 2010-03-13
Contrary to popular opinion, you're not running as "root" (or the Administrator) in MS Windows, at least not if:
1) You're running Vista or Win7
2) You have not gone to the trouble to unhide the "real" Administrator account and then, logged in using it.

Instead, you're running as a general user, only getting "root" permissions when you (or an app) requests them.

What tends to happen most often is that some form of malware replaces one or more "genuine" system files with its own.  This is when running "sfc /scannow" launches an app that compares the system files against checksums to see if any were replaced, or are missing, and then replaces/reinstalls them.

---

### Post by Chris_cur on 2010-03-13
> **getyourkarthick said:**
> How to backup /home and /etc directories?and how to restore it back..Can you give me some detailed information on this?

You can download "Simple Backup Config"and "Simple Backup Restore" from either Synaptic or Add/Remove. 

You can also make a .tar.bz2 or .tar.gz of your home directory.  This option takes a little while to finish and you will still have to export that .tar to a dvd or external harddrive.

If you would like I can post directions for either.

---

### Post by yeats on 2010-03-13
> How to backup /home and /etc directories?and how to restore it back..Can you give me some detailed information on this? 

The other posters have good suggestions.  I use rsync, which is a command line tool.  Basic usage would be:

```

rsync -av /home /*backup/directory/path*
```

where */backup/directory/path* is the path to the external media (like a CD-RW or external hard drive).  The "-av" options mean "use _a_rchive mode and be _v_erbose about it."

---

### Post by paydaydaddy on 2010-03-13
I have had a couple of occassions where my computer would not boot and was able to repair it by hitting esc just prior to booting from harddrive. You have a 3 second window to do this. You will get a screen with a list of kernal (kernel?) options to load or recover. By choosing recovery of the latest kernal the system was able to repair itself and boot. This may be what you are looking for.

---

