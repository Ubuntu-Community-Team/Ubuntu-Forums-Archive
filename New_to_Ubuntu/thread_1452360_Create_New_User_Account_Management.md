---
title: "Create New User Account Management"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by held7over on 2010-04-11
Ubuntu 9.10 Gnome first time install on a Compaq Presario 2100

I have installed Ubuntu on a friend's computer. They need a second user. I used the gui for Account Management to create a new user named "nuri", but it had some error when I told it to create the new user. 

There is no sign of a new user either at /home or when I re-run Account Management, but when I attempted again to create "nuri" it says it already exists.

I then tried the commandline, even though I do not quite understand how to set up capabilities that way. (I don't want to give administration capabilities.) Here is what happened:

adam@pebbles:~$ sudo userdel -r nuri
userdel: user 'nuri' does not exist
adam@pebbles:~$ sudo useradd nuri
useradd: group nuri exists - if you want to add this user to that group use -g.
adam@pebbles:~$ 

What should I be saying here to create user 'nuri' and have it make the /home/nuri stuff with no admin ability, but able to use the internet, printers, etc.?

Thanks :)

---

### Post by Didius Falco on 2010-04-11
It looks like you have the group, but not the user. To add that user to the group, open a terminal and type

```
sudo addgroup nuri nuri
```

You can then use the gui to set up privileges the way you want them.

Regards,

Didius

---

### Post by held7over on 2010-04-11
Thanks Didius Falco.  Here is the strange thing that happened--

adam@pebbles:~$ sudo addgroup nuri nuri
[sudo] password for adam:
addgroup: The user 'nuri' does not exist.
adam@pebbles:~$

---

