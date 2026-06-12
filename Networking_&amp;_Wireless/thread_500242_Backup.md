---
title: "Backup"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by AlanR8 on 2007-07-13
Evening all

Hope this is the right place for this post.

Just bought a 500 gig Freecom network drive. Nice piece of kit and you DON'T need to install any special software to get it to work in Linux or Doze. I just needed the instructions for the IP address but I went to my router to see the attached devices.

So up and running and in Kubuntu I can create new folders and delete them, add files to the folders, delete them and open them from the network drive. No problems.

I bought the drive as a backup device. Using the installed backup software in KUBUNTU, Keep, I go through the "wizard" but when it gets to the "Where to back up to" question, it sees the samba share but says I don't have permission to create a folder! WTF!!!

I've added backup, root and sudo to my profile and still the same result. 

Any ideas would be much appreciated.

---

### Post by sdowney717 on 2007-07-13
how about creating a 'root' login and seeing if that works.

you can log in as 'root' instead of your user name, and root has no restrictions.

---

### Post by AlanR8 on 2007-07-15
Have tried running Kate, the KDE backup program as sudo and still I get a permissions error. This is beginning to annoy me. Any other suggestions?

The remote network drive is formatted as FAT32 if that helps any.

---

