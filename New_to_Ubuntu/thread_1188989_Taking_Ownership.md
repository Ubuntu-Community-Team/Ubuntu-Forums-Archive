---
title: "Taking Ownership"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by VoodooLoveDog on 2009-06-16
I've done some hunting and can't seem to find the command that will allow me to take ownership of every file and folder on a mounted drive in order to copy them.

Some background. I recently migrated a friend's PC from an 7.10 installation to a new 9.04 installation on newer HW. I pulled the old drive and mounted it via a USB cable. All I want to do is copy the two user folders from /home to a location on my laptop so I can then xfer specific folders to the new PC via a USB key. 

I ran the command "sudo -s nautilus" so I could be elevate to root and copy the files but I keep getting errors that relate to "Permission Denied". I right-click the user's root home folder and choose to take ownership, but it only seems to work on the folder I've right-clicked. 

Is there a command to allow me to take ownership of every darn file/folder under the user's root folder?

Thanks for the help.

---

### Post by ZackM on 2009-06-16
try just becoming root.

```
sudo bash
```

Use at your own discretion.

---

### Post by VoodooLoveDog on 2009-06-16
This doesn't seem to help. At least the way I'm doing it. If I run "sudo bash" then execute nautilus, I still run into a problem with files in subfolders not having the proper permissions to allow me to copy.

I know in windows (sorry) I can choose to take ownership of the all subfolders and files of a given directory. This doesn't seem to be the case the way I'm doing it.

---

### Post by Dragonbite on 2009-06-16
```
sudo su
```
Gives you root privledges

```
cp -rf /home/xyz /media/secondharddrive
```
"r" is recursive (do all folders), "f" force

Are the permission errors for YOUR home directory, as in you are trying to copy a file that is in use?

Can also look into rsync, which may work better (grsync is the GUI front-end).

Or you could try backing it up with Just-In-Time backup utility and then restore it to the new drive?

Oh, if you have any links/symlinks then that may mess things up. Try copying everything else.  I got in trouble with my CrossOver and its recursive links to other parts of my /home directory.

Maybe try copying the non-hidden files and folders first, then unhide and go through the hidden folder one-at-a-time and see which ones are throwing you the error. You may not need that folder.

---

### Post by snakeman21 on 2009-06-16
Let's say your drive is mounted at /media/disk/.  Open a terminal and type:

```
sudo chown username /media/disk
```

Replace "username" with your username and "disk" with the actual mountpoint of the drive.  It will ask for your password.  Enter it and hit enter, this will grant ownership to you.  You do not need to do this every time, only once.  Linux will recognize it every time you plug it in thereafter.  

*The command "chown"  means CHangeOWNer.

---

### Post by VoodooLoveDog on 2009-06-16
Thanks for the reply. I did a little more homework and re-asked my question to Google. Here's the command I used as root:

chmod -R +rw /media/disk/home/"username1"
chmod -R +rw /media/disk/home/"username2" 

This made all of the files/folders in the user's directory read and writable. From there I copied the files out to a directory I had created on my desktop.

I wasn't aware of that -rf switch on the cp command, so it looks like I learned a few things from this thread. Thanks again!

---

### Post by ZackM on 2009-06-16
> **VoodooLoveDog said:**
> Thanks for the reply. I did a little more homework and re-asked my question to Google. Here's the command I used as root:

chmod -R +rw /media/disk/home/"username1"
chmod -R +rw /media/disk/home/"username2" 

This made all of the files/folders in the user's directory read and writable. From there I copied the files out to a directory I had created on my desktop.

I wasn't aware of that -rf switch on the cp command, so it looks like I learned a few things from this thread. Thanks again!

Nicely played! Haha. Glad to see you got it. Sorry I couldn't be of more help.

---

