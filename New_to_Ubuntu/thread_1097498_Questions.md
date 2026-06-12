---
title: "Questions???"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by EJIbarra95 on 2009-03-16
Hello guys! I'm new to this forum. I am running Intrepid Ibex on a USB bootable device as instructed by pendrivelinux.com. Okay, for the questions:

1.) I can't install nVidia drivers. Everytime I go to System > Administration > Hardware Drivers, I activated nVidia on the list, then it downloads the driver but a while later, an error occured. 

2.) I installed Ubuntu (finally) using Wubi. It worked fine. I booted with Ubuntu, a loading bar in a window appeared, then a while later, it is stops in 82% and won't move. I tried it again. The same problem occured.

Thanks in advance. :)

---

### Post by leonardo_neo on 2009-03-16
> 
2.) I installed Ubuntu (finally) using Wubi. It worked fine. I booted with Ubuntu, a loading bar in a window appeared, then a while later, it is stops in 82% and won't move. I tried it again. The same problem occured.


I don't know answer for your first question. But for your second question, I have noticed that during installation when it is somewhere near 80%, it take some time to progress further.....How much time did you give for installation? Usually it take 20 mins for complete installation. Did you wait at least for 30 mins??

---

### Post by hyper_ch on 2009-03-16
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by orethrius on 2009-03-16
If I remember correctly, the nVidia driver issue is directly related to the ATi driver issue; that is to say, the current version of X.Org in Ibex doesn't support direct (3D) rendering on either chipset, and should be fixed by the time Jaunty releases (or in X.Org 5.2 if somebody wants to put the effort into running that on current systems).

---

