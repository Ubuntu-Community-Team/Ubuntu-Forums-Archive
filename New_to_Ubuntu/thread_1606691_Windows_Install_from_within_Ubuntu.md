---
title: "Windows Install from within Ubuntu"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Meliority on 2010-10-26
Is there a way to install windows onto free disk space from within ubuntu?

---

### Post by l-x-l on 2010-10-26
Check out the Wubi install option. It installs Ubuntu inside Windows.

[WUBI]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by waynefoutz on 2010-10-26
> **Meliority said:**
> Is there a way to install windows onto free disk space from within ubuntu?

Within Ubuntu? The only way I can think of doing that is by installing it in Virtualbox. 

If you mean install Windows AFTER Ubuntu on a separate partition to dual boot, yes, but you'll have to partition it first, and you'll have to reinstall Grub afterward to be able to boot Ubuntu again. 

Here is a guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Obviously, it's a lot easier to install Windows THEN Ubuntu.

---

### Post by ArgusVision on 2010-10-26
You could install it in a virtual machine. Thats how I've done it any way.
Check out [www.virtualbox.org](www.virtualbox.org) and [www.vmware.com](www.vmware.com)

---

### Post by Rex Bouwense on 2010-10-26
Are you asking if you can install Windows inside of Ubuntu?  Wubi will allow you to install Ubuntu inside of Windows.  You can install Windows and Ubuntu side by side in their own partitions choosing to boot for one or the other when you turn on your machine.  I have never heard of being able to install Windows inside of Ubuntu but that doesn't necessarily mean that it can't be done.  Someone with more knowledge may be able to tell you if it can be done. You can run Windows programs in Ubuntu using Wine, but that wasn't your question.

---

### Post by Meliority on 2010-10-27
Yeah that looks like a good couple of options. As I understand it wine1.3 is emulating xp and I was hopping to use more current features of windows since wine hasnt exactly been ideal. 
 
Thanks for the suggestions!

---

### Post by migs73 on 2010-10-27
A virtual machine is the best option, but you have to share your ram, so you'll need plenty. What 'more current features' of windows were you looking for?

---

### Post by GrouchyGaijin on 2010-10-27
> **ArgusVision said:**
> You could install it in a virtual machine. Thats how I've done it any way.
Check out [www.virtualbox.org](www.virtualbox.org) and [www.vmware.com](www.vmware.com)

If you use Virtual Box get the installer from their website and not the repository if you want to use USB with Windows.

That is how I use my scanner that is not supported in Ubuntu.

---

### Post by migs73 on 2010-10-27
> **GrouchyGaijin said:**
> If you use Virtual Box get the installer from their website and not the repository if you want to use USB with Windows.

That is how I use my scanner that is not supported in Ubuntu.

+1 to that. And then install guest additions (instructions on the website).

---

### Post by aeiah on 2010-10-27
you should be aware that virtual machines dont perform as well as ones that deal with the hardware directly (ie, ones installed normally). so whilst it can be convenient to have windows as a virtual machine (so you just start up windows like any other ubuntu application) it won't perform well with games, for example.

---

### Post by mcduck on 2010-10-27
> **Meliority said:**
> Yeah that looks like a good couple of options. As I understand it wine1.3 is emulating xp and I was hopping to use more current features of windows since wine hasnt exactly been ideal. 
 
Thanks for the suggestions!

Actually you don't get much of the Windows features at all, since Wine doesn't emulate Windows, it only handles some translation between windows app and Linux system (emulating a modern OS would be really heavy, most likely beyond usable even on powerful new computer). So you don't get any of the Windows UI with Wine, only the running program itself.

If you actually want a Windows *desktop* inside your Linux install, virtualization is the only option. And if you want to be able to play games and such, you'll just have to dualboot (or check if the game runs with Wine).

edit: if you want something like the Wubi install for Ubuntu, dualbooting but keeping Windows installed inside the Linux filesystem, that's not possible. Windows isn't able to do such thing. (Not that I'd see any reason to use Wubi to install Ubuntu inside Windows FS either, really)

---

### Post by migs73 on 2010-10-27
> **aeiah said:**
> you should be aware that virtual machines dont perform as well as ones that deal with the hardware directly (ie, ones installed normally). so whilst it can be convenient to have windows as a virtual machine (so you just start up windows like any other ubuntu application) it won't perform well with games, for example.

+1 That is why I was asking what 'features' the OP was looking for.

---

### Post by ArgusVision on 2010-10-27
Another thing about VM's is that they typically don't do 3D Rendering. So those graphics intensive games are a bust. VMware is supposed to be working on support for that but I haven't actually tested it. Between the Graphics and memory usage it's not a gamers option.

---

### Post by waynefoutz on 2010-10-27
> **ArgusVision said:**
> Another thing about VM's is that they typically don't do 3D Rendering. So those graphics intensive games are a bust. VMware is supposed to be working on support for that but I haven't actually tested it. Between the Graphics and memory usage it's not a gamers option.

For Windows gaming, I just dual boot. I don't think there is any shame in that.  I use XP rather than Vista or 7 because the footprint is a LOT smaller. I also run with no antivirus, so I do NOT open a browser in Windows, unless you count the one built into Steam. Steam runs ok in WINE, but it still has graphics glitches that I don't get in Windows.  I use it exclusively for gaming. You can install XP and quite a few games on a 40 gig partition.

---

### Post by ArgusVision on 2010-10-27
I understand about the dual-boot. The first step is to admit you have a problem... :biggrin:

---

### Post by waynefoutz on 2010-10-31
> **ArgusVision said:**
> I understand about the dual-boot. The first step is to admit you have a problem... :biggrin:

I have an EVDO card, a GPS unit, and a couple other devices that require Windows software to get firmware updates as well. So 40 gigs out of a 250 gig hard drive for XP isn't that big of a sacrifice.

---

