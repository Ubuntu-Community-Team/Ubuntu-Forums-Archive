---
title: "What is mounting / unmounting"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by thadacto on 2009-02-10
I have two hard drives, one is dual boot Ubuntu 8.04 / Windows XP and the other was from an old computer which was installed when I bought my new computer, as it had lots of info that I wanted. It originally had Windows 98 but the shop I bought the computer wasn't able to get Win 98 to function (the new computer is an AMD 64). I used a partition manager to partition the second drive (partitions called WIN98 and ENGLISH) and I only use it for storage.
Some of my Ubuntu programs (Ubuntu, Rhythmbox, GIMP) can "see" the two partitions  while other programs cannot (OpenOffice, KMPlayer, Scribus). Someone has suggested that I have not mounted the partitions. Hence, what is mounting and unmounting the partitions?
Any help much appreciated.

---

### Post by muteXe on 2009-02-10
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

That's what it is.

[http://www.psychocats.net/ubuntu/mountwindows#menu](http://www.psychocats.net/ubuntu/mountwindows#menu)

That's how to do it through the GUI.  Check out the rest of that last site for more details.

Tom

---

### Post by Simian Man on 2009-02-10
Well, when a man and a woman love each other very much...

---

### Post by arjuntank on 2009-02-10
> **Simian Man said:**
> Well, when a man and a woman love each other very much...

Hell yeah!

---

### Post by tarps87 on 2009-02-10
The short answer is mounting makes the drive accesable to the os, 
unmounting closes the connection to the drive. The same type of thing as safely removing a external drive on windows

If you open the drive using nautilus (the file browser) this should mount it for you, to unmount right click and select unmount
If you want to mount it on boot there are some GUI apps but I can't remember their name, I usually just modify the fstab file:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by thadacto on 2009-02-10
Thanks muteXe for the links.

---

### Post by muteXe on 2009-02-10
You're welcome mate.  I'd explain more, but my boss is sitting quite close to me, and i'm supposed to be working :)

---

### Post by thadacto on 2009-02-10
To MuteXe: Surprised you got into work - I see that you're having problems with the weather over there!

To tarps87: Thanks mate those were very useful links.

Unfortunately, I'm not very good with Linux nor all this terminology - for that, Windows was easier to follow. However, I now have the partition appearing in OpenOffice in both "open file" and "save" commands. Interesting to see if it's still there when I reboot.
Many thanks again to both of you.

---

### Post by tarps87 on 2009-02-10
> **thadacto said:**
> 
To tarps87: Thanks mate those were very useful links.

Unfortunately, I'm not very good with Linux nor all this terminology - for that, Windows was easier to follow. However, I now have the partition appearing in OpenOffice in both "open file" and "save" commands. Interesting to see if it's still there when I reboot.
Many thanks again to both of you.

Apologise, the graphic application I was thinking of is called pysdm you can install it by typing this into a terminal (applications -> accessories -> terminal)
```
sudo apt-get install pysdm
```
This should guide you through making the drive available when you login.
You will find the application in System -> Administration
If you browse to the drive (there should be an icon of the desktop) this will mount the drive for you which will mean that OpenOffice will be able to use it.

If you think of using the 'safely remove' in windows when you want to remove a usb device it is the same type of thing. Once remove windows can not use the device. I hope this is a bit clearer

> **muteXe said:**
> You're welcome mate.  I'd explain more, but my boss is sitting quite close to me, and i'm supposed to be working :)

Mine has gone home :)

---

### Post by thadacto on 2009-02-10
I've rebooted and all is working fine. All applications can now see the partition.
I used the NTFS application. Not a very good name for the application, I thought it was something to do with the Windows  file system. So I never investigated it or to be more honest, I steered away from it.
Thanks again to both of you.

---

