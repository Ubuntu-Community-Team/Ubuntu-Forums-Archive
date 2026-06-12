---
title: "File Structure"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by mike628 on 2010-07-10
Hello,
I have a NAS box that allows only an admin to log in through Putty. When I log in I am at ~ (root?). Is there a difference between root and admin (superuser)?
What is the best resource, online or book ,that explains the file system AND permissions?
 
Thanks

---

### Post by KdotJ on 2010-07-10
Hey,

Firstly, the ~ symbol means you are at your home directory. 
Secondly, its not a good idea to log in as root, in fact if its Ubuntu you're logging into, it won't be as root (unless you enabled the root account)

Root is basically admin (super user), but you normally log in as a normal user. Then when you need to perform "admin" tasks, you put the "sudo" prefix in front of the command which will then prompt you for your password to continue. It is safer this way...

As for the filesystem, [THIS]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") page is helpful to get an explanation

---

### Post by mike628 on 2010-07-10
This my problem. Iv'e stated it before. I log in as admin....My  Prompt:
login as: admin
[EMAIL="admin@192.168.1.8's"]admin@192.168.1.8's[/EMAIL] password:
[~] #
My .bash_profile and .bashrc BOTH have  a PATH with a particular path.
When I look at the files with vi it shows the path
but when I echo $PATH it doesnt show up.
Why not?

---

