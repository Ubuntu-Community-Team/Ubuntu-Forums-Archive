---
title: "x11vnc before X (And yes, I searched!)"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by king0lag on 2010-08-09
I have a machine that I do not have physical access to. It is currently running Ubuntu 10.04. I currently access it via SSH and have had no problems for some time. However, the recent need to access it via VNC has come up and I am unable to get it working. For reference, tightvnc works as expected but does not allow me the functionality I need. I need to get x11vnc working.

The first thing I did of course was google for a solution and the closest thing I could find seems to be out of date. If someone could help me with the following it would be greatly apprecaited.

From [https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login](https://help.ubuntu.com/community/VNC/Servers#x11vnc-before-login)

The first problem I encounter: I must edit the file [COLOR="DarkOrchid"]/etc/gdm/gdm.conf-custom[/COLOR] so it will not disconnect me after logging in. As far as I can tell this file does not exist. (Another site suggested [COLOR="DarkOrchid"]/etc/gdm/custom.conf[/COLOR] but I can't find any file that looks even remotely like this in the directory :()

My next problem occurs when I attempt to use the suggested [COLOR="DarkOrchid"]-auth /var/lib/gdm/:0.Xauth[/COLOR] switch. This is invalid. I also tried the suggested switches [COLOR="DarkOrchid"]-auth /var/gdm/:0.Xauth[/COLOR] and [COLOR="DarkOrchid"]-auth /var/lib/gdm/:0.Xauth[/COLOR] to no avail. I took x11vnc's suggestion and [COLOR="DarkOrchid"]ps wwwwaux | grep auth[/COLOR] but could not find anything promising.

All under sudo of course.

Please be gentle, I'm still relatively new to remote access on Ubuntu.

Edit: -auth guess does not work either.

---

### Post by krunge on 2010-08-09
Is the X server and/or gdm even running on that machine?

---

### Post by Peter09 on 2010-08-09
Normall VNC in all its flavours requires a valid desktop to work - if you want to be able to log in to a machine the try NXFree, this will allow you to establish a desktop from a headless server.

---

### Post by king0lag on 2010-08-09
> **krunge said:**
> Is the X server and/or gdm even running on that machine? Yes, but it is not logged in. It is at the login screen. The setup for the machine was a basic home install and an install of the ssh software.

> **Peter09 said:**
> Normall VNC in all its flavours requires a valid desktop to work - if you want to be able to log in to a machine the try NXFree, this will allow you to establish a desktop from a headless server.It has a valid desktop it's just not logged in. I am unsure of what NXFree is but I will look into it thanks :)


Edit: As a follow up if it's going to be a problem I might be willing to just have Ubuntu automatically log-in. I'm not sure how to change this through the console so either way I'd have to make at least one x11vnc session work to make the change :(

I was hoping I wouldn't have to resort to auto-logins because of the insecurity that follows.

---

### Post by krunge on 2010-08-09
> **king0lag said:**
> Yes, but it is not logged in. It is at the login screen. The setup for the machine was a basic home install and an install of the ssh software.

Please paste in the output of this command:
```
ps wwaux | egrep 'auth|gdm'
```

---

### Post by king0lag on 2010-08-09
```
ps wwaux | egrep 'auth|gdm'
```

```
username       1119  0.0  0.0   3312   792 pts/0    S+   11:34   0:00 egrep --color=auto auth|gdm
```

Nothing.

I did a quick reboot and it gave me this for a bit, not sure if it helps.

```
root       995  0.0  0.1   4440  1500 ?        Ss   11:41   0:00 /bin/bash /etc/gdm/failsafeXServer
root      1010  0.0  0.0   3056   568 ?        S    11:41   0:00 xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log
username       1101  0.0  0.0   3312   796 pts/0    S+   11:41   0:00 egrep --color=auto auth|gdm
```

Honestly I was getting more before when I ran the suggested (with [COLOR="DarkOrchid"]ps wwwwaux | grep auth[/COLOR]), perhaps installing/uninstalling tightvnc messed something up :(

---

### Post by bodhi.zazen on 2010-08-09
You have two options.

IMO your best option is ssh. You can forward X applications with 

ssh -X user@server

Be sure to look at how to secure ssh (use keys, disable passwords, etc).

Your second option is to use a different VNC server.

The default server, vino, connects to a running X session, which is why you are having problems.

vnc4server will start a new session.

Be warned, VNC is not secure and is one of the most common cracks on these forums.

Perhaps your best option is to use a web based interface such as webmin.

---

### Post by king0lag on 2010-08-09
> **bodhi.zazen said:**
> You have two options.....

I think I might clarify that the machine only has an open SSH port to the world. Everything else is tunneled. (IE my VNC connection goes to localhost:5900) That being said I am not connecting to this machine from another Ubuntu machine. I need to access it from various Mac and Windows boxes as I travel.

The reason I am trying to use the x11vnc service is because the tightvnc client makes some kind of dummy desktop that locks me out of a lot of Ubuntu functionality. For the same reason a web administrator would not be to my use, as anything I could do there would be easier to do via SSH anyway.

I'll look into different VNC servers though, I am rather disappointed as I didn't think logging in through a VNC via the GUI would cause me such problems. I've only recently used VNC on Mac and PC and it has been the norm :( I'd always assumed that the GUI was part of the X session but I forget how different things are in the lands of *nix!

Well off for lunch hopefully someone might have an updated version of the page I linked above so I can get x11vnc (vino as you say) working or I'll keep an eye out for a service that allows me the access I need. Thank you again for your help!

---

### Post by bodhi.zazen on 2010-08-09
VNC is as easy to use on Linux as any other OS, the behavior is dependent on the VNC server and there are more options on Linux.

I am not a big fan of VNC , and less a fan of the default.

You can ssh -X on Windows (look at xming which is portable) and OSX. I find ssh is sufficient for most of what I need from a remote connection , and if not, just forward a single application or gnome-panel (do you really need the entire desktop ?).

Another option is FreeNX, better performance and security.

---

### Post by king0lag on 2010-08-09
I'm not much a fan of VNC either but when the need arises :(

Thank you I will look into these options! X seems to do a lot more than I've anticipated!

Edit: Marking as solved since it seems there are easier ways to do what I am trying.

---

