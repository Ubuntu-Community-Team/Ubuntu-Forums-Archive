---
title: "If that it's not possible:"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by justsomecomments on 2010-10-30
Hi. I recently tried 2 liveCDs: Ubuntu 10.10 and Linux Mint 9 Isadora, and I have some suggestions, only about Ubuntu ....

I had to leave the PC for a few minutes, and the screensaver was activated, I moved the mouse, and the system asked me for a username and a password. My 1st guess was enter, enter. My 2nd: ubuntu, enter, enter and it worked.

Suggestions:

1 A message every time the systems boots from the liveCD: your username is blabla you will need it if the screensaver is activated, and it is set for 5 minutes.
If that it's not possible:

2 Disable the screensaver
If that it's not possible:

3 Disable the need for user and password when the screensaver activates, on linux mint liveCD you don\t need it.
If that it's not possible:

4 At least put the information on the homepage, I tried to find it, on [http://www.ubuntu.com/](http://www.ubuntu.com/) , [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) , [http://ubuntuforums.org/](http://ubuntuforums.org/) , and  [http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329) .
Maybe it is there, but I could not find it
If that it's not possible:

5 At least reduce the time it needs to be functional after you typed the user and password, On my 2 GigaHertz PC with 640 Megas of RAM, It needs more than 3 minutes to put again the menus, the icons, etc.

Thanks to all the people that have read all my rant. I feel better now :)

And I would be glad if one or more of these suggestions help to make that the persons that try a liveCD, decide to stay on Ubuntu. And help fight the bug#1: [https://launchpad.net/ubuntu/+bug/1](https://launchpad.net/ubuntu/+bug/1)

Note: English is my 2nd language, so please if a moderator could correct all my mistakes, so this text is more easily readable, because the way it is now, maybe not everybody can understand what I am trying to say ...
Maybe also modify the two tags I put, or add more. Change this post to another forum, etc.

Goodbye.

---

### Post by CharlesA on 2010-10-30
The default username and password on the livecd is ubuntu - no password.

I could have sworn it was documented somewhere.

---

### Post by yabbadabbadont on 2010-10-30
> **CharlesA said:**
> I could have sworn it was documented somewhere.

It is now...  here.  ;)

---

### Post by CharlesA on 2010-10-30
> **yabbadabbadont said:**
> It is now...  here.  ;)

True.

If you don't know the password, you can set it per the LiveCD docs [here]("https://help.ubuntu.com/community/LiveCD").

Since sudo doesn't require the user password on the livecd, that's easy enough to do. :)

---

### Post by sisco311 on 2010-10-30
> **CharlesA said:**
> The default username and password on the livecd is ubuntu//ubuntu.

I could have sworn it was documented somewhere.

I'm pretty sure that in earlier releases the username was ubuntu and the password was blank (the hash in /etc/shadow was U6aMy0wojraho, see: [thread]513820[/thread]).

If memory serves, now sudo and policykit are configured to allow admin users to run application as root without a password, but I don't know what's the default user's (ubuntu) password.

Anyway the OP has a valid point, on the Live CD gnome-screensaver should not prompt you for a password.

---

### Post by uRock on 2010-10-30
I have the 10.04 LiveCD on a thumb drive. When logged out or the screensaver comes on, the user name is ubuntu and there is no password. Leave it blank and hit enter. I use my thumby at college and even though it is not really secure with these settings, most people will just walk away when they see it needs to be logged in. 

```
username= ubuntu
password= "no password"
```

---

### Post by CharlesA on 2010-10-30
Good catch sisco.

I just checked on a 10.04.1 livecd and I wasn't prompted to enter a password on suspend or when the screensaver was on.

I just checked the hash in /etc/shadow and the password is blank.

uRock beat me to it. :P

---

### Post by uRock on 2010-10-30
> **CharlesA said:**
> Good catch sisco.

I just checked on a 10.04.1 livecd and I wasn't prompted to enter a password on suspend or when the screensaver was on.

I just checked the hash in /etc/shadow and the password is blank.

uRock beat me to it. :P
Yup, the first time I went to walk away from my PC at school I hit the lock screen button and realized when I returned that I only needed to hit enter or the space bar to unlock, so now I log out. I haven't tried it yet but I think you can create an account on the persistent thumb drive image. Will post back later after trying.

---

### Post by CharlesA on 2010-10-30
If it's persistent, you could even just set a password for the ubuntu user and leave it at that. :)

---

### Post by uRock on 2010-10-30
> **CharlesA said:**
> If it's persistent, you could even just set a password for the ubuntu user and leave it at that. :)
The only downside is that if I should install to someone's system using the thumb drive, it also copies all of my settings and such to the installed system. If I can create my own account on it, then I can have my settings in it and just remove my /home from the new install.

---

### Post by CharlesA on 2010-10-31
> **uRock said:**
> The only downside is that if I should install to someone's system using the thumb drive, it also copies all of my settings and such to the installed system. If I can create my own account on it, then I can have my settings in it and just remove my /home from the new install.
Valid point. :)

---

### Post by sisco311 on 2010-10-31
> **uRock said:**
> ...it also copies all of my settings and such to the installed system.

Nope.

---

### Post by uRock on 2010-10-31
> **sisco311 said:**
> Nope.
It did on the last install I did with my 10.10 thumby.

---

### Post by sisco311 on 2010-10-31
> **uRock said:**
> It did on the last install I did with my 10.10 thumby.

Interesting...,  in that case, I would try to create a new user with an uid less than 1000...

---

### Post by CharlesA on 2010-10-31
> **sisco311 said:**
> Interesting...,  in that case, I would try to create a new user with an uid less than 1000...

What would that do?

---

