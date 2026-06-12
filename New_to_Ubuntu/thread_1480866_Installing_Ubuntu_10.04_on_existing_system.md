---
title: "Installing Ubuntu 10.04 on existing system?"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by Skillet98 on 2010-05-12
Alrighty, this could be quite a long post so if you don't want to read a wall of text... walk away now.

I haven't been here in quite some time, so forgive me if this belongs somewhere else. I figured since I'm still an absolute beginner, it belongs here. :p

Now, I would like to install Ubuntu 10.04. Personally, I think it just looks amazing. But through my travels around this thing we call the internet, I heard a little something about that particular distro using th new Grub 2 boot loader.

I'm on an Asus laptop running Windows Vista and an older version of Xubuntu that I used to also installed the KDE desktop. I can't remember which versions these are.

I seem to remember hearing something about Grub 2 not recognizing Windows installations or somehow making it so that you are unable to load windows through that loader.

I just recently re-installed Vista on my laptop and spent a lot of time reconfiguring a lot of programs and files. I'm not really in the mood to do that again.

So my question is this... is there any way to install Ubuntu 10.04 WITHOUT also installing Grub 2? Or did I simply hear wrong and there's nothing to worry about?

I'm going to make some backups of my most important files on Vista but I also have about 100GB of music an another 50GB of images, photoshop documents, files for work, and a ton of programs I'd rather not re-install at this time. :p

For those who didn't want to read all of that... I want to install Ubuntu 10.04 on a computer that's currently running Windows and another Linux distro with no complications and Windows still being accessible... tell me how.

---

### Post by aysiu on 2010-05-12
> **Skillet98 said:**
> 
So my question is this... is there any way to install Ubuntu 10.04 WITHOUT also installing Grub 2? Or did I simply hear wrong and there's nothing to worry about? Either [Wubi](http://www.psychocats.net/ubuntu/wubi) or [VirtualBox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by Skillet98 on 2010-05-12
Yeah-no...

I don't want to install it as a program in Windows. That's pretty much just pointless in my opinion.

Also, Wubi apparently only works if the current boot loader being used is Windows'.

I'm actually running Grub 1 right now. Which is my current boot loader. It works well, allowing me to select windows or Ubuntu when  start my system.

Is there really no other way to do this with Grub 2?

---

### Post by aysiu on 2010-05-12
> **Skillet98 said:**
> Yeah-no...

I don't want to install it as a program in Windows. That's pretty much just pointless in my opinion.

Also, Wubi apparently only works if the current boot loader being used is Windows'.

I'm actually running Grub 1 right now. Which is my current boot loader. It works well, allowing me to select windows or Ubuntu when  start my system.

Is there really no other way to do this with Grub 2?
If you reinstalled Vista, what's managing Grub? Do you still have Xubuntu installed? If so, just upgrade to 10.04. Grub2 will not be installed if you upgrade (you'd have to separately upgrade that).

Also, Wubi doesn't install Ubuntu as a Windows program... well, it sort of does, but after it does, you can boot into Ubuntu as a fully functional OS. It does **not** boot Windows. It just lives on the Windows partition as a virtual partition.

---

### Post by Skillet98 on 2010-05-12
Currently, my xubuntu/kubuntu installation is managing Grub. I downloaded Xubuntu a couple years ago and when I got my laptop last year, I ended up partitioning the hard drive and installing Xubuntu. 

I had some problems with Vista a few months ago and had to re-install everything. I also decided to install the Kubuntu Desktop. So that's wa I'm currently using.

So according to what you said, could I just load the Ubuntu desktop and then upgrade to version 10.04 through KDE and have the desired effect with no Grub 2 boot loader?

---

### Post by narendraD on 2010-05-12
Well Technically you can upgrade you Xubuntu with Kubuntu and it will not update grub. However upgrading a system with 2 DE's is likely to break a few packages and leave your system affected to any extent. I would suggest remove Kubuntu (because that was installed as an addon to Xubuntu) as well as any KDE apps and then upgrade. when you have a successfull upgrade then you can add KDE and KDE apps later.
Best of Luck.

---

### Post by aysiu on 2010-05-12
Two desktop environments won't result in broken packages, but you will probably have a very cluttered system.

But, yes, you can just install Ubuntu 9.04 and upgrade to 9.10 and then upgrade to 10.04, and you will stay with Grub.

9.10 and 10.04 both use Grub2.

---

