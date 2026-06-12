---
title: "Low Plymouth screen reolution in Maverick (GeForce GTX 260)"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by veroslav on 2011-02-07
Hi all,

I've just installed Ubuntu 10.10 (dual boot with Windows 7) and am trying to resolve the few small issues I still have. This is one of them.

I've heard of many people having the issues with Plymouth and the ugly looking screen at launch/shutdown but I would like to get an advice for my situation specifically.

So, every time I boot Ubuntu, first there is only an underscore (_) blinking for a few seconds. Then, an ugly screen (low res) showing "Ubuntu 10.10" or similar is shown for a brief period of time, and then after that the login window is shown in the correct resolution.

Also, on shutdown, I get a similar ugly screen (low res) that displays some text about processes being shutdown, and then the computer shuts down.

I've found a lot of people recommending this in order to fix the Plymouth issues:

```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash

sudo update-initramfs -u
```Is this the way to go for me as well? Is there a risk of destroying anything by running the commands above? I've installed the closed drivers from NVidia for my card (GeForce GTX 260), the ones that popped up in "Additional Drivers" menu.

What is your recommendation?

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by ajgreeny on 2011-02-07
One possible way out is to try **Startup manager** from the repos, which can set the various resolutions and make all the difference to plymouth displays.  It may be a bit trial and error, but I have used it in Linux Mint 10 with success, when I tried that.

---

### Post by veroslav on 2011-02-07
Thank you for your response,

I've looked up StartUp-Manager and it appears to do exactly what I want and also
it appears that it can remove and limit the number of kernel versions that appear in the boot menu, currently it is displaying two but I would like it to only show the one (latest) I am actually using.

I will have a go tonight when I am back home from work.

Thanks again.

Regards,
Veroslav

---

### Post by ikt on 2011-02-07
> **veroslav said:**
> What is your recommendation?

Honestly, I have the exact same issue, and got a hold of it very early on after plymouth was released during the early alphas:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/563878](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/563878)

I also dual boot with windows 7, not so much anymore, but I when I think about how the windows 7 boot up looks a lot better, but my ubuntu boot up takes half the time the win7 bootup takes, I don't seem to care as much.

---

### Post by veroslav on 2011-02-07
Hi Ikt,

I agree with you, it is absolutely not a big issue, its just that I've managed to fix a couple of major issues after the installation (getting wireless to work) that I dont think fixing the Plymouth resolution should be that hard. I mean, everything else works perfectly so I would like this to work perfectly as well :)

However, reading the link pointing to the bug description you've posted in your post, it appears that using the Start-Up Manager might not be the best idea and might not relly fix the issue. Could anyone confirm any success by using this tool to fix the Plymouth resolution issue?

Thanks.

Regards,
Veroslav

---

### Post by Huss on 2011-02-12
I had a similar issue after a few updates; The boot/shutdown splash was even worse after I installed the radeon driver 'fglrx'.

After trying start-up manager and a few other bits of advice I came across this post:
[]("http://askubuntu.com/questions/16874/boot-screen-in-low-graphics-text-mode")

One warning about following this work around, I got the resolution wrong (1280x900) and I had to boot into command line to fix it. 

The resolution isn't perfect but better than the verbose and basic option.

---

