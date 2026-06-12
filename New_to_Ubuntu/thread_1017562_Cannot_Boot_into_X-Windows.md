---
title: "Cannot Boot into X-Windows"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Avenue on 2008-12-21
Hello Everyone, 

I installed Samba on my Ubuntu 8.10 machine, rebooted and suddenly my X-Windows does not work.  I am able to log in using my username/password on what looks to be a giant terminal screen.  After logging in, I ran the following command:

```
sudo /etc/init.d/gdm restart 
```

Unfortunately, absolutely nothing happens. 

I then ran the following to remove Samba:

```
sudo apt-get remove samba
```

Samba is then removed, and again I tried restarting X-Windows but still it does not succeed.  

How do I fix this??

Thanks!!

---

### Post by northern lights on 2008-12-21
Can you post the exact error you get when running ```
sudo /etc/init.d/gdm start
```(the "re" prefix is redundant if you're in CLI only)

---

### Post by Avenue on 2008-12-21
Thanks for the reply.  

I just tried the command you suggested and...nothing. After I type the command, it asks for my password.  After supplying the password, nothing happens and I get the following:

```
username:~$
```

Correct me if i'm wrong, but that's just a line stating that another command can be typed in, correct?  

So actually, I don't get an error...just another line which is ready for another command.  

Make sense?  

How can I get around this and get back into X-Windows?

---

### Post by northern lights on 2008-12-21
Yeah, that's just a new command prompt.

I don't really see how this could be connected to the samba install, but since you're saying it happend right after and you modified nothing else, let's do two things.

First off run ```
sudo aptitude purge samba && sudo apt-get autoclean
``` to fix remove the samba's not needed dependencies also.

Thereafter run ```
sudo dpkg-reconfigure xserver-xorg
```to freshly setup X.

Reboot.

Now what?

---

### Post by Avenue on 2008-12-21
So I ran the commands as instructed, now i'm at a screen where its says:

**xserver-xorg postinst warning: overwriting possibly customized installation file.  Backup in etc/x11/xorg.config20081221053450**

I'm now back at a command line.  Should I reboot now?

---

### Post by northern lights on 2008-12-21
Yes.

And if you don't get a GUI, issue ```
sudo /etc/init.d/gdm start
```again, hopefully with better results.

If neither gives you a graphical interface. Something else is screwed. You didn't alter runlevels, did you?

---

### Post by PmDematagoda on 2008-12-21
It seems a bit weird that you are not even getting a GUI in the form of "bullet-proof X", perhaps it may be more than a borked xorg.conf file, if it is, then the contents of /var/log/Xorg.0.log is your best bet of knowing exactly why the X-Server isn't starting.

---

### Post by Avenue on 2008-12-21
Okay, so I rebooted, then attempted to start the gdm...still nothing.  I am back at the command prompt.  

I'm not sure what the runlevels are, so hopefully that this means I didn't alter them seeing as I don't know what they are.  

HOWEVER - 

I did just now remember that I did something with my video driver the other day under the Hardware Manager (I forget exactly what it's called at the moment).  I just bought a new 22'' monitor, and the resolution which I needed wasn't available so I went out and updated the driver through the Hardware Manager.  I was able to successfully get the resolution I needed.  I'm running a slightly older Nvidea video card.  

Could this be the problem?  If so, how do I fix this?

---

### Post by PmDematagoda on 2008-12-21
> **Avenue said:**
> Okay, so I rebooted, then attempted to start the gdm...still nothing.  I am back at the command prompt.  

I'm not sure what the runlevels are, so hopefully that this means I didn't alter them seeing as I don't know what they are.  

HOWEVER - 

I did just now remember that I did something with my video driver the other day under the Hardware Manager (I forget exactly what it's called at the moment).  I just bought a new 22'' monitor, and the resolution which I needed wasn't available so I went out and updated the driver through the Hardware Manager.  I was able to successfully get the resolution I needed.  I'm running a slightly older Nvidea video card.  

Could this be the problem?  If so, how do I fix this?

If there wasn't a problem before installing Samba, and if the Samba install did not fiddle with the xorg.conf file(not at all likely, Samba and X are two different things), then it must be something else, especially since you don't seem to be getting fail-safe X at the least.

---

### Post by northern lights on 2008-12-21
> **PmDematagoda said:**
> not at all likely, Samba and X are two different things
I concur.

> **Avenue said:**
> I'm not sure what the runlevels are, so hopefully that this means I didn't alter them seeing as I don't know what they are.
If you've never read the word "runlevel", you probably didn't change anything here. However, in Ubuntu, booting into runlevel 3 would for instance result in CLI only without even a failsafe X (Multi-user mode without a GUI). Run```
who -r
```to find out what you're on.

> **Avenue said:**
> I'm running a slightly older Nvidea video card.  
Could this be the problem?  If so, how do I fix this?
Please post the output of ```
sudo lshw -C display
```to verify what graphics device you're running and whether it's properly setup.

---

### Post by Avenue on 2008-12-21
Okay, my system is very very slow at the moment.  It's taking me forever to get any commands to run.  

So far, 

 - it says that my Xorg log does not exist.

 - I am at runlevel 2

 - sudo lshw -C display does nothing and brings me right back to a command prompt.

Am I screwed/need to re-format/re-install?

---

### Post by northern lights on 2008-12-21
> **Avenue said:**
> - I am at runlevel 2
This is perfect. Runlevels as culprits are as of now out of the question.

> **Avenue said:**
> - it says that my Xorg log does not exist

- sudo lshw -C display does nothing and brings me right back to a command promptThis behavior is wicked. I've never seen it before.

> **Avenue said:**
> Am I screwed/need to re-format/re-install?
I dislike giving this advice. However, if you have all you're data backed up and didn't have you're Ubuntu too personalized yet, such that it is easily recoverable, you might want to opt for it, depending on how comfortable you are with installing.

---

### Post by Avenue on 2008-12-21
To be honest, this machine is a secondary which I use to run Ubuntu so that I can play/get used to it.  I've learned a great deal in the past week alone, but luckily I don't have much data on it.  The only thing that sucks is that my configuration will have to be reset, but I guess i'll get over it.  If I have to re-format/re-install, I will.  

It's 6am here in Seattle, i'm going to get some sleep first before I re-format.  If anyone has any additional ideas, please let me know. 

Thanks for the help!

---

### Post by Avenue on 2008-12-21
Okay Guys, 

So I was finally able to get a response after running

```
sudo lshw -C display
```

What I get after running the command is

```
Framebuffer Devices
```

Is this enough to go on, or am I indeed screwed?

I'm just trying to figure out what went wrong in case I encounter this issue again.  

Anyone be able to help?

---

### Post by Tatty on 2008-12-21
This all sounds very wrong.  It sounds like there may have been some corruption happen to the data on your hard drive somehow.

Personally I would do a re-install, as trying to fix this may be much more hassle than its worth.

Alternatively if you wanted to mess, you could see it as a fun method of learning linux...

---

### Post by Avenue on 2008-12-21
Ooops, sorry, didn't realize my previous post went through.  

Below is an update when I ran the following command:

```
sudo lshw -C display
```

Here are the results:

```
Product:       nv11ddr [Geforce 2 mx200]
Vendor:        nvidia corporation
Physical ID:   0
bus info:      pci@0000:01:00.0
Version:       b2
Width:         32 bits
Clock:         66mhz
Capabilities:  pm agp agp-2.0 bus_master cap_list
Configuration: driver=Nvidia latency=32 maxlatency=1 mingnt=1   module=Nvidia
```

Is this something we can work with?  

I'm just trying to figure this out in case I encounter this issue again in the future, sure would like to learn from this.  

Can someone help?

---

### Post by PmDematagoda on 2008-12-21
Can you see if:-
```
ls /var/log
```
shows anything.

---

### Post by northern lights on 2008-12-22
> **Avenue said:**
> ```
Product:       nv11ddr [Geforce 2 mx200]
Vendor:        nvidia corporation
Physical ID:   0
bus info:      pci@0000:01:00.0
Version:       b2
Width:         32 bits
Clock:         66mhz
Capabilities:  pm agp agp-2.0 bus_master cap_list
Configuration: driver=Nvidia latency=32 maxlatency=1 mingnt=1   module=Nvidia
```
Your graphics device appears to be set up correctly.

The problem appears to directly involve your xserver.

If all fails, you might want to reinstall X before setting up a whole new system.

```
sudo aptitude purge xserver-xorg
```

```
sudo apt-get update && sudo apt-get install xserver-xorg
```

You could consider doing the same with the meta-package *ubuntu-desktop*.

---

### Post by mr.vanker on 2008-12-22
I read a good bit of this thread, and I am having a similar problem.

Except, I didn't really make any changes. All I did was install GNUSound, and try to open it a few times (but it kept crashing). I don't think that I uninstalled any Xserver components or anything like that, but I just can't get X to start. I've tried several commands, and I've basically come to understand that X may be uninstalled. I try

> aaronw$ sudo /etc/init.d/gdm

It says that it says that Gnome is running, I restart it, it restarts, then it'll tell me that gnome will resume when the next X session starts.

I try
> aaronw$ gnome-session

It tells me that gnome is unable to start (it gives me a different error code every time I put it in).

Then I try
> aaronw$ startx 

It tries to start X and gives me a weird error.

All in all, I found a command for X that required me to go to the X11 folder, and I found out that the folder did not exist.

Is there any way that I can install X from the CD? apt-get isn't working for me, it builds the dependency tree, but then after I confirm that I want to install, it tells me it was unable to fetch the packages.

Any help is appreciated! ](*,)

---

### Post by northern lights on 2008-12-22
> **mr.vanker said:**
> Is there any way that I can install X from the CD?

Look into using *apt-get cdrom* rather than *apt-get install* check ```
man apt-get
``` for synatx.

Please don't hijack threads. It is, in my opinion, a much better choice to start a new one.

---

