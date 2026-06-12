---
title: "os startup options"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Pedro Pino on 2008-12-26
Hello, I use Ubuntu 8.10. When I start up,I get options to startup with besides the Ubuntu 8.10. I would like to startup only with Ubuntu 8.10. 
How can I clear the os startup list? Thanks!

---

### Post by hamofgrey on 2008-12-26
Luckly someone else just posted about the same problem so I did a quick copy n paste job!:

 Re: Cleaning up the GRUB boot up menu
Hi there,

Here is a tutorial on how to clean GRUB up. Enjoy:

[http://www.howtogeek.com/howto/ubunt...fter-upgrades/](http://www.howtogeek.com/howto/ubunt...fter-upgrades/)

This will show you how to get rid of different options from grub. Makesure that you test everything works in the kernel upgrades before you delete the other older kernel options from the list.

Also I personally think it's important not get rid of things like the Recovery and MemTest options, otherwise if anything major goes wrong you have no real way of being to sort the problem out. You are still able to boot into these options using grub but it will require a little bit of extra effort by typing something into the command line.

Perhaps a better way of explaining it is, that when you use Windows Vista on a laptop or PC and there is a power cut on the next boot Vista will ask you if you want to boot up in the regular fashion or boot up in other recovery modes (e.g. with command-line etc). It would be dangerous to get rid of all the options as you may depend on some of the recovery features in certain situations. The same can be applied to Ubuntu, there may be certain situations where some of the recovery features are also needed.

I hope this helps
Last edited by hamofgrey; 7 Minutes Ago at 07:18 AM..
hamofgrey is online now Report Post   	Edit/Delete Message

---

### Post by scragar on 2008-12-26
It's all store in the grub list file:
```
gksu gedit /boot/grub/menu.lst
```

---

### Post by kostkon on 2008-12-26
You could install *Start-Up Manager* for a GUI utility that allows you to edit many of your boot options. Here's [a good guide about it]("http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html").

---

### Post by drs305 on 2008-12-26
I highly recommend StartUp-Manager. It is a gui application that will let you tweak a variety of grub's menu.lst items, including the number of kerenls you see, the default OS, whether you see the menu and/or for how long, etc.

You install it from the terminal with:
```

sudo apt-get install startupmanager
```

To run, System > Administration > StartUp-Manager.

Here is a tutorial that will explain how to set it up and explains the options:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by JohnFH on 2008-12-26
> **hamofgrey said:**
> Luckly someone else just posted about the same problem so I did a quick copy n paste job!:

 Re: Cleaning up the GRUB boot up menu
Hi there,

Here is a tutorial on how to clean GRUB up. Enjoy:

[http://www.howtogeek.com/howto/ubunt...fter-upgrades/](http://www.howtogeek.com/howto/ubunt...fter-upgrades/)



You mean this link don't you? :
[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")

---

### Post by theozzlives on 2008-12-26
```
sudo apt-get install startup-manager
```

system>administration>startup manager

uncheck show boot menu

---

