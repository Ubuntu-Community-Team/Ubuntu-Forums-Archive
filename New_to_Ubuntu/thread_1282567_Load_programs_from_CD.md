---
title: "Load programs from CD"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by PartsMan on 2009-10-04
I had a brain fart the other day. Was having trouble with my internet and had the bright idea to remove and reload network manager. Of course I soon realized that I couldn't reload it without internet.

Can I load network manager from the cd or something?

---

### Post by amingv on 2009-10-04
I think you can, if you add the cd to the repos 
```
sudo apt-cdrom add
```
Or you can also connect using the terminal (with ifconfig or dhclient)

---

### Post by PartsMan on 2009-10-04
I still can't load it in add/remove or synaptic.

---

### Post by PartsMan on 2009-10-04
I think I have it reloading on a wired connection. I guess it is just the wireless that I am fighting.

---

### Post by PartsMan on 2009-10-05
I have internet fine on a wired connection but it won't search for wireless.

No little balls chasing each other up in the corner.:confused:

---

### Post by achase79 on 2009-10-05
If you have internet access I would suggest getting wicd.  I believe that it works better than the regular network manager.

---

### Post by achase79 on 2009-10-05
If you do want to reload from the cd just hit alt-f2 and type ```
gksu gedit /etc/apt/sources.list
```
and remove the "#" before the cdrom source.
then open synaptic and click reload or refresh.  Then you can install the network-manager

---

### Post by PartsMan on 2009-10-07
It is working now. Not sure what I did but thanks for all the help. Apparently it helped.:)

---

### Post by PartsMan on 2009-10-12
That no good sorry piece of #%&* quite again last night. When I needed it most. The whole reason I have that computer is to write papers for school. Started my paper Saturday no problem. Powered up Sunday and could not research because my internet would not connect! I have a good wireless signal (60-70%) it just wont connect to it! 
I had to borrow a windows laptop to research while I typed on my computer. Why is it that every time I change hardware I have to trick, fight or reload Ubuntu to get to use it?


OK. Sorry. Rant over.

---

### Post by PartsMan on 2009-10-22
> **achase79 said:**
> If you have internet access I would suggest getting wicd.  I believe that it works better than the regular network manager.

Could not find it.

Gave up and moved my desk across the house to the modem.
:(

---

