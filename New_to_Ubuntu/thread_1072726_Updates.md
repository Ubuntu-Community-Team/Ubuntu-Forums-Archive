---
title: "Updates?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by R@inm@n on 2009-02-17
Hello again...
I have two HDD's in my computer, one runs Win XP and the other has Ubuntu...two OS on two separate drives.

My question concerns updates to the Ubuntu OS. Almost every time I log onto Ubuntu I get new updates to download. The Grub screen has a list of the different releases when I boot into Ubuntu about 9 inches long. I don't mind updates, but I seem to be getting an awful lot of them. Do I have a setting wrong somewhere causing this to happen?  I feel like a developer...heheheh... so many updates.

R.

---

### Post by Ms_Angel_D on 2009-02-17
Hi,

No your not doing anything wrong. Unlike windows ubuntu's updating program also updates your installed software, so when ever there is an update to any software, plus any security or ubuntu updates you will be notified of the updates.

How often do you boot into ubuntu and what version are you using? Have you been updating from previous versions of ubuntu to new versions, if so that could explain the "list" your referring to.

---

### Post by R@inm@n on 2009-02-17
I usually boot into Hardy Heron a few times per week. As far as I know, i'm running the latest release.  I'm currently writing this in XP.


R.

---

### Post by spcwingo on 2009-02-17
Those extra entries you see are extra kernels.  You can remove the old ones, but I suggest keeping at least one old one around in case the current install gets bricked somehow.  To remove just open up synaptic and search for linux-image.

---

### Post by drs305 on 2009-02-17
> **R@inm@n said:**
> The Grub screen has a list of the different releases when I boot into Ubuntu about 9 inches long. I don't mind updates, but I seem to be getting an awful lot of them. Do I have a setting wrong somewhere causing this to happen?

As spcwingo mentioned, the easiest way to reduce the number of kernel options displayed is to remove them with synaptic. Search for linux-image, see which ones you have installed, and remove some of the older ones (lower numbers). Linux won't let you uninstall the one you are using, and I second the opinion of keeping at least one older one that worked.

To confirm which kernel you are using, run this command:
```

uname -r

```

You will get a number such as *2.6.27-11-generic* (for intrepid). In this case, you could uninstall linux-image-2.6.27-7-generic, 2.6.27-9-generic, etc. Again, it's recommended you keep at least one extra one.

While you are cleaning things up, you can also type the kernel number in the synaptic search window, such as 2.6.27 and can also remove the associated linux-header (for example: linux-headers-2.6.27-7-generic).

Removing these older kernels from synaptic will automatically remove them from the grub menu as well.

For tweaking the grub menu options and displays, I recommend StartUp-Manager. There is a link to a tutorial in my signature line.

---

### Post by R@inm@n on 2009-02-17
Thank you.  I will follow all the instructions as posted.

 R.

---

