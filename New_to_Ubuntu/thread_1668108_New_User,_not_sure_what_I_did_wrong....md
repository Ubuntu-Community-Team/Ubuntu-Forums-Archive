---
title: "New User, not sure what I did wrong..."
date: 2011-01-15
forum: New to Ubuntu
---

### Post by yanks0221 on 2011-01-15
Hi,

I just installed ubuntu on my machine.  everything went fine and I am able to log in.  When i get to the "desktop" all i see is the wallpaper.  Am I doing something wrong?

---

### Post by NightwishFan on 2011-01-15
I doubt it, try going back to the login screen, and choose "Safe Mode" from the drop down menu below the login box.

Edit: Oh! Netbook version. Try using "Ubuntu Desktop or Safe Mode". You might not have 3d capable hardware and that is why Unity wont launch. You are using Ubuntu 10.10 am I correct?

---

### Post by Smart Viking on 2011-01-15
hm..
Open a tty by pressing CTRL+ALT+F1
then login,
then launch the following command
```
DISPLAY=:0.0 gnome-panel
```
then go back to the GUI b pressing CTRL+ALt+F7.

Did it work?

---

### Post by yanks0221 on 2011-01-15
> **NightwishFan said:**
> I doubt it, try going back to the login screen, and choose "Safe Mode" from the drop down menu below the login box.

Edit: Oh! Netbook version. Try using "Ubuntu Desktop or Safe Mode". You might not have 3d capable hardware and that is why Unity wont launch. You are using Ubuntu 10.10 am I correct?


yes 10.10 and safe mode worked.  must be something with my video card or something like that?

---

### Post by yanks0221 on 2011-01-15
> **Smart Viking said:**
> hm..
Open a tty by pressing CTRL+ALT+F1
then login,
then launch the following command
```
DISPLAY=:0.0 gnome-panel
```then go back to the GUI b pressing CTRL+ALt+F7.

Did it work?


hmm nope this didn't work for me.

---

### Post by NightwishFan on 2011-01-15
Ok, when you are in the normal desktop. Go to System -> Administration -> Additional Drivers (or Hardware Drivers, icon is a green chip). Then if one is there and recommended for you (Nvidia probably), then install it and reboot when it is finished. Then you should be fine.

If you see no drivers listed, It is likely you will need to use the standard desktop edition(which should be installed, and easy to get, no need to reinstall). That will work fine.

---

### Post by yanks0221 on 2011-01-15
> **NightwishFan said:**
> Ok, when you are in the normal desktop. Go to System -> Administration -> Additional Drivers (or Hardware Drivers, icon is a green chip). Then if one is there and recommended for you (Nvidia probably), then install it and reboot when it is finished. Then you should be fine.

If you see no drivers listed, It is likely you will need to use the standard desktop edition(which should be installed, and easy to get, no need to reinstall). That will work fine.


thanks for your help!  it's a lot easier to use when i can see something besides the wallpaper :D

---

### Post by NightwishFan on 2011-01-15
No problem, I will be around so tell me if you hit any roadblocks.

---

