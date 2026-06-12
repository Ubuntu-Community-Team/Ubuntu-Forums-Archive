---
title: "CCSM fail, how to uninstall it from a live cd?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-12-10
hi
sth happened whean i was seting up an effect in the CCSM and noe i can enter to my sesion, not even on safe mode nor terminal mode. so im quite ****** up.

i guess i can uninstall CCSM. im on a live cd now. 
so, how should i do this?

like this?

```
sudo apt-get uninstall compizconfig-settings-manager 
```

please, i need to get into my sesion again cuz firefox under cd live is too slow, i have my finals tomorrow 8am (sth like 10 more hours over here!) and i NEED to keep studying.

thanks.

---

### Post by JoshuaRL on 2008-12-10
What exactly where you doing and what happens now when you turn on the computer?

---

### Post by gettinoriginal on 2008-12-10
I am not quite clear at which point you cannot get on, but try this

Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Resume normal Boot > Enter

If that does not solve your problem, repeat the process but also use Try to fix X server.


Good Luck   :p

---

### Post by jsf_pp on 2008-12-10
> **gettinoriginal said:**
> I am not quite clear at which point you cannot get on, but try this

Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Resume normal Boot > Enter

If that does not solve your problem, repeat the process but also use Try to fix X server.


Good Luck   :p

ok im doin this right away.
i'll be (i hope) back soon.

---

### Post by jsf_pp on 2008-12-10
> **JoshuaRL said:**
> What exactly where you doing and what happens now when you turn on the computer?

i dont remember exactly what efect i was changin but i had some problems woth another one so i disabled the last one and then my screen was only lines and color all aroun.

(sorry about my explanation but my english sucks and im kind of complicated right now...besides my hypothalamus its not working properly and i cant remember all with exactitude)

---

### Post by jsf_pp on 2008-12-10
> **gettinoriginal said:**
> I am not quite clear at which point you cannot get on, but try this

Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Resume normal Boot > Enter

If that does not solve your problem, repeat the process but also use Try to fix X server.


Good Luck   :p

ok i did both and i didnt work.
what else can i do?

can i uninstall ccsm????
how to do it from a live CD???

thanks

PD: now, this is what i get after login in:

[IMG]http://i37.tinypic.com/2h54sqp.jpg[/IMG]

---

### Post by markbuntu on 2008-12-10
If the login screen works, you can change your session to gnome safe mode and you should be able to get a desktop. There is a little icon at the bottom of the login screen to do this with.

---

### Post by jsf_pp on 2008-12-10
> **markbuntu said:**
> If the login screen works, you can change your session to gnome safe mode and you should be able to get a desktop. There is a little icon at the bottom of the login screen to do this with.

yeah, you know, about that, i ve tried on the login screen: options> and then i have these huuuuuuuuge font so when i try to select the gnome safe mode one i only can read GNOME SAF... and even though i hit it the login screen comes back and then i get inside to be welcomed by a annoying purple screen of dead.

help please!

---

### Post by markbuntu on 2008-12-10
OK, try this. Boot up in safe mode and use the reconfigure x option to set the driver to VESA and set the screen resolution to your screen size. That should get you a normal size login screen and a normal gnome safe mode gui.

---

### Post by jsf_pp on 2008-12-10
> **markbuntu said:**
> OK, try this. Boot up in safe mode and use the reconfigure x option to set the driver to VESA and set the screen resolution to your screen size. That should get you a normal size login screen and a normal gnome safe mode gui.

ok, im not quite sure how to do it, but i'll do it anyway.
so, please, tell me, how to boot up in safe mode? its the same as recovery mode?
so i have to do it in grub>esc> ?

---

### Post by JoshuaRL on 2008-12-10
Safe mode is supposed to be a graphical way to interact with the system, but without any special drivers or resolutions.  It should work for you.  Recovery mode is a CLI (command line interface) that gives you control over the guts of the system.  It drops you into the terminal as root, kind of like this:
```

root@yourcomputer~$:

```
Be careful what you do in Recovery Mode, because you have root access and can hurt your system.

---

### Post by jsf_pp on 2008-12-10
> **JoshuaRL said:**
> Safe mode is supposed to be a graphical way to interact with the system, but without any special drivers or resolutions.  It should work for you.  Recovery mode is a CLI (command line interface) that gives you control over the guts of the system.  It drops you into the terminal as root, kind of like this:
```

root@yourcomputer~$:

```
Be careful what you do in Recovery Mode, because you have root access and can hurt your system.

sorry about my stupidity, but please tell me then, how to boot up in safe mode?

---

### Post by JoshuaRL on 2008-12-10
Its one of the options when you get to the graphical login.  It was detailed in an earlier post in this thread.

---

