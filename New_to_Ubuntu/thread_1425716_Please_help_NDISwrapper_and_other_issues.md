---
title: "Please help: NDISwrapper and other issues"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by noixzx on 2010-03-09
I'm kind of at the end of my rope here.
I switched to Ubuntu because I tried to recover my laptop. It was running Windows XP, riddled with viruses, but the recovery disks were messed up and wouldn't work... which uninstalled everything and I could not get it back.

Now, I would prefer to have my old XP back because the whole Terminal thing is confusing the hell out of me, and installing things on Ubuntu seems to be like pulling teeth. I can't, because I installed Ubuntu to the ENTIRE hard drive. (Would attempting to recover it bring back Windows?!)

If I could get two things to work, I could deal with it.
First, the monitor has an inverted screen.
I would like to have Wine to run PowerStrip.
But that can't happen without an internet connection.

I've been trying to get NDISwrapper to work to no avail. Everything I've searched for (and I usually have 30 tabs open, because all of this is SO CONFUSING TO ME)

The only way I can do this is by downloading it from this computer, putting it on a USB stick, and moving it to my Ubuntu laptop. I've tried extracting it first, and simply moving the unextracted ndiswrapper-1.56.tar.gz file.
I have no idea how to do this. I feel like an idiot. :(
No idea where to start.
I would appreciate it if someone would give me an explanation that makes sense for once.
I want wireless!

(Basically, that's the short version. I'm trying to get my WiFi to work, "No network connection". )

My network adapter is broadcom BCM4311 802.11b/g WLAN.

Everything I've read says something about the boot disk... I booted from a flashdrive.

---

### Post by undecim on 2010-03-09
On my computer, I have BCM4322 and the STA driver works better than NDISwrapper. According to the package description from aptitude, this should work on BCM4311 cards as well.

If you can get a temporary ethernet connection (i.e. connect to your router directly with a network cable), then you can install your wireless drivers easily from System -> Administration -> Hardware Drivers.

If you can't get the ethernet connection, you can use another computer with internet access (which you appear to have, seeing as you are on the forums) to download the "bcmwl-kernel-source" package and all its dependencies with Keryx: [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by noixzx on 2010-03-09
I'd appreciate it if you could walk me through this in simple terms.
Yes, I have a computer that has internet connection as well and a flash drive.
This has been giving me an immense headache, and I don't even know where to start.
I'm downloading Keryx now. What do I do after that?

Edit: I read the tutorial and followed it, but on the very first step it sats "python: can't open file 'keryx.py': [Errno 2] No such file or directory"

Why does this have to be so DIFFICULT?

Okay, after that, I put in the directory...

Oh sheesh. Someone just walk me through this. I don't know anything about using Terminal, have no idea what to do when it comes to anything Linux-related.

---

### Post by undecim on 2010-03-09
Well you can always download the packages one at a time from [http://packages.ubuntu.com/karmic/allpackages](http://packages.ubuntu.com/karmic/allpackages) (change the "karmic" part of that address to whatever version you are using if you are using something other than 9.10)

This can be a bit of a headache though, because you will also need to download all the dependencies for each package. If you try to install one and don't have the dependencies, it will give you an error message telling you which packages you are missing, so there will be some back-and-forth between your two computers.

I know that for bcmwl-kernel-source (the Broadcom STA driver) you need at least dkms, fakeroot, and patch, but there may be some other dependencies.

To install one of the packages, just double click on it from the file manager.

---

### Post by k3lt01 on 2010-03-09
Download [ndiswrapper-common]("http://packages.ubuntu.com/lucid/all/ndiswrapper-common/download") and [ndiswrapper-utils-1.9 for i386]("http://packages.ubuntu.com/karmic/i386/ndiswrapper-utils-1.9/download") or [ndiswrapper-utils-1.9 for amd64]("http://packages.ubuntu.com/karmic/amd64/ndiswrapper-utils-1.9/download") (they are linked to the a page of download locations so click on the link, choose a location to download from and download them to your desktop).

Double click on them to install and then after they are installed follow this procedure.

# Note: Make sure drivers are visible on the Desktop then copy and paste each command into a terminal to install the wireless network drivers for the wireless card.

```
cd Desktop

sudo ndiswrapper -i yourdriver.inf

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

echo "ndiswrapper"|sudo tee -a /etc/modules

sudo shutdown -r now
```

Edit: ndiswrapper used to be on the install disk in Main until Karmic so if your not using Karmic you shpuld only need to use th install disk to find them.

---

### Post by anewguy on 2010-03-10
It's been a while, but I think since something like 8.04 or 8.10 you have also needed to blacklist the drivers that come with ubuntu if you use ndiswrapper for the bcm 4xxx series (others I don't know).  I know you need to blacklist b43 for sure but I know there are a couple more also but don't remember their names (like ssb or something).  Right now I'm on a Windows machine so I don't have access to Ubuntu or I could tell you straight out.

Someone else following this thread, please help the user do the blacklisting as well if they use ndiswrapper (without doing so, the wireless still will not work).

In addition, if the user is able to download ndiswrapper or get it from the LiveCD (pool/main/n) they should also try installing and using ndisgtk.  It takes the command line out of the equation.


Dave ;)

---

### Post by k3lt01 on 2010-03-10
> **anewguy said:**
> In addition, if the user is able to download ndiswrapper or get it from the LiveCD (pool/main/n) they should also try installing and using ndisgtk.  It takes the command line out of the equation.Dave I have never been able to get ndisgtk to remember  on reboot that is why I always recommend the cli option.

---

### Post by anewguy on 2010-03-10
You know, I've heard others say that as well.  It just worked for me when I used it, so perhaps I was one of the lucky ones?  I also have used ndiswrapper many times and recommended it many times - it does usually seem to work right away as long as you follow all the steps, spell correctly, and remember to blacklist.  Sorry to hear ndisgtk didn't work for you.

Dave :)

---

