---
title: "Remote applications from Windows?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by paal on 2009-06-19
I've been searching a bit around, but couldn't find anything that fits (mostly because I don't know what it's called:) ). I'd like to connect to a windows remote desktop from Ubuntu, but instead of showing the whole windows screen like Remote Desktop Viewer does, I'd like to get the applications up in Ubuntu along with my other running applications. Kind of what Xming does, just the other way around. Is this possible?

---

### Post by DustyMP on 2009-06-29
Yes it can be done with the terminal server client. Look in the internet folder of the applications menu. If it's not there go to Applications -> Accessories and open a terminal. Enter:

```
 sudo apt-get install -y tsclient 
```

That should install it for you. Now when you open it up you can set the IP to connect to, login, password, so on. If you click on the display tab you can set the screen size with the first couple options.

---

### Post by lavinog on 2009-06-29
I don't think it is possible with remote desktop, but ultravnc has a feature to only show the active application. Unfortunately the ultravnc client is only written for windows, but it works great with wine.
The feature I was referring to is a crosshair on the toolbar, once you connect to the desktop, click on the crosshair, then the app window you want to isolate.

---

### Post by albinootje on 2009-06-29
> **paal said:**
> I'd like to connect to a windows remote desktop from Ubuntu, but instead of showing the whole windows screen like Remote Desktop Viewer does

This might help :
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)
[http://linux.com/archive/feature/124908](http://linux.com/archive/feature/124908)
[http://collegegeek.org/2007/03/31/windows-applications-in-linux/](http://collegegeek.org/2007/03/31/windows-applications-in-linux/)

---

