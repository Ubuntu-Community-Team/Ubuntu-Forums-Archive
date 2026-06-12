---
title: "nvidia driver (96) not allowing display on restart"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by beshortys1 on 2009-10-12
Recently put xubuntu 9.04 on outdated pc. Downloaded proprietary driver (Nvidia 96), then told to restart to enact changes.  After restarting the screen is blank (light blue) and my mouse pointer is visible...read somewhere you have to allow proprietary drivers somewhere.  

Can someone tell me how to do this through the terminal? Or is it easier to simply reinstall, and do it before restarting?

I'm a noobie to linux and command-line alike...I can change directories that's about it.

-b.

---

### Post by powel212 on 2009-10-12
run
```
sudo /usr/bin/nvidia-settings
```

Then configure the settings - hit save settings to X configuration file to lock them in.

then restart.

Now the settings will stick.

I hope that helps

Powel

---

### Post by beshortys1 on 2009-10-12
Gives me 

```

sudo:  /usr/bin/nvidia-settings: command not found

```

When I just try to go to that location, it gives me

```

-bash: cd: /nvidia-settings: No such file or directory

```

Does this mean the driver is not there, or someplace else?

-b.

---

### Post by ConXtionS on 2009-10-12
I had ALOT of problems with my old nvida fx2 card.... I thought the problems were with the drivers, but it turned out that LINUX did not see my monitor correctly...

So.... long story short.... when you use the plain linux driver do you have LOTS of Resolutions or just a few like up to 800X600....  If you have just a few then you need to get a different monitor (thats what I did) or we have to find a way to get linux to know what your monitor will do...

Hope that helps ya bro

Jim

---

### Post by beshortys1 on 2009-10-13
With the initial linux driver, I only have a few options 800 x 600 being the highest. When it was running xp I know it could handle like 1024 x 640 or 768, I think.

-b

Thank to everyone who's helping me by the way.

---

