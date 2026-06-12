---
title: "removing directory on desktop"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by xXNI4NI on 2009-03-10
i downloaded a failed version of java and compiled it onto my desktop by mistake 
all-in-all i got the correct version and everything's fine except for this annoyance reminding me to mv my files before i compile them.
i tried sudo nautilus -> desktop and it wasn't there
opened terminal
sudo rmdir jre...
it is not empty
tried again
cd ~/Desktop
su
rmdir "jre..."
file not found
tried to change the permissions but it is set to root so that is scratched and it appears i am about out of options and have made myself quite the annoyance
thanks in advance

don't know if chmod would help at all but don't see as how read/writing/or exec. would come into play but anyways feel free to help :(

---

### Post by joenieburg on 2009-03-10
rm -R jre....


in a lot of case in ubuntu u need to put a capital -R behind.
Like change file permission and all directory inside do like
chmod -R 777 Desktop
this cause alle files in your Desktop to be accessed by everyone (u don want this)

---

### Post by xXNI4NI on 2009-03-10
AHA! that worked! to think i was two characters shy of salvation hah. what did -R do? I'd like to learn from this. :KS

---

### Post by joenieburg on 2009-03-10
I think it means go to all directory and files in a folder.
It works with changing file permissions  (chmod -R 777 *)
and it also works with changing file owner (chown -R root:users *)

---

### Post by WhiskyChris on 2009-03-10
I believe the -R stands for recursive, meaning do the action for this folder and all files/folders inside.

---

