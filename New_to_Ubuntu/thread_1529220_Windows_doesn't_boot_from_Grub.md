---
title: "Windows doesn't boot from Grub"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by hungryOrb on 2010-07-11
HI all,

For a while, I've had 9.10 installed on a workstation at work. It worked great for a long time, but then I think I did one update, and ubuntu wouldn't load from grub, something about device not specified or something. I looked through posts and tried things, but nothing worked. I was a bit discouraged so just left it and used windows mostly. However, today I had some time, so wanted to try upgrading it to 10.04, which seemed to fix a similar problem on a laptop I have. After upgrading, I purged grub-pc and common, and reinstalled, just to be safe. After reboot, and after a cold start, Ubuntu now starts perfectly! Fantastic!!

However, windows now does not start at all.. After selecting it, the screen goes black, like it's going to start loading, and then the grub menu appears again, and I can choose again..
Any ideas? I tried grub legacy install from synaptic too, but no effect. 
It just hasn't happened before, so I wasn't prepared :(

Thanks for any consideration.
Robin

---

### Post by garvinrick4 on 2010-07-11
When you are in Linux you did. Just checking.
```
sudo update-grub
```
```
sudo grub-mkconfig
```

---

### Post by garvinrick4 on 2010-07-11
If does not work updating grub download this to desktop and run to put
get a text file and post here so we can see what your boot looks like.


[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by lidex on 2010-07-12
Probably overwrote your MBR
Have a look here:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by oldfred on 2010-07-12
If none of the previous have worked, show us where everything is installed.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

