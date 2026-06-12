---
title: "Root Permission/Log In"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by carbonbased on 2010-01-26
I'm being denied access to a hard drive on my PC--denied as in not allowed to move data files to it, and being told I do not 'own' the device--that it's owned by root.

Alright, so I tried to log in as root to change the permissions on the drive. But the password I used when installing, for root, will not work. Now--I am certain that I know the pw--it's very simple and I use it all the time. In fact, it's the same pw as my 'personal' acount. (the pc is in my house--no threats around)

Why is the pw I entered when installing not working? No other pw has been used, for root or my personal acct.  What fresh hell is this? =)

---

### Post by phidia on 2010-01-26
What filesystem is the drive? NTFS or something else? I think it would help to know the specific error messages you are seeing; how the drive is connected (usb, sata, ?) and how the drive is being mounted?

---

### Post by carbonbased on 2010-01-26
> **phidia said:**
> What filesystem is the drive? NTFS or something else? I think it would help to know the specific error messages you are seeing; how the drive is connected (usb, sata, ?) and how the drive is being mounted?

The drive can be mounted by my personal acct. But using Nautilus, I could not move directories from another drive to it.  It was an NTFS, but a few days ago I emptied it and formated to ext4. (recently switched from WinXP to Ubuntu--from dual boot, to uno boot). So, 'cut' from drive A to 'paste' to drive B, but 'paste' didn't show in the menu.

Went into Disk Utility and saw that the drive is owned, all permissions apply only to root.

I was getting similar strangeness in BASH today while installing something. I finally found the advice to use: su -i, which worked--it took me to root right away, even after I was being told that 'authorisation failed'.

---

### Post by phidia on 2010-01-26
You should search for drive mounting-see the comunity docs. You can automount that drive by editing fstab.

---

### Post by anaconda on 2010-01-26
you can start nautilus (=file browser) with root rights with: (in terminal)
```
sudo nautilus
```

then you should be able to copy anything you want.

---

### Post by presence1960 on 2010-01-26
You need to set the permissions for that disk. Open a file browser and mount that disk by highlighting it on the left pane. You will know it is mounted when you see directories/files on the right. 

Now open a terminal and run ```
gksu nautilus
```
This will open a file browser with root priviledge.

On the left pane choose Filesystem. On the right open the Media folder. Find your disk and right click it. Choose Properties. Click on the Permissions tab. At the top for Owner use the drop down box to select your user account. For Folder access choose Create & delete files. 

For Group set the group you belong to (usually the same name as your user account). For folder access choose Access Files. At the bottom click apply to enclosed files button.

You may have to reboot for the permissions to take effect. You will now own that device and be able to perform read/write operations to it.

---

### Post by presence1960 on 2010-01-26
> **anaconda said:**
> you can start nautilus (=file browser) with root rights with: (in terminal)
```
sudo nautilus
```

then you should be able to copy anything you want.

That will work, but you shouldn't  open a root browser every time you want to copy files.

The best solution is to set permissions so the user owns that device. Then the user will be able to read/write to that device without root priviledge.

---

### Post by anaconda on 2010-01-26
And if the disk is used for file storage (no operating system in it) then you can change the permissions of all the files and directories on it by:

sudo chmod a+rw -R /media/disk
(gives all read& write acess to all files on the disk maybe not the best solution, because directories need also the x right to work (execute))

but maybe even better would be 
sudo chown -R yourusername::yourusername /media/disk
(changes all the files to be owned by yourusername)
  
Just change the yourusername to be ..well.. your username

and change the directory /media/disk to be whatever your disk is mounted to...

---

### Post by presence1960 on 2010-01-26
> **anaconda said:**
> And if the disk is used for file storage (no operating system in it) then you can change the permissions of all the files and directories on it by:

sudo chmod a+rw -R /media/disk
(gives all read& write acess to all files on the disk maybe not the best solution, because directories need also the x right to work (execute))

but maybe even better would be 
sudo chown -R yourusername::yourusername /media/disk
(changes all the files to be owned by yourusername)
  
Just change the yourusername to be ..well.. your username


and change the directory /media/disk to be whatever your disk is mounted to...

I gave the graphical solution of this because I didn't know how experienced the OP is.

---

### Post by carbonbased on 2010-01-26
Very helpful information. Problem solved.
----
Love the boot script. Great idea.


Thanks!

---

### Post by presence1960 on 2010-01-26
> **carbonbased said:**
> Very helpful information. Problem solved.
----
Love the boot script. Great idea.


Thanks!

Glad you got it fixed! You learned two ways to do the same thing today- a graphical and a cli based solution. Either will work. That is the power of linux. For every task there is usually more than one way to get it accomplished.

The boot info script- the credit goes to meierfra for that. He provides a great tool for us to use when troubleshooting set up & boot problems. We don't have to blindly guess what the person has on their machine.

---

