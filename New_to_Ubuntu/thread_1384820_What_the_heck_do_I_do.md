---
title: "What the heck do I do ?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by ericstrom on 2010-01-18
I added OpenShot video editor to me system. Seems to be working great. Very pleased. But suddenly I can't open Pidgen anymore. I get a message saying opening Pidgen, then it just disappears.It seems to be trying to open but just can't. I also noticed that Empathy IM client doesn't open either (but doesnt even seem to be trying)

Running Karmic 9.10

Any suggestions or ideas would be appreciated. What do I do ?****

---

### Post by fooman on 2010-01-18
try opening pidgin or empathy from a terminal and see what output that gives.

---

### Post by ericstrom on 2010-01-18
OK, that sounds like a good idea. But how do I do that ??

---

### Post by pastalavista on 2010-01-18
In a situation like yours, I would first run in Applications|Accessories|Terminal these commands```
sudo apt-get update

sudo aptitude safe-upgrade
```
then try the clicks again and if they still don't open then do what fooman suggests.. in the very same terminal enter```
pidgin

empathy
``` and see what's up

---

### Post by Diametric on 2010-01-18
> **ericstrom said:**
> OK, that sounds like a good idea. But how do I do that ??
 
You should just be able to type in "empathy" or "pidgin" from a terminal and it will open
 
Edit:  Looks like someone alredy told 'ya!  Good luck.

---

### Post by ericstrom on 2010-01-18
I followed pastalavisa's suggestions. The typed pidgen and got the following message :

eric@eric-desktop:~$ pidgen
No command 'pidgen' found, did you mean:
 Command 'pidgin' from package 'pidgin' (main)
pidgen: command not found


So what does that mean ? What now ?

---

### Post by pastalavista on 2010-01-18
> **ericstrom said:**
> I followed pastalavisa's suggestions. The typed pidgen and got the following message :

eric@eric-desktop:~$ pidgen
No command 'pidgen' found, did you mean:
 Command 'pidgin' from package 'pidgin' (main)
pidgen: command not found


So what does that mean ? What now ?

it means you spelled pidgin wrong. spell it right this time. :P

---

### Post by ericstrom on 2010-01-18
Thanks pasta. A bit of a duh moment there. My apologies. But this time I spelled it right and got the following:

eric@eric-desktop:~$ pidgin
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Illegal instruction

I also noticed I'm having problems with the Software Center. It opens but then shuts right down.

Ideas ?

---

### Post by pastalavista on 2010-01-18
Wow.. don't know what that's all about, but according to google is [this stuff]("http://alereimondo.no-ip.org/OpenCV/34").

If that's important to you, I'll leave to the experts, but if not, what I would do is a full reinstall of Ubuntu in MANUAL mode and UNCHECK the 'format' boxes on the partitioner menu. That will give you a fresh default install without removing any files created since the first install. It will undo any changes to the system (updates) but nothing in the home directory will be touched so few things will need to be reconfigured.

edit... be sure to use the exact same user name if you reinstall.

---

### Post by gypsumwolf on 2010-01-18
After you downloaded the Ubuntu ISO did you do a checksum to see if it was all downloaded correctly? Sometimes if its not you can get weird errors on a fresh install.

---

### Post by ericstrom on 2010-01-18
I would like to do the full reinstall ?  May I ask how I go about doing that. I don't have a Karmic disk by the way. 

By the way Pasta, thanks much for helping me through this.

---

### Post by ericstrom on 2010-01-18
I'd like to do a fresh ubuntu install. How do I do that ? Can I do it without a disk ?

---

### Post by PenguinInside on 2010-01-19
Well, do you have a DVD writer? 

Just download the Karmic ISO (CD image) from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Then go to Applications: Accessories: CD/DVD Creator. That's the simplest way to install Ubuntu.

You can also do it from a USB disk, but it's somewhat more complicated to create the disk. (You can try System: Administration: USB Startup Disk Creator)

---

