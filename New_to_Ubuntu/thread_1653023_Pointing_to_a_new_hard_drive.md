---
title: "Pointing to a new hard drive"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by jermza on 2010-12-26
Hi there.

I am not a techie, so I'll try my best to explain, and hope that you help me on my noob level. 

I have two hard drives.  A small one and a big one.  Ubuntu is installed the small one, with the goal being to use the big one for all my storage and work files.  In the event that something goes wrong with Ubuntu, the drive can be formatted and re-installed without affecting my files on the big hard drive.  In other words, the small hard drive is intended purely for the operating system, while the big hard drive is intended for everything else.

However, it seems that everything is on the small hard drive - Documents, Downloads, Music, etc.  Which is obviously not what I wanted.  I have to physically move everything from the folders across onto to the big hard drive.

How do I get those shortcuts to point to the big hard drive instead of the small hard drive?  Is it even possible?

---

### Post by spiky001 on 2010-12-26
Hi yes this is a good idea have a read here it explains what you need to do [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by diablo75 on 2010-12-26
This is what you want:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I re-wrote this particular article recently so... I've got a little experience with doing this.  I'll be up all morning.

---

### Post by vanadium on 2010-12-26
It may be much easier and safer for you to keep both your system files and your /home on the system partition, and move only your data to the large partition. Then, you can replace the folders by symlinks to the new location.

For example:

* Move your Documents folder to the large partition
* Create a symlink "Documents" where the original Documents folder was as following:
- open two file browser windows.
- In the second window, navigate to your large partition such that you see your moved "Documents" folder.
- Press Ctrl+Shift and drag "Documents" to your first window. Release the mouse button: a link "Link to Documents" is created. Rename it to "Documents".

Do this for any data you want to reside on the big partition.

---

### Post by cgroza on 2010-12-26
Don't bother moving the /home, just put symlinks that point to the folders you want to store your data.

---

### Post by jermza on 2010-12-29
Thank you very much.

I have successfully followed your advice.

---

### Post by audiomick on 2010-12-29
You might like to mark the thread as solved. That is possible in the "thread tools" drop down.

---

