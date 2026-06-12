---
title: "Plain Ubuntu without any packages"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by crazyfuturamanoob on 2009-06-21
By default, Ubuntu has a lot stuff like Ekiga, OpenOffice, Evolution and games installed. I never use them. They just fill menus and hard disk and annoy me with their presence.

I want Ubuntu with only X-server and gnome, nothing else. So I could install just the packages and programs I need. What do you recommend?

---

### Post by x22 on 2009-06-21
start with the server edition--then add what you want.

---

### Post by Gen2ly on 2009-06-21
> **x22 said:**
> start with the server edition--then add what you want.

That'll do or you can remove the gnome desktop meta package (the meta package is a grouping of gnome applications) and prune from there.  I'd guess that either method take about the same time to reach your goal.

---

### Post by starcraft.man on 2009-06-21
Is that really necessary? I mean the standard install with all those extra programs you don't need is between 2-3 GB (or less). My current root is 5.0 GB and that's after I installed a huge load of AV and other graphical apps. By comparison, the average HDD today is what, 300 to 500 GB? Even if you have an ancient HDD it shouldn't take up much space, I still have a prehistoric IBM Deskstar drive that's 60 or 120 GB, even on that the space used by root would be insignificant. The majority of anyone's drive is always occupied by files (i.e. video, music, pictures, podcasts).

Just saying, if you really can't live with em wasting space follow x22's suggestion. You can always stop them from showing in the menu by right clicking on Applications and deselecting whole folders you don't want.

---

### Post by master_kernel on 2009-06-21
Or you could use the alternate install CD and choose the sets of software you want.

---

### Post by crazyfuturamanoob on 2009-06-21
Yes, this is absolutely unnecessary. I can still use Ubuntu, those apps don't matter. But I'm going to do a fresh install, so why not?

I can't just hide them from menu because they still exists haunting me. Server edition comes with Apache and other server programs I don't want. 

But I will try server edition unless you tell me why "alternate install CD" is better and where to get it.

---

### Post by Cheesemill on 2009-06-21
I've found that the best way to do a minimal install is the following (I've done it several times myself):

Install a minimal CLI system using the alternate install CD.
Don't select anything at the 'Select packages' screen.
When you've booted into your new install, just do the following:
```
sudo aptitude update && sudo aptitude -y full-upgrade && sudo aptitude -y install xorg && sudo aptitude -y install gdm gnome-core ubuntu-artwork fast-user-switch-applet && shutdown now -r
```This will give you the smallest install possible, just add what you want from here.
Bear in mind that this won't give you any applications at all, good ones to start off with installing are firefox and synaptic.


Edit - Instead of the Alternate Install CD you can go for the 9.04 Mini CD. It's only 10MB as it retrieves the current versions of all packages from the internet during install. This way you start off with a fully up to date system from the moment you've installed.

Edit 2 - If you want a graphical boot screen instead of all the scrolling text messages, install *usplash* and *usplash-theme-ubuntu* as well.

---

### Post by kansasnoob on 2009-06-21
Well, you CAN install Ubuntu minimal:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

And then install whatever desktop you choose.

I've tried a lot of things this way, recently my primary focus has been on installing a virgin Gnome desktop on Ubuntu minimal, but I always run into problems with sound and or X.

I've been playing with Debris Linux and it's great fun, but far from stable!

The bottom line is that Ubuntu is based on Debian so you can go as far back as you please in development and build up from there - until your brain explodes!

---

### Post by Cheesemill on 2009-06-21
> **kansasnoob said:**
> I've tried a lot of things this way, recently my primary focus has been on installing a virgin Gnome desktop on Ubuntu minimal, but I always run into problems with sound and or X.

I used to have problems with X as well until I learnt that the best thing to do is install xorg first, **by itself**, before installing your desktop environment.

To the OP. Other packages you'll probably want to install are:

gnome-system-tools  -  Contains tools such as Date & Time, Users & Groups, Network Configuration
gnome-volume-manager  -  Speaks for itself
jockey-gtk  -  Hardware Drivers front-end

---

### Post by kansasnoob on 2009-06-21
Installing the newest xorg first is an excellent idea! Why didn't I think of that????????????

Thank you!

---

### Post by Bachstelze on 2009-06-21
Just to clarify a few things:

Ubuntu without any packages is impossible. The kernel is in a package, Bash is in a package, Apt is in a package, etc. *Everything* is in a package. No packages = nothing.

> **Cheesemill said:**
> 

When you've booted into your new install, just do the following:
```
sudo aptitude update && sudo aptitude -y full-upgrade && sudo aptitude -y install xorg && sudo aptitude -y install gdm gnome-core ubuntu-artwork fast-user-switch-applet && shutdown now -r
```This will give you the smallest install possible, 

Since you added stuff, it can't be the "smallest install possible", since it was even smaller before. Even right after you installed with a minimal CD, there are a few unnecessary things.

---

### Post by ugm6hr on 2009-06-21
For Intrepid, but should apply to Jaunty too:
[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

---

### Post by Cheesemill on 2009-06-22
> **HymnToLife said:**
> Just to clarify a few things:
 
Ubuntu without any packages is impossible. The kernel is in a package, Bash is in a package, Apt is in a package, etc. *Everything* is in a package. No packages = nothing.
 
 
 
Since you added stuff, it can't be the "smallest install possible", since it was even smaller before. Even right after you installed with a minimal CD, there are a few unnecessary things.
 
OK then. What I meant to say was
 
The smallest install possible that fulfilled all of the OP's criteria :)

---

### Post by crazyfuturamanoob on 2009-06-22
> **kansasnoob said:**
> Well, you CAN install Ubuntu minimal:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

And then install whatever desktop you choose.

I've tried a lot of things this way, recently my primary focus has been on installing a virgin Gnome desktop on Ubuntu minimal, but I always run into problems with sound and or X.

I've been playing with Debris Linux and it's great fun, but far from stable!

The bottom line is that Ubuntu is based on Debian so you can go as far back as you please in development and build up from there - until your brain explodes!

> **Cheesemill said:**
> I've found that the best way to do a minimal install is the following (I've done it several times myself):

Install a minimal CLI system using the alternate install CD.
Don't select anything at the 'Select packages' screen.
When you've booted into your new install, just do the following:
```
sudo aptitude update && sudo aptitude -y full-upgrade && sudo aptitude -y install xorg && sudo aptitude -y install gdm gnome-core ubuntu-artwork fast-user-switch-applet && shutdown now -r
```This will give you the smallest install possible, just add what you want from here.
Bear in mind that this won't give you any applications at all, good ones to start off with installing are firefox and synaptic.


Edit - Instead of the Alternate Install CD you can go for the 9.04 Mini CD. It's only 10MB as it retrieves the current versions of all packages from the internet during install. This way you start off with a fully up to date system from the moment you've installed.

Edit 2 - If you want a graphical boot screen instead of all the scrolling text messages, install *usplash* and *usplash-theme-ubuntu* as well.

> **ugm6hr said:**
> For Intrepid, but should apply to Jaunty too:
[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

Many ways to do it. Which is the best? Also, I want to use my two 320 Gb HD's as one HD with RAID0.

---

### Post by Cheesemill on 2009-06-22
Obviously it all comes down to personal preference, but I've found that my way gives you an install that is recognisably Ubuntu but without all of the apps that you would find on a standard install.

If you want to switch to Debian instead of Ubuntu then go for it, after all personal choice is one of the big attractions of open source software.

The DistroWatch link that ugm6hr posted is basically the same method that I use, but it talks you through extra packages that you may need. It's just goes into more detail where i said 'just add what you want from here'. In fact alot of the how-to is redundant if you take my route and install gnome-core, this is because it is just a meta-package which contains the following:
```
gnome-control-center
gedit
gnome-applets
gnome-icon-theme
gnome-menus
gnome-panel
gnome-session
gnome-settings-daemon
gnome-terminal
metacity
nautilus

```as well as a couple of others, if you search for gnome-core in synaptic then right-click > Properties you'll see what I mean.

The PsychoCats tutorial is also very good (I've used it myself), but is intended more for low spec machines that struggle with running Gnome, it uses IceWM instead. If you want an install that looks and feels like regular Ubuntu and your machine easily meets the minimum specs then you obviously want Gnome as your window manager.

As for software RAID 0, I've never used it as all of my RAID setups have been with hardware, but there are loads of threads on these forums as well as other how to guides on the internet that will explain it to you.

I'd suggest using VirtualBox or another VM solution and trying all the methods out yourself before deciding which suits you the best :)

---

### Post by LowSky on 2009-06-22
I'll make a suggestion, use another distro. For instance Arch linux... this way you get a minimal install and get to learn more about linux.

---

### Post by Cheesemill on 2009-06-22
+1 for Arch (but only if you're up for a challenge!!!!!)

---

### Post by DGortze380 on 2009-06-22
> **crazyfuturamanoob said:**
> Server edition comes with Apache and other server programs I don't want. 


Only if you select it during the install.

---

### Post by LowSky on 2009-06-22
> **Cheesemill said:**
> +1 for Arch (but only if you're up for a challenge!!!!!)

what challenge? their website has one of the best guids for setting up the operating system, sure its a good long process, but you end up with a great customizable end product

---

### Post by Cheesemill on 2009-06-22
> **LowSky said:**
> what challenge? their website has one of the best guids for setting up the operating system, sure its a good long process, but you end up with a great customizable end product

It's only to be recommended if you're comfortable with the terminal, I wouldn't suggest it to someone as their first linux distro that's for sure :) (I'm an Arch user myself).

---

### Post by Paqman on 2009-06-22
Debian also offers a netinstall that can build you nice usable system without lots of junk.

---

### Post by crazyfuturamanoob on 2009-06-23
I tried DistroWatch.com instructions with 9.04 amd64 alternate CD.  It failed to configure network automatically, and I can't configure it manually. Partitioning: Too many options, fields, settings and flags in manual configuration. Aborted installation.

---

### Post by ugm6hr on 2009-06-23
> **crazyfuturamanoob said:**
> I tried DistroWatch.com instructions with 9.04 amd64 alternate CD.  It failed to configure network automatically, and I can't configure it manually. Partitioning: Too many options, fields, settings and flags in manual configuration. Aborted installation.

If an Advanced install is too complex for you, just stick with the default.  Or be prepared to do some research for yourself.

---

### Post by crazyfuturamanoob on 2009-06-24
Ok. I give up. Too complex. :(

---

