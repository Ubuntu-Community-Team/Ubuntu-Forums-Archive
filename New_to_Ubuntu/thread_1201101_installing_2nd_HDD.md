---
title: "installing 2nd HDD"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by angry ogre on 2009-06-30
so i have an 80gb with 9.04 as my main drive and i just bought a 500 gb and want to start putting media on it however when i try to open the new drive i get the "unable to mount" message, can someone give me a hand installing this drive? thankx

---

### Post by m9ke on 2009-06-30
Sounds like you may need to set a mount point.  I had the same problem when I added a drive.  

Went thru multiple posts till I got it working.  

You can read the steps at
[http://ubuntuforums.org/showthread.php?t=529296&highlight=m9ke](http://ubuntuforums.org/showthread.php?t=529296&highlight=m9ke)

---

### Post by angry ogre on 2009-06-30
thanks bro,i'll give it a shot

---

### Post by angry ogre on 2009-06-30
well the drive is formatted and installed however now i have a new issue, when i try and move some of my media to it i get a message that i don't have permission,how do i fix this, can someone please help me out on this?

---

### Post by m9ke on 2009-07-01
I had a problem a lot like this when I installed my second drive.  

In the link in my first post, check out the second part of comment #12 where taurus talks about:

"Then, I would change the ownership of /media/bigdrive from root to your login name, m9ke, so you can write to it without using sudo."

Of course your login name isn't m9ke, and your drive is not named bigdrive, but if you substitute your names for mine, you will be on the right track.

---

### Post by angry ogre on 2009-07-02
so i got it mounted and entered the commands to allow my user to write to the drive but when i try to transfer media i still get that damn "you don't have the necessary permissions blah blah blah,did i miss something? i open the properties and i can't change the permissions, i don't know what to do .

---

### Post by frunns on 2009-07-02
What's the output of ls -al /path/to/root/folder/of/device?

---

### Post by angry ogre on 2009-07-02
ls: cannot access /path/to/root/folder/of/device?: No such file or directory
brandon@brandon-desktop:

---

### Post by frunns on 2009-07-02
> **angry ogre said:**
> ls: cannot access /path/to/root/folder/of/device?: No such file or directory
brandon@brandon-desktop:

Read what the path said. :P Either cd to the folder it's mounted in or give the path to it.

---

### Post by angry ogre on 2009-07-02
i was trying to drag-n-drop some music,how do i write media to that file, when i open the drive there's a lost and found folder that's it and i can't create a music or movie folder,i'm coming from xp and this is my first linux box so i've no idea how to write to said file.

---

### Post by sdlynx on 2009-07-02
you can't drag and drop until you have the permissions to do so

---

### Post by angry ogre on 2009-07-02
just in case someone else has the same issue,after formatting,and mounting if permissions are req'd, i used "sudo nautilus" in the terminal and selected the new drive, then right click properties then the permissions tab,modify as needed then click the "apply permissions" button and voila i was done.

---

