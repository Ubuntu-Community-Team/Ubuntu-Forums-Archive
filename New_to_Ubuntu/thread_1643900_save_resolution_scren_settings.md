---
title: "save resolution scren settings"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by yae7 on 2010-12-12
Hi:

i have set resolution screen to 1024*768 85Mhz (via menu / preferences / monitor settings). And the resolution is applied correctly. 

The problem is that when I enter again in the desktop (because i quit, restart, etc) the resolution is 1280*960

Why does not it load the resolution that I have saved?

> 
OS: lubuntu 10.10
Video card: ATI Radeon 7000
Monitor: Philips wit max. resolution 1024*768 and 85 mhz freq.

Thanks in advance.

---

### Post by sandyd on 2010-12-12
> **yae7 said:**
> Hi:

i have set resolution screen to 1024*768 85Mhz (via menu / preferences / monitor settings). And the resolution is applied correctly. 

The problem is that when I enter again in the desktop (because i quit, restart, etc) the resolution is 1280*960

Why does not it load the resolution that I have saved?



Thanks in advance.
you will have to generate your own xorg.conf and add modelines.

check it out ->
1. Save all your work
2. Press Control + ALT + F1
3. login
4. ```

sudo killall gdm
sudo killall kdm
X -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf

```
5. ```

sudo gdm
```
6. login
7. post output of
```

cat /etc/X11/xorg.conf
```
and ill add in your modelines,.

---

### Post by tajiknomi on 2010-12-12
[SIZE=2]This thread is about Nvidia ,but you can check it fot ATI as well >[/SIZE] [http://ubuntuforums.org/showthread.php?t=768822](http://ubuntuforums.org/showthread.php?t=768822)

Also > [http://ubuntugeek.com/forum/index.php?topic=45.0](http://ubuntugeek.com/forum/index.php?topic=45.0)

---

### Post by yae7 on 2010-12-12
> **sandyd said:**
> you will have to generate your own xorg.conf and add modelines.

check it out ->
1. Save all your work
2. Press Control + ALT + F1
3. login
4. ```

sudo killall gdm
sudo killall kdm
X -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf

```
5. ```

sudo gdm
```
6. login
7. post output of
```

cat /etc/X11/xorg.conf
```
and ill add in your modelines,.

not runs any step.....

gdm: no process found
kdm: no process foun
no file or directory
etc etc

---

### Post by cavalier911 on 2010-12-12
**Lubuntu 10.04 LTS**

See these threads:

Configures resolution with xrandr in lxsession autostart for single user after login:
[http://ubuntuforums.org/showthread.php?t=1536228](http://ubuntuforums.org/showthread.php?t=1536228)

Configures resolution globally for all users prior to login when xserver starts with xorg.conf:
[http://ubuntuforums.org/showthread.php?t=1544285](http://ubuntuforums.org/showthread.php?t=1544285)

This is an alternative way to stop the xserver without a reboot to single user recovery mode from grub2 menu.

Lubuntu uses the upstart system and lxdm as it's display manager. To stop lxdm and kill xserver to drop to console issue this command in lxterminal.

```
sudo service lxdm stop
```

this bring you to login prompt, create and configure your xorg.conf

Restart xserver

```
sudo service lxdm start
```

---

### Post by yae7 on 2010-12-14
Yes. i have tried this: 
> **cavalier911 said:**
> **Lubuntu 10.04 LTS**
Configures resolution with xrandr in lxsession autostart for single user after login:
[http://ubuntuforums.org/showthread.php?t=1536228](http://ubuntuforums.org/showthread.php?t=1536228)

and now runs fine! :D

thanks

---

