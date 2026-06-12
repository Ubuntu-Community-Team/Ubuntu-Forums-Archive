---
title: "Help Needed Please"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Singer on 2011-02-15
hello friends 
well i am new to ubuntu and i have installed ubuntu 10.10 inside windows.. 
there are 2 problems i am currently facing 

1) disk space low alert: even after dedicating a 15 Gb partition with 10 Gb free space(after installing ubuntu) i still get the low disk space warning. how can i over come that??
2) how can i get google chrome replace firefox in all aspects (including Replacing the Firefox icon near System Settings on the Top panel)

hope to get a reply soon 
Thanks 
Singer

---

### Post by Paqman on 2011-02-15
> **Singer said:**
> 
1) disk space low alert: even after dedicating a 15 Gb partition with 10 Gb free space(after installing ubuntu) i still get the low disk space warning. how can i over come that??


If you open up System Monitor how much actual space does it show you using?

> 
2) how can i get google chrome replace firefox in all aspects (including Replacing the Firefox icon near System Settings on the Top panel)


You can set Chrome as the default browser by going into Chrome's menu, there will be an option in there to make it the default. To replace the Firefox icon on your top panel simply right click on the Firefox icon and delete it, then you should just be able to drag the Chrome icon from the menu onto the panel.

---

### Post by Singer on 2011-02-15
yes Mr. Paqman i was able to replace firefox and ya when i checked the system monitor
in the system tab the available disk space is shown 11.3 Gb but when checking on the File Systems tab
i see a root labeled [/dev/loop0] which has 2.6 Gb as total space and 232 MB free.. how is that possible?
i didnt make any partition like that Please help...

---

### Post by oldfred on 2011-02-15
If you installed wubi it is just a file inside the NTFS partition. When you install it you set a file size, but that is not the same thing as the partition size.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by opensource10 on 2011-02-15
> **Singer said:**
> 
2) how can i get google chrome replace firefox in all aspects (including Replacing the Firefox icon near System Settings on the Top panel)

hope to get a reply soon 
Thanks 
Singer

Hello Mate....

you can use synaptic package manager in Ubuntu 10.10. Do search "chrome" and there will be a button to install :)

---

### Post by Paqman on 2011-02-15
> **Singer said:**
> 
i see a root labeled [/dev/loop0] which has 2.6 Gb as total space and 232 MB free.. how is that possible?
i didnt make any partition like that Please help...

It was created automatically. You can free up some space by following the advice in [this guide]("http://ubuntuforums.org/showthread.php?t=140920"). I'd also run:
```
sudo apt-get autoremove
```
and uninstall any kernels you aren't using. The latter will free up a lot of space, but if you aren't sure how to do so just ask and we'll give you details.

---

### Post by Singer on 2011-02-15
> **Paqman said:**
> but if you aren't sure how to do so just ask and we'll give you details.

Please Mr.Paqman it will be helpful if you dont mind :D

---

### Post by Paqman on 2011-02-15
> **Singer said:**
> Please Mr.Paqman it will be helpful if you dont mind :D

No problem. Open up Synaptic and search for installed packages starting with "linux-image". You should get several with names like linux-image-2.6.35-xx-generic. You can mark them all except the most recent one for complete removal and hit "apply". I would then also run:
```
sudo apt-get autoremove
```
in a terminal to remove anything that was installed along with them.

---

### Post by Singer on 2011-02-26
problem solved 

i reinstalled ubuntu selecting 15 gb as drive space
now i have 12 gb free...

---

