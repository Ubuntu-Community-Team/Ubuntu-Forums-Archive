---
title: "Change splash screen and Ctrl + Alt + Fx terminal resolutions"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by sdlynx on 2010-04-27
I updated to 10.04 (RC) and everything is basically fine, but after installing nVidia's proprietary drivers, the resolution for the boot up splash screen is now much smaller, along with the resolution for any of the terminals I can bring up with Ctrl + Alt + F[1-7].

Is there some setting(s) I can change to fix this?

---

### Post by Jon Monreal on 2010-04-27
The easy way to change the boot resolution would be to get StartUp-Manager (just search the Ubuntu Software Centre under Applications for startup-manager and find the package with the same name and install it).

For the terminal, you may wish to edit your settings (Edit -> Profile Preferences).

If you need further assistance, please feel free to ask.

---

### Post by sdlynx on 2010-04-27
> **Jon Monreal said:**
> The easy way to change the boot resolution would be to get StartUp-Manager (just search the Ubuntu Software Centre under Applications for startup-manager and find the package with the same name and install it).

For the terminal, you may wish to edit your settings (Edit -> Profile Preferences).

If you need further assistance, please feel free to ask.

I attempted this, but when I changed the resolution to 1024 x 768 (24 bit) on my 1280 x 800 monitor, I only get a series of random dots showing up for either tty1-7 and also the boot up screen.  I've tried 16 bit and 8 bit, neither of which worked.  If I lowered the resolution back to 800 x 600 then my problem wouldn't be solved...

---

### Post by Jon Monreal on 2010-04-28
If you want to see what modes are supposed to be supported, you can try
```
sudo apt-get install hwinfo
```then
```
sudo hwinfo --framebuffer | grep 'Mode'
```Also, when you say "I only get a series of random dots", are they larger  and go off the screen? Thanks.

EDIT: Sorry, I missed the Ctrl + Alt + Fx part. To fix this, go to a terminal and type
```
sudo dpkg-reconfigure console-setup
```
and change settings as required.

---

### Post by sdlynx on 2010-04-29
I've attempted to attach an image that shows what is showing up at the top of my screen when I switch to any of the tty's and also while the computer boots up/shuts down.

I installed hwinfo and my graphics card supports basically every setting.  Reconfiguring console-setup didn't seem to work, because I actually think that the same problem is affecting the terminals and the bootup/shutdown screens.

Any ideas from the image?

---

### Post by Jon Monreal on 2010-04-29
Take a look at [this]("http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html"); looks like it could be a problem with the NVIDIA drivers (that can be fixed).

---

### Post by sdlynx on 2010-04-30
> **Jon Monreal said:**
> Take a look at [this]("http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html"); looks like it could be a problem with the NVIDIA drivers (that can be fixed).

Thanks! I just couldn't find out what the name of the boot screen thing was (plymouth, for future reference).  Now I should be able to find my way out.

Edit: I followed the instructions at the bottom of that page, which led me to comment #34 on launchpad, and now it works.

---

### Post by Jon Monreal on 2010-04-30
Glad to hear everything worked.

If you don't have any further problems, could you mark this thread as solved by going above the first post on the page and selecting Thread Tools>Mark as solved?

Thanks.

---

### Post by MyKal on 2010-05-21
could you possibly post the steps you took to fix the problem before adding solved to your header as most of us click on "solved" links because we are looking for solutions rather then just reading conversations for 20 minutes

sorry if that sounds hostile i just couldn't think of a better way to word it

---

### Post by sdlynx on 2010-05-23
> **MyKal said:**
> could you possibly post the steps you took to fix the problem before adding solved to your header as most of us click on "solved" links because we are looking for solutions rather then just reading conversations for 20 minutes

sorry if that sounds hostile i just couldn't think of a better way to word it

My apologies, here's what I did.

1) [http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html](http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html) the steps on this page (most of which I had already done... strange).

2) ```
* In /etc/modprobe.d/blacklist-framebuffer.conf, comment out "blacklist vesafb" and add "blacklist vga16fb"
 * In /etc/initramfs-tools/modules, add fbcon and vesafb
 * Run update-initramfs -u
```

3) added GRUB_CMDLINE_LINUX=" vga=792" in /etc/default/grub

Considering I did this a while ago, the steps may not be 100% accurate, but I believe it is about right.

---

