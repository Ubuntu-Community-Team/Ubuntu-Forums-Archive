---
title: "No Shut Down or Restart"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by laidback on 2010-05-14
Have a new version of 10.04 LTS that I'm trying. But here's an odd thing, the Shut Down or Restart options don't (always) work, I have to Log Out and shut down from there. I say don't work, they appear to be OK when I first boot, it's after that following other HDD activity that they stop working.

I tried putting a new applet for Shut Down on the task bar but that produced the same result.   

Any ideas?

Kindest Regards

Laidback

---

### Post by drs305 on 2010-05-14
I don't have a specific solution but it could be that your 'other' hard drives/partitions may not be unmounting before you log out. Try closing out your apps and then unmounting your other fstab partitions with the following command. You will get 'busy' error messages for partitions which can't be unmounted, such as / and /home, but it should unmount other partitions. 
```
sudo umount -a
```

Then try shutting down without logging out. If it works, at least we will have an idea of *why* it isn't allowing you to shut down as a normal user.

---

### Post by ZGStyle on 2010-05-14
The same issue here. :(
I can't even Log out.
The only option is to fire-up terminal and do:
```
sudo poweroff
```

And this issue is on both my PCs.

---

### Post by laidback on 2010-05-14
drs305,

There aren't any other HDDs, I use a caddy system so my other Ubuntu installations aren't even attached, the only HDD is the one running 10.04. I was referring to activity other than that at boot up, i.e. opening Open Office etc. Sorry for the confusion caused.

---

### Post by drs305 on 2010-05-15
I tried searching for bugs that might have been reported but can't really do a comprehensive search without knowing more about what actually happens when you try to shutdown. The chances are good that since two of you are reporting the same behavior that it is affecting others as well. 

Try searching Launchpad for bug reports with the terms "lucid bug shutdown" and then some of the specifics you encounter. [https://bugs.launchpad.net/]("https://bugs.launchpad.net/")

You could also try Google, which usually provides a more familiar interface.

---

### Post by laidback on 2010-05-15
Bug 574331 is very similar but I don't end up at the login screen, for me nothing happens, I'm left at the desktop.

Bug 544191 is also similar.

---

### Post by laidback on 2010-05-16
If I "Switch User" I can Shut Down from the Login Screen. I cannot log out from the desktop.

Think I'll wait before I upgrade.

---

### Post by laidback on 2010-12-03
I think I now know what the problem is. It's because I have the OOo Quickstart available in the top panel. Remove that and things go back to normal.

---

