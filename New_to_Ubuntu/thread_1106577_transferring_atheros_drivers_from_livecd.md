---
title: "transferring atheros drivers from livecd?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by DutchShrek on 2009-03-25
hey all,
Sorry about having to ask this here since the Ultimate Edition has it's own forum.
But you guys were quick to help me earlier and I hoped you could point me in the right direction here as well.

ok so I have a Netgear WG311T network card.
And I know for a fact that it works in Ubuntu 8.10.
It even works in the LiveCD before I installed it.

I saw a video of Ubuntu Ultimate Edition and I found that so cool that I just had to try that out.
I like snazzy stuff, sue me :)

Anyway, the wireless is not working.
I'm asuming it's a driver issue but since I'm so new to Linux I would have no idea whre to even start installing it.
Or where to look in finding it for that matter.
But as I said with LiveCD I can connect, this leads me to believe that the drivers are on the ISO I have.
Can anyone point me to the right files, and a page somewhere with instructions for installing them?

Thanks in advance

---

### Post by lkraemer on 2009-03-26
Please open a Terminal window and do:
```

lshw -C network
ndiswrapper -l


```
Then post the output.

lkraemer

---

### Post by kevmitch on 2009-03-26
Avoid using ndiswrapper if you can. By the title of your post I'm guessing you've go an atheros card. What card exactly?
```
lspci
```
In any case, older atheros cards are supported by the ath5k driver that's been in the kernel for quite a while now. But ath9k only got into the kernel in 2.6.27 (the version in Ubuntu 8.10). Once drivers get into the kernel that means they "just work" like you described. What kernel are you running?
```
uname -a
```

My educated guess without knowing what Ubuntu studio edition is or what card youhave is that it has a kernel that's older than 2.6.27 and your card needs the ath9k driver. Unfortunately, however it's not as simple as just copying the driver over because drivers have to match the kernel. There are two possibilities:

1) Get a backported ath9k driver which you might find in the "linux-backports-modules" package for your kernel through synaptic or apt.
2) Get the at least the 2.6.27 kernel for your studio edition install. The quick and dirty thing would be to download it directly from [hardy]("http://packages.ubuntu.com/intrepid/linux-image-2.6.27-11-generic") or even 2.6.28 from [jaunty]("http://packages.ubuntu.com/jaunty/linux-image-2.6.28-11-generic"). You can install those with 
```
dpkg -i <debfile>
```

Of course 1) would be the more bulletproof way to go about it.

---

### Post by DutchShrek on 2009-03-26
well appearantly the kernel used is 2.6.27.7 and since you say one would find that in 8.10 then i find it even more weird that it can't connect.

sadly im extremely new to aything linux related.
someone else mentioned madwifi
but I have no idea how to install anything on ubuntu.
even your last command for installing the deb file was gibberish to me.

Of course I could always reinstall regular ubuntu 8.10 so i can have internet. but then I still won't know how to do anything.
im not one to give up that easily.
for now im going to search around for anything related to this.

but in the meantime if you could point me to some places that have clear advice on installing packages I'd greatly appreciate it.


edit:
I had also read several times about copying the sys and inf files of the windows folder and to install the driver with that.
installing worked but it's still not connecting.

I found out through the terminal that the atheros card I have is : Atheros AR5001X+ Wireless Network Adapter

---

### Post by DutchShrek on 2009-03-26
nevermind all this.

I went ahead and installed a newer version of the same OS, and it's connecting properly now.
so , without actually solving the issue, it is now solved for me :P

---

### Post by kevmitch on 2009-03-27
Great! 

The copying .sys and .inf files is necessary for using ndiswrapper. This used to be standard procedure for atheros cards, but now you want to avoid it as there are much better drivers in the kernel. 

Normally, you want to install packages through synaptic (The add/remove thing at the bottom of the applications menu). You can also use apt-get or aptitude on the command line (Accessories->Terminal). However in the cases that you want to manually install a .deb package that you got from somewhere else, you can dpkg -i on the command line. I just realised now that you can also just double click it and that will install it as well.

---

### Post by DutchShrek on 2009-03-28
well even though this matter has been fixed for the most part I'm still curious about those drivers present in the kernel.

You see, as I explained (and semi-solved), in [this topic]("http://ubuntuforums.org/showthread.php?t=1108442") the speeds are still somewhat slow on Ubuntu.

By installing Madwifi it seems to have improved a bit, but Vista is still much faster in downloading files.
Of course, this could mean a number of things.
I know for a fact that unless I use IDM in Windows, I don't get the speeds I should be getting from my card.
So perhaps it's simply a matter of finding a better download manager.

But I did have a few problems yesterday with the connection dropping out every 5 minutes.
That by itself leads me to believe the drivers can be improved upon.
But again, I'm not a Linux guru. In windows I know my way around, but in here it's going to take some serious digging to find out what is going on.

For now, this thread should be considered solved.
But I'm not giving up just yet to find out more about this matter :)

---

### Post by kevmitch on 2009-03-28
Well, like I said 2.6.27 was the first kernel to include the ath9k driver. I have noticed quite a bit of improvement since then. In particular, I don't get draft n speed in 2.6.27, but I do in later versions. You could try installing linux-backport-modules for 2.6.27 which should contain a newer version of the driver compiled for your current kernel. Failing that you could try installing compat-wireless [http://linuxwireless.org/en/users/Download]("http://linuxwireless.org/en/users/Download").

---

### Post by k3lt01 on 2009-03-28
Just to clear a little confusion this isn't entirely correct.> **kevmitch said:**
> Normally, you want to install packages through synaptic (The add/remove thing at the bottom of the applications menu). You can also use apt-get or aptitude on the command line (Accessories->Terminal).Synaptic is accessed through System> Administration>Synaptic Package Manager.

Add Remove is the same concept but doesn't use Synaptic's GUI.

---

