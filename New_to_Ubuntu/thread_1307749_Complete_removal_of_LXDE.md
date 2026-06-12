---
title: "Complete removal of LXDE"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by nns2006 on 2009-10-31
Hi,
I am trying to remove LXDE from my laptop.I have already performed
> sudo apt-get remove lxde and > sudo apt-get clean 
still i can see some of files(lxde-common,lxde-setting daemon,lxde-core,lxpanel,lxappearance,lxrandr,lxmenu-data,lxterminal) in synaptic manager by typing  lx  . Should i remove these files manually? Is there any way to completely remove lxde through terminal?

Thanks in advance

I also run > sudo apt-get autoremove

---

### Post by ibuclaw on 2009-10-31
Check the output of:
```
dpkg -l | awk '{print $2}' | grep "^lx"
```
If that outputs all LXDE packages, and nothing else, run:
```
sudo aptitude purge $(dpkg -l | awk '{print $2}' | grep "^lx")
```

To remove them all at once.

Regards
Iain

---

### Post by nns2006 on 2009-10-31
Thank you tinivole, I am able to remove them all.

---

