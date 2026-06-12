---
title: "[SOLVED] Folder Locked?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by efexD on 2009-01-01
Hello, I created a folder using mkdir and when it shows in my home directory it has a lock, and i can't figure out why. I've tried doing chmod -R 755 directoryname on it and still nothing. It still shows a lock. Any help?

---

### Post by sofasurfer on 2009-01-01
In terminal type, sudo nautilus. Now you are the using the file browser as the super user. Now, browse to that directory and right click on it. Now click on 'permissions' and make yourself the owner. 

It was locked because it was created with the sudo command and since it is in your /home directory you were trying to access it as a ordinary user. A locked directory needs super user to open it. Usually a directory in your /home folder should have permissions set so you are the owner.

Confusing, but you'll get it in time.

---

### Post by efexD on 2009-01-01
Thanks! That did it. :popcorn:

---

