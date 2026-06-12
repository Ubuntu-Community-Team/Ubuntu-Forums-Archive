---
title: "NVIDIA Issue"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by CGumpLinux on 2010-11-12
I dont know what i am doing wrong here but i am sure its due to my inexperience
so i am trying to install nvidia drivers 
i go into  
```
sudo -i
```

and than i run 
```
init 3
```

but when i run my installer for the drivers it tell me i need to be root... when i am already installing as root@blahblah

any help or ideas what i am doing wrong would be greatly apprecaited

---

### Post by Perfect Storm on 2010-11-12
You install the nvidia restricted drivers: 

System ---> Administration ---> Additional Drivers.

Select the Nvidia driver. It will download and install the driver. Then reboot afterwards.

---

### Post by sikander3786 on 2010-11-12
I think you are trying to install from a package downloaded from manufacturer's website?

You don't need to do that as Nvidia drivers are already in the repositories.

Just follow **Artificial Intelligence's** instructions.

You'll need to select the current, recommended driver from that list.

If you are running 10.04, you will find the drivers under System > Administration > Hardware Drivers instead of Additional Drivers.

Good Luck!

---

### Post by CGumpLinux on 2010-11-12
thx guys i did that at first i just wasnt sure if it really was that simple cause iam having really poor graphics

---

