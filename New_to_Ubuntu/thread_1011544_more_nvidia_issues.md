---
title: "more nvidia issues"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by skydiving85 on 2008-12-14
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." how the hell do i do this as every thing/ place i have tired to run this as a 'root' is not running as a root, what is a root anyway ?

---

### Post by taurus on 2008-12-14
```
**sudo** nvidia-xconfig
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Tatty on 2008-12-14
I highly recommend you read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Once you understand root and sudo it will make things much easier.

To run nvidia-xconfig as root you need to add either sudo to the front of it:
```
sudo nvidia-xconfig
```

If this is a graphical app then you should add gksu in front of it instead of sudo.  But from reading the nvidia documentation it sounds like it is not graphical.

How did this nvidia problem appear?  How did you install the Nvidia driver?

---

### Post by agathian on 2008-12-14
when it comes to NVIDIA cards - envyNG is your friend.. check it out
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

it should be in the official repositories...

---

### Post by skydiving85 on 2008-12-14
yeah well that goes in part with tried every thing .... but i think my drivers are all messed up in have uninstalled reinstalled, and watched them go bonkers multiple times using ever known way now... does any one know of a GOOD set of instructions for installing these awkward drivers, i have a gforce 8300 gs or whatever... i remember when i first did this it was simple and seamless... what happened to that ?

---

### Post by skydiving85 on 2008-12-14
i am also not finding the drivers under the system admin hardware display.... i think this means i need every thing ?

---

### Post by Tatty on 2008-12-15
First make sure all you have all the repos selected in System->Administration->Software Sources.  Close this dialog, If it asks you if you want to reload the packages list then do so. 

Next go to System->Administration->Hardware Drivers and see if it lists your driver.

If that fails then install envyng-gtk:

```
sudo apt-get install envyng-gtk
```

Then run envyng from Applications->System Tools->Envyng and see if that can install your driver.

---

