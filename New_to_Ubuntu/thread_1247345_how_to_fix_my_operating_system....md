---
title: "how to fix my operating system..."
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Katty2008 on 2009-08-22
Okay, well I just found out that I have a combination of ubuntu and kubuntu on my computer.It didn't want to put kubuntu on it, so my boyfriend put ubuntu on and tired to force it to change into kubuntu. Now, I need a way to get it to kubuntu. Can anyone help me??

---

### Post by DGortze380 on 2009-08-22
> **Katty2008 said:**
> Okay, well I just found out that I have a combination of ubuntu and kubuntu on my computer.It didn't want to put kubuntu on it, so my boyfriend put ubuntu on and tired to force it to change into kubuntu. Now, I need a way to get it to kubuntu. Can anyone help me??

Your post is very confusing.

Can you please clarify ... do you want Gnome (Ubuntu) or KDE (Kubuntu)?

Please open a terminal (Applications -> Accessories -> Terminal) and post the output of the following:

```
sudo fdisk -l
```

---

### Post by Bölvaður on 2009-08-22
go into

System &#8594; Administration &#8594; Synaptic Package Manager

look for ubuntu desktop
uninstall it.

make sure kubuntu desktop is installed before doing so.
log out, log back in.

---

### Post by kansasnoob on 2009-08-22
Look at this part:

> Playing Around
KDE/Gnome Comparison
Install KDE
Install XFCE
Install IceWM
Pure Gnome
Pure KDE
Pure XFCE
Make your own Ubuntu remix 

of this tutorial:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by 3rdalbum on 2009-08-23
KDE and Gnome can co-exist; you switch between them by clicking "Options > Sessions..." at the login screen. Some ways of installing KDE will change your startup screen to say "Kubuntu"; this can be changed, but it's normal.

---

### Post by earthpigg on 2009-08-23
> **kansasnoob said:**
> Look at this part:



of this tutorial:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

+1

this is exactly what i was going to link.

uninstalling kubuntu-desktop or _*any other metapackage will not actually uninstall **anything**.*_

a metapackage is just a list of dependencies - a list of other stuff to install. removing it is just removing the list, not the listed stuff itself.

---

### Post by earthpigg on 2009-08-23
also, why would you trust someone else with administrative access to your computer??

---

### Post by Katty2008 on 2010-08-08
He was trying to fix my computer. It was my husband. I let him do it. By the way, fixed the problems.

---

