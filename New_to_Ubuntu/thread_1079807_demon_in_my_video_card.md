---
title: "demon in my video card"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by moondoggy17 on 2009-02-24
ok so i couldn't get ubuntu to start after i installed my video card. i removed it reinstalled ubuntu  thought i got the nvidia drivres installed but when i go to start up i get this

[IMG]http://i105.photobucket.com/albums/m201/goemon17/DIGI0001.jpg[/IMG]



i don't know whats going on but this is what i'm workin with
ASUS Guppy mobo
celeron D @ 2.93 ghz
1.25 gb of ram
nvidia geforce 6200 256 mb factory overclock
80 gb hitachi deskstar
ubuntu 8.04.1 lts

---

### Post by Catalyst2Death on 2009-02-24
sorry, but have you tried starting it without the video card installed?  Plug the monitor into the onboard video port and see if you can boot, that will at least isolate the problem to the video card...

also check here:
[http://ubuntuforums.org/showthread.php?t=918166](http://ubuntuforums.org/showthread.php?t=918166)

and:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229753](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229753)

Looks like you'll have to boot without the video card.

I would try purging the nvidia drivers, putting the video card back in and trying again.  If that doesn't work, you could try to install the drivers before you plug the video card in (but I don't know if this will work)

---

### Post by moondoggy17 on 2009-02-25
ty for the links they helped a little but still having problem but this is what i did

with video card still installed i went into bios and changed my primary video adapter to onboard, saved and shut down
connected my monitor to onboard video and booted ubuntu
logged in (yay) and saw that there was a restricted driver installed restricted driver and rebooted 
changed bios setting back to pci and booted and guess what i got......................................................

[IMG]http://i105.photobucket.com/albums/m201/goemon17/DIGI0004.jpg[/IMG]

any thoughts?

---

### Post by Catalyst2Death on 2009-02-26
Try this:

boot into recovery mode, if you get to a login prompt, great then you can install the nvidia drivers manually.  If not, follow the steps you previously did to boot from the on board graphics and then follow these steps:

if you are using the onboard card and get to the login screen, first hit ctrl+alt+f2
then:

```
sudo killall gdm

```
(optionally, to make sure you don't miss updates first:) NOTE: you may need to restart here
```
sudo apt-get update && sudo apt-get upgrade
```

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/180.29/NVIDIA-Linux-x86-180.29-pkg1.run

```
```
chmod +x NVIDIA-Linux-x86-180.29-pkg1.run

```
```
sudo ./NVIDIA-Linux-x86-180.29-pkg1.run

```

if all goes well, it will prompt you through the installation, compile the kernel module and configure X11 for you.  Then, reboot switch to the nvidia card if you need to and cross your fingers.

---

