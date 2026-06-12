---
title: "Keep Messing Up Ubuntu 10.04. Tired or Reinstalling."
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Demrtnz on 2010-07-25
So, i have been using ubuntu for over a week now and i have managed to mess it up and had to reinstall it twice. the first because the updater wouldn't update any more and the second because i could fix a xserver issue. the last install, all i did was reboot and it messed up. i am just wondering if this is cause i am doing something wrong? or is ubuntu not great for beginners such as me? i switched over from windows vista and i love linux except for how fragile ubuntu seems to be? can i make more durable, so i am less likely to have to keep reinstalling due to messing up something? i really don't want to go back to windows. any helps or tips for a complete noobie would be great!

---

### Post by Lpeop on 2010-07-25
I too am regretting upgrading to 10.1.  I am going to get and old CD and install an earlier version of Ubuntu.  I didn't have any problems with earlier versions.  My 10.1 won't download the updates either.  It takes like hours and then everything freezes.  I just usually re-boot and everything seems ok until the next freeze.

---

### Post by Goolie on 2010-07-25
Try the check CD integrity option, if that fails try remaking the CD. 

Also, I had problems when I downloaded from the *alternat download *locations.  But the normal download it worked like a charm.

=\

---

### Post by linux18 on 2010-07-25
for updating, I have the all-in-one solution for 90% of synaptic errors: 
```

 sudo apt-get -f || echo "ERROR 0"
 sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
 sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
 sudo apt-get clean || echo "ERROR 3"
 sudo apt-get autoclean || echo "ERROR 4"
 sudo apt-get autoremove || echo "ERROR 5"
 sudo apt-get update || echo "ERROR 6"
 sudo apt-get --fix-broken upgrade || echo "ERROR 7"

```and for the X server its a little more dificult:

```
 

-choose recovery mode at grub
-drop to a root prompt
-type  " telinit 3 " and login
-then type " xinit "
-when xinit starts type: " metacity & " - for ubuntu OR " compiz & " - if you have it OR flux/openbox & - if you have it OR " fvwm & " - for xubuntu
-then type " gnome-panel " & -for ubuntu OR " xfce4-panel & " -for xubuntu
-lastly type " nm-applet & " -for networking
 
```probably run through that list once, write down the steps, and try it on a working system, because if X breaks, you need to know what to do.

anyway, those are my two scripts that seemingly fix 15% of all ubuntuforums problems.

---

### Post by bodhi.zazen on 2010-07-25
> **Demrtnz said:**
> So, i have been using ubuntu for over a week now and i have managed to mess it up and had to reinstall it twice. the first because the updater wouldn't update any more and the second because i could fix a xserver issue. the last install, all i did was reboot and it messed up. i am just wondering if this is cause i am doing something wrong? or is ubuntu not great for beginners such as me? i switched over from windows vista and i love linux except for how fragile ubuntu seems to be? can i make more durable, so i am less likely to have to keep reinstalling due to messing up something? i really don't want to go back to windows. any helps or tips for a complete noobie would be great!

I assume the issue is that you are new to Linux or Ubuntu (or both). A fresh install takes 20 minutes tops and sometimes it is easier to start fresh.

IMO it is common to reinstall frequently when you are new to Ubuntu, over time the need to reinstall lessens.

I suggest you start a thread when you are having a problem, perhaps we can assist.

---

