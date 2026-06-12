---
title: "dual boot windows and linux"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by retro-rocket on 2011-04-30
how do i partition my computer so i can run windows too dual boot, i already have ubuntu 10.4 installed

---

### Post by Rubi1200 on 2011-04-30
Are you saying that Ubuntu is installed and now you want to add a partition for Windows?

Best thing to do is post the output from this command so we get a better idea of what is going on:

```
sudo parted -l
```
(lowercase L not 1)

---

### Post by retro-rocket on 2011-04-30
yes i have linux already installed and i would to make a partition for windows

---

### Post by retro-rocket on 2011-04-30
hello i have a lenovo laptop with ubuntu 10.4 operating system, i would like to make a part of my pc seperate so i can run windows on it if i need to, where do i start ?

---

### Post by amissot on 2011-04-30
Hi

When I did it I installed windows first and then used the Ubuntu live CD to take me through the installation. So it would probably be best if you back up all your files and anything you need install windows deleting your Ubuntu installation in the process then reinstall Ubuntu and select multiple operating systems.

However you could just install virtual box or something similar and run windows inside Ubuntu.

Hope this helps.

---

### Post by Linjie on 2011-04-30
[https://help.ubuntu.com/community/WindowsDualBoot#Installing Windows After Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing Windows After Ubuntu)

---

