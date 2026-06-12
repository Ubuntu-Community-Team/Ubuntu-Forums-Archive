---
title: "NVIDIA 9800GT driver"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Rrasyrogenees on 2009-02-11
i downloaded the NVIDA driver but it won't let me install it.  i do not have enough experience to know what i have to do to get it to accept it.  i downloaded the file NVIDIA-Linux-x86_64-180.22-pkg2.run and the how to says to open it by put sh in front of it and the file name but what i get is "sh: Can't open NVIDIA-Linux-x86_64-180.22-pkg2.run".  so now my question is... why can't it open it and what do i need to do to be able to open it?  
i tried with and without writing sudo and got the same thing except having to enter my password for sudo.  is there anyone that lives in san bernardino,ca that i can bring my computer to help me fix me?  (i am sure it is not the computer as much as it is me that is screwing it all up).  and i should mention that it is cutting deeply into my WoW time... not good, not good... (is it time to panic yet?)

---

### Post by hyperyoda on 2009-02-11
> **Rrasyrogenees said:**
> i downloaded the NVIDA driver but it won't let me install it.  i do not have enough experience to know what i have to do to get it to accept it.  i downloaded the file NVIDIA-Linux-x86_64-180.22-pkg2.run and the how to says to open it by put sh in front of it and the file name but what i get is "sh: Can't open NVIDIA-Linux-x86_64-180.22-pkg2.run".  so now my question is... why can't it open it and what do i need to do to be able to open it?  
i tried with and without writing sudo and got the same thing except having to enter my password for sudo.  is there anyone that lives in san bernardino,ca that i can bring my computer to help me fix me?  (i am sure it is not the computer as much as it is me that is screwing it all up).  and i should mention that it is cutting deeply into my WoW time... not good, not good... (is it time to panic yet?)

It may not have the correct file permissions to execute. Try this:

$ chmod +x NVIDIA-Linux-x86_64-180.22-pkg2.run
$ ./NVIDIA-Linux-x86_64-180.22-pkg2.run

Zach

---

### Post by Crafty Kisses on 2009-02-11
Once you have downloaded the NVIDIA driver you need to stop your X server, so press Cntrl-Alt-F2. Once you have done that you need to run the following:
```
sudo /etc/init.d/gdm stop

```
Then once you've done that you need to run the following, remember I'm just guessing the file is called NVIDIA-Linux and it's saved to your desktop, so remember substitute your information:
```
cd ~/Desktop
chmod +x NVIDIA-Linux.run
sudo ./NVIDIA-Linux.run
```
Once the installation is done, restart the X server with:
```
sudo /etc/init.d/gdm start

```

---

### Post by Rrasyrogenees on 2009-02-11
thank you Codename... it downloaded but now i am stuck in whatever place that is and it will not let me come back to the desktop again... what did i do or not do that created this?  (i am on my second OS on my computer to be able to access here).

---

### Post by Crafty Kisses on 2009-02-12
I'm not sure what you mean by "It won't let me come back to my desktop" by that do you mean that when you reboot you're getting a blank screen? Do you mean you installed the driver and you don't know what to do now? If you installed the driver correctly, you can run the following:
```
sudo /etc/init.d/gdm start
```
Then that will start X backup, if that doesn't start it and the driver is installed correctly you can try rebooting, and you can do that by running the following:
```
sudo shutdown -r now
```

---

### Post by Rrasyrogenees on 2009-02-12
thanks for all your help Codename... i did the easy way out and reinstalled since i have Two OS's on my computer anyway and the one i am really trying to work with is the one i want to run WoW.  i was able to download and run what you gave to me and it worked since i did this before doing anything else (other than the updates after installing).  so far... it is working now but i have yet to get wine and WoW installed to see what that will do now so i will keep you posted here when i get that done but so far so good... thanks again.

---

### Post by Rrasyrogenees on 2009-02-12
now my problem is that gecko installer doesn't seem to be working to get the end user for WoW to let me "agree" and move to downloading WoW.  i use the online WoW client since my disc seem to be corrupted so i think i will start a new thread addressing gecko, wine and WoW.

---

