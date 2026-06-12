---
title: "School Network"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by gforster on 2008-05-31
Hello, I am trying to research how to set up a network for a school computer lab. I am thinking about ltsp, possibly through edubuntu. 

What I am wondering is - is there a way to have an account for each student so that they can login to any computer and have all of their content, but only their content, accesible from that computer?

I am thinking this would be useful in a computer lab where they can freely choose any computer, but they need access to their work stored on the server. But, you don't want a student to access anyone elses work.  Any thoughts or suggestions?

---

### Post by bluefrog on 2008-05-31
how many concurrent connections?

edubuntu (or ltsp) is indeed what you are looking for.

count 128 MB RAM per client for the server + 512 MB for the server itself.

Or you could set up a "normal" server with fat clients with LDAP for authentication but keep /home on the server and export them.

---

### Post by gforster on 2008-05-31
There are about 20 computers in the lab currently. Right now they are running on microsoft server 2003. They do not currently have logins (there are only allowed to be in there when a teacher is in there), but for safety and security, I think separate accounts would be ideal. Would I just have one /home partition on the server? How would each account be separated?  Forgive my possibly ignorant questions, but I only use ubuntu on my laptop and desktop at home.  I have little to no networking experience.

---

### Post by bluefrog on 2008-05-31
if you are using a linux terminal server the homes could all under/home.
Each homes accessible only by the respective user (same as in windows server).

best thing for you to set up a pricate lab using virtualbox for example and install edubuntu to play with and see what it does.

---

