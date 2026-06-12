---
title: "help me set up intel 2200 wireless"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by drmoore1 on 2008-04-06
Ok so I am a complete newby so I need a little more detail on this than just the how-to. Hopefully its an easy fix. Ok first of all when I tried to instal the linux headers I get this :

```
dylan@dylan-laptop:~$ sudo apt-get install linux-headers-$(dylan)
bash: dylan: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 135 not upgraded.
```

So I thought maybe I was ok and went on down to where I download the firmware

I installed the firmware to my desktop(thinking maybe I need to move it somewhere?) then entered the code ```
sudo tar xvzf ipw2200-fw-2.3.tgz

```

and in return it says this:
```
dylan@dylan-laptop:~$ sudo tar xvzf ipw2200-fw-2.3.tgz
tar: ipw2200-fw-2.3.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

What am I doing wrong here? Thanks

---

### Post by drmoore1 on 2008-04-06
Hmm ok I got it figured out but for future reference, was I in the wrong directory and is that why it wouldn't install? Thanks

---

