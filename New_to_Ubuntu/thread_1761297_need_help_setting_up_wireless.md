---
title: "need help setting up wireless"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Jeffrey Kang on 2011-05-18
I'm not sure what information I should include here - I'm a complete beginner.

Dell latitude d610
running ubuntu 10.04.2
currently using windows xp desktop
I have a netgear wireless n150 wnr1000 v2 router

How do I set up wireless for the laptop?

---

### Post by josephmills on 2011-05-18
please press ctrl+alt+t then could we please see a ```
lspci -vnn | grep 14e4 
``` paste it here thanks and welcome to ubuntu

---

### Post by Jeffrey Kang on 2011-05-18
I don't have internet on the laptop running ubuntu.
I'm running windows xp on this one which I'm using to speak on the forums.
How do you expect me to copy and paste it into here?

---

### Post by josephmills on 2011-05-18
I dont expect you to do anything look at this it might help post number 44 you need the b43-fwcutter and the firmware-b43-installer or just look at how to install with out the internet [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by Jeffrey Kang on 2011-05-18
14e4:4324
b43-fwcutter with the firmware-b43legacy-installer

I'm pretty sure this is what I need.

---

### Post by josephmills on 2011-05-18
do what you think you should there ):P

---

### Post by Jeffrey Kang on 2011-05-18
Wow, thanks Joseph!
It worked!

May I ask permission to link to your tutorial from my website?

---

