---
title: "ubuntu won't start"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by framos on 2009-06-06
So a couple of days ago I installed ubuntu and it was working great so I started installing packages to check out what I can do (couple of games, video editing, etc.) then I tried to install a package (which I don't remember what it was called) so that my graphic card would work better.

Thing is the package didn't work as I wanted it to and now I can't even start up ubuntu. When I try turning it on the screen goes black and it stops working. I was able to get the command line up to check what packages I had installed so that I could uninstall the one that broke my ubuntu. Is there any way to check which one is the latest packages that were installed?? Or check what day packages were installed??

I have been looking around and have not been able to find anything. Thanks :D

---

### Post by shifty_powers on 2009-06-06
have you tried booting into the recovery console and selecting fix graphical problems?

---

### Post by Crafty Kisses on 2009-06-06
We need a lot more information than this. First off what kind of video card do you have? Now you mentioned you can't remember what package you installed for your video card, but by any chance was it Envy, or did you just install the ATI or nVidia drivers from Synaptic? We need to figure out what kind of graphics card you have first I'll get to that here. Now this could be a X issue, so try reconfiguring your X server and running this other command to figure out what graphics card you have:
```
lspci
sudo dpkg-reconfigure xserver-xorg
```
Now once you run that it will ask you a bunch of questions, if you're not sure about a question just answer it to the best of your ability. Then you need to reboot, and then try to boot into Ubuntu again, and hopefully you have a running GUI, but if you don't post back and I'll help you further.

---

