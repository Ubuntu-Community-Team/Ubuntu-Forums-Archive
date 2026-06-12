---
title: "VNC questions"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by SOG420 on 2007-05-07
I'm not sure if this is the right forum for this but I'll put it here anyway, I was wondering if anyone could recomend a VNC server/viewer program for two Feisty distros. The built in remote destop only has 8 bit support and I'm looking for higher quiality hopefully free. Thanks
P.S. Mods feel free to move this post if it doesn't belong here

---

### Post by compiledkernel on 2007-05-07
sudo apt-get install vncserver vncveiwer 

:)

---

### Post by SOG420 on 2007-05-07
here is the output of those commands
[K apt-get install vncserver vncviewer
Password:

Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done


Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree       


Reading state information... 0%

Reading state information... 1%

Reading state information... Done

Package vncviewer is a virtual package provided by:
  xtightvncviewer 1.2.9-21
  svncviewer 1:0.1.1-8
You should explicitly select one to install.
E: Package vncviewer has no installation candidate
]0;user1@maglap: ~user1@maglap:~$ exit
exit

Script done on Mon 07 May 2007 01:44:16 PM CDT

---

### Post by nuclearpidgeon on 2007-05-07
Hmm... That's odd

Try
sudo apt-get install vnc4server vnc4viewer

---

