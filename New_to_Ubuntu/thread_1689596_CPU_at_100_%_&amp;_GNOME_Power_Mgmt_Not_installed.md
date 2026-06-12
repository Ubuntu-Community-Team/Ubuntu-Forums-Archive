---
title: "CPU at 100 % &amp; GNOME Power Mgmt Not installed"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by prandoman on 2011-02-17
Dear All,

I have been using Ubuntu on my Toshiba Satellite for past 3 years and I had a very smooth working. However, one day due to battery power failure my system shut down in the middle of the update and since then I get the "GNOME Power Management Not installed" during startup and also, my CPU always keeps performing at 100% even though there are no jobs running.

Please help in this regard.

With thanks and regards

---

### Post by rvchari on 2011-02-17
try giving a "top" (without quotes) in terminal to see if some hidden processes r running. some runaway processes must b running that keeps ur cpu engaged....
this will give u a hint on whats going on in the back end (not visible)

---

### Post by prandoman on 2011-02-17
Hey, upon executing the TOP command, I saw the following ... 

564 S    9  0.4   0:16.50 gdu-notificatio    
  607 messageb  20   0 24268 1852  752 S    9  0.1   0:27.89 dbus-daemon        
 5891 prando    20   0  186m  13m 9440 S    8  0.7   0:20.86 update-notifier    
    1 root      20   0 19460 1828 1208 S    7  0.1   0:18.53 init               
  492 root      18  -2 16948  876  312 R    7  0.0   0:16.72 udevd              
12770 prando    20   0  660m 200m  30m R    7 10.0   0:41.85 firefox-bin        
 5314 prando    20   0  265m 5088 3640 S    4  0.2   0:04.58 pulseaudio         
  471 root      20   0 21332 1296  948 S    3  0.1   0:07.43 mountall           
 1365 root      20   0  191m  34m  11m S    3  1.7   0:23.24 Xorg               
  485 root      20   0 12644  764  548 S    3  0.0   0:03.95 upstart-udev-br    
16015 prando    20   0  182m  24m  14m S    3  1.2   0:08.01 npviewer.bin       
  487 root      16  -4 17612 1476  288 S    1  0.1   0:04.25 udevd              
  605 syslog    20   0  120m 2184  972 S    1  0.1   0:01.93 rsyslogd           
 5781 prando    20   0  289m  38m 8692 S    1  1.9   0:03.56 compiz.real        
  614 haldaemo  20   0 34168 4740 3684 S    1  0.2   0:01.78 hald  

There was this gvfs-gdu-volume process that occupied most of my CPU .. I'd love to hear some insight into it.

Thanks and regards

---

### Post by NightwishFan on 2011-02-17
Try running this command to fix packages, then reboot.
```
sudo apt-get -f install
```

---

