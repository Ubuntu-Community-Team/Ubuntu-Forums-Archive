---
title: "Solid Wireless Connection Suddenly Failed"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Game Over on 2009-05-19
My internet has worked perfectly since I installed Ubuntu and set up my connection... until now :(  

I'm running Jaunty on a HP dv6000, and just before this happened I download and installed the Educational desktop for Ubuntu + removed a couple programs via Add/Remove, some of which came with the Edubuntu package (basically thats what it is right?)

My wireless card is working, but is disconnected. Everything under Network Connections is now gone/missing + I can not add a new connection; It will not let me apply the changed after I +Add IP, Gateway, WEP, etc.

Please help. I am 7 days into Ubuntu and loving it, I just got a little tangled up here!

Thanks,
Alva

---

### Post by Game Over on 2009-05-19
No help??

I tried this
[https://help.ubuntu.com/9.04/internet/C/connecting-wireless.html](https://help.ubuntu.com/9.04/internet/C/connecting-wireless.html)
but can not find my Network Manager anywhere. Did I delete something? Everything is working peach, but my internet connection has flat out vanished, and the place I enter the WEP key won't let my apply or +Add the changes. The place I originally entered the Static IP and Gateway up and left when I upgraded from 8.10 to 9.04

~Alva

---

### Post by Game Over on 2009-05-19
Bump please.

---

### Post by anjilslaire on 2009-05-19
try
```

sudo apt-get install network-manager-gnome
```

That should reinstall the network manager if it was removed.

---

### Post by Game Over on 2009-05-19
Done.
Now it says:

network-manager-gnome is already the newest version.
That following packages were automatically installed and are no longer required:
.......lists them.......
Use 'apt-get autoremove' to remove them'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I'm lost...
I still can't find the NM or where to set up my WEP + Static IP.
Thank you or your reply, friend!

---

### Post by Game Over on 2009-05-19
I entered nm-applet & into the terminal and it came back with:

** (n-applet:5509): WARNING **: < WARN > applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.
Return: 3

~Alva

---

### Post by Game Over on 2009-05-19
Bump.

Still having issues. Any help would be great.

Please and thanks. :popcorn::popcorn::popcorn:

~Alva

---

