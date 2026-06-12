---
title: "first login on forum"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by fransubu on 2008-08-27
Hi everybody, I just got logged in ! ):P
So, how does this forum work ? I just send a message, and somebody replies ? Well, if it is that easy, I might be able to do that !

So, here's my first issue. I am learning/testing on Ubuntu now for 4 weeks, until the late hours every day ...

I have managed to install Ubuntu server, add the dektop, configure samba for a Windows domain, and connect a XP system on it.

As I plan to have a few users on the server, I would like to create scripts to configure the server (users, machines, shares), this for quick restore or migration to a new server.

So, I would like to setup everything (users, groups, shares) using command lines, to be put in scripts.

This is how far I've got :
- List groups a user is belonging to : OK (groups command)
- List members of a group : OK (members command, I had to install it)
- List shares : OK (net usershare info)
- List all users : OK (cat /etc/passwd |greb "/home" |cut -d: -f1)
- Group create : OK (groupadd)
- Group delete : OK (groupdel)
- user create : OK (useradd, smbpasswd)
- user delete : OK (userdel, smapasswd -x)
- add a user to a group : OK (usermod)
- delete a user from a group : OK (usermod)
- share create : almost OK (net usershare add, but read-only from XP)
- share delete : OK (net usershare delete)

I was however unable to find out :
- list all groups : ?
- add a group to a group : ?
- delete a group from a group : ?
- Share create read/write ?

This is my share command :
net usershare add sh /home/sh "share on /home/sh" sh:f

When I list all the shares (net usershare info), I get : 

[sh]
path=/home/sh
comment=share on /home/sh
usershare_acl=Unix Group\sh:F
guest_ok=n

In the ubuntu desktop, the share option "allow other people to write" is not set.
How can I have it set by command line ?
I am going the right way with all this ?
Thanks for any reply !
(Is this post to long ?)
Frans

---

