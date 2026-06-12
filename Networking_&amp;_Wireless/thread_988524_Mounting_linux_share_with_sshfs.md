---
title: "Mounting linux share with sshfs"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by dagring on 2008-11-20
I have installed the sshfs-fuse package, and successfully mounted the share on my desktop. The problem is when I try to access the share. I get the message: There is no application installed for this file type. 

I have done a $ls -l and there is practical no information to seen for this share. There are only question marks. 

Can anybody give me a hint where to search for the answer to this problem?

dagr

---

### Post by Jive Turkey on 2008-11-20
It sounds like your client is trying to automatically open some file in the mounted directory when you open it.  I have had some instances of a similar problem when mounting, nautilus pops up in the dir, and then mplayer or something comes up and tries to open a file that it isn't even associated with for no reason.  Its weird and probably a security risk too.

Lets try some terminal commands to open nautilus in the directory and see if we can capture some instructive messages.

---

### Post by dagring on 2008-11-20
Which commands?

---

### Post by scottuss on 2008-11-20
(Error post, please see below for what I meant to put!)

Mods, please remove this!

---

### Post by scottuss on 2008-11-20
What happens when you go to Places > Connect to server > SSH and then enter the info there (don't specify a folder)

It should mount the share automatically and open the / directory in Nautilus for you.

---

### Post by Jive Turkey on 2008-11-20
ok, here's what I got running "nautilus-connect-server" from a terminal (which is equal to Places>Connect to Server in the menu).

```
user@client:~$ nautilus-connect-server

** (nautilus-connect-server:303): WARNING **: Wrong permissions for /tmp/orbit-ck

user@client:~$ MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/user/.gvfs/sftp on XXX.XXX.XXX.XXX/home/user/TS.
Seek failed


Exiting... (Quit)

```If there was a smiley for horrified surprise I would put it here, I did not type that command to open mplayer it was called by nautilus, I think because the folder is named TS, like one might see in a DVD image, it is not a video folder.  nautilus should just open the folder IMHO and not pass any files to other applications, very dangerous potentially.

---

### Post by dagring on 2008-11-21
I tried to use the natutilus-connect-server. I got the folder on my desktop, but i doesn't get the folder on the list of mounted devices/folders, and I have tried to cd into it, but cannot find it.

The reason I want to mount the folder, is that I want to synch this folder with another on the host machine, and this cannot be done without mounting.

---

### Post by supremedalek on 2008-11-21
I am still waking up, so do not mind if I sound spaced out. Anyway, what happens if you mount the share just above where your file is?

---

### Post by dagring on 2008-11-21
That sounds spaced out, but if I understand you right. I go one level up to the mother folder? 

The folder where the "mounted" folder is within, is on the desktop, and cannot be found in the file lists I know of. It's just a short cut named "sftp on 192.168.1.106".

---

### Post by supremedalek on 2008-11-21
Hmmm. If you call your machine boris and the machine the files you want spider, what is the path in spider to reach the files you seek?  Ex: I save my picts in a machine called trento. If I want to get to them from my laptop, monaco, I do something like

```
raub@monaco:~$ sshfs dalek@trento:Pictures/Originals Pictures/Originals 
dalek@trento's password: 
raub@monaco:~$ pushd Pictures/Originals/
~/Pictures/Originals ~
raub@monaco:~/Pictures/Originals$ ls
163CANON        2007-04-18  2007-10-01  2007-12-29  2008-08-05
[...]
2007-04-16      2007-09-29  2007-12-25  2008-08-04
raub@monaco:~/Pictures/Originals$ 

```

So they are mounted to ~raub/Pictures/Originals in monaco.

---

