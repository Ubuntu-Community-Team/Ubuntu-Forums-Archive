---
title: "Permission denied to move file in Terminal"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-14
I tried to move a file using:

mv filename.flv /home/.system (hidden folder i created through terminal) but got a "permission denied" error

It let me do it (cut & paste) through Nautilis immediately afterwards.

Any ideas why?

---

### Post by vipulkelkar on 2009-10-14
It should not give any problem..I tried it..it allowed me to do it..
Try it with 'sudo'

---

### Post by macabrem on 2009-10-14
> **smileyguy said:**
> I tried to move a file using:

mv filename.flv /home/.system (hidden folder i created through terminal) but got a "permission denied" error

It let me do it (cut & paste) through Nautilis immediately afterwards.

Any ideas why?


I don't move files with the terminal very much, but do you need another slash "/.system/"?

---

### Post by smileyguy on 2009-10-14
Sorry guys - wrong syntax or file path.

I was allowed to create in /home/ but forgot to ad my user name when moving. 

This meant I had a file needing deleting in /home/ when it should have been /home/username

I assume I have write only permissions on /home

Deleted it using sudo thanks vipelkulkar

---

