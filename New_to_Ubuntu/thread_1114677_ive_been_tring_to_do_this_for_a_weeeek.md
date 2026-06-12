---
title: "ive been tring to do this for a weeeek"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by trig on 2009-04-03
im tring to install a genius tablet using the tutorial from [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html). it says to save a file here.... Miriad have provided a precompiled driver for Hardy and can be obtained from [http://specificcrap.arbitrarycrap.com/wizardpen_drv.so](http://specificcrap.arbitrarycrap.com/wizardpen_drv.so). Just download the driver and put it in /usr/lib/xorg/modules/input/... where is that folder at. i can not find it to save the package to it. plaase help...

---

### Post by spiderbatdad on 2009-04-03
As a normal user, you will not be able to save a file to a system directory like that. You would have to save to your desktop or home, then, as admin, using root permissions, make the file owned by root, and move the file to /usr/lib/xorg/modules/input. This can be done easily from the command line or graphically by running nautilus as root, ie., ```
gksu nautilus.
```

Perhaps option 2 is easier? Have you tried options 2?

---

### Post by trig on 2009-04-03
i am right now

---

### Post by trig on 2009-04-03
when i tried it, i got this daffy@daffy-desktop:~$ gksu nautilus.

(gksu:14517): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
daffy@daffy-desktop:~$ tar -zxvf wizardpen-0.6.0.alpha1.tar.gz
tar: wizardpen-0.6.0.alpha1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
daffy@daffy-desktop:~$ tar -zxvf wizardpen-0.6.0.2.tar.gz

---

### Post by spiderbatdad on 2009-04-03
ok. You can extract (untar) the package by right clicking on it and selecting, extract here. The reason you got error "no such package" I suspect is because the package is on your Desktop (capitol D) When using the terminal you need to be in the correct directory. The terminal open in your home directory. To change to desktop:
```
cd Desktop
```To change directly to the folder you extract:
```
cd Desktop/foldername
```The tab key will help you auto complete folder names.

If you go to desktop first...then the next cd would simply be into foldername... not Desktop/foldername

---

### Post by hyper_ch on 2009-04-03
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by trig on 2009-04-03
it is starting to install im on the 3rd step
thanks

---

### Post by trig on 2009-04-03
wizardpen.c:88: warning: data definition has no type or storage class
wizardpen.c:90: warning: data definition has no type or storage class
wizardpen.c:92: warning: data definition has no type or storage class
wizardpen.c:95: warning: data definition has no type or storage class
wizardpen.c:97: warning: data definition has no type or storage class
wizardpen.c: In function 'DeviceInit':
wizardpen.c:662: warning: passing argument 3 of 'InitValuatorClassDeviceStruct' makes integer from pointer without a cast
wizardpen.c:662: error: too many arguments to function 'InitValuatorClassDeviceStruct'
make[2]: *** [wizardpen.lo] Error 1
make[2]: Leaving directory `/home/daffy/wizardpen-0.7.0-alpha1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/daffy/wizardpen-0.7.0-alpha1'
make: *** [all] Error 2
daffy@daffy-desktop:~/wizardpen-0.7.0-alpha1$ 
....not sure what that means...

---

### Post by spiderbatdad on 2009-04-03
did you do step 3 before try to compile the package?
```
sudo aptitude install xutils libx11-dev libxext-dev build-essential xautomation xinput xserver-xorg-dev
``` You can run this command again. Make sure all packages install.

---

