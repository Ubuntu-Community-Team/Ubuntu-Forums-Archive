---
title: "ununstalled Nouveau nothing in additional drivers"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by JohnCUbu on 2010-11-11
i followed the guide here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
but after i uninstall Nouveau nothing shows up in additional drivers
so, following other posts, i uninstalled all nvidia drivers sudo apt-get purge nvidia*
still nothing
so  i installed everything from the package manager that had 96(the needed driver) and it downloads but cannot install
i have 9.10 on a usb drive, it sees a i need 96, installs it and and I have my effects so I know it can be done.
If I try to reboot after any of this I either just hang at splash or sometimes I get boot without gui. I've been doing this on usb drives so I don't mess up my real comp. It shouldn't be a problem it the 9.10 work. But anything with 10.10 Nouveau preinstalled is a pain.

---

### Post by sikander3786 on 2010-11-11
Please tell us which graphics card, model are you using. Post the output of

```
lspci | grep VGA
```

---

### Post by JohnCUbu on 2010-11-11
VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

I'm now having a personal minor emergency and may be afk for a few hours, if it one thing its 10 others...
I did the headers thing like the guide said but cant find linux-restricted

---

### Post by JohnCUbu on 2010-11-11
I know its old card.   But it works on 9.1 with compiz> 

---

### Post by sikander3786 on 2010-11-11
Yes it might work with 9.10 but not supported in Maverick.

[http://ubuntuforums.org/showthread.php?t=1592628](http://ubuntuforums.org/showthread.php?t=1592628)

---

### Post by beew on 2010-11-11
The 96 package is not supported in Maverick.

Here is my solution, now I get compiz and everything using the Nvidia driver.

[http://ubuntuforums.org/showthread.php?t=1598591](http://ubuntuforums.org/showthread.php?t=1598591)

There is another work around using the  nouveau driver with some 3d acceleration experimental packages, see also the link above for a  link to one of those tutorials. Somehow that didn't work for me.

---

### Post by JohnCUbu on 2010-11-11
Thanks for the links guys! It looks like I'm not the only person trying to keep old computers alive :) I have another 4 year old (NVIDIA 6150) and a new netbook(Intel drivers work!). I'd like to get them all on linux if the drivers will let me.I wonder how long I can run old distros like 9.10 if I have to?

---

### Post by beew on 2010-11-11
> **JohnCUbu said:**
> Thanks for the links guys! It looks like I'm not the only person trying to keep old computers alive :) I have another 4 year old (NVIDIA 6150) and a new netbook(Intel drivers work!). I'd like to get them all on linux if the drivers will let me.I wonder how long I can run old distros like 9.10 if I have to?

I used that method in my link to install Ubuntu 10.10 and nvidia-96 on a 7 year old laptop and I get Compiz and all the 3d effects.  It works better than Windows NT which came with the PC, and Windows XP which I installed there to replace NT (but have to disable compiz or switch to openbox or fluxbox when doing computationally demanding stuffs, it has only 512M of ram). I have also installed 10.04 before I switched to 10.10, 10.04  worked out of the box on this machine without tweaking. 

You don't have to run old distro if you don't want to. :)

My main Ubuntu machine is 5 year old and it rocks with 10.04. I have a new machine, but haven't made up my mind whether to install 10.04 or 10.10, still testing. :)

---

### Post by JohnCUbu on 2010-11-11
I won't be home for a couple of hours to test the methods, but now you have me in the mood to dig out my old win98 machine from the closet and get it working again ;) I'm afraid if I stay with 9.10, they will only support it until I think early 2011, and I don't know if that means no more update afterwards or what that means. Thanks again.

---

### Post by sikander3786 on 2010-11-12
> I'm afraid if I stay with 9.10, they will only support it until I think early 2011, and I don't know if that means no more update afterwards or what that means.

Yes that means, no more updates after April 2011.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

