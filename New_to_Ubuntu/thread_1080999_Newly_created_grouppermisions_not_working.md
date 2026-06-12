---
title: "Newly created group/permisions not working"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by sayeo87 on 2009-02-26
On a Fedora server, I have a directory "dir_a" that I want to give users in the group "grp_a" access to. But the path to dir_a is /root/dir_a. First of all I'd like to ask is this even possible? Giving non-root user permissions to a directory that is inside /root?

So in /etc/groups I created a new group by adding the line
"grp_a:x:511:myUsername,user1,user2...."

Then as root I did
"chown -R :grp_a dir_a"
followed by
"chmod g+rwx dir_a"

Doing an ls -l showed the expected output:
"drwxrwxr-x  9 root grp_a"

But alas, when I tried to cd into the directory as a normal user by doing "cd /root/grp_a" I get a permission denied.

Can anybody spot what I'm doing wrong?

---

### Post by tarps87 on 2009-02-26
It does not work because the directory is in the root directory which only root can read/access
Or at least this is the case on Slackware

---

### Post by PukingPenguin on 2009-02-26
Unless I'm misreading this:
```
"drwxrwxr-x 9 root grp_a"
```
It indicates the OWNER of the directory is root, and the GROUP is grp_a.
Why? Just change ownership to a non-root user...root can always access everything anyway.

---

### Post by tarps87 on 2009-02-26
> **PukingPenguin said:**
> Unless I'm misreading this:
```
"drwxrwxr-x 9 root grp_a"
```
It indicates the OWNER of the directory is root, and the GROUP is grp_a.
Why? Just change ownership to a non-root user...root can always access everything anyway.

This still wouldn't work as the root directory is only accessible by root and I would suggest not changing the permissions of system directories. Also this would allow access to that 'non-root' user and not other users in that group.

Why is it that you want to create the directory in /root?

---

### Post by raptor2552 on 2009-02-26
Did you logout and back in again? This will pick up your user id in the new group

---

