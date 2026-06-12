---
title: "Installing Ubuntu Inside Windows Vista help?"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by SPazzo on 2009-08-31
Hi.  I am a total noob to Ubuntu and Linux in general.  I have the 9.04 disc.  I want to install it inside Windows.  I followed the steps (insert disc, click install inside windows, fill out the required forms, restart).

Now, when I booted up my computer the boot screen came up.  I clicked Ubuntu.  Then a screen came up saying something like that I should boot up with *"noapic"*.  And it just stayed like this.

How do I got about doing this?

Thanks.

---

### Post by sideaway on 2009-09-01
> **SPazzo said:**
> Hi.  I am a total noob to Ubuntu and Linux in general.  I have the 9.04 disc.  I want to install it inside Windows.  I followed the steps (insert disc, click install inside windows, fill out the required forms, restart).

Now, when I booted up my computer the boot screen came up.  I clicked Ubuntu.  Then a screen came up saying something like that I should boot up with *"noapic"*.  And it just stayed like this.

How do I got about doing this?

Thanks.

I believe in GRUB, there's a couple of options, basically, highlight the option, press 'e' this will allow you to edit the command line.

At the end of the kernel line add the words noapic so it should look something like:
```
kernel /boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro quiet splash noapic
```

Something like that anyway. Once you're into ubuntu edit /boot/grub/menu.lst so the change stays permanent.

---

### Post by steveneddy on 2009-09-01
I personally feel like you should use [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") on Windows to install Ubuntu in.

You will be much happier instead of using Wubi.

Please read all of the documentation before installation and running this software.

Don't hesitate to ask LOTS of question if you don't understand.

---

### Post by Paqman on 2009-09-01
> **steveneddy said:**
> I personally feel like you should use [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") on Windows to install Ubuntu in.

You will be much happier instead of using Wubi.


Not necessarily. Virtualisation is very different to dual booting, and very resource-intensive. Wubi is an excellent way to get into Ubuntu IMO.

---

### Post by anujpathania on 2009-09-01
What you did was dual boot using wubi, if you want virtualization (virtual machine) you need to use software like VMWare.

Also in IMHO, dual boot is way better than Virtual Machine, performance wise.

---

### Post by Paddy Landau on 2009-09-01
> **SPazzo said:**
> Hi.  I am a total noob to Ubuntu and Linux in general.  I have the 9.04 disc.  I want to install it inside Windows.
Just to clarify...

You don't install Ubuntu "inside" Windows, just as you wouldn't install Windows "inside" a Mac.

You can install Ubuntu and you can install Windows, but they are completely different operating systems.

If you are a Windows user, the easiest way -- if you want to experiment and find out more -- is to install [Wubi]("http://wubi-installer.org/").

After you've installed it, reboot. You'll be given the option of starting Windows or Ubuntu. This will happen every time you reboot.

Wubi has certain limitations (e.g. it's slower and less reliable, and you can't see your Ubuntu files from Windows), but it will give you a good idea of what Ubuntu is like, and whether you want to install it seriously.

If you don't like Ubuntu, you just uninstall Wubi from Windows. Simple.

If you do like it, then you uninstall Wubi, and install Ubuntu properly. There are plenty of threads in this forum to explain how to do a native installation. You don't have to lose your Windows; instead, you can dual-boot with Windows.

HTH

---

### Post by Paqman on 2009-09-01
> **Paddy Landau said:**
> 
You don't install Ubuntu "inside" Windows, just as you wouldn't install Windows "inside" a Mac.


Actually the Wubi installer does refer to installing "inside" Windows (at least, it did the last time I tried it. Maybe not the most accurate piece of terminology, but close enough in my book.

---

### Post by SPazzo on 2009-09-01
> **Paqman said:**
> Actually the Wubi installer does refer to installing "inside" Windows (at least, it did the last time I tried it. Maybe not the most accurate piece of terminology, but close enough in my book.

In the disc I got it actually says *"Install inside Windows".*

Anyway.  I just tried doing what sideaway said and it worked.

Thank you so much.

---

### Post by lackhand on 2009-09-01
> **SPazzo said:**
> In the disc I got it actually says *"Install inside Windows".*

It does indeed say that.  But it is a bit misleading.  :D  

I've played with VirtualBox a little bit, and I think I prefer dual-booting, but then it depends on what you really want to do with it.  Wubi isn't a great longterm solution, but is a good way to try Ubuntu out if you're just not sure about it.  Once you decide to install and use Ubuntu for good, you should move away from Wubi.

---

### Post by SPazzo on 2009-09-01
> **lackhand said:**
> It does indeed say that.  But it is a bit misleading.  :D  

I've played with VirtualBox a little bit, and I think I prefer dual-booting, but then it depends on what you really want to do with it.  Wubi isn't a great longterm solution, but is a good way to try Ubuntu out if you're just not sure about it.  Once you decide to install and use Ubuntu for good, you should move away from Wubi.

Yep, that's my plan.  I'm just using Wubi to get the hang of it until I can afford another computer.  I kinda do need to keep Vista, and I don't really want to do a dual-boot.

---

### Post by Paddy Landau on 2009-09-01
> **SPazzo said:**
>  I'm just using Wubi to get the hang of it until I can afford another computer.  I kinda do need to keep Vista, and I don't really want to do a dual-boot.
You already have a dual-boot with Wubi -- you have to choose one or the other at boot-time!

As long as Wubi works for you, it's fine, but do be aware that it's a little slower and less reliable than a native installation. If you want to keep Ubuntu permanently, I do recommend that you uninstall Wubi and install Ubuntu as a native installation, dual-boot.

---

