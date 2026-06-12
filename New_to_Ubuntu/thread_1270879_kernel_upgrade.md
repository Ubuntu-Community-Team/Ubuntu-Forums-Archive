---
title: "kernel upgrade"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by manners2345 on 2009-09-20
I am currently downloading the latest upgrade for Ubuntu for the  kernel, headers and such. If like the previous several months, it will say it is upgraded. but if I look at the menu list nothing is there except the old one, 2.6.24-23. how do I get the menu list to update so the current one is there
thank you in advance
manners2345

---

### Post by Liolikas on 2009-09-20
In Ubuntu like disro it should happen automatically but if not so small problem.

Just look inside boot with:
ls /boot
You see new kernel? Good.
Now:
sudo gvim /boot/grub/menu.lst
And then you will see block of settings for each kernel. Just copy-paste one block and change numbers in pasted one to same what you saw in ls /boot. Be carefull not to make mistakes! Because in rare case of very bad mistake you will have to manually enter grub commands to boot (not adviced) or just fix file from livecd.

---

### Post by manners2345 on 2009-09-20
I am presuming I do this in a terminal.

I get 2 responses

unable to resolve host

givm no such command


manners2345

---

### Post by Liolikas on 2009-09-20
gvim is text editor one of my favorites. Try something else like gedit.

---

### Post by mathfeel on 2009-09-20
> **manners2345 said:**
> I am presuming I do this in a terminal.

I get 2 responses

unable to resolve host

givm no such command


manners2345
It's "gVIm" (all lower case).

I believe if you do upgrade a kernel image and its modules, dpkg_configure would reset menu.lst for you. You probably should run the package manager and see which kernel versions are installed. If you want to know which version you are running, run the command
```
uname -a
```

---

### Post by manners2345 on 2009-09-22
sorry for the late reply,at my age, 70+ I sometimes get hit with extreme case of CRS. In other words I forgot I was doing this, SORRY

that uname -a command shows I am running 2.6.24-23

going to synaptic shows 3 generic kernels installed,the latest 2.6.24.24-26

how do I do a dpkg_config

---

### Post by Zoot7 on 2009-09-22
They're just patches to the same kernel version eg. 2.6.24-23 or 2.6.24-24. 

If you want to upgrade the kernel to the latest version (2.6.31) a good app to check out is kernelcheck:
**[http://kcheck.sourceforge.net/]("http://kcheck.sourceforge.net/")**
I recently used it on Jaunty to upgrade to 2.6.31. :)

---

### Post by manners2345 on 2009-09-23
I think I have SOLVED my problem, at least partially. I just did a copy an pastefrom menu list to menu list changing the 23 numbers to 24, then did a save. 

according to uname -a I am now running a different kernel

---

