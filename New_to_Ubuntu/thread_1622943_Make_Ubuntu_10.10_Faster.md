---
title: "Make Ubuntu 10.10 Faster?"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by itrs on 2010-11-16
If there any possible way to accomplish this? I've heard Linux is like a billion times faster than Windows. I find it slow... it goes into this semi crash moments.

---

### Post by Peter09 on 2010-11-16
Depends what you are trying to do. There are always a set of 'pinch points' on a computer which slow it down no matter what O/S you are using - disk speed, network and internet speed, graphics card etc. As a normal user I would guess that you may see little difference in speed between Linux and Windows because in a modern machine compute power far exceeds a normal users requirements.
 
If you are seeing delays in graphics rendering it could be a mismatch between graphics card and driver.
 
Note that when an application is busy or waiting in Ubuntu its window is greyed out, is this what you are seeing perhaps.
 
Other than that you need to see what is keeping your system busy to cause the delay. Try installing htop.

---

### Post by NightwishFan on 2010-11-16
Linux (the kernel) is very very fast. A desktop distribution based on it, your milage may vary. Perhaps try using the LTS edition, Ubuntu 10.04. It is both fast, stable (in the more Debian definition of unchanging), and supported for a long time.

Though there are a few tweaks you can do to improve performance in a positive way. If you have around 1gb or more ram, install Preload. This will improve application loading times. It is easily found by searching "preload" in software center. You can them improve memory usage by doing the following:

1. Press alt+f2, a dialog box should come up. Type:
```
gksudo gedit /etc/sysctl.conf
```
2. Type your password when prompted, and a text file should come up. Scroll the whole way to the bottom of the file and add this on a new line to the bottom of the file:
```
vm.swappiness = 20
vm.vfs_cache_pressure = 50
```
3. Save the file, reboot and enjoy!

These tweaks should improve perceived performance of a Linux system towards desktop users.

---

### Post by TNT1 on 2010-11-16
> **NightwishFan said:**
> ur password when prompted, and a text file should come up. Scroll the whole way to the bottom of the file and add this on a new line to the bottom of the file:
```
vm.swappiness = 20
vm.vfs_cache_pressure = 50
```3. Save the file, reboot and enjoy!



Mine already had vm.swappiness = 10 and had a # infront of it.

---

### Post by NightwishFan on 2010-11-16
The # means it is commented out. You will have to remove the comment for it to take effect. 20 is a bit more conservative of a value than 10. I am sure either will do fine.

---

### Post by barbedsaber on 2010-11-16
linux IS a billion times faster than windows
just not all linux distros

I've had arch linux on a 900mhz CPU running rings around brand new laptops with windows 7 (of course it took me almost 2 weeks to set up, but that's another story)

the point I'm getting at is, gnome is big, and uses a lot of resources.
if you're struggling a bit with it, have a go at xfce. It's still really user friendly, but doesn't have quite the same requirments.

you can do this by either installing xubuntu, or downloading the package ```
xubuntu-destkop
```

and selecting xfce from GDM (that is, when you log in, select xfce)
personally, I would suggest installing xubuntu if you want to get a speed increase, far cleaner than adding tonnes of packages to an ubuntu install.

---

### Post by Megaptera on 2010-11-16
Sorry to barge in, but what does "vm.vfs_cache_pressure = 50" do? I've googled and found it suggested in various places but not clearly explained.

Thanks.

---

### Post by NightwishFan on 2010-11-16
It adjusts the amount of cache to use browsing the file system.

---

### Post by Megaptera on 2010-11-16
Thanks!!

---

### Post by wog on 2010-12-18
Is 50 more cache _pressure than default, or less?

What *are* the defaults for each of these?

---

### Post by beew on 2010-12-18
It could be your hardware. I have 10.10 on several computers and it is superfast. The specs vary, but it is fast even on  a modest laptop with only 1G of ram and single core 2Ghz processor.

---

### Post by akand074 on 2010-12-18
It's super fast on my computer :D Though at this point it's not a matter of the OS speed anymore..

---

### Post by NightwishFan on 2010-12-18
Defaults are vfs_cache_pressure=100 and vm.swappiness=60

---

