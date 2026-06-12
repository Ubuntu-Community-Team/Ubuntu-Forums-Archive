---
title: "NVIDIA and low graphics mode problem"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by frankh on 2009-03-02
I though I saw a (sticky?) thread about this in here a little while back, but I cannot for the life of me find it now.

The problem is that, after installing NVIDIA drivers downloaded from nvidia.com, next time the system boots, it complains about not being able to configure the display hardware correctly, and you're forced to start in Low Graphics mode. There seems to be a driver conflict, and I remember that you had to make sure that some nvidia drivers were uninstalled, and do something with the restricted-drivers file, _before_ installing the NVIDIA drivers manually.

Can someone point me in the right direction?

---

### Post by emshains on 2009-03-02
You should get envy, it will install the driver properly. Get it from [http://linux.softpedia.com/get/System/Software-Distribution/Envy-36960.shtml]("http://linux.softpedia.com/get/System/Software-Distribution/Envy-36960.shtml")
I can't say for certain, but I think it might be found in the repositories as well.

---

### Post by tad1073 on 2009-03-02
[http://ubuntuforums.org/showthread.php?t=1071283](http://ubuntuforums.org/showthread.php?t=1071283)[ ]("http://ubuntuguide.org/wiki/Ubuntu:Intrepid#NVidia_Driver")

---

### Post by Sirron on 2009-03-02
> **emshains said:**
> I think it might be found in the repositories as well.

Instructions to install envy via the repositories are located [_here_]("http://albertomilone.com/envyngfaq.html#A").

---

### Post by presence1960 on 2009-03-02
> **frankh said:**
> I though I saw a (sticky?) thread about this in here a little while back, but I cannot for the life of me find it now.

The problem is that, after installing NVIDIA drivers downloaded from nvidia.com, next time the system boots, it complains about not being able to configure the display hardware correctly, and you're forced to start in Low Graphics mode. There seems to be a driver conflict, and I remember that you had to make sure that some nvidia drivers were uninstalled, and do something with the restricted-drivers file, _before_ installing the NVIDIA drivers manually.

Can someone point me in the right direction?

Open a terminal and enter

> sudo apt-get install envyng-qt envyng-core

This will install envy. Then run envy to install your drivers.

---

### Post by frankh on 2009-03-02
I tried envy last time, and got the message that my system (8.10) was not supported. It wasn't able to install or uninstall anything.

---

### Post by balaknair on 2009-03-02
The first thing is to make sure you've got the correct drivers for your card. 

To uninstall the old drivers safely:

ctrl-alt-F1 to get to text console--> Login with your user name and password

Stop the Xorg GUI
```
sudo /etc/init.d/gdm stop
```

Remove the Old drivers with envyng-
```
sudo apt-get install envyng-core
sudo envyng -t
```

Use the envyng text based utility to uninstall the driver(just follow the onscreen instruction that envy gives you.

Next you can install the nVidia drivers(the latest version I think is 180.35 Get it here [ http://www.nvnews.net/vbulletin/showthread.php?t=128939/ ]( http://www.nvnews.net/vbulletin/showthread.php?t=128939/ ) ):

```
sudo apt-get install build-essential linux-headers-`uname -r`
cd Desktop
```
Assuming you saved the Nvidia driver package to the desktop

```
sudo sh ./NVIDIA***.run
```

Restart the GUI
```
sudo /etc/init.d/gdm start
```


**OR**

Just stick with the version in the Canonical repos(180.11)

---

### Post by aviedw on 2009-03-02
First you have to uninstall everything that has to do with nvidia using the package manager. Then download the nvidia package from the website. Then hit ctrl alt f2 and in the command line type sudo killall gdm and then then install the nvidia package. But whats most important is that no previous nvidia drivers can be on your system.

---

### Post by frankh on 2009-03-02
Well, I did that a while ago actually, after I got the conflict. I removed everything, and then installed the downloaded drivers. Then it worked for a couple of reboots, and now the system is 100% fried:

- Unless I press and hold a key (f.ex. Alt), nothing at all happens after I've selected Ubuntu in Grub. If I press and hold Alt, the system SLOWLY boots, until it tries to load the NVIDIA drivers a couple of times, before complaining about having to start in Low Graphics mode. And after that, nothing more happens. 

I was able to get a console running, and did the same removal procedure, and reinstalled the downloaded NVIDIA drivers. Then I started gdm, and everything looked ok. Until I tried shutting down. The progress indicator didn't move until I pressed and held Alt, at which point it slowly moved until it seemed to be "done". Then nothing more happened, and I had to use the power button to shut down.

Then, when trying to start up again, the exact same thing happened.

Now, I know that Ubuntu isn't as stable and robust as Debian, but this is just plain ridiculous.

---

### Post by frankh on 2009-03-02
> **balaknair said:**
> 
**OR**
Just stick with the version in the Canonical repos(180.11)

HOW do I do that? If there is an apt-driver which works, it would be much better for the system health to use that, instead of compiling things, which is besically asking for trouble in a debian package based system.

---

### Post by presence1960 on 2009-03-02
> **frankh said:**
> I tried envy last time, and got the message that my system (8.10) was not supported. It wasn't able to install or uninstall anything.

That is strange, I used Envy on kubuntu 8.10 and it worked just fine.

---

### Post by balaknair on 2009-03-02
> **frankh said:**
> HOW do I do that? If there is an apt-driver which works, it would be much better for the system health to use that, instead of compiling things, which is besically asking for trouble in a debian package based system.

Just use the 'Hardware Drivers' applet in System menu> Administration> Hardware Drivers to enable the 'restricted drivers'. If you have a supported nVidia card, the applet will detect it and present a list of suitable drivers. If the 180.* series isn't in the list, just install the modaliases package for the 180 drivers(sudo apt-get install nvidia-180-modaliases). Alternatively, you can use apt-get or synaptic to install the drivers.

It would be advisable to uninstall the custom nvidia drivers before attempting to install the drivers. Log into the tty(Ctrl-Alt-F1) as before, stop GDM and remove the 'non-apt' drivers. Since you said you had trouble with Envy, try this
```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
```

Then install the drivers with apt-get
```
sudo apt-get install nividia-glx-180
```

Or via the hardware drivers manager
start GDM--> it'll take you low graphics mode--> once logged into low graphics mode, System> Administration> Hardware Drivers> Enable the drivers and reboot.

Hope this helps.
All the best.

---

### Post by frankh on 2009-03-02
Ok. Someone says "do this", and other say "do this". Can someone please help me with a simple, complete list of how I can get rid of the old drivers and install new ones?

I just reinstalled the system for the second time. Then I ran envy, and uninstalled the files. Or did I? It reported the files uninstall, but Gdm was still not using generic drivers when I started it, and Synaptic showed a long list of installed nvidia-X packages. So I removed all of them, and installed the 180-drivers from the Canonical repo. Result: Broken Gdm/x. No way to fix it quickly or easily. So, I reinstalled the system again.

Now, before I do ANYTHING, can someone tell me if this is enough?

1. Install the system. Actually, the default drivers makes Gnome look ok, but there are no configuration options that I can find, for things like dual monitors etc. (I'm using a laptop, so I NEED that option.)

2. Open a terminal, and shut down gdm (with the init script)

3.
```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove

sudo apt-get install nividia-glx-180

```

4. Start gdm (init script)

Will this enable me to reboot the system and not being forced to the good, old Low Graphics mode?

NB: When I shut down gdm (with the init script), and installed envy, I got an error message when trying to start it again, and I had to reboot to be able to start it. The same happened when I tried installing the canonical repo drivers.

---

### Post by frankh on 2009-03-02
Update:

When I get to step 3 above, typing 

```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings

```

apt insists that it cannot find any of the packages. There are, of course, a bunch of nvidia stuff installed when I check in synaptic. But the above procedure yields nothing.

---

### Post by balaknair on 2009-03-02
OK, sorry for the delay in replying. I just tried out everything I suggested on my system here(it's a desktop box with an 8400GS GPU), and switched from the 180.22 drivers I had to the 180.11 from the repos, and then to 180.29 from the nVidia site. 

It seemed to work fine.

On a new install:
The nVidia restricted drivers are not installed by default on a vanilla Ubuntu install, you have to enable them via the hardware drivers applet. So in that case all you have to do is enable the restricted drivers via System Menu> Administration> Hardware Drivers. Wait for the install to finish(the progress bar might not work and be stuck at 0%, but the download continues in the background), reboot when prompted, and upon restarting, things should be working).

---

### Post by frankh on 2009-03-02
No problem - I don't expect people to be on the lookout and reply right away :-)

Well. I open the Hardware Drivers app, and see 2 NVIDIA drivers listed. None of them are activated, and clicking the Activate button just asks for the user's password, and then does absolutely nothing.

The Help text says to ENABLE them by clicking the checkbox next to the driver name. This doesn't work, though.

However - if they're not enabled or activated, shouldn't I then be able to just install the drivers from the NVIDIA home page, without getting any conflicts with existing/old drivers?

The only nvidia packages I can find with Synaptic now are:
nvidia-common
nvidia-71-modaliases
nvidia-96-modaliases
nvidia-173-modaliases
nvidia-177-modaliases

---

### Post by balaknair on 2009-03-02
I updated my previous post about this very thing.
It seems the progress bar doesn't work, but the drivers are being downloaded and installed in the background. Just wait a while(how long do you think it would take a 19-20 MB file to be downloaded with your internet connection? plus another 2-3 minutes for the actual installation and configuration).

---

### Post by frankh on 2009-03-02
Thanks for the help. I'll give it some time. I've got a 10mb line, but you never know the speed of the website at that exact time :-)

---

### Post by balaknair on 2009-03-02
> **frankh said:**
> 
However - if they're not enabled or activated, shouldn't I then be able to just install the drivers from the NVIDIA home page, without getting any conflicts with existing/old drivers?

Actually, yes, you should be able to install the nVidia-packaged drivers.

You might want to run a full system update before you do that though(a new 8.10 install ships with the 2.6.27-7 kernel, which is updated to 2.6.27-9 and then to 2.6.27-11). The nVidia-packaged drivers will need to be uninstalled and reinstalled (so a new kernel module is compiled) each time the kernel is updated. That's why it's usually safer to stick with drivers from the repos, updates to kernel modules are shipped along with kernel updates.

To see the 180 drivers in the repos, sudo apt-get install nvidia-180-modaliases

---

### Post by frankh on 2009-03-03
I did this now, with absolutely no success:

- Reinstall the system
- Did a complete systems update
- Made sure no NVIDIA drivers were installed
- Installed the downloaded 180 drivers from nvidia.com
- Restarted the system

Another completely ridiculous thing: When I start up, nothing happens unless I press and hold a key on the laptop keyboard. If I do that, the system starts slowly. It's like a bad joke.

- When gdm starts, I get the same error message:

Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "type1" (module does not exist, o)

- Then, when I select to start the crap in Low Graphics mode, THIS error appears:

There already appears to be an X server running on display :0. Should another display number be tried?

WHAT?????!!!!!!!!!!!!!! What IS this?!?!?!



No offence to anyone here, but I have NEVER seen anything more ridiculous than this, and I've worked with linux, windows and osx for many years. It simply does not work, or so it seems. And this is Ubuntu, which is said to have the best hardware support of all linux distros, and which is supposed to be very easy to install and configure.

---

### Post by balaknair on 2009-03-03
Hi.
I'm not sure just what the problems with Ubuntu and your laptop are, but it looks like it's more than just the graphics card. I'm afraid I'm out of ideas for now, if I can think of something else, I'll post it here. Couldn't any bugs similar to what you described in Launchpad bug tracker either, so you might consider filing a bug report there

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

 In the meantime, I hope someone with more experience with *nix can come up with an answer to your issues(if you were to add some info about your hardware- laptop make, GPU model, it might be helpful).

All the best.

---

### Post by frankh on 2009-03-03
Before I do that:

I'm now reinstalling the system for the fifth time, planning to try this ONCE more before giving up on Ubuntu alltogether.

Can you tell me, step by step, what do do after installing the vanilla system, if I want to install the nvidia-drivers from the repository? What to check first, what to remove, what to add and what to install.

Thanks for all help, man. One more try :-)

---

### Post by balaknair on 2009-03-03
OK. This is what I do for PCs with problem GPUs(though I always have trouble with ATI cards, never with nVidia), what I consider the safest route.

Step 1: Install Ubuntu, boot into new installation, make no changes to resolution, refresh rate etc.
Step 2: Run Update manager, install updates--> kernel updates mean you'll need to reboot
Step 3: Once all updates have been installed, System menu> Administration> Hardware Drivers> Check what drivers are available. Select the one marked 'Recommended' and click 'Activate'. If the system has been fully updated, I think it ought to be 180.11.
Give it maybe 10 minutes to install, and when prompted, reboot.

Under most circumstances, upon reboot, you should see the nVidia splash screen and things should work OK. 

I also think you ought to check what model your card is- some onboard nVidia GPUs like the 8100 series seem to have a lot of issues with Linux, even with the latest drivers.

---

### Post by frankh on 2009-03-03
Thanks for that last one. Nice, clean and to the point :-)

It seems it sometimes pays to breathe deeply, and think every step through before you execute it slowly and carefully.

After the last try, installing he drivers via via the Hardware Drivers application, the system actually booted as it should. I tried a couple of more reboots, and it seems to work. The real test will be starting it after connecting the external monitor.

Thanks for the help - I really appreciate it :-)

---

### Post by balaknair on 2009-03-03
Glad to know it worked(at least thus far).
Happy to be able to help.

Wish you luck with the external monitor too.

Have fun.

---

### Post by frankh on 2009-03-04
It worked even after connecting the monitor - fantastic :-) I have no illusions though, and I will wait until after at least one sucessful update before making a conclusion.

However, what about the next kernl upgrade? Is it necessary to completely uninstall the nvidia drivers before upgrading, and then reinstalling them again afterwards?

---

### Post by athaki on 2009-03-04
> **frankh said:**
> It worked even after connecting the monitor - fantastic :-) I have no illusions though, and I will wait until after at least one sucessful update before making a conclusion.

However, what about the next kernl upgrade? Is it necessary to completely uninstall the nvidia drivers before upgrading, and then reinstalling them again afterwards?

I've never had to reinstall the nvidia drivers after a kernel upgrade.  However, your mileage may vary.

---

### Post by balaknair on 2009-03-04
Updates shouldn't be much of a problem is you use the drivers from the Ubuntu repos. It's only when you use the drivers from other sources(such as the nVidia website) that you need to uninstall the drivers.
Since you used the drivers packaged by the Ubuntu dev team, there shouldn't be any problem when updating.

---

### Post by frankh on 2009-03-05
Thanks. There's at least a theoretical possibility that everything won't go straight to hell, then :-)

---

### Post by balaknair on 2009-03-05
I think so. I'd say the likelihood of things fouling up are pretty slim(not non-existant, but slim) if you stick with the Ubuntu repos. I'll wish you an extra shot of luck though. :D

---

### Post by mistypotato on 2009-03-06
frankh......

Take it from another relative ubuntu newbie....

It CAN get frustrating at times.   Sometimes it seems a problem has just landed in your lap exclusively.  I have 5 computers running ubuntu now and 80% + of the time things just work right on the first try.   But about 20% of the time it takes some work and some help.

You just happened to hit that 20% a bit early it seems.

Try to remember that it "could" be something about your particular hardware or configuration that is confusing ubuntu.

Having been through my share of "not so Kodak" moments, I can say with 100% certainty that ubuntu is worth the effort.

Lots of people here will give their version of a fix, and some of those will not work in your particular situation, and a few will be spot on.   So, keep reading the responses and you'll get it....and you'll be a bit more learned on a VERY good OS in the process.   

And whatever you do, "try" not to vent of the folks here kind enough to help, cause they don't have to :D

Hang in there....you'll get it resolved and it'll feel great.

PS...Just so you know, I'm here at this thread rightnow because I'm having the same problem with a fresh in stall I just did so I'm in the same boat and can't get it to work......yet :P

---

### Post by mistypotato on 2009-03-06
frankh,

just to let you know, I got mine working now.

I tried envy....but it did not work for me.

****** [COLOR="Red"]Update[/COLOR] - [COLOR="DarkOrange"]this was added 4 days later[/COLOR] ***************
After reinstalling ubuntu server 8.20 on another local PC, I couldnt get the  nvidia drivers working using my method below, so once again I tried the envyng method and THIS time it worked on that PC and successfully installed the driver so I guess sometimes it works ....and sometimes not?)
*******************************************************************************************

So, I read back where another member had suggested you go into Synaptic Package Manager and do a few things..... your answer suggested you didn't really understand.  I made the exact same oversight first time.

Try going back into synaptic PM and click on Settings --> Repositories
then make sure the "Software restricted by copyright or legal issues" is checked and also "Proprietary drivers for devices".

Then click on the 3rd party software tab and check both archive.canonical.com repositories.

Then go to the Updates tab and put a check mark in the "Unsupported Updates (Intrepid back ports) box.

Then close everything and do a system update.

A lot of updates should start.

When it's done, restart.

This worked for me anyway.

Hope it works for you.

---

