---
title: "Detecting Wireless on Ubuntu"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by billhopkinson on 2011-07-19
I have installed Ubuntu 10 on a PC, and Ubuntu 11 on an old laptop.
Neither detect any wireless connections, nor does a manual connection work using SSID and network key on WPA personal.
Both have hardware for wireless, so what do I have to do to detect and use wireless?
My PC at the moment has a direct ethernet connection which works automatically, but I need to move the PC eleswhere.

---

### Post by westie457 on 2011-07-19
> **billhopkinson said:**
> I have installed Ubuntu 10 on a PC, and Ubuntu 11 on an old laptop.
Neither detect any wireless connections, nor does a manual connection work using SSID and network key on WPA personal.
Both have hardware for wireless, so what do I have to do to detect and use wireless?
My PC at the moment has a direct ethernet connection which works automatically, but I need to move the PC eleswhere.

Hello, welcome to the forums.

You have no drivers or you have an incorrect driver installed.

We will start with the PC for now.

Go to Applications > Accessories > Terminal.
In the terminal type in ```
lspci
```

using your mouse in the terminal window highlight the output and copy it. Then come back here and in a new reply click on # at the top of the panel paste into the ```

``` tags.

This will let us know what to look for.

The same process can be used for the laptop as well.

---

### Post by Matt__ on 2011-07-19
/edit Westie has got it....I didnt post fast enough... :)

but check iwconfig too.

---

### Post by Bucky Ball on 2011-07-19
This:

```
sudo lshw -C network
```

... might be more helpful. ;)

Also, in System>Administration>Additional Drivers, is there anything for your wireless disabled? If so, get online with a cable and enable it.

---

### Post by wep940 on 2011-07-19
If you have, or can have, the PC connected by wire, then do the following:
 
- open a terminal window (applications/accessories/terminal)
- type:  sudo apt-get update <press enter> and wait for it to finish
- click on system/administration/additional drivers - this will start an online search for drivers, and if found, will show on the screen.  You'll just have to click on the Enable to start using it.
 
Since we don't know for sure if this will work, also remember to post back the information already requested.  If you don't know, you'll need to do those commands in a terminal window as well (applications/accessories/terminal)

---

