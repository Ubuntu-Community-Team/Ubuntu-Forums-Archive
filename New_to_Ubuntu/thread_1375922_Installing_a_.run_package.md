---
title: "Installing a .run package"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by a mad pigeon on 2010-01-08
Hello there! I'm just starting out using Ubuntu through VMware and I'm trying to install Nvidia drivers. I've read most of the Ubuntu beginner's guide already so I understand how to use the terminal and how to set files to execute. I've already set the package to run as an executable, and when I try to run it in the terminal, the installer tells me I need to install it with root permissions. Can I install it on my user account through the terminal? I've switched the mode using sudo su so it has a # sign but I don't understand how to run it. Any help please? :D

---

### Post by fromthehill on 2010-01-08
if you need nvidia drivers you have to activate them in system> administration> hardware drivers

you don't need the nvidia drivers inside vmware so it will just say you don't need drivers

---

### Post by a mad pigeon on 2010-01-08
So I don't need to get the drivers from the Nvidia site? Does Ubuntu detect, download, and install the drivers through hardware drivers or the software center?

---

### Post by mk1w86 on 2010-01-08
Goto:

System>>Administration>>Hardware Drivers

and activate the latest driver for your card. :)

EDIT: Sorry didn't read post above.

---

### Post by bodhi.zazen on 2010-01-08
> **a mad pigeon said:**
> Hello there! I'm just starting out using Ubuntu through VMware and I'm trying to install Nvidia drivers. I've read most of the Ubuntu beginner's guide already so I understand how to use the terminal and how to set files to execute. I've already set the package to run as an executable, and when I try to run it in the terminal, the installer tells me I need to install it with root permissions. Can I install it on my user account through the terminal? I've switched the mode using sudo su so it has a # sign but I don't understand how to run it. Any help please? :D

When using VMWare, Ubuntu will not use the Nvidia drivers, so no need to install them.

Virtualization does not directly use your hardware.

What you want is to install the VMWare Tools into the guest (NOT the Host).

[VMware/Tools - Community Ubuntu Documentation]("https://help.ubuntu.com/community/VMware/Tools")

---

### Post by daimaru on 2010-01-08
for future reference this might be helpful. If you have changed any script to be executable with 
```
chmod +x scriptname
```you can run it using 
```
./scriptname
```or ```
bash scriptname
```"bash" depends on what shell you are using.
of course this is also true for .run files
```
./nvidiadriver.run
```

---

