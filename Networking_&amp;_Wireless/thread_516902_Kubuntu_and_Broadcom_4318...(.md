---
title: "Kubuntu and Broadcom 4318...:("
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by thisperishedmin on 2007-08-03
First of all, let me say that I absolutely love Ubuntu 7.04, it fires right up and the wired network connection was working beautifully from the start.  The package installers make life alot easier, and the user interface is great.  Now, the (seemingly) infamous Broadcom wireless disaster... 

Ive been fighting with trying to get ndiswrapper working with bcmwl5.inf drivers, and have this much accomplished: 

```
cody@cody-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
```

Beyond this point, I'm totally lost with getting anything working.  There seem to be tons of explanations with ubuntu, but none of them are getting me connected with Kubuntu.  Does anyone have any ideas or a better explanation from where to begin?  If competely reinstalling kubuntu is the place to begin I'll do it too.

Thank you in advance...I would love to get this running fully and completely...after that I'll quickly be crossing over to linux :-D

---

### Post by splintercellguy on 2007-08-03
You need to blacklist the bcm43xx driver:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

and I think reboot.

---

### Post by thisperishedmin on 2007-08-03
Hey, thanks for the tip.  I entered that but ndiswrapper -l still outputs the same thing.

I tried to retrack and delete all ndiswrapper parts and begin the process over again and seem like ive lost ground now haha.  Im making progress backwards.  How can you completely remove all ndiswrapper and drivers and clear the blacklist?

thanks...

---

### Post by splintercellguy on 2007-08-03
Hmm, perhaps you have forgotten to do the modprobe stuff:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Did you reboot after doing so?

---

