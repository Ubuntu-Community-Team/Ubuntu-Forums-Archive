---
title: "how do I automate terminal commands"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by noworldorder on 2010-04-30
in order to mount an external hard drive I have to make the following commands in terminal:

sudo -a
  	 	 	 	 	 	  mount -t smbfs //192.168.1.104/MediaShare /mnt/MediaShare  
 mount -t smbfs //192.168.1.104/Backup /mnt/Backup


rather than doing this every time is there a way that I can automate this process so it happends whenever I boot up?


Thanks ~ chris

---

### Post by dv3500ea on 2010-04-30
make  a file called, for example 'automount.sh' with contents:
```

#!/bin/sh
mount -t smbfs //192.168.1.104/MediaShare /mnt/MediaShare 
mount -t smbfs //192.168.1.104/Backup /mnt/Backup

```
next run
```

chmod +x automount.sh

```
next go to System -> Preferences -> Startup Applications
click add
browse for the file for command
prepend 'gksudo ' to the command text box (without the quotes)

---

### Post by noworldorder on 2010-04-30
this is perfect but I am a total newbie...  

what program do I write the commands in and what do I save the file as.

thanks - chris

---

### Post by blueridgedog on 2010-04-30
You can use any text editor, gedit comes standard and will work fine.

---

### Post by Girya on 2010-04-30
use gedit to write the script. 
save as  automount.sh

open up a terminal and paste ```
chmod +x automount.sh
``` into the command line 

google linux shell scripts and dive down the rabbit hole

good luck kevin

---

### Post by noworldorder on 2010-05-01
hmmm.... I wonder what I am doing wrong. It doesn't work yet.   Does it matter where I save the file?  I made a 'scripts' folder in Documents.  Does the file need to be n root?

In 'start up programs' this is what I have under command

/home/chris/Documents/SCRIPTS/gksudo automount.sh

any thoughts about why it isn't working?

thanks ~ chris

---

### Post by ankspo71 on 2010-05-01
> **noworldorder said:**
> in order to mount an external hard drive I have to make the following commands in terminal:

sudo -a
  	 	 	 	 	 	  mount -t smbfs //192.168.1.104/MediaShare /mnt/MediaShare  
 mount -t smbfs //192.168.1.104/Backup /mnt/Backup


rather than doing this every time is there a way that I can automate this process so it happends whenever I boot up?


Thanks ~ chris

Have you already tried using fstab to mount these?
[http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)
This should give you a good head start.
And this link explains what you see in fstab:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by Paqman on 2010-05-01
> **noworldorder said:**
> 
rather than doing this every time is there a way that I can automate this process so it happends whenever I boot up?


Absolutely.

In short:
[LIST=1]
[*]Create a folder as a mount point on your system
[*]Add an entry to /etc/fstab that mounts the network share to that location when you boot
[/LIST]

You'll also get better performance if you use cifs instead of smb. [Detailed instructions here.]("http://ubuntuforums.org/showthread.php?t=261366")

---

### Post by noworldorder on 2010-05-01
I entered the following in fstab:

mount -t smbfs //192.168.1.104/MediaShare /mnt/MediaShare  
 mount -t smbfs //192.168.1.104/Backup /mnt/Backup

no results - I really don't know what I am supposed to enter exactly so I am not surprised it didn't work

---

### Post by mechro on 2010-05-01
> **noworldorder said:**
> I entered the following in fstab:

mount -t smbfs //192.168.1.104/MediaShare /mnt/MediaShare  
 mount -t smbfs //192.168.1.104/Backup /mnt/Backup

no results - I really don't know what I am supposed to enter exactly so I am not surprised it didn't work

Those are not the correct settings for an fstab entry... I don't know the entries required to mount a "samba network drive" in fstab.

Going back to your automount script, try this command...

```
gksudo /home/chris/Documents/SCRIPTS/automount.sh
```

---

### Post by mechro on 2010-05-01
Another link which may help you figure out the correct fstab entries...

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Paqman on 2010-05-01
> **noworldorder said:**
> 
no results - I really don't know what I am supposed to enter exactly so I am not surprised it didn't work

Exact details of what to put in fstab are in the link I posted orginally. Here it is again in case you missed it: [How to mount Windows shares automatically]("http://ubuntuforums.org/showthread.php?t=288534").

Personally I don't bother fiddling about with netbios names like it mentions, I just assign a static IP to my NAS in the router and point my fstab entry at that. Just skip over that whole section if you choose to do the same.

---

### Post by noworldorder on 2010-05-01
Success! thanks 

> Those are not the correct settings for an fstab entry... I don't know the entries required to mount a "samba network drive" in fstab.

Going back to your automount script, try this command...

 	Code:
 	gksudo /home/chris/Documents/SCRIPTS/automount.sh


---

