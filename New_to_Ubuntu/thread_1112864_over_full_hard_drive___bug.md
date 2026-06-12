---
title: "over full hard drive ?  bug ?"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by lightnin on 2009-04-01
so - I installed a 10gb HDD to have a play at installing and upgrading and backing up/restoring my home directory.

I found out that you can make a syanptic list of all your pakages and re-install them.

all looked ok and everything seemed like it had worked, but I had ran out of room.

remember this is a 10gb drive

[IMG]http://i121.photobucket.com/albums/o238/RichAAC-UK/Screenshot-1.png[/IMG]


there is more data on the disk than will fit !?!
should ubuntu let this happen ?

needless to say, it didn't run too well , up to the point that it wouldn't let me log in.

is it a bug ?

if it is a bug, should I report it ?

I was using 8.10 - and fully up to date.  

Thanks for looking :)

---

### Post by 3rdalbum on 2009-04-01
Your filesystem contains more than just physical data on your main hard disk, so no - it's not a bug, it's just counting the virtual filesystems as well as the real filesystem.

---

### Post by lightnin on 2009-04-04
that doesn't make sense to me, but thanks for the answer :)

---

### Post by 3rdalbum on 2009-04-04
Linux creates "files" that actually represent hardware devices; this makes things very convenient because if you want to send data out through a serial port, you don't need to fiddle around with low-level programming, you just literally write data to the appropriate file and it automatically gets sent.

Those files are shown as having sizes, but in actual fact they take up no space on any disk. Virtual files.

Linux also allows userspace programs to look at and modify parameters and properties of the currently-running hardware and software, and the way it does this is through virtual files. For instance, if you look inside the /sys directory, you can find a file that contains the current speed of the CPU and what method is used to raise or lower ths speed. You can actually write the name of a different method into the "speed governor" file and the kernel will automatically apply that method. These files also appear to have size to them, but in fact they don't take up any hard disk space.

All running programs have information about themselves stored in the /proc directory. Each program's file in /proc appears to take up as much HDD space as RAM space, but in fact this file is not taking up any HDD space.

When Gnome goes to count the size of your filesystem, it also counts the size of these virtual files. It has no way of knowing that they are merely figments of the kernel's imagination. In addition, any external drives are mounted in /media, so their contents also get counted as they are part of the filesystem.

I like to think of it a different way: An empty, clear plastic lemon squash bottle with yellow celephane wrapped around the inside of the bottle. It looks like the bottle is full of lemon squash, but if you pour some liquid into the bottle you will discover that the bottle was actually empty.

---

### Post by Net_Resident on 2009-04-04
That was an interesting explanation 3rdalbum, thank you for taking the time to write it.

---

### Post by 3rdalbum on 2009-04-04
I'm glad it was of interest.

---

### Post by lightnin on 2009-04-06
Thanks very much for that 3rdAlbum !

so, the key is, I am looking at the 'filesystem' size - not the hdd size.

your explaination has made it clear to me now.

---

