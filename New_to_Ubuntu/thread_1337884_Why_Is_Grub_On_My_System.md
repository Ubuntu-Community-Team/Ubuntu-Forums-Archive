---
title: "Why Is Grub On My System?"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by ken0069 on 2009-11-25
OK so I was excited to find out how easy Ubuntu was to work with after my initial install on a mule box.  Then I opted for a clean install on my main multiboot system computer only to find that Ubuntu wanted to install Grub boot loader to handle my boot up options.  Since I wasn't interested in having Grub do this, I stopped the install, disconnected all other drives and then restarted a clean install on that single drive.  NO MENTION OF GRUB DURING THIS PROCESS!  Afterwards I connected the other drive and all was well for a while.  Now, a week later, I've got a BETA version of Grub showing up each time I boot??  DIDN'T WANT THIS AS IT SLOWS DOWN BOOT TIME????

On my multiboot system I go into BIOS and select the boot drive there.  That way I don't have grub on my main boot drive and not know how to get it off if something goes haywire.  Now I got it acting up on my Ubuntu drive and I don't know why or how it got there?

So, anyone got a clue as to why I'm getting this Grub boot menu each time I try to boot Ubuntu?  And no, it doesn't show up when I boot to the drive with Windows XP.

Thanks,]

Ken

---

### Post by Cheesemill on 2009-11-25
You still need grub, Ubuntu wont boot without a bootloader !!!

---

### Post by falconindy on 2009-11-25
It's impossible to load **any** operating system without some sort of bootstrapping software. You have it on your other computer, I assure you. If 5-10s extra on your boot time bothers you **that** much, hit your power button and go grab yourself a cup of coffee. You'll find a login prompt (or desktop) when you come back.

Just a heads up -- if you were to sit and watch Grub every time you boot (let's say you boot twice a day), Grub takes roughly 2 minutes of your life **per week**, or .018% of it. Given Take a deep breath. Everything will be okay.

---

### Post by Vaphell on 2009-11-25
you can disable countdown by setting it to 0, it will run default option without asking.
And bootloader is mandatory, computer needs to know where the operating system is on hdd. The fact that you don't see it doesn't mean it's not there - usually bootloader is muted because people have 1 system (especially in the win world, where people are afraid of too much info).
When you change booting sequence in bios you merely start it from the boot record of the newly selected drive. For example drive1 was default and you change it to drive2. Computer used to read drive1 boot sector to get info about available OSes, now it reads it from drive2.

---

### Post by BenAshton24 on 2009-11-25
You need grub (or similar) to boot ubuntu, so you have always had it... perhaps before you simply weren't seeing it and now grub has detected another operating system, most likely after reconfiguring after an update, and now it is showing more options. Just remove the other options ar set the timeout to 1s or something, there are plenty of tutorials on how to do this.

---

### Post by yanceypd on 2009-11-25
You can disconnect other drives before installing Ubuntu.  Install Ubuntu so grub writes only to that drive.  After instalation reconnect other drives then boot select in bios.  Try the grub selection for a while you will probably prefer it after a while.

---

### Post by 73ckn797 on 2009-11-25
> **yanceypd said:**
> you can disconnect other drives before installing ubuntu.  Install ubuntu so grub writes only to that drive.  After instalation reconnect other drives then boot select in bios.  Try the grub selection for a while you will probably prefer it after a while.


+1

---

### Post by ken0069 on 2009-11-26
Here's the problem.  I've got two almost identical computers that are multiboot that are running Ubuntu as well as Winders XP and Vista.  The OTHER computer still does NOT do this.  Only this one does it and as I stated before, it didn't do it at first.  
 
I just don't like stuff changing that I didn't change or wasn't given the option to change and was wondering if this happened during updates.  If it did, then I want to know how to stop it from happening on the other box.  
 
As far as having grub loaded on my primary drive goes, not a chance!  It that one ain't broke, then I'm not going to fix it and don't want to take the time searching for an hour to find out how.  
 
The one thing that has impressed me about this version of Ubuntu is that to this point I haven't had to execute a single command line to make it do everything I want.  After running Suse, and Red Hat before that, I was impressed.
 
So I guess now I'll have to do a search to find out how to change that timer to zero to get rid of this problem.
 
Thanks all for the info/suggestions.;)
 
Ken

---

### Post by Paqman on 2009-11-26
> **ken0069 said:**
> 
So I guess now I'll have to do a search to find out how to change that timer to zero to get rid of this problem.

```
gksu gedit /etc/default/grub
```

Change the Grub timeout to 0, then:
```
sudo update-grub
```

---

### Post by ken0069 on 2009-11-27
> **Paqman said:**
> ```
gksu gedit /etc/default/grub
```
 
Change the Grub timeout to 0, then:
```
sudo update-grub
```
 
Hey thanks for the info, but it didn't work.  Still get the 10 second count down at boot!!  Looked in that file and sure enough, it's set at zero but still does the count down??  
 
After searching for the better part of an hour I found out others had the same problem so I'll fix it tomorrow with fdisk and a format C: /u and be done with it!  Yeah, I got no patience with crap like this!  Learned a long time ago with Windows not to run anything beta, and that's what this bootloader says it is!
 
Thanks again for trying to help.  Have a nice day.
 
Ken

---

### Post by wilee-nilee on 2009-11-28
Startup manager in synaptic will adjust the grub time out to 0 if that floats your boat. It seems that you have unsubstantiated opinions that are keeping you from having a clearer look and the ability to accept change.

---

### Post by ken0069 on 2009-12-02
snip

UPDATE:

After sleeping on this and letting that drive sit for a few days until a cooler head could prevail, I got to thinking about that zero setting?  Booted to Ubuntu and when the grub loader came up, it sat there and wouldn't automatically start linux.  I had to hit the enter key to get it to finish the boot.  So, I got to thinking that even in Winders sometimes zero means infinity so I changed that value to 1 then rebooted and now it flashes that grub loader screen for one second but then goes on and boots Ubuntu.  

So, while the command line stuff was correct, the zero setting was not but hey, it does work now!

And thanks again!;)

Ken

PS, and if you think I was quick to get pissed on this, just wait until I ask for help loading 3D drivers for my ATI video card!  :shock:  :biggrin:

---

### Post by phoenixcor on 2009-12-19
could someone inform me of how to edit the startup manager in synaptic.  i would not call is a problem, but i let my 3 year son use the computer at his discretion.  I have one hard drive for old PC business files and another for the family use which is where ubuntu is located.  grub gives several options at startup and i want it to go straight into ubuntu as opposed to my three year trying to learn programming

---

### Post by 73ckn797 on 2009-12-20
> **phoenixcor said:**
> could someone inform me of how to edit the startup manager in synaptic.  i would not call is a problem, but i let my 3 year son use the computer at his discretion.  I have one hard drive for old PC business files and another for the family use which is where ubuntu is located.  grub gives several options at startup and i want it to go straight into ubuntu as opposed to my three year trying to learn programming


If you install "startupmanager" from Synaptic you will then have a graphical way of changing boot order of grub2 and adjusting the time the boot menu is showing before loading the default OS. Once it is installed you will find it under System/Administration.

---

### Post by steveneddy on 2010-01-21
If you are using 9.10, most of the software is either beta of close to beta software.

9.10 release is the bleeding edge release.

I you want stability, try 8.04 or 8.10.

And also, after readying your post history, I might suggest that you run Linux is a VM instead of multi booting all the time.

You can run multiple OS's in VirtualBox without all the made up in your mind issues about boot time. You can also run OS' at the same time in a VM.

Do whatever you want. but these issues you are having are mainly issues brought on by yourself.

---

