---
title: "Creating a New User - what happens?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by 2lid8xh2o8 on 2011-08-17
What is the shell equivalent to everything that happens when a user is made during installation?

I created a user during installation and couldn't log on, I made a typo in the username. I went into rescue mode but couldn't fix it, so i removed the user and just created a new one and added a password. After doing this and logging in, I found that I couldn't do a sudo command because the user I created wasn't in the list of sudoers. To add to the fire, I couldn't log on as root. I don't think I even knew what the root password was.

All sorts of questions came up during this, but what I'd really like to know most of all is what exactly happens in the background when ubuntu makes a user for you. If I ever had to do this in rescue mode, it would be helpful to leave no stone unturned int the process.

---

### Post by LowSky on 2011-08-20
The first Ubuntu user is kind of an odd ball. Basically its a normal user with sudo access.

Arch Linux has a great wiki, and part of that wiki is how to create a new user. I'm not sure of it working completely but maybe it will.

When you boot choose recover mode from grub, then pick the option for root console. Sorry drawing a blank on the real name.

then when you get a working console type

```
adduser
```

then it should bring up this type of prompt:
```
Login name for new user []: PICK A NAME

User ID ('UID') [ defaults to next available ]:LEAVE BLANK FOR DEFAULT

Initial group [ users ]: LEAVE BLANK FOR DEFAULT

```
Here you will need to enter groups like sudo but other important things too, here is the list you should need. NOTICE I DO NOT USE SPACES!!!!
```

Additional groups (comma separated) []: **audio,lp,optical,storage,video,wheel,games,power,scanner,sudo**
```

The rest should be blank, just use the defaults.
```

Home directory [ /home/username ]: LEAVE BLANK FOR DEFAULT

Shell [ /bin/bash ]: LEAVE BLANK FOR DEFAULT

Expiry date (YYYY-MM-DD) []: LEAVE BLANK FOR DEFAULT
```


see this for more info
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#Adding_a_User](https://wiki.archlinux.org/index.php/Beginners%27_Guide#Adding_a_User)

---

### Post by Wim Sturkenboom on 2011-08-20
> **2lid8xh2o8 said:**
> ... After doing this and logging in, I found that I couldn't do a sudo command because the user I created wasn't in the list of sudoers.

There are options in the GUI tool to make the user an 'administrator'.
> **2lid8xh2o8 said:**
> 
To add to the fire, I couldn't log on as root. I don't think I even knew what the root password was.
...
...
If I ever had to do this in rescue mode, it would be helpful to leave no stone unturned int the process.
Ubuntu sets up a root account with an invalid password hash, so you never can login like that (i.e. *_su -_* does not work). In recovery mode however, you're not prompted for a password so your OK there.

---

### Post by 2lid8xh2o8 on 2011-08-23
LowSky, thank you for the detailed information. This is the first time I've seen commands like that and they will certainly help. Adding the user to groups was something I overlooked, and I'm wondering is not adding the user to the sudo group had something to do with my problems.

Sturkenboom, I never knew you couldn't login as root from within a ubuntu session. Thats interesting and helpful news to me. Also, I'm aware there is a graphical way to do this. The ubuntu installation I'm running doesn't have a graphical interface, its a server. Thanks anyways.

---

### Post by Wim Sturkenboom on 2011-08-23
> **2lid8xh2o8 said:**
> Sturkenboom, I never knew you couldn't login as root from within a ubuntu session. Thats interesting and helpful news to me. Also, I'm aware there is a graphical way to do this. The ubuntu installation I'm running doesn't have a graphical interface, its a server. Thanks anyways.Sorry. Assumption is the mother of all evil :P

---

### Post by carrarin on 2011-08-23
Everytime you create a new user, his /home/user/ dir will be populated with the stuff from /etc/skel . if theres somehting that you want all your users to have. Stick it in /etc/skel

---

