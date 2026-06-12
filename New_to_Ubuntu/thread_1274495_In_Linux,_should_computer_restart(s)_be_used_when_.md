---
title: "In Linux, should computer restart(s) be used when applications are removed?"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by mikodo on 2009-09-24
Hello everyone,

When I was using MS; it was recommended doing two computer restarts after removing a "program" to completely purge all dependencies. In Ubuntu using either Applications -> Add/remove or  sudo apt-get --purge remove "application"; is it also recommended doing a couple of restarts after? My guess it is probably not necessary with GNU/Linux, but I don't know for sure.

Thanks.

---

### Post by drs305 on 2009-09-24
No. If you need to restart anything, the system will tell you. This isn't Windows ;-)

---

### Post by Finalfantasykid on 2009-09-24
I think the dependencies will still be there, but there are other easier ways to get rid of them.

```
sudo apt-get autoremove
``````
sudo apt-get clean
``````
sudo apt-get autoclean
```Then you can also go over to synaptic package manager and delete everything under 'residual config' (I think that is what it is called, I'm not on Ubuntu at this moment).

Then you can also download the program...

```
sudo apt-get install gtkorphan
```You should be able to get rid of everything in the orphaned tab.  
[quote=http://www.marzocca.net/linux/gtkorphan.html] At GtkOrphan's first run, you should initialize your system in order to keep track of needed packages, even if they are reported as orphaned.
In the main window, expand the "Options" section and check the "Show all orphan packages, not only those in the libs section" checkbox. Note: with this option, GtkOrphan will report as "orphaned" all those installed packages that are not dependencies for any other. In this way, for instance, packages such as gparted, ubuntu-desktop, wine will be listed too, as they are "top-level" packages and no other package depends on them. Now you can traverse this list and right-click->hibernate each package you want to keep and that you don't want to be reported as orphaned anymore. The hibernation list will keep these files and will not show them anymore. You can access and modify the hibernation list as you want, from the View menu or from the right-click popup menu. 
[/quote]

If you have never done this before, or have not done all this stuff in a while, you can probably free up a gig or two from your harddrive...

---

### Post by mikodo on 2009-09-24
Thanks folks. I get to play some more and clean up my Ubu at the same time!

Mike

---

### Post by rakete on 2009-09-25
yeah, playing with the system is the best and funniest way to learn linux... but always be aware that things can break apart when playing around (always backup your sensitive data) :)

Have Fun!

---

### Post by scorp123 on 2009-09-25
> **mikodo said:**
> In Ubuntu using either Applications -> Add/remove or  sudo apt-get --purge remove "application"; is it also recommended doing a couple of restarts after? Pointless exercise.

Another pointless exercise many Windows-converts do is to de-install and install a program again and again if it misbehaves. That too won't do anything here. It would be better to check your config files in /etc and your settings underneath your own /home directory and watch for error messages a program might produce.

The only reason why a Linux system should require a reboot is when update the kernel or if you have failing hardware ... or a system freeze (can happen on some hardware).

---

### Post by LowSky on 2009-09-25
> **mikodo said:**
> Hello everyone,

When I was using MS; it was recommended doing two computer restarts after removing a "program" to completely purge all dependencies. 
Thanks.

I have never heard of doing 2 restarts after removing an application in windows. Very few even need one restart.

---

### Post by mikodo on 2009-09-25
> **Finalfantasykid said:**
> I think the dependencies will still be there, but there are other easier ways to get rid of them.

```
sudo apt-get autoremove
``````
sudo apt-get clean
``````
sudo apt-get autoclean
```Then you can also go over to synaptic package manager and delete everything under 'residual config' (I think that is what it is called, I'm not on Ubuntu at this moment).

Then you can also download the program...

```
sudo apt-get install gtkorphan
```You should be able to get rid of everything in the orphaned tab.  


If you have never done this before, or have not done all this stuff in a while, you can probably free up a gig or two from your harddrive...

Thanks; Fun exercise and I got rid of the residual stuff.

To other posters: Thanks for the increased knowledge of GNU/Linux and advice.

Mike

---

