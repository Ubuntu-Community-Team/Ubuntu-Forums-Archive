---
title: "New PC troubles"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by Strategist01 on 2010-12-21
Hi guys.

So I recently got and built a new PC, very nice and all should run everything very well!

Now, I have a GTX 460 FTW edition (768 MB) - and a Samsung BX2450 monitor. Now I am currently in 640x800 resolution when I should be at 1090x1024 (I think). I have looked and seen that I needed to DL the latest drivers - which I have. However, installing them is a different matter. I ran them in terminal, with root privileges which I got from doing a gksudo of nautilus and running in terminal. But it says that I must exit the X server. That has been a bit of a mystery to me. How would I go about setting this up?

Also, I have another Ubuntu 10.04.1 install on my laptop - is there any way I could bring certain programs across without having to download them from the web? Thanks!

---

### Post by matt_symes on 2010-12-21
Hi

Press CTRL ALT F1 together to open a console.

Then type

```
sudo /etc/init.d/gdm stop
```

This will stop X.

Kind regards

---

### Post by Verbeck on 2010-12-21
try doing it from tty1 (alt+ctrl+F1)
sudo service gdm stop

for the second issue, try aptoncd to copy stuff from /var/cache/apt/archives from one computer to the other
(you could do it manually too if you want)

---

### Post by Strategist01 on 2010-12-21
Thanks. I will try that now and see how it goes.

---

### Post by matt_symes on 2010-12-21
Hi

Also have a look in the apt archive directory.

```
ls /var/cache/apt/archives/
```

Kind regards

---

### Post by msandoy on 2010-12-21
What is wrong with the restricted driver installation in the systems menu?

---

### Post by Strategist01 on 2010-12-21
Ok, I have done that - managed to stop X and install the drivers and then restart it. I now have full 1920x1080 resolution! Thanks so much ^^. I will try to move the stuff across tomorrow, but still a bit unclear as how to do that...

---

### Post by Verbeck on 2010-12-21
glad you got it working
to move the stuff, navigate to /var/cache/apt/archives and copy .deb file from there to a thumb drive/
and from the other computer, run *gksu nautilus* to open the root nautilus window and copy the stuff off the thumb drive to var/cache/apt/archive
(or you could do it with a gui using aptoncd on both machines: create a .iso one one>copy it to the other >use restore from the program and select the iso)

after that, the programs could be installed from the software center/synaptic without downloading, unless there's a newer version in the software channel
(make sure the software sources are the same)

---

### Post by Strategist01 on 2010-12-21
Ok. So I copy the /var/cahe/apt/archives from the PC old install, then copy that into the same directory of the new install?

---

### Post by Verbeck on 2010-12-21
> **Strategist01 said:**
> Ok. So I copy the /var/cahe/apt/archives from the PC old install, then copy that into the same directory of the new install?
yes. if both of them uses the same repos, it would work

---

