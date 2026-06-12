---
title: "NVIDIA-Linux-x86-177.82.pkg1 how to install"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by tibucu on 2008-12-13
Hi everybody I am trying to install the orriginal driver for my desktop, as a new user of Ubuntu (8.10 ) I used in a terminal the command "sudo sh NVIDIA-Linux-x86-177.82.pkg1.run " but the reply was no file found,what to do PLEASE help.

---

### Post by Paqman on 2008-12-13
Open System > Admin > Hardware Drivers. The Nvidia 177 driver will be available to install automatically.

---

### Post by tibucu on 2008-12-13
Thank you for reply but I want to install the genuine Nvidia from the downloaded file,if you can help i will apreciate !!

---

### Post by Paqman on 2008-12-13
It's exactly the same driver, just prepackaged for you with a nice easy installer. You can trust anything from the Ubuntu repos 100%.

---

### Post by tomtom1982 on 2008-12-13
You should really take the package from the ubuntu repository.

But if you absolutely want to use the driver from nvidia page all you have to do is what you can read on the nvidia-site were the driver is given to download. You also have to be logged in as root on command line without X-Server.

---

### Post by Kareeser on 2008-12-13
Try "sudo ./NVIDIA-Linux-x86-177.82.pkg1.run"

---

### Post by tibucu on 2008-12-13
Just tryed what Kraeeser saidand received :sudo: ./NVIDIA-Linux-x86-177.82.pkg1.run: command not found what do you suggest. thk for your reply

---

### Post by Paqman on 2008-12-13
You need to download the package, then cd into the directory that it's located in, then try running it.

---

### Post by tjwallace on 2008-12-13
You have to make it executable to be able to run it (chmod +x NVIDIA-Linux-x86-177.82.pkg1.run).

Also, GDM cannot be running when you install, so you must switch to a different terminal (Ctrl + Alt + F2), shut down GDM (sudo /etc/init.d/gdm stop), and then run the nvidia script (sudo ./NVIDIA-Linux-x86-177.82.pkg1.run).

However I would recommend you install the driver from the Ubuntu repository.

---

### Post by Paqman on 2008-12-13
> **tjwallace said:**
> 
However I would recommend you install the driver from the Ubuntu repository.

The main reason everyone keeps saying this, btw, is that if you install it manually like you're asking, then it will break every time there's a kernel update.

If you install from the repo, it won't break.

---

### Post by maandverband on 2008-12-13
> **Paqman said:**
> The main reason everyone keeps saying this, btw, is that if you install it manually like you're asking, then it will break every time there's a kernel update.

If you install from the repo, it won't break.

As far as I know it won't break anymore in Ubuntu 8.10 because of DELL's DKMS.

---

