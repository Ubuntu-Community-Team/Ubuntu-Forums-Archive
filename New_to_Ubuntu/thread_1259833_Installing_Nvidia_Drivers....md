---
title: "Installing Nvidia Drivers..."
date: 2009-09-06
forum: New to Ubuntu
---

### Post by GriZzlEnLS on 2009-09-06
Hey I guess I should look here first (I'm not a beginner with linux, but I am still very much a noob) Now I haven't really had a chance to use linux on my desktop (Still have it working on my laptop without a problem) Well Since that last time I've used linux on my main desktop was 8.10 and I was running an older 8800GT. Now everything on my system has changed (Specs are in my sig). Well long story short I will install the system as I have been for the last 2 years and use the restricted drivers or use ENVY to install my nvidia drivers. After installing the restricted drivers or using ENVY I am unable to boot with xserver running. I have tried to restart it but with no use the only way I have found to get around it was to reinstall. Now before I even install the drivers, I am running dual monitors one 20 the other 22in, it mirrors the monitors and I am unable to view outside of a certain res. I have never seen this issue before it is almost that the default res is smaller, which it is it stays at 1152x864, and after I install the drivers it states that res 1152x864 failed and it will try and run in 1024x768 then without a splash screen asks me to login. Now I noticed both drivers were the 180.xx version nvidia drivers. I have tried to install the 185.xx driver from nvidia's website without luck (I am unable to install). Any thoughts? I love this OS on my laptops, and HTPC but for some reason this new system just doesn't like it! Any help would be great, thanks in advance.

EDIT: the 9400GT has been taken out just to see if that caused an issue, and at this time is no longer in the system.

---

### Post by overdrank on 2009-09-06
My apologies, what is it that you are requesting? How to install the nvidia drivers? What was the error when trying to install the drivers?

---

### Post by GriZzlEnLS on 2009-09-06
I want to beable to run the 185 drivers if possible or if there is some other way of running the 180 that would work also. I am unable to install the 185 when trying to install them from the guide on nvidia's website I get this:

xcsas@FrankieII-Linux:~/Desktop$ sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg2.run
sh: Can't open ./NVIDIA-Linux-x86-185.18.36-pkg2.run

---

### Post by overdrank on 2009-09-06
> **GriZzlEnLS said:**
> I want to beable to run the 185 drivers if possible or if there is some other way of running the 180 that would work also. I am unable to install the 185 when trying to install them from the guide on nvidia's website I get this:

xcsas@FrankieII-Linux:~/Desktop$ sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg2.run
sh: Can't open ./NVIDIA-Linux-x86-185.18.36-pkg2.run

Hi and I believe it would be ```
sudo sh NVIDIA-Linux-x86-185.18.36-pkg2.run
``` if you have cd to the directory which is the Desktop.

---

### Post by pastalavista on 2009-09-06
> **GriZzlEnLS said:**
> ...I am unable to install the 185 when trying to install them from the guide on nvidia's website I get this:

xcsas@FrankieII-Linux:~/Desktop$ sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg2.run
sh: Can't open ./NVIDIA-Linux-x86-185.18.36-pkg2.runfirst you must ```
sudo chmod -x NVIDIA-Linux-x86-185.18.36-pkg2.run
```to make the file executable... and use either 'sh' or './' to run it but not both

---

### Post by GriZzlEnLS on 2009-09-06
Well after trying that I now get:

xcsas@FrankieII-Linux:~/Desktop$ sudo sh chmod -x NVIDIA-Linux-x86_64-185.18.36-pkg2.run
sh: Can't open chmod

or I get this: 

xcsas@FrankieII-Linux:~/Desktop$ sudo chmod -x ./NVIDIA-Linux-x86_64-185.18.36-pkg2.run
xcsas@FrankieII-Linux:~/Desktop$ 

am I doing something wrong?

EDIT: also tried another way and got this:

xcsas@FrankieII-Linux:~/Desktop$ sudo chmod ./ -x NVIDIA-Linux-x86_64-185.18.36-pkg2.run
xcsas@FrankieII-Linux:~/Desktop$

---

### Post by pastalavista on 2009-09-06
the chmod command does not use sh or ./ just copy and paste what I wrote if you're in the right directory

```
sudo chmod -x NVIDIA-Linux-x86_64-185.18.36-pkg2.run

and then

sh NVIDIA-Linux-x86_64-185.18.36-pkg2.run
```

---

### Post by oldos2er on 2009-09-07
There is a ppa for the Nvidia 185 drivers. Here's a howto: [http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

---

