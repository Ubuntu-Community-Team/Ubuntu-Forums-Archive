---
title: "ERROR: File '/usr/lib/xorg/modules/extensions/libglx.so' is not a symbolic link."
date: 2010-11-20
forum: New to Ubuntu
---

### Post by mistypotato on 2010-11-20
After updating my 9.10 Ubuntu OS today I got the following FATAL error....

**ERROR: File '/usr/lib/xorg/modules/extensions/libglx.so' is not a symbolic link.**

Fortunately, I survived....but I still had to get my GUI back......so....

I had previously installed the nividia driver **NVIDIA-Linux-x86-256.53.run**
which I had downloaded from downloads.nvidia.com

Apparently after upgrading, the configuration files were messed up and when I rebooted, I could only arrive at a command prompt.

Since I had not deleted the downloaded driver, I simply RAN it again....

sudo /etc/init.d/gdm stop

cd Desktop

sudo sh ./NVIDIA-Linux-x86-256.53.run


This joyfully started the Nvidia installation program again (boy was I glad) and faithfully
re-installed the packages needed.   At one point, it correctly found that a file had been replaced by a symbolic link or something like that and I thought it was all over...but to my surprise, Nvidia has added a catch for that in the installation and it was able to overcome that and successfully re-install the drivers.

When it finished I rebooted and all was wonderful in Ububooland once again.

---

### Post by ohmster on 2012-03-07
Misty is right. I just had the same issue. I was in gnome (I use CentOS 6.2) and it comes with compiz, the most awesome 3D desktop you ever saw. My compiz cube was awesome, hold shift, control, mouse 1 to rotate to one of the other desktops. It stopped working, a quick check showed compiz was still installed, but trying to run the command "glxgears" in a term window failed. That means you have no 3D video drivers loaded. So I ran the same nvidia install script and got the same error message. I googled for it by copy and paste and landed here.

Misty is right, nvidia fixed the issue all by itself but if you ever have to fix this manually, here is an easy way.

Find the file that should be link with locate:
/usr/lib/xorg/modules/extensions/libglx.so
/usr/lib/xorg/modules/extensions/libglx.so.290.10
[root@paulspcworks extensions]#

And you can create the link yourself if you have to like this:

16 Mar  7 12:46 libglx.so -> libglx.so.290.10
5073552 Mar  7 12:46 libglx.so.290.10

Just my two cents.
~Ohmster

---

