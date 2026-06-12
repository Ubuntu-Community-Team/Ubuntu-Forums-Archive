---
title: "how do i see where files are installed"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by RememberWhenItRained on 2011-04-15
can i search or see where files are installed in the terminal?
I'm trying to get to my conky.conf file but i don't know where it is. I already tried the find files feature.

---

### Post by bug67 on 2011-04-15
Don't have my Linux in front of me now but, A lot of the program configuration and preference files are hidden in your user folder.  If you open up your home folder and select "show hidden files,"  a bunch of folders previously unseen will show up.  They will be proceeded by a "."

I don't have conky installed but look for a folder named ".conky"

Worth a shot anyhow.  I'm sure someone that knows for certain will pop in sooner or later.

---

### Post by RememberWhenItRained on 2011-04-15
don't see it yet. not in home?

---

### Post by Paqman on 2011-04-15
> **RememberWhenItRained said:**
> don't see it yet. not in home?

User-specific config files will always be in your home folder. Conky's config file is at /home/username/.conkyrc IIRC. Haven't used it for years myself though...

---

### Post by dcsoldschool53 on 2011-04-15
> **RememberWhenItRained said:**
> can i search or see where files are installed in the terminal?
I'm trying to get to my conky.conf file but i don't know where it is. I already tried the find files feature.

When you get a chance, look in /var/cache/apt/archives folder.

---

### Post by RememberWhenItRained on 2011-04-15
> **dcsoldschool53 said:**
> When you get a chance, look in /var/cache/apt/archives folder.
good call. (why was it there? accidental deletion?)

---

### Post by David_UK on 2011-04-15
> **RememberWhenItRained said:**
> can i search or see where files are installed in the terminal?
Yes.  Try the [find]("https://help.ubuntu.com/community/find") command.

Sorry, just re-read your first post.  You might already have tried that.

---

### Post by akakingess on 2011-04-15
you can also use the ```
whereis <application>
``` command to find apps that you can't locate, also when looking through nautilus for hidden files, you should be able to hit CTRL + H and that should show you all of the 'hidden' files within that current directory.  Hope that helps in the future.

---

### Post by Fraoch on 2011-04-15
From the command line, use:

```
ls -a
```

to show hidden files.  What you're probably looking for is .conkyrc and it's in /home/[your user name]/.

---

### Post by RememberWhenItRained on 2011-04-15
if it is in  /var/cache/apt/archives should i move it to /home?

---

### Post by Hoopz on 2011-04-15
or use the locate command  ```
locate filename
```

---

### Post by Fraoch on 2011-04-15
> **RememberWhenItRained said:**
> if it is in  /var/cache/apt/archives should i move it to /home?

Actually I see where conky.conf is and no, it does not belong in /home.  It belongs in /etc/conky/conky.conf.

/home[your user name]/.conkyrc, which contains the settings and which is probably the one you want to edit if you want to change what's displayed, does not seem to be installed.  I believe it's created the first time you run conky as a user (allowing different users to have different conky settings).  So since you're using the terminal you may not have run X yet, therefore it hasn't been created yet.

You can take the pre-existing .conkyrc copied off the apt cache, edit that, and save that into /home/[your user name].  I'm pretty sure conky won't overwrite .conkyrc if it finds it.

---

### Post by RememberWhenItRained on 2011-04-15
> **Fraoch said:**
> Actually I see where conky.conf is and no, it does not belong in /home.  It belongs in /etc/conky/conky.conf.

/home[your user name]/.conkyrc, which contains the settings and which is probably the one you want to edit if you want to change what's displayed, does not seem to be installed.  I believe it's created the first time you run conky as a user (allowing different users to have different conky settings).  So since you're using the terminal you may not have run X yet, therefore it hasn't been created yet.

You can take the pre-existing .conkyrc copied off the apt cache, edit that, and save that into /home/[your user name].  I'm pretty sure conky won't overwrite .conkyrc if it finds it.

ugh, i don't see .conkyrc in /home/[username]/

---

### Post by oldos2er on 2011-04-15
Have you run conky yet? If not, that's why there's no .conkyrc.

---

### Post by Fraoch on 2011-04-15
> **RememberWhenItRained said:**
> ugh, i don't see .conkyrc in /home/[username]/

Please re-read my post.

---

### Post by ram0042 on 2011-04-15
To list all packages installed on the system, from a terminal prompt enter:
```
dpkg -l
```
It is the most accurate way of finding the packages

In alternative (In case of many package listings)
```
dpkg -l | less
```

---

