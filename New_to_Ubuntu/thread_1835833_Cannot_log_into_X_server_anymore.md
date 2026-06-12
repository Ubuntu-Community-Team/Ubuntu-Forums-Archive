---
title: "Cannot log into X server anymore?"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by sylvainrb on 2011-08-30
Hello,

I am running 10.04 on a Thinkpad X200 and I today I wasn't able to start the X server. I usually boot and log in my Ubuntu via the terminal, and then issue the 'startx' command if I need to go into the GUI's...

Here's the ouput I got from the terminal after entering 'startx' (my screen turns black but I can see the output going back to tty1):

Waiting for X server to begin accepting connections.
No protocol specified
..
No protocol specified
,,
(infinite loop)

I'll do more research tomorrow but I thought I'd ask and maybe someone has a solution  for me in the morning. Thanks!

---

### Post by raja.genupula on 2011-08-30
ctrl+alt+ f7 

or 
sudo service gdm stop
sudo service gdm start

execute them one by one

---

### Post by seawolf167 on 2011-08-30
If 

```
sudo service gdm restart
```doesn't work, try to reconfigure the xserver

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by sylvainrb on 2011-08-30
Ok I will try when I get home tonight. Thanks!

---

### Post by sylvainrb on 2011-08-30
> **seawolf167 said:**
> If 

```
sudo service gdm restart
```doesn't work, try to reconfigure the xserver

```
sudo dpkg-reconfigure xserver-xorg
```

The first command works but the second one seems to not do anything... I really dislike the gdm theme so that's why it was disabled in the first place. 

But the 'startx' command still doesn't work...?

---

### Post by sylvainrb on 2011-08-30
Never mind I solved the problem: I just had to delete all .Xauthority* files in my home folder. Everything is back to normal now :)

---

### Post by EslamAK on 2012-12-15
I have the same problem here and neither of those solutions work with me

Can anybody tell me what to do or how to remove all .x files from home from terminal

---

