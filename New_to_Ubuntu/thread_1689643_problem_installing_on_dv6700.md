---
title: "problem installing on dv6700"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by nicktheww2fanatic on 2011-02-17
hey there folks, I'm trying to install Ubuntu 10.10 (64 bit) on my wife's old HP Pavilion dv6700.  Here are the specs:

AMD Turion X2 TL-60 2.0Ghz
3GB RAM
NVIDIA GeForce 7150M/ nForce 630M

Now, when I try to run ubuntu, whether its installed from USB, DVD or Wubi, it always looks like this:

[IMG]http://i54.tinypic.com/153pms9.jpg[/IMG]

How do I fix this???

---

### Post by PunkLV on 2011-02-17
1: This happens when you start from LiveCD as well?
2: Did you install nvidia drivers from repositories?
3: Are these Nvidia's drivers?
4: Alt+Ctrl+F1 -> login ```
sudo service gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install nvidia-glx
sudo service gdm start
```

---

### Post by nicktheww2fanatic on 2011-02-17
> **PunkLV said:**
> 1: This happens when you start from LiveCD as well?
2: Did you install nvidia drivers from repositories?
3: Are these Nvidia's drivers?
4: Alt+Ctrl+F1 -> login ```
sudo service gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install nvidia-glx
sudo service gdm start
```

1. Yes
2. No
3. Can't figure out how to get the drivers installed, can't click anywhere...
4. I can't even connect to a network, so will this work?

---

### Post by Hippytaff on 2011-02-17
You should be able to connect via ethernet without any problems. If so you can either boot to your dodgy desktop, press CTRL+F1 and then follow PunkLV's instructions or at the os/kernel selection screen (grub menu) choose recovery/rescue mode and again follow the instuctions. Also you can try (at the grub menu) highlighting ubuntu, pressing e (to enter the grub options windows thingy) and changing the words 'quiet splash' to 'nomodeset' Press CTLR+X to boot - if you get to the desktop choose to install the recommended Nvidia Driver from the menu Adminstration -> Additional Drivers.

---

### Post by nicktheww2fanatic on 2011-02-17
> **Hippytaff said:**
> You should be able to connect via ethernet without any problems. If so you can either boot to your dodgy desktop, press CTRL+F1 and then follow PunkLV's instructions or at the os/kernel selection screen (grub menu) choose recovery/rescue mode and again follow the instuctions. Also you can try (at the grub menu) highlighting ubuntu, pressing e (to enter the grub options windows thingy) and changing the words 'quiet splash' to 'nomodeset' Press CTLR+X to boot - if you get to the desktop choose to install the recommended Nvidia Driver from the menu Adminstration -> Additional Drivers.

Thanks!  Pressing E, then changing that line did it for me!  I just downloaded and installed the nvidia drivers, and now its running great!

---

### Post by Hippytaff on 2011-02-17
Excellent - glad you managed to sort it. :-)
 
Remember to mark the thread as solved in the thread tools at the top of the page ;-)

---

### Post by nicktheww2fanatic on 2011-02-17
> **Hippytaff said:**
> Excellent - glad you managed to sort it. :-)
 
Remember to mark the thread as solved in the thread tools at the top of the page ;-)

one step ahead of you there!  Thanks for the assistance!

---

### Post by Hippytaff on 2011-02-17
> **nicktheww2fanatic said:**
> one step ahead of you there! Thanks for the assistance!
 
oh yeah doh! :roll:
 
your welcome!

---

