---
title: "ubuntu, kubuntu and windows (triple boot) possible?"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Rushyang on 2010-04-16
Bonjour guys,

I've installed "Ubuntu Karmic Koala" with wubi into Windows 7 x64 Ultimate. I wondered, can I install now Kubuntu with wubi as well? Please note that I want a complete different distro, I am aware of installing KDE environment along with GNOME.. I don't want to do that. 

So will I able to have triple boot that way? Suggestions are welcomed.

---

### Post by sandyd on 2010-04-16
> **Rushyang said:**
> Bonjour guys,

I've installed "Ubuntu Karmic Koala" with wubi into Windows 7 x64 Ultimate. I wondered, can I install now Kubuntu with wubi as well? Please note that I want a complete different distro, I am aware of installing KDE environment along with GNOME.. I don't want to do that. 

So will I able to have triple boot that way? Suggestions are welcomed.

in ubuntu, just install the package "kde-minimal" or "kde-full" or "kubuntu"desktop". that will give you kubuntu.

---

### Post by e4uforums on 2010-04-16
Personally, I would fire up gparted and create a new partition for Kubuntu.  When installing Kubuntu it should upgrade GRUB and give you the option of all 3 OS's.

I've seen plenty of triple boot systems before.

Here is a forum post that goes into a bit more detail, it's a bit old, but the process is mostly the same.

[http://ubuntuforums.org/showthread.php?t=220452](http://ubuntuforums.org/showthread.php?t=220452)

---

### Post by Rushyang on 2010-04-16
> **e4uforums said:**
> Personally, I would fire up gparted and create a new partition for Kubuntu.  When installing Kubuntu it should upgrade GRUB and give you the option of all 3 OS's.

I've seen plenty of triple boot systems before.

Here is a forum post that goes into a bit more detail, it's a bit old, but the process is mostly the same.

[http://ubuntuforums.org/showthread.php?t=220452](http://ubuntuforums.org/showthread.php?t=220452)


I don't want to create a new partition.. Can't I use [SIZE=1]_**WUBI** _[/SIZE]again? for installing a kubuntu? Please read my question carefully.. :P

---

### Post by e4uforums on 2010-04-16
I'm not sure why you couldn't use WUBI to do another install. 

 WUBI installs the OS to a file on the Windows system and modifies the boot file to add the option for the new OS.  So, assuming you had the proper space available, I don't see you would not be able to.

Please read the website carefully, [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)   :P

>              **How does Wubi work?**

             Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the Windows file system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real hard disk.
         


---

### Post by Serpher on 2010-04-16
Wubi is not a good route to go for any instillation. I would just repartition everything.

---

### Post by e4uforums on 2010-04-16
> **Serpher said:**
> Wubi is not a good route to go for any instillation. I would just repartition everything.

I agree.

---

### Post by Sir Jasper on 2010-04-16
Hi,

I am not sure that your existing Wubi counts counts as a dual boot. If it does not, then if you can have a double Wubi it would not be a triple boot.

I do not know the answer. I am just trying to clarify any possible confusion in the question.

Do let us know how you get on.

My regards

---

