---
title: "[SOLVED] stuck in root eee pc"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-12-23
I have rebooted my system and now i'm stuck in root.

Can someone help me ?

---

### Post by Titan8990 on 2008-12-23
Stuck as root user? Root of your harddrive?


details please.

---

### Post by Dadsgé on 2008-12-23
> **Titan8990 said:**
> Stuck as root user? Root of your harddrive?


details please.


I don't get to my login screen and it looks like i'm in terminal...
black backgroung, asking me my username and pasword.

---

### Post by snowpine on 2008-12-23
Are you running Ubuntu, or the Xandros that comes stock with the eee?

Enter your username and password, then type 'startx'... does that do the trick?

---

### Post by Titan8990 on 2008-12-23
It sounds like you are selecting recovery mode instead of the regular Ubuntu.

---

### Post by zephyrcat on 2008-12-23
That sounds like X is not starting up correctly. What were you trying to do when this happened?

I would log in and type this:
```
startx
```
I don't know if that is the right approach, though.

EDIT: Ooops, you beat me.

---

### Post by Dadsgé on 2008-12-23
It doesn't work. I'm using ubuntu. It also gives me an error ```
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. wOuld you like to view the X server output to diagnose the problem ? 
```

if i click yes: ```
 warning could not generate /etc/X11/xorg.conf.failsafe for vesa driver 
```

---

### Post by zephyrcat on 2008-12-23
Now we get in to more complicated territory...

You need to correct your X configuration. You could manually edit your xorg.conf file, but I don't recommend it. I believe the correct command to reconfigure X is this:

```
dpkg-reconfigure xserver-xorg
```

EDIT: Posting the output of this command might also help:

```
cat /etc/X11/xorg.conf
```

That will display your X configuration.

---

### Post by Titan8990 on 2008-12-23
It should be noted that if he IS in recovery mode he will not be able to start the GUI run level due to security measures in Ubuntu.

---

### Post by Dadsgé on 2008-12-23
well i am not in recovery mode, and that 'cat /etc/X11/xorg.conf' doesn't show everything.
my screen is to little and i cannot scroll so i can't see everything...

---

### Post by Titan8990 on 2008-12-23
You should use:

cat /etc/X11/xorg.conf | less


This will allow to scroll through the output.

---

### Post by snowpine on 2008-12-23
Is this a fresh install, or was it working then it broke?

---

### Post by Dadsgé on 2008-12-23
another question: how come i get this error now?
i've installed and upgraded a lot of things and i rebooted a few times, never had this error before...
i've rebooted more than once after these upgrades or modifications (fixes for eeepc) so why does it keeps on hanging now?

---

### Post by Dadsgé on 2008-12-23
> **snowpine said:**
> Is this a fresh install, or was it working then it broke?

it worked and now it is broken...

---

### Post by Dadsgé on 2008-12-23
> **Titan8990 said:**
> You should use:

cat /etc/X11/xorg.conf | less


This will allow to scroll through the output.

OK that works :)

---

### Post by Dadsgé on 2008-12-23
wait, the output says i should type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Dadsgé on 2008-12-23
wouldn't it be easier to reinstall ubuntu?
i've backed up my homepartition before i did the fixes...
so i'll just need to install and delete some programs
but that isn't much work as i did not installed that much of additional programs :)

---

### Post by Titan8990 on 2008-12-23
Since a Ubuntu install only takes 30-45min, I say go for it.

---

### Post by Dadsgé on 2008-12-23
> **Titan8990 said:**
> Since a Ubuntu install only takes 30-45min, I say go for it.

ok, thanx everyone for thinking about it :)

---

