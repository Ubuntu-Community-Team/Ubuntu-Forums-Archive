---
title: "adobe flash plugins ?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by usman idrees on 2009-01-06
i have installed Adobe flash plugin to run online video on youtube but still it is not working ? 
do i need to restart the system ?

---

### Post by thegreenblob on 2009-01-06
How did you install it? (There are several ways :P)

---

### Post by usman idrees on 2009-01-06
i opened mozilla and then searched a video. it then demanded for plugins and it automatically directs to download adobe flash plugin. i clicked yes and its done. this is the whole story.:)

---

### Post by thegreenblob on 2009-01-06
Hmmm... You shouldn't have to reboot. But you might wanna try restarting firefox.

If it still doesn't work try:

```
sudo apt-get install flashplugin-nonfree
```

In the terminal. (Applications --> Accessories --> Terminal). Then restart firefox and... it should work. Hope this helps.

---

### Post by SunnyRabbiera on 2009-01-06
It might also help if you remove gnash as it can interfere with flash.
To remove it is easy, go to system
then to administration
then to synaptic package manager
search for gnash
and next to the packages marked gnash there are probably green boxes
right or left click these boxes and select "mark for complete removal"
hit apply
and if you get a screen asking if you want to remove additional packages again hit reply, synaptic is easy to figure out.

---

