---
title: "a couple of noob ssh questions"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-06-15
ive just started dabbling in ssh as ive just got a netbook and need to transfer files between that and my desktop and i have a couple of questions

does the ssh server start on login, to make it safe i only want it to start when i tell it to,

is it connected to the internet or only over local network, im using the default settings although i changed the option so it doenst accept passwords and uses a key instead, i dont want to leave myself open to attack because i havent researched enough into it yet

any good guides would be cool too
thanks 
mark

---

### Post by seawolf167 on 2011-06-15
[Here is a guide]("https://help.ubuntu.com/community/SSH").

It will start on startup and you can access it through WAN if you have the proper port forwarded from your gateway to your computer (22; which you can change if you want too).

---

### Post by CaptainMark on 2011-06-15
if i dont want it to run on start up should i just remove ssh keyagent from startup apps?

---

### Post by seawolf167 on 2011-06-15
> **CaptainMark said:**
> if i dont want it to run on start up should i just remove ssh keyagent from startup apps?

To stop it from starting on boot, do the following

```
gksu gedit /etc/init/ssh.conf
```

comment out the line that starts with "Start on" (i.e. with a '#' symbol), save and close the file.

now every time you want to start the ssh service you need to type

```
sudo service ssh start
```

---

### Post by CaptainMark on 2011-06-15
great thanks, im almost set, one more question though, i thought i used the exact same process to set up my pc as a server and my netbook so i can ssh back and forth at will but when i go from my pc(local) to my netbook(remote) i dont need to type the passphrase i made for the public key, however when i go from my netbook(local) to pc(remote) then i have to type the passphrase each time, where is this setting and how do i alter it?

---

### Post by seawolf167 on 2011-06-15
[This is a little old]("http://lani78.wordpress.com/2008/08/08/generate-a-ssh-key-and-disable-password-authentication-on-ubuntu-server/"), but should still work just fine - take a look at line 9.1

---

### Post by CaptainMark on 2011-06-15
i have the options listed no, no, yes respectivly but they are the same on both machines

---

