---
title: "A little understanding needed on how nvidia drivers work please"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by psfelgate on 2009-07-09
Hello, this is more of a question of how the nvidia drivers work in ubuntu so that I can understand for myself.

The reason I'm asking is because on my desktop pc I have jaunty installed and I ran ```
sudo apt-get install nvidia-glx-180
``` This installed the drivers but I kept getting errors about there being no nvidia module available to load during boot.

So I removed kernel 2.6.28-13-generic, booted up with kernel 2.6.28-11-generic and then ran ```
sudo apt-get install nvidia-glx-180
``` This time when I booted something called DKMS started running and appeared to be compiling the nvidia driver.

After that I installed kernel 2.6.28-13-generic again and this time it was able to find the nvidia module.

My question is: Why was the nvidia-glx-180 package unable to compile the module just because I had a newer kernel than the stock version? There was never any indication when installing nvidia-glx-180 that I needed a specific kernel to compile it.

I guess I just want to understand a bit more about how this module compiling thing works :p

---

### Post by nhasian on 2009-07-09
when i first started using ubuntu with 8.04 i wanted the newest nvidia driver so i downloaded it and installed it from their website.  i learned that everytime the kernel was updated, it would break the driver and i had to recompile it so i could get high resolution desktop again.  

Then when i upgraded to 8.10 i just decided to stick with the restricted drivers in system->administration->hardware drivers.  now when the kernel gets updated, it automatically recompiles the nvidia driver for it.  much easier that way :)  also when newer versions of nvidia drivers appear in the hardware drivers you can easily switch to them.  for example it was easy to go from 177 to 180.  i think i'm on 185 now.

---

### Post by psfelgate on 2009-07-09
Question: Why must the nvidia drivers be recompiled when upgrading the kernel and not other drivers like wifi etc.?

And also why didn't nvidia-glx-180 compile itself the first time it was installed? I had to reboot using the older kernel before it would start auto compiling the driver and then it had to do it again when I rebooted into the new kernel.

And lastly, where did you get 185? is there a package available for it? The latest one I saw in synaptic was 180

Sorry for all the questions, but the more one knows about how linux works the easier it is to solve problems when they happen.

EDIT: Thanks for the response ;)

---

### Post by mano cazalet on 2009-07-09
[DKMS]("http://linux.dell.com/projects.shtml#dkms") stands for Dynamic Kernel Module Support

as for the new and beta drivers there are some ppa's with debs

---

### Post by psfelgate on 2009-07-09
> **mano cazalet said:**
> [DKMS]("http://linux.dell.com/projects.shtml#dkms") stands for Dynamic Kernel Module Support

as for the new and beta drivers there are some ppa's with debs

Forgive me, but what do you mean by ppa's?

---

### Post by mano cazalet on 2009-07-09
Personal Package Archives
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

---

### Post by Paqman on 2009-07-09
As nhasian said, using the Hardware Drivers tool is by far the easiest way to handle graphics card drivers. It'll automate the whole thing for you.

---

### Post by psfelgate on 2009-07-09
> **Paqman said:**
> As nhasian said, using the Hardware Drivers tool is by far the easiest way to handle graphics card drivers. It'll automate the whole thing for you.

I know it is the easiest thing to do but I want to understand how linux works as well :)

I'd still like to know why only the nvidia driver had to be recompiled but not other drivers when updating the kernel?

---

### Post by Paqman on 2009-07-09
> **psfelgate said:**
> 
I'd still like to know why only the nvidia driver had to be recompiled but not other drivers when updating the kernel?

Are you definitely using any other non-open source drivers?

---

### Post by psfelgate on 2009-07-09
> **Paqman said:**
> Are you definitely using any other non-open source drivers?

It is a stock jaunty install from a live-cd. Only thing I've done so far was:

```

sudo apt-get update
sudo apt-get upgrade
*reboot
sudo apt-get install linux-image-generic
*reboot
sudo apt-get install nvidia-glx-180
sudo nvidia-xconfig
*reboot

```

After the above X couldn't start anymore because of not being able to find the nvidia module.

So I did this:

```

sudo apt-get remove linux-image-generic
*reboot and select older kernel

```

It was at this point that DKMS only kicked in and started compiling the driver.

Then I installed the new kernel again:

```

sudo apt-get install linux-image-generic
*reboot

```

Now DKMS kicks in again and starts compiling the nvidia module again and everything works.

So the question is why didn't it just do that when I first installed nvidia-glx-180?

Why do I have to remove the new kernel and reboot just to get it to compile the driver?

---

### Post by Nexusx6 on 2009-07-09
> Question: Why must the nvidia drivers be recompiled when upgrading the kernel and not other drivers like wifi etc.?

Other drivers are in fact upgraded with a kernel update. Someone with better understanding and elaborate or correct, but in essence the linux kernel has very good generic drivers for just about every standard device in a computer: hard drive, keyboards, CD drives, mouse, etc etc. Included in this list are the drivers for wifi. It stands then that when you do a kernel update you update the drivers as well for these components. 

The Nvidia drivers don't fall into this category. The drivers you're installing are proprietary, meaning no one outside of Nvidia is aloud to see the source code, and are installed separately of kernel. I can't really elaborate more than that, but I hope you have the general idea.

---

### Post by psfelgate on 2009-07-09
> **Nexusx6 said:**
> Other drivers are in fact upgraded with a kernel update. Someone with better understanding and elaborate or correct, but in essence the linux kernel has very good generic drivers for just about every standard device in a computer: hard drive, keyboards, CD drives, mouse, etc etc. Included in this list are the drivers for wifi. It stands then that when you do a kernel update you update the drivers as well for these components. 

The Nvidia drivers don't fall into this category. The drivers you're installing are proprietary, meaning no one outside of Nvidia is aloud to see the source code, and are installed separately of kernel. I can't really elaborate more than that, but I hope you have the general idea.

That makes sense to me. But now it makes me wonder why I don't have to recompile drivers for ndiswrapper? because ndiswrapper, as far as I know, is not built into the kernel.

Could it be that the ndiswrapper module is compiled in such a way that it is independant on the kernel? :? Am I correct?

---

### Post by Nexusx6 on 2009-07-09
The clue about NDISwrapper is in its name. NDISwrapper is not a driver, it's a wrapper, it helps translate the window's driver instructions into ones that the Linux OS can understand, but it isn't a driver in of itself.

---

### Post by WatchingThePain on 2009-07-09
I have always loved installing Nvidia driver on Ubuntu. Just a tick in a box Lol. Haven't seen that anywhere else. Some distro's mate it's hell to get the Driver installed. Then enable desktop effects et Voila!.

Another thing that helps (only some distro's) is Envy.

---

