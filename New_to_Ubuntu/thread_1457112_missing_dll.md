---
title: "missing dll"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by altkon on 2010-04-18
I have a dual boot WXP/Ubuntu iso CD 8.04,
by which I had added Ubuntu as a second choice to my WXP SP3
OS which up to now worked fine.
But as of a few days when I choose to boot from Ubuntu
refuses to do so due to "a missing DLL".
What is the best solution for a fix or recovery??:(
Thanks a lot.
Regards

---

### Post by ajgreeny on 2010-04-18
Is this a wubi install of ubuntu from within windows?

---

### Post by altkon on 2010-04-18
It is from within windows.

---

### Post by steveneddy on 2010-04-18
This needs to be asked in the Wubi forum.....

I see there isn't a Wubi forum here anymore - so - my standard answer for those that choose to use Wubi:

[Wubi sucks and will more often than not cause hair pulling issues]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu").

From the link:

> Because the installation requires an intact functioning Windows system, it is recommended to install Ubuntu in this manner for **short-term evaluation purposes only**. **[COLOR="Red"]A permanent Ubuntu installation should be installed in its own partition, with its own filesystem[/COLOR]**, and should not rely on Windows.

I recommend using a virtual machine like [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") to install Ubuntu while running Windows - which is real easy AAMOF - or simply partition the drive and use Ubuntu as it was designed, in it's own world.

First uninstall Wubi and download and follow the link provided to download [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") and install Ubuntu in VB.

EDIT:

This link may help, but I still encourage the OP to use VirtualBox or partition the drive for a full installation.

[https://wiki.ubuntu.com/WubiGuide#Troubleshooting](https://wiki.ubuntu.com/WubiGuide#Troubleshooting)

---

### Post by altkon on 2010-04-18
The problem is I dont know how to uninstall Ubuntu??:confused:

---

### Post by 3rdalbum on 2010-04-18
> **altkon said:**
> The problem is I dont know how to uninstall Ubuntu??:confused:

Ubuntu doesn't use DLLs, Windows does. Must be a problem with the Windows bootloader.

You can remove Ubuntu using the Add/Remove Applications control panel in Windows. Then boot up from the Ubuntu CD and install Ubuntu that way.

---

### Post by altkon on 2010-04-19
> **3rdalbum said:**
> Ubuntu doesn't use DLLs, Windows does. Must be a problem with the Windows bootloader.

You can remove Ubuntu using the Add/Remove Applications control panel in Windows. Then boot up from the Ubuntu CD and install Ubuntu that way.

Add/Remove Applications contain only WXP software under my hard disk partition C.
Ubuntu is dual installed on same hard disk but different partition therefore not included.
Appreciate if you could suggest a different solution.
Thanks.

---

### Post by e4uforums on 2010-04-19
If you installed using WUBI, there is an entry in Add/Remove Programs for Ubuntu.
[http://wubi-installer.org/images/wubi-uninstall.png](http://wubi-installer.org/images/wubi-uninstall.png)

If you did not install using WUBI, I can't think of a reason you'd be getting a DLL error at Ubuntu boot.

---

### Post by altkon on 2010-04-19
No I did not use WUBI.

Is there a way to unistall by using my Ubuntu 8.04 Live CD.(iso)
An then reinstall it??

---

### Post by e4uforums on 2010-04-19
If you did not use WUBI, you can boot to the live cd and just reinstall over your existing Ubuntu install.

---

### Post by altkon on 2010-04-19
When I reboot from the live CD in orderto reinstall asks to repartition from the start whereas I want to ask to reinstall over the existing install.
Can you guide me thru please??

---

### Post by e4uforums on 2010-04-19
When it asks you where you want to install, choose the existing Ubuntu partition.

---

### Post by ajgreeny on 2010-04-19
When the installer gets to the partitioning screen choose manual partitioning.  A screen will appear with a graphical display of your disk and partitions, and you can then choose to use those two partitions for your install, the larger one as /, or root, and the small one as swap.

Just make sure you do not do anything to your windows partition, probably sda1, or you are in big trouble.

---

### Post by lisati on 2010-04-19
> **altkon said:**
> It is from within windows.

> **altkon said:**
> No I did not use WUBI.

Is there a way to unistall by using my Ubuntu 8.04 Live CD.(iso)
An then reinstall it??

:confused: Which is it?

---

### Post by xumuk37 on 2010-04-19
and why do you need to "uninstall" it? o_O why don't you just re-format ubuntu containing partition or do fresh installation without formatting?

---

