---
title: "nx"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by steve2112 on 2010-09-16
can someone please tell me how to create a new user account  in nx ?, there were 2 of us running a dediacted server  but my m8 has left due to work commitments, now another friend has stepped in but i cant remember how to create a name & password so he can log in to nx, thanks for any help

---

### Post by endotherm on 2010-09-17
IIRC, you just create a new unix user. you can add one via System -> Administration -> Users and Groups.

---

### Post by steve2112 on 2010-09-17
i have no user & groups option !!

[IMG]http://i269.photobucket.com/albums/jj61/johnna2112/Capture2-5.jpg[/IMG]

and thanks for the speedy reply !!!!

---

### Post by Clever_Username on 2010-09-17
Have you tried 'adduser' from a command prompt? 
And by the way, a little description in your thread title will go along way towards getting the gurus that watch this site to help you. Just sayin'

---

### Post by steve2112 on 2010-09-17
when i try the cmd prompt i get [IMG]http://i269.photobucket.com/albums/jj61/johnna2112/Capture-11.jpg[/IMG], i need him to have full acess to this but im stuck :confused:

---

### Post by 101011010010 on 2010-09-17
Hello.
Have you tried adding Users and Groups to your Applications menu?
Right click over the "Applications Places System" menu and select> Edit Menus. Scroll down and select Administration and you should be able to add anything you need.
I hope this helps.

---

### Post by steve2112 on 2010-09-17
yes i had done that but dont have the options  [IMG]http://i269.photobucket.com/albums/jj61/johnna2112/Capture2-6.jpg[/IMG] is all i got , nothing else, no usergroups new user etc !

---

### Post by endotherm on 2010-09-17
you aren't using a live cd, are you? 
if not, hit Alt + F2, and enter 
```
gksu users-admin
```
does that launch the users and groups utility?

if not, then the good ol'e cli will save the day:
```
sudo adduser <newUserName>
```

---

### Post by steve2112 on 2010-09-17
thanks m8, he has a account now =D> thanks a lot for all your speedy replies & great info, were both new to ubuntu so stand by for more crazy questions :lolflag: once again thanks a lot !

---

