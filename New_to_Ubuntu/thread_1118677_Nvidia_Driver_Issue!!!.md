---
title: "Nvidia Driver Issue!!!"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by tampablendie on 2009-04-07
Hey guys I'm relatively new to Ubuntu and have run into a serious video driver problem. I downloaded the install file from Nvidia specifically for my platform. I disabled X by running

sudo /etc/init.d/gdm stop

I then ran the install file

sudo sh NVIDIA-Linux-x86_64-180.44-pkg2.run

Upon restart there is a header saying that it is checking battery life( don't know why because this is not a laptop??) then there seems to be an error message saying something like

running local boot scripts etc/rc.local

I'm not a hundred percent on that as the error whips by, and is then followed by a window stating that my video driver is not configured and that I am in low graphics mode. So I configure the video driver and go to desktop.

I have tried to go to the menu item nvidia xconfig settings. But it always gives me an error stating that I'm not running an x config file and to run

nvidia-xconfig

which I do and still I can't get into nvidia xconfig settings. So I disabled the proprietary drivers in hardware settings and restarted. Everything booted up alright with no errors, so I tried to enable the proprietary drivers again and rebooted.

Now the system crashes everytime I try to boot with multicolored screen.

Help!!  Thanks in advance guys!

How do I get rid of the manual install I tried and get the program "Hardware Drivers" to work again??

---

### Post by madverb on 2009-04-07
try doing a manual reinstall of the nvidia drivers

sudo apt-get install nvidia-177-kernel-source

---

### Post by tampablendie on 2009-04-07
Thanks for the reply Madverb.  I think I'm past that point now, my system is totally screwed up!  I ran a command to figure out what kernel I was running(can't remember the command now), which told me I was running kernel .23.  So I installed the Nvidia pakages for that kernel.  Well it turns out that I was actually running kernel .16 contrary to what the terminal said.  So now there are like 9 different options in the boot menu.

Ahhhhhh !!!! This is so frustrating!  I can't even find documentation on how to restore the system to a previous state!

*** Warning Long Winded Rant Ensuing***

I wish the official Ubuntu documentation were a bit more in depth; especially for installing programs and drivers.  The official Ubuntu documentation for installing files pretty much says to use what the Ubuntu repositories have.  That is akin to telling Windows users to only use programs from Windows.com, even if they are out of date???  The documentation needs an explanation of how installation packages work, and figuring out what dependancies are required.  This is especially important for Nvidia video card users who know that Nvidia releases a new driver every couple of months and that those drivers usually post big gains for graphically demanding applications.

Whew, that being said if someone could help me restore my system to the state it was in before the failed Nvidia driver I would be so happy!:guitar:

And if anyone could explain to me what a Linux installation package consists of (or should consist of), and how to use them properly without destroying your system; I would be so happy as to write a beginners tutorial for others!

---

### Post by Therion on 2009-04-07
You don't mention what version of Ubuntu you're using so we can try an old standby and see if it works for you.  Open a Terminal and then copy and paste the following:```
sudo dpkg-reconfigure xserver-xorg
```This should walk you through reconfiguring your xorg configuration file and hopefully fix things.  If this fails post back and we'll try something else.

In short, though, the most routine way to install restricted drivers is to simply click on on the Hardware Driver Manager (System/Administration), pick the driver you want to use and double-click to download/install it.  Only when, and if that fails, should you seek out alternative methods.

---

### Post by wanderingshaodw on 2009-04-07
Ok Having a similar issue, I think.  Loaded 9.04x64 with a dual boot of vista ultix64 and all went great installed the drivers from system Hardware drivers nvidia 180.xx and as soon as I restart got a message about Apci doing something that linux is not used to and to contact linux mait, and then to complain to my bios vendor.  So I figured since I have never updated my Bios that this would solve the issue so I flash bios delete ubu 9.04 and then reinstall worked great nvidia drivers same error. So basically I am at a prompt to login and no way to get to actual gui.  So I tried dmesg | "something" and got a message about setting bios to give up some ram 64mb which I doubt has anythin to do with my issue since it works fine until the nvidia drivers are installed for 2*9500 gt cards in sys.  If I need to list error code I would be glad to if I knew how from a prompt.

Thanks in advance for any help

---

### Post by tampablendie on 2009-04-07
Yah sorry I'm on 8.04 LTS.

I've tried the dpkg command, and it didn't solve my problem.  I did however find myself in some type of recovery screen.  After removing several Nvidia kernel pakages I was unable to boot into Gnome desktop.

So I held CTRL-ALT-F1 to get into a CMD prompt.  I stopped gdm and started it again and tried to get to desktop again with CTRL-ALT-F7.  No good just a black screen with a flashing underscore.  So I went back to cmd prompt to reboot.  I used the command "sudo shutdown -now"

This brought me to the recovery screen I was talking about.  The options were.

1- resume normal booting
2- repair broken packages
3- fix config X
4- test memory

I repaired broken packages, fixed config x, and resumed normal booting.  The system was then able to boot into Gnome desktop.  The resolution appeared correct but there was no "restricted driver" option in the program hardware drivers.

And I still have three Kernel options in Grub. the options are 
.23 generic, .16 server, and .16 generic.

Is there some way to restore the system to a previous state?  I screwed everything up yesterday morning so if I could restore to that point I would be so happy.  I could do some more reading about Ubuntu and linux in general and then screw my system up again!!!:lolflag:

That's how you learn right?  You guys better hope I don't become a sugeon!

---

### Post by Therion on 2009-04-07
At this point my suggestion would be to try LiveCD's of 8.10 and 9.04 (you can still run it from a LiveCD even though it's still in beta) and see if one works better with your current hardware profile.  8.04 doesn't sound like it's panning out for you.  

I've found Jaunty to be freakishly stable and friendly since late-alpha stage; but that's me and my system's hardware.  Still, you're sounding pretty borked at this point.  Might be worth looking at a fresher release.

---

