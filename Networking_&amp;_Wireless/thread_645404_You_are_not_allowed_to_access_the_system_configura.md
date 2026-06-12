---
title: "You are not allowed to access the system configuration :("
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by vpvega on 2007-12-20
It seems like I have no privileges to access System>admin>network. Also I get the same error for:
Users and Groups
Time and Date
Shared Folders
Services

I'm having trouble getting my video drivers (ATI X800) installed because the screen goes blank upon booting. 
The only way I can get ubuntu to boot is in Recovery Mode, by typing startx. 
Now once up and running I cannot access the Internet and I cannot enter the network settings. 
Is this because I booted in recovery mode?

I'm sorry if this thread is in the wrong forum, but since I want to get the internet up and running this section seemed the more relevant. Thanks for any help.

---

### Post by erfahren on 2007-12-20
what kind of error are you getting? Is it just requesting your password?

---

### Post by erfahren on 2007-12-20
oh, I see what you're saying. 

while you're in recovery mode (before you start X) try doing (switch user):
```

su *your-user-name*

```

The problem is that, by default, Ubuntu doesn't set up the root user with any privileges 

to change that once you are logged in under your username go to: Sys > Admin > Login Window > Security tab and check "Allow local system administrator login"

and under Users and Groups go to the properties of the root user and set the user privileges

---

### Post by vpvega on 2007-12-20
I tried it, let's say my username is apple
But while installing ubuntu I put in apple as the username when I was prompted to do so.
what else can be done?

> 
root@ubuntu:~# su apple
apple@ubuntu:/root$ startx
xauth: creating new authority file /home/apple/.serverauth.4970
xauth: creating new authority file /home/apple/.Xauthority
xauth: creating new authority file /home/apple/.Xauthority

X: user not authorized to run the X server, aborting . giving up
xinit: connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): server error.



---

### Post by andrewoftheelves on 2007-12-20
sudo chmod gou+rwx /(nameoffile)

gou is group, owner, user  
rwx is read write exicute

just choose who you want to give the permissions too, and which permissions to give, ex.
sudo chmod g+rw /home/albino/forestnymph

hope this helps

---

