---
title: "Can't access USB drive share"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by SonicSteve on 2007-03-01
Greetings everyone,
I'm trying to share usb drives. Either thumb drives or external 20gb usb hard drive. Neither one is accessible though over the network. The share can be seen but they are impossible to connect to. 
1. I either get a login window asking for a password, If I try to enter a password it rejects it
2. or a generic "the folder contents could not be displayed" message.


I'm sharing between 2 Ubuntu computers. The filesystem on the external 20gb drive is ntfs and I'm successfully using NTFS-3g with it. The thumb drives are just FAT. 

Is there some restriction on sharing USB drives?

---

### Post by SonicSteve on 2007-03-02
OK let's ask this a bit differently,

Is anyone sharing USB external hard drives with either samba or NFS successfully? I haven't really investigated NFS much yet but it's next on my list. To this point I've tried samba.

---

### Post by SonicSteve on 2007-04-11
This will either help or make it more confusing.
I connected a windows computer to the network and it can access the shares perfectly. still the same response from Ubuntu computers though. 
I should have mentioned that they are samba shares. I don't understand why I can share samba between Ubuntu machines well except when I'm sharing from a USB source drive. 
Would it be better if I mounted the drive in FSTAB instead of allowing automount for USB drives?
I think I'm just talking out loud now. :-$  Don't you know the value of talking to your self? I've solved many computer problems this way.

I know this was a poorly constructed request for help, sorry.

---

### Post by znejk on 2007-04-22
Hey im having the same prob between 2 ubuntu feisty machines. The fstab option does not fix anything :( will post if i find solution :)

---

### Post by arcticblue on 2007-09-18
I can see that many threads go largely ignored in this forum... I have a curse that when I post to a thread, the thread dies.  Let's see if it happens again.  

Having the same problem here.  I have all my movies and music on an external and want to share it with my other feisty machine.  It can see the share, but it absolutely refuses to go in to it.  It says something along the lines of "Folder could not be found".  I've tried connecting with smbclient and it fails also.  I've added it to fstab and also used automounting.  I do not have any Windows machines to test it with, but if I can't get this working, I'm going to have to say buh-bye to ubuntu.  Someone out there must know an answer to this.  

This is a pretty big problem and something that is trivial to do in Windows.  This needs to be seriously looked at in future versions of ubuntu.  It is stuff like this that slows adoption down.

---

### Post by arcticblue on 2007-09-18
Just FYI, I have submitted a bug report about this.  [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/140686](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/140686)

---

### Post by Wordcrasher on 2007-10-04
Hi,
I have the same exact problem. I can share folders on internal disks between my 2 Ubuntu machines. 
When I try to access a shared folder on my USB HDD i get error: "The folder contents could not be displayed".

---

### Post by funkameleon on 2007-10-04
I have the same problem

I can see my shared folders on my external USB hard drive, but I can't access it neither from a winxp machine nor a ubuntu machine, via LAN using samba. No problem for the shared folders on my internal drives.

I tried everything Ive read about on the net, it just doesn't work

---

### Post by Wordcrasher on 2007-10-04
Ehi,
I found the solution here [http://ubuntuforums.org/showthread.php?t=452984](http://ubuntuforums.org/showthread.php?t=452984).

---

