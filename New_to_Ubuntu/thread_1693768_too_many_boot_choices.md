---
title: "too many boot choices"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by wordmaster on 2011-02-23
I am running a dual boot with Ubuntu 10,04 and windows. When the computer starts, there is a large number of linux boot choices and it seems to keep growing. How can I get that down to one linux and one windows choice?

Thank you for your help.

---

### Post by Wtower on 2011-02-23
I found the following guide quite thorough:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Frogs Hair on 2011-02-23
The Ubuntu Tweak package cleaner works well for removing old kernels and has some other functions you might find useful .

---

### Post by Rubi1200 on 2011-02-23
GRUB Customizer is also a useful tool (with tutorial):
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by Kirboosy on 2011-02-23
+1 on [Ubuntu Tweak]("http://ubuntu-tweak.com/")

You can manually create a GRUB Conf but keep in mind you would have to edit everytime you updated to a new kernel. :)

---

### Post by tpjk on 2011-02-23
here's how to do it manually:

first, you need to find out which kernel version you are running. fire up a terminal and type ```
uname -r
```the output is going to be something like ```
2.6.32-28-generic
```now open up synaptic and in the quick search field, type linux-image-generic. (you might want to sort the results by name to find the different kernel versions faster.) scroll down to where all available installed kernel versions are listed; the names of the packages you need to look for all follow this pattern: linux-image-VERSION-generic (where VERSION is a sequence of digits like the one in the output of the uname -r command). you can then (completely) remove all kernel versions except for the one you're currently running. DO NOT, however, remove the package called linux-image-generic!!
just to be safe, check out the following screenshot:
[http://dl.dropbox.com/u/4831676/kernel-versions.png](http://dl.dropbox.com/u/4831676/kernel-versions.png)

hope this helps.:popcorn:

---

### Post by tpjk on 2011-02-23
PS: if you want to KEEP the different kernel versions and just don't want them LISTED as boot options during startup, you'll want to follow the suggestions made by everyone that posted before me. if you actually want to GET RID OF the old kernel versions, you should follow my instructions.

---

### Post by hansolo4949 on 2011-02-23
+1 Ubuntu tweak. I have found it to be very useful in cleaning out junk on Ubuntu, and cleaning out old kernels, which is your problem. Ubuntu tweak is the simplest option for you, unless you like using the terminal:). The Janitor (included with ubuntu under the administration menu in system) may also help, though sometimes the entries for the kernels doesn't get removed. 


To get Ubunut tweak, just google it, and it will be one of the top results. Enjoy!

---

