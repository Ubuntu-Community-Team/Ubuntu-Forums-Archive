---
title: "Change primary monitor"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Kungal on 2010-09-07
Hi all,

I have just installed Ubuntu and I am trying to change my primary monitor.  

Can anyone tell me how to do this.

Thanks

---

### Post by silverglade00 on 2010-09-07
We need more information. Which version of Ubuntu do you have installed? What kind of video card do you have? Do you have the proprietary drivers installed for your video card? Sometimes it is as simple as swapping the cables around on the back of the computer.

---

### Post by bodhi.zazen on 2010-09-07
Assuming you have a nvidia card ...

```
gksu nvidia-settings
```

There is a place in the nvidia settings to set your primary monitor.

---

### Post by Kungal on 2010-09-08
Thanks for those replies.

The   gksu nvidia-settings  thing dosen;t do anything.  I am prompted for my password then noting happens.

I am using a laptop with an external monitor so I can't swap the cords around unfortunately.

As far as I can tell my graphics card is a Mobile Intel(R) 965 Express Chipset Family

I am usung Ubuntu 10.04-Desktop  (is there one made specially for laptops?)

I have no idea whether my drivers are proprietary and I;m not sure how to find out.

I'm surprised there isn't a simple change my primary monitor button as in Windows.  

Thanks

---

### Post by excetara2 on 2010-09-20
Is there a quick way to do this if your using default ubuntu settings for an ati driver (open source driver)?? I'm not using fglrx.

Thanks

---

### Post by johnmay on 2010-11-29
Found two links to a quick method: [http://ubuntuforums.org/showthread.php?t=1309247](http://ubuntuforums.org/showthread.php?t=1309247) and [http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions](http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions)

I used the second link with instant success.

---

### Post by accord2k8 on 2011-03-21
Hi Johnmay,

This worked perfectly  for me thanks.
I also added it in StartUp programs so it automatically sets it by default upon login.

Thanks for sharing!
Ian

---

### Post by beelzebufo on 2012-12-31
> **johnmay said:**
> Found two links to a quick method: [http://ubuntuforums.org/showthread.php?t=1309247](http://ubuntuforums.org/showthread.php?t=1309247) and [http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions](http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions)

I used the second link with instant success.


I  used the second with instant success as well, thank you.

---

### Post by oldos2er on 2012-12-31
Old thread closed.

---

