---
title: "GRUB - Need to get it to stop listing every kernel"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-29
Is there a way I can prevent the list of kernels from growing to infinity? It seems rather annoying since when I want to choose window, I must scroll all the way down to the bottom (there is no fast/1 key way that I know of).


Second, I am having problems with the newer kernel versions, so I choose to stay with a certain version. Is there a way I can default this version to be selected first?

---

### Post by Elfy on 2010-03-29
It depends entirely on which version of grub you are using as to how to actually do this. 

```
grub-install -v
``` will show you what you have.

For 1.x - check out this link [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

For 0.x then if you run 

```
cat /boot/grub/menu.lst
``` paste it here we can look at it.

To remove kernels search in synaptic for linux-image and mark the older kernels fro complete removal.

Startup manager will also allow you to choose which to boot I think and deal with grub kernel entries - [http://ubuntuforums.org/showpost.php?p=5112620&postcount=1](http://ubuntuforums.org/showpost.php?p=5112620&postcount=1)

---

### Post by dannyboy79 on 2010-03-29
what ubuntu are you running? do you know what grub you have installed. the old grub can be fixed easily. just use 
gksudo gedit /boot/grub/menu.lst
and then just read the config file for having a certain kernel be the default. 0 is the first kernel, and so on. so if you have 3 kernels installed and you wanted the 2 one to be the default, then the default choice number is 1. because kernel 1 is actually number 0 to grub.

as far as not showing all the kernels. if you're not going to use them again, just go into synaptic and remove them. that's the best solution. otherwise I believe again, there is an option for only showing so many current kernels in grub's menu.

this is all of course if you're using the old grub, if you have the new grub. I can't help ya.

---

### Post by itisbasi on 2010-03-29
Check out the Grub2 wiki.
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Rayve on 2010-03-30
Downloading startupmanager from Synaptic will let you choose a default kernel to boot into.

After you download and install, it will be under System > Administration > Startup-Manager.  

If you need to change kernels while booting up, press the Shift key as GRUB loads and you will get your list of kernels again.

---

### Post by Roger Allott on 2010-03-30
All of the responses you've had are good, but in my opinion the best (i.e. easiest over the long term) solution is to install Ubuntu-Tweak.

In there, you can clean up your system of unneeded kernels, as well as cleaning up your cache, configuration files and various other stuff.

---

### Post by jaycee23 on 2010-03-30
> **Roger Allott said:**
> All of the responses you've had are good, but in my opinion the best (i.e. easiest over the long term) solution is to install Ubuntu-Tweak.

In there, you can clean up your system of unneeded kernels, as well as cleaning up your cache, configuration files and various other stuff.

+1 for ubuntu-tweak - great piece of software!

---

