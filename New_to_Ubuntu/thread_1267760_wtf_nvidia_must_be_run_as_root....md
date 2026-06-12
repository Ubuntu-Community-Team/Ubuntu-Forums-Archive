---
title: "wtf nvidia must be run as root..."
date: 2009-09-16
forum: New to Ubuntu
---

### Post by I WILL DO IT on 2009-09-16
am trying to run a .run file....

---

### Post by Paqman on 2009-09-16
What are you actually trying to do? Install Nvidia drivers? If so, go to System > Admin > Hardware drivers and use that to install.

---

### Post by Mike_IronFist on 2009-09-16
> **I WILL DO IT said:**
> am trying to run a .run file....

Oooh. Installing the NVIDIA drivers downloaded from the website requires a little bit of advanced knowledge. Don't try to do that unless you're sure you can't use the drivers from "System -> Administration -> Hardware Drivers"

---

### Post by nhasian on 2009-09-16
i also suggest using the built in nvidia drivers.  if you _do_ want to install the binary drivers from nvidia's website you have to do a few things.  this is from memory so i hope i dont miss any steps:

1) mark the .run file as executable with chmod +x
2) press ALT-Control-F2 to drop to a terminal
3) stop the graphical display with:

```
sudo /etc/init.d/gdm stop
```

4) then run your nvidia installation script.  
5) return to the gnome desktop with:

```
sudo /etc/init.d/gdm start
```

not too difficult but the cumbersome thing is you have to redo the nvidia driver every time you update the kernel.

---

### Post by Mike_IronFist on 2009-09-17
> **nhasian said:**
> i also suggest using the built in nvidia drivers.  if you _do_ want to install the binary drivers from nvidia's website you have to do a few things.  this is from memory so i hope i dont miss any steps:

1) mark the .run file as executable with chmod +x
2) press ALT-Control-F2 to drop to a terminal
3) stop the graphical display with:

```
sudo /etc/init.d/gdm stop
```

4) then run your nvidia installation script.  
5) return to the gnome desktop with:

```
sudo /etc/init.d/gdm start
```

not too difficult but the cumbersome thing is you have to redo the nvidia driver every time you update the kernel.

I think you should note that the command to run the nvidia script is "sh name.run" (without the quotes), that the user must pick YES when asked to update their X config file, and that rebooting is safer than trying to restart gdm while the system is still running.

Oh yeah, and if the script is copied to your home folder, IWILLDOIT, you can just enter in the name of it, you don't have to enter the path to it.

---

### Post by nhasian on 2009-09-17
i dont remember having to type sh before the command.  i just did ./xxx.run whatever the version of the display driver was...  anyway yeah your right, probably best to reboot with:

```
sudo shutdown -r now
```

anyway, not bad from memory eh?  I last did that back when i was running 8.04 before 8.10 came out.  ever since I upgraded to 8.10 and beyond i always just used the drivers from the repos.

> **Mike_IronFist said:**
> I think you should note that the command to run the nvidia script is "sh name.run" (without the quotes), that the user must pick YES when asked to update their X config file, and that rebooting is safer than trying to restart gdm while the system is still running.

Oh yeah, and if the script is copied to your home folder, IWILLDOIT, you can just enter in the name of it, you don't have to enter the path to it.

---

