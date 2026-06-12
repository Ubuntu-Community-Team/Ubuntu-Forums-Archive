---
title: "Lucid Console problem"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Gone fishing on 2010-05-01
If I alt control F1 etc I'm not getting the login to a console just a blinking cursor.

Graphical seems to be fine.

Problem with the nvidia driver??

---

### Post by Gone fishing on 2010-05-01
OK I don't get this with my laptop which seems fine.

But my desktop I'm also getting graphical on Alt Control F2 sometimes

---

### Post by the.phantom on 2010-05-01
sorry i haved no solution

i have been using Ubuntu for a few years and when i installed it
i wound up using the default drivers
hardware driver said they had a "approved" driver for my nvida 98
so i installed it, and crashed the system with garbage on the screen and could not find any way to uninstall as was just a mess of colors and such so reinstalled and using the default driver only
can only get 1024 X 760 out of it, but it mostly works

---

### Post by Gone fishing on 2010-05-01
Thanks I'm just using the driver recommended in hardware drivers.

I seem to be getting lots of lucid problems :(

---

### Post by chriswyatt on 2010-05-01
I had that actually once or twice when switching to TTY; it was only temporary though and fixed itself when I went to GUI then back.

I've also got an NVidia card.

---

### Post by Gone fishing on 2010-05-02
Went to launchpad and it looks like a bug - I hope thy fix it because it is a bad one.

---

### Post by GSF1200S on 2010-05-02
I dont know about you guys, but if I run:
```
sudo /etc/init.d/gdm stop
```
my monitor totally shuts off (no signal detected). If I ctrl alt to a different tty, my monitors shut off as well. I can ctrl alt f7 and im back to X, but I cannot get any kernel console at all.

Ive managed to fix plymouth on lucid using uvesafb (this problem existed before I managed this) and I still have this issue. I have a 9800GTX+ running 195 drivers installed through Hardware Drivers.

I have no such issue on Arch, Xubuntu 9.10, nor have I had any issues when I ran debian, sidux, and gentoo.

---

### Post by Gone fishing on 2010-05-02
The problem seems to have resolved itself. I did an update, the update installed 2 packages and the problem seems to have gone (rebooted about 10 time to check) I can now get to tty.

A mystery but I'm pleased.

---

### Post by GSF1200S on 2010-05-02
> **Gone fishing said:**
> The problem seems to have resolved itself. I did an update, the update installed 2 packages and the problem seems to have gone (rebooted about 10 time to check) I can now get to tty.

A mystery but I'm pleased.

I even installed the pre-released updates and didnt have any luck with this issue. In my case, I know that its due to the Nvidia driver. After the updates (and kernel update), I had to enter low graphics mode for some reason. After I reinstalled the driver through Hardware Drivers and applied changes to Xorg, I killed X (wondering if, since I was running vesa drivers at that point, the console would work). The console worked fine, and I was able to switch tty's just fine. As soon as I rebooted into Nvidia drivers, my monitors shut off when I kill X/gdm. I use the console alot, so this is killing me. Sometimes I find myself booting to 9.10 because of this ;). Perhaps a bug in the new driver? I didnt have this issue with the drivers in Karmic (they are 185 versus 195 though).

---

### Post by jbatista on 2010-05-23
I did a fresh install of Lucid, amd64, this weekend on a new desktop (Intel i7 920, 8GB RAM, ASUS GeForge GT220 with HDMI). 
I installed the NVidia controller and it seems to have solved a couple of weird crashes where I'd lose control over the keyboard but not the mouse (the pointer would move, but unfortunately I couldn't click anything, and the system monitor applet would not budge either ... I hard to hard reset!).

The boot screen was on low resolution, and on the first or second reboot (I forgot which) I got a window claiming that the screen was running on low resolution (which it was). 
The splash screen is still showing on low resolution, however after GDM starts all seems OK. I've tinkered with /etc/default/grub (particularly setting GRUB_GFXMODE=1920x1080 and GRUB_GFXPAYLOAD_LINUX=keep) and ran update-grub, but it seems to have made no difference.

The console screens (Ctrl+Alt+F1 through F6) seem to be gone, with only a large cursor blinking (I'm guessing it's still on low resolution). I'm a little worried because those six suckers have helped me out in the past when X was playing up. And I'm also hesitant to going back to VESA and turn off the NVidia driver for fear that the X crashes return.

I suppose this is an issue of the NVidia driver with the virtual consoles, but I'm not sure where I should be looking at to solve this.

UPDATE: I looked into this thread: [http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-%3D-black-blank-screen-385376/](http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-%3D-black-blank-screen-385376/)
and I've found there is no /etc/inittab file present in my system!! Pretty weird, as the system runs the same. I don't know if this is a Lucid thing.

---

