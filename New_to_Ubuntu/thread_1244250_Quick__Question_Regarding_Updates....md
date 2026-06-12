---
title: "Quick  Question Regarding Updates..."
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-08-19
The update manager has been coming up a lot lately, and I've been faithfully installing the updates one after the other, even if I don't QUITE get what they're for.  But are all these updates piling on top of one another and taking up unnecessary room on my HD?  Or do they overwrite earlier programs?

---

### Post by philinux on 2009-08-19
The updates dont pile up. They upgrade packages to newer versions. Most of the time taking no more space than before.

Also look at the man pages for apt. ```
man apt-get
``` and the wiki for info.
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

In the file system look in /var/cache/apt/archives

Running 

```
sudo apt-get autoclean
```

or clean will remove cruft.

---

### Post by Paddy Landau on 2009-08-19
Sometimes, the update gives you a new kernel. The old kernels remain in place. Once you've booted successfully into the new kernel, you can safely delete all but the latest two kernels.

Here are some instructions to clean up.

[LIST=1]
[*]Uninstall old kernels as follows.
[LIST]
[*]Get your system up-to-date.
[LIST]
[*]Open Synaptic Package Manger (*System > Administration > Synaptic Package Manager*).
[*]Press *Reload* at the top.
[*]Press *Mark all Upgrades* at the top.
[*]If not shaded out, press *Apply* at the top.
[/LIST]
 
[*]Remove old kernels.
[LIST]
[*]On the left near the bottom, select *Status*.
[*]On the left near the top, select *Installed*.
[*]On the right, scroll down to *linux-headers*.
[*]Note the version numbers, which look something like *linux-headers-2.6.24-23*. You want to find the latest two versions (with the biggest numbers) and leave them alone. All older versions (with the smallest numbers) you right-click and *Mark for Complete Removal*. **N.B. Do this only for packages called *linux-headers*.**
[*]Repeat the last step for packages called *linux-restricted-modules*, *linux-image* and *linux-ubuntu-modules* (you may not have the last one).
[*]Press *Apply* at the top.
[/LIST]
 
[/LIST]

[LIST]
[*]Close Synaptic Package Manager
[/LIST]
 
[*]Go to terminal (Applications > Accessories > Terminal).
[*]Type the following command.```
sudo apt-get clean && sudo apt-get autoremove
```
[/LIST]
There is a small possibility that you'll need to reboot.

But as the Linux system is so much smaller than Windows, it probably won't make much difference to you unless you are tight on space.

---

