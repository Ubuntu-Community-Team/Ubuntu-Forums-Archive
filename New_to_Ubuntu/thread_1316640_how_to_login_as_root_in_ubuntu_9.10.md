---
title: "how to login as root in ubuntu 9.10"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by dharanitharan on 2009-11-06
hi friends,
              today i ve installed ubuntu 9.10 :popcorn:. in that i cannot login as root :confused:. there is no options available in login screen :D:p.
is there any other way available...



thanks :p

---

### Post by alien8predator on 2009-11-06
go to accesories---.terminal:

type:

sudo "command (ie: sudo apt-get update)

followed by your password. 

Then you are logged in for root for so many minutes and you can update your system and install software through the terminal. if you wait a long time you will have to type in your password again to become root again.

---

### Post by SunnyRabbiera on 2009-11-06
Actually its a very BAD idea to log in as root, I know on windows its easy because all users are given access to all the system but there lies why its insecure.
Are you running a server?

---

### Post by dvlchd3 on 2009-11-06
Debian based systems utilize sudo instead of su.  If you need to execute something as the superuser (root) simply add a sudo to the front of the command, and type __your__ password in when prompted.

I.E. 
```

sudo /etc/init.d/apache2 restart

```

If you need to have a "root" prompt (note this is not a real root prompt, however, it is essentially the same thing) you can use the command:

```

sudo -i

```

---

### Post by dharanitharan on 2009-11-06
i just wanted to save the wvdial file... for that it shows u don ve any permission.. for this i wanted login as root

---

### Post by dharanitharan on 2009-11-06
what i want is to login as the root from d login screen itself

---

### Post by SunnyRabbiera on 2009-11-06
> **dharanitharan said:**
> i just wanted to save the wvdial file... for that it shows u don ve any permission.. for this i wanted login as root

Yeh you need to use sudo, again this is how Ubuntu works.
Using root accounts is a very bad idea, trust me.

> **dharanitharan said:**
> what i want is to login as the root from d login screen itself

Again root is not there by default in ubuntu, for a reason.

---

### Post by dharanitharan on 2009-11-06
okay sunny ... i agree.. but how to save that file

---

### Post by cosine352 on 2009-11-06
so you can do
> sudo cp "file to copy" "destination"

---

### Post by alien8predator on 2009-11-06
> 

If you need to have a "root" prompt (note this is not a real root prompt, however, it is essentially the same thing) you can use the command:

```

sudo -i

```

I learned something new again. thx for that :)

---

### Post by SunnyRabbiera on 2009-11-06
The best way to get into the root of ubuntu is to install gksudo nautilus, that way you bypass the terminal.

---

### Post by 3rdalbum on 2009-11-06
> **dharanitharan said:**
> i just wanted to save the wvdial file... for that it shows u don ve any permission.. for this i wanted login as root

No, you don't need to log in as root in order to edit this file. That's a little bit like using a grenade to kill bees.

Install the "nautilus-gksu" package from Synaptic Package Manager. The next time you log in, you will be able to right-click the "wvdial" file and choose "Open as Administrator" from the menu. Now you can modify and save the file as you want, because the text editor is running as root.

If you need to move, rename, copy or delete files you can right-click a folder and "Open as Administrator", which opens up a file browser with root privileges.

---

### Post by SunnyRabbiera on 2009-11-06
> **3rdalbum said:**
> No, you don't need to log in as root in order to edit this file. That's a little bit like using a grenade to kill bees.

Install the "nautilus-gksu" package from Synaptic Package Manager. The next time you log in, you will be able to right-click the "wvdial" file and choose "Open as Administrator" from the menu. Now you can modify and save the file as you want, because the text editor is running as root.

If you need to move, rename, copy or delete files you can right-click a folder and "Open as Administrator", which opens up a file browser with root privileges.

Yeh its a good tool, I always install it on a fresh buntu install.

---

### Post by aysiu on 2009-11-06
> **dharanitharan said:**
> what i want is to login as the root from d login screen itself
We don't support that here.

More details (including how you can edit whatever system file you need to edit):
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

