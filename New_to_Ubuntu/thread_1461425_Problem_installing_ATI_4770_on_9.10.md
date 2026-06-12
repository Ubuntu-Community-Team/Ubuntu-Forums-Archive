---
title: "Problem installing ATI 4770 on 9.10"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by George7a on 2010-04-24
Hello all,

I have just replaced my old GT7300 nvidia with HD 4770. I am trying to "activate" the driver from the "hardware drivers" and I am getting:
> Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

I have been reading and trying stuff like:
1)EnvyNG
2)adding the following rep:
> 
[http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu](http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu)

3)updates..

and it did not work
The log is also attached.

Any advices?

- George

---

### Post by Jon Monreal on 2010-04-24
> **George7a said:**
> 
I have been reading and trying stuff like:
1)EnvyNG

Hello,

Take a look [here]("http://albertomilone.com/envyngfaq.html#A") for full instructions on how to install and use EnvyNG.

You shouldn't need to worry about step 2, but just to make sure you can go to System -> Administration -> Software Sources and make sure "Community-maintained Open Source software (universe) is checked)". Also, you'll probably want to do the first command in 3 to get a graphical interface.

If you've already done all of this and it didn't work, please let us know.

---

### Post by George7a on 2010-04-24
I followd the steps and here is what I am getting "error 2"

> george@george-u:~$ sudo apt-get install envyng-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**envyng-qt is already the newest version.**
The following packages were automatically installed and are no longer required:
  kdenlive-data nvidia-185-libvdpau nvidia-185-kernel-source
  libpostproc-unstripped-51 install-package libavformat-unstripped-52
  libavfilter-unstripped-0 gdebi-kde libswscale-unstripped-0 libsigc++0c2
  libmlt-data libavdevice-unstripped-52
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
george@george-u:~$ sudo envyng -t
/usr/bin/envyng: line 6: cd: /usr/share/envy: No such file or directory
python: can't open file 'interface.py': [Errno 2] No such file or directory
george@george-u:~$ sudo apt-get install envyng-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
envyng-core is already the newest version.
The following packages were automatically installed and are no longer required:
  kdenlive-data nvidia-185-libvdpau nvidia-185-kernel-source
  libpostproc-unstripped-51 install-package libavformat-unstripped-52
  libavfilter-unstripped-0 gdebi-kde libswscale-unstripped-0 libsigc++0c2
  libmlt-data libavdevice-unstripped-52
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
george@george-u:~$ sudo envyng -t
[B]/usr/bin/envyng: line 6: cd: /usr/share/envy: No such file or directory
python: can't open file 'interface.py': [Errno 2] No such file or directory[/B]
george@george-u:~$ 


---

### Post by realzippy on 2010-04-24
Run

```
sudo apt-get install envyng-gtk
```

to install envy correctly in gnome...



...but,your driver should appear in hardware-drivers

---

### Post by George7a on 2010-04-24
it does appear! but When I activate it I got the error that I posted above..

---

### Post by realzippy on 2010-04-24
-edited post from envyng-core to envyng-gtk,did you notice?

BTW,there should be a GUI also...(search the menue)

---

### Post by Jon Monreal on 2010-04-24
Yeah, sorry qt is for KDE. But EnvyNG core should still work.

Had you tried installing EnvyNG before?

---

### Post by George7a on 2010-04-24
I have updated the kernel and now the drivers are working ok and installed.

I still can not get my "cube" and other graphic features back! 

I guess I better open a new thread for this issue, right?

---

