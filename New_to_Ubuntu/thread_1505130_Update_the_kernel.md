---
title: "Update the kernel"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by tmette on 2010-06-08
Ok, I'm still considering myself a newbie at this stuff, so here it goes.

I noticed the Update manager has downloaded the newer kernel (currently running 2.6.32-22-generic).  However, it never applies it.  From doing research on the forums, I'm guessing I have to select it at the Grub menu?  From then on will it boot into the new kernel?

Also, I don't get a Grub menu because Ubuntu is the only OS on this machine (Meerkat Ion from Sys76).  I've tried holding down Shift on a restart, but it still boots to the login screen.  I would actually like to see the Grub on every boot-up if possible.  I'm assuming to do this I have to edit the /etc/default/grub file in the Terminal?  If so can someone help explain it to me?  I've been reading over [this guide]("http://ubuntuforums.org/showthread.php?t=1195275"), but still kind of fresh at this and want to be sure.  I don't want to go screwing up the Grub! :p

Also, what is the real advantage of upgrading the grub?

---

### Post by tim48134 on 2010-06-08
Hi, fellow n00b here! Ok, to change some options for grub with a fancy  GUI, install 'startupmanager' from Synaptic, or using apt-get. The kernel  upgrade issue, I am not sure what you mean by it never applies it. If  the updates install successfully and it boots directly into Ubuntu, then  it should be using the newer kernel. You can always check by opening a terminal and running "uname -r". Hope this helps!

---

### Post by tmette on 2010-06-08
> **tim48134 said:**
> Hi, fellow n00b here! Ok, to change some options for grub with a fancy  GUI, install 'startupmanager' from Synaptic, or using apt-get. The kernel  upgrade issue, I am not sure what you mean by it never applies it. If  the updates install successfully and it boots directly into Ubuntu, then  it should be using the newer kernel. You can always check by opening a terminal and running "uname -r". Hope this helps!

Thanks for the info!  I'm sure it is the new kernel and I've just got my numbers confused.  I will install the Startup Manager tool.

---

### Post by Paqman on 2010-06-08
You can check which kernel you're booted up into using the following command in a terminal:
```
uname -r
```

If you're booted up into the latest (which you should be by default) then you can just go ahead and uninstall the earlier kernels using Synaptic. Filter for "linux-image", but make sure you leave the current one installed. Some people like to leave two kernels on their machine at all times, but if the current one is booting and working ok I don't see the point. Uninstalling old kernels will free up a lot of disk space, too.

---

### Post by nhasian on 2010-06-08
if for some reason when you install a newer kernel and it doesnt automatically set it up for you, you can simply run from a terminal:

```
sudo update-grub
```

Want to install the latest stable kernel 2.6.34?  see my post [here]("http://www.uluga.ubuntuforums.org/showpost.php?p=9348970&postcount=8")

---

