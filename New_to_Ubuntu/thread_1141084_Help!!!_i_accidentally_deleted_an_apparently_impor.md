---
title: "Help!!! i accidentally deleted an apparently important system file!"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-28
frustrated with wireless problems, (i have now reinstalled the ath9k drivers 12 times, failure every time. they USED to work, until i followed this guide: 
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)
(see first post made by volanin)

now it doesnt work anymore. so i followed his uninstall, which also failed miserably. 
desperate to rid my computer of this defective package, i searched in teh "included files" section of the auto-generated DEB

which **claims** to install a file in 
(some directory: i can no longer get to it anymore as the DEB has been deleted, the auto-DEB generator won't build a DEB anymore, and the linux file hierarchy is a tangled mess)

i deleted ath9k.ko    

is there anywhere that i can find/install this file again without nuking the OS?

---

### Post by asuastrophysics on 2009-04-28
nobody has any ideas where i could find ath9k.ko online?

well could someone possibly file host this for me real quick so i can put it back? :popcorn:

---

### Post by kpkeerthi on 2009-04-28
Follow the same guide and reinstall the driver.

---

### Post by asuastrophysics on 2009-04-28
solved: 
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

i tried reinstalling using his guide. failed. it kept asking for ath9k.ko ; 
which is in the "included files" tab of the DEB installer, but isn't actually installed. i love unofficial DEBS that don't work

bottom line, if you're a beginner,
(been using for 6 months, still have no clue how this OS works) 
don't follow anyone's guides. only look at official documentation. i just wish that google would display official docs first. 

i now have wireless, but same problems;

can't connect to my home network, it has no security but somehow the laptop gets disconnected from it. my WIFI has just gone through 20 networks and couldnt connect to any of them :(

---

