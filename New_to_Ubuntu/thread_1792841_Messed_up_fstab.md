---
title: "Messed up fstab"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by twhansen on 2011-06-28
Hi guys.

Well, I am definitely a newbe, so I am sure someone out there will be laughing their pants off over the trouble I brought myself in.

I was trying to mount some network drives, I found this post:

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

and thought I was home free. I tried to do what it said, but apparently messed things up big time in the process. Now my Ubuntu partition starts up with the command line and I cant get into the GUI and I can't edit fstab back to what it originally was (I can edit the file using Editor, but can't save it (even after starting Editor with sudo). If I can start up the GUI I can probably find my way through the mess I have created. But why oh why does it suddenly start up with only the command line?

Hopefully someone can guide me on my way.

Thanks.

Thomas

---

### Post by Elfy on 2011-06-28
Hi, if all you did was edit fstab and it failed - boot into recovery mode - that is the second ubuntu option.

It'll take you to a small menu - choose root, no need for network. Edit the file with the cli editor 

nano /etc/fstab

undo your changes - save the file with ctrl+X, Y, Enter.

Then type reboot and enter

---

### Post by twhansen on 2011-06-28
Hi.

Thanks for your input. It went all fine until I tried saving fstab. It then tells me that he file system is read-only. I find that strange. When I am in root - recovery mode, am I not super user?

Thomas

---

### Post by Elfy on 2011-06-29
> **twhansen said:**
> Hi.

Thanks for your input. It went all fine until I tried saving fstab. It then tells me that he file system is read-only. I find that strange. When I am in root - recovery mode, am I not super user?

ThomasYou should be. I assume you tried with sudo as well just to see.


You could try and do it with a livecd - you'll need to mount your partition - click on the appropriate one in Places. 

Obviously not just /etc/fstab as that would not be your install one - it'll be /media/*something*/etc/fstab if you try and do it with nano.

---

### Post by Ozymandias_117 on 2011-06-29
Another problem could be that the changes are making it mount as read only, you could try. ```
mount -o remount,rw /
``` (pretty sure that's right, on my phone so I can't check the man page :P)

---

