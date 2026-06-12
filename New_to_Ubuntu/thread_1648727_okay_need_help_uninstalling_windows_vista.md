---
title: "okay need help uninstalling windows vista"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by jakegrimes123 on 2010-12-19
pokay so i installed Ubuntu 9.04 (i know its old!) and now when i start up my pc  it gives me an option to run either windows or ubuntu. Ubuntu is running quite slow which i believ is because windows vista is using up alot of memory. so i need newbie friendly step by step instructions of how to completely remove windows vista and have Ubuntu as the only os.
also prefferebly i would rather not have to uninstall and reinstall ubuntu.
thanks for the help:)

---

### Post by coffeecat on 2010-12-19
> **jakegrimes123 said:**
> Ubuntu is running quite slow which i believ is because windows vista is using up alot of memory.

I'm afraid your logic doesn't stand up. Whether you have a conventional dual-boot with Ubuntu on its own partition or a wubi install (with Ubuntu in a virtual disk inside your C: partition), Vista is not running when Ubuntu is running. There is no way that Vista could use up memory needed by Ubuntu. There must be another reason why Ubuntu is running slow.

Whatever the reason, you are wasting your time trouble-shooting a 9.04 installation. It is no longer supported - no more updates. I suggest you consider installing a newer supported version, 10.04 or 10.10, and reconsidering whether or not you want to get rid of Vista.

Do you have a wubi install or Ubuntu install on its own partition? If you don't know the answer, boot up Ubuntu, open a terminal and post the output of:

```
sudo fdisk -lu
```

---

### Post by karthick87 on 2010-12-19
If you have installed ubuntu on its own partition.Then by installing gparted you can remove the vista partition..

To install gparted:
```
sudo apt-get install gparted
```

After installation,gparted will be found under System>>Administration>>Gparted.Delete the vista partition and update your grub to ged rid of the vista entry in your grub menu.
```
sudo update-grub
```

---

### Post by bodhi.zazen on 2010-12-19
> **jakegrimes123 said:**
> pokay so i installed Ubuntu 9.04 (i know its old!) and now when i start up my pc  it gives me an option to run either windows or ubuntu. Ubuntu is running quite slow which i believ is because windows vista is using up alot of memory. so i need newbie friendly step by step instructions of how to completely remove windows vista and have Ubuntu as the only os.
also prefferebly i would rather not have to uninstall and reinstall ubuntu.
thanks for the help:)

As coffeecat indicated, while yo are free to remove Windows , that is almost certainly NOT the cause of your poor performance. The only exception I could think of would be if your Ubuntu partition were full, and in that event it needs more space.

---

### Post by RJ12 on 2010-12-19
While I am no fan of Windows Vista, I agree with everyone else. You should hold off un-installing Vista for a while until you are sure you don't need it anymore. I hate to say it, but many people come to the forums feeling confident and blow off Windows, then in usually at least a day come back saying they need Windows back. Also Windows Vista should not be making Ubuntu slow, as they are completely separate from each other. If you are low on HDD space for Ubuntu, or using WUBI then maybe that could be slowing it down. If you don't know how to find this information then please go to the Applications Menu, hover over Accessories then click Terminal. Then type in this code

```
sudo fdisk -lu
``` 

that is a lower case L and U, you can copy and paste the command if you really want to get it correct. As a warning, when it asks you for the password, it will look like you are not typing it in. But it does that (some call it a bug, some call it a security feature) just continue typing it in, then press enter. If you can post the output here in code tags (push the button that looks like a pound/hash mark to the left of the "< >" button then paste the output in between the things that say "```

```"


We should then be able to tell you if you are using WUBI, or running out of disk space.

Hope I helped :) and welcome the forums / Ubuntu

---

### Post by Shintek on 2010-12-19
I really recommend always using the latest version, unless you have a very good reason.

---

