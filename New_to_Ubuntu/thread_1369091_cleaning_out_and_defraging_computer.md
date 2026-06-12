---
title: "cleaning out and defraging computer"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by mlitman3577 on 2009-12-31
I am new to linux. I need to know how to clean out my coputer and defrag it. How do you do this on Ubuntu?

---

### Post by Captain_tux on 2009-12-31
There really isn't such a thing as "defrag" with Linux... What is it that you wish to accomplish?

---

### Post by QIII on 2009-12-31
"Defragging" as you know it is generally not necessary with Linux because the file system is entirely different.

What do you mean by cleaning up?

---

### Post by gabo.cr on 2009-12-31
Yes, defrag doesn't exist in Linux.
But you could clean it a bit using this command in terminal:

```
sudo apt-get autoclean
```

---

### Post by mlitman3577 on 2009-12-31
Well I would think that everything I do goes into a file, and you would need to clean it up otherwise the computer will slow down. Like on windows how you empty your temp files.

---

### Post by bkratz on 2009-12-31
Information regarding "defragging"

[http://ubuntuforums.org/showthread.php?t=1298370&highlight=defrag](http://ubuntuforums.org/showthread.php?t=1298370&highlight=defrag)

---

### Post by danastasio on 2009-12-31
Temp files in linux are just that. They are created and destroyed all the time. Every shutdown, the /tmp folder is cleared out. The file system that you are most likley using (ext4) does fragment. Saying that a FS does not fragment is foolish, however, the rate of fragmentation is -extremley- low. Say 1 fragmented file per 100,000. Generally there is no need to "defrag" your computer and it will not slow down over time. If however, you find that your computer is not booting because of some filesystem error, you can boot into the recovery console provided with grub, (hold down shift and choose the second option) and run the following.

```
e2fsck -fvP
```

this will find any errors and correct them. Generally speaking, I run this once a year and almost never find any problems.

Windows != Linux and they do not share each others problems. There is also no registry in linux and as such you will never have to clean that out! 

Given time you will understand this better.

---

### Post by Paqman on 2009-12-31
A Linux filesystem on a desktop machine is pretty unlikely to get fragmented to the point it will really affect performance. About the only time it'll happen is if your routinely operate with the drive over 90% full.

As for cleanups, there's always Computer Janitor. Double check that you're ok with it uninstalling things before you hit the ok button though.

Overall Linux desktops tend to require a lot less maintenance than Windows does, which is one of my favourite things about it.

---

### Post by ssulaco on 2009-12-31
from the terminal run 
```
sudo apt-get autoclean
```
 Clean up  partial package
```
sudo apt-get clean
```
Clean up  the apt cache
```
sudo apt-get autoremove
```
Clean up  any unused dependencies
```
sudo apt-get autoremove application-name
```
use the autoremove command whenever you want to uninstall an application.


Read this for a how to "Get rid of old residual config package"
[http://www.ehow.com/how_2251696_clean-up-packages-ubuntu.html](http://www.ehow.com/how_2251696_clean-up-packages-ubuntu.html)
also you might try Bleachbit...its in the repos,Ive had real good luck with it,read the documentation here:
[http://bleachbit.sourceforge.net/documentation](http://bleachbit.sourceforge.net/documentation)
I would install it using synaptic from the repos,if you do decide to try it .....DO NOT check "places" under Firefox,it will wipe your bookmarks out
You should never have to defrag your system
[http://linux-sxs.org/housekeeping/frag.html](http://linux-sxs.org/housekeeping/frag.html)

---

### Post by ElevenWarrior on 2009-12-31
> **ssulaco said:**
> from the terminal run 
```
sudo apt-get autoclean
```
 Clean up  partial package
```
sudo apt-get clean
```
Clean up  the apt cache
```
sudo apt-get autoremove
```
Clean up  any unused dependencies
```
sudo apt-get autoremove application-name
```
use the autoremove command whenever you want to uninstall an application.


Read this for a how to "Get rid of old residual config package"
[http://www.ehow.com/how_2251696_clean-up-packages-ubuntu.html](http://www.ehow.com/how_2251696_clean-up-packages-ubuntu.html)
also you might try Bleachbit...its in the repos,Ive had real good luck with it,read the documentation here:
[http://bleachbit.sourceforge.net/documentation](http://bleachbit.sourceforge.net/documentation)
I would install it using synaptic from the repos,if you do decide to try it .....DO NOT check "places" under Firefox,it will wipe your bookmarks out
You should never have to defrag your system
[http://linux-sxs.org/housekeeping/frag.html](http://linux-sxs.org/housekeeping/frag.html)
thanks didn't know about all those commands.

---

