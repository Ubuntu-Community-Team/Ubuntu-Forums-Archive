---
title: "The start up screen"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by irishy on 2011-02-26
Help please I am struggling to clear some of the list  on the screen that lists what operating system I want to start up ie windows or ubuntu I now have many versions of ubuntu listed 
I hope this makes sense

---

### Post by Anton K on 2011-02-26
To clear the list of available OS you can follow these ways, that are not mutually excluded - you can use them all together:
[B]
Remove old/unused kernels
[/B]To find out the kernel you're using at the present moment you can use next command:
```
uname -r
```
Then go to Synaptic and remove packages of unused concrete kernels. Their names will look like this:
linux-image-<version>-generic, for instance linux-image-2.6.35-23-generic.
Package named linux-image-generic better leave installed.
[B]
Disable Linux recovery[/B] (for Grub)
Uncomment the following line in /etc/default/grub (need root privileges):
```
GRUB_DISABLE_LINUX_RECOVERY="true"
```Then update Grub:
```
sudo update-grub2
```[B]
Uninstall memtest[/B]
Remove package named memtest86+:
```
sudo apt-get remove memtest86+
```

---

### Post by grahammechanical on 2011-02-26
I installed a little Utility called Grub Customizer. It lets you hide some of the entries (lines) in the Grub menu. It does other things as well. Here is the link:

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

Regards.

---

### Post by vivek.pandey on 2011-02-26
> **grahammechanical said:**
> I installed a little Utility called Grub Customizer. It lets you hide some of the entries (lines) in the Grub menu. It does other things as well. Here is the link:

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

Regards.

sorry to post here but i followed your steps but got an error message while installing in synaptic. here is the  message

E: cherokee: subprocess installed post-installation script returned error exit status 2
E: libcherokee-mod-rrd: subprocess installed post-installation script returned error exit status 2

---

### Post by irishy on 2011-02-26
Thank you all very much my problem is now resolved

---

