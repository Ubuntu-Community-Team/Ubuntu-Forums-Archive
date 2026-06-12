---
title: "UbuntuStudio killed my wireless!"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by Personatech on 2008-02-22
I pulled my old Dell Latitude C610 out of retire as I want to play with some low-end video and audio production.  Aha - good opportunity to try out UbuntuStudio!  The Dell had Edubuntu 7.04 which supported my wireless pcmcia card (Xterasys XN-2423G 802.11G) with no hiccups.  

First things first - the Update Manager wanted to upgrade to 7.10.  No problem, I do the update and wireless is still working.

Then I use Synaptic to install all UbuntuStudio packages in the Gutsy repository.  Reboot the system and BOOM!, no wireless!!  In fact, the card doesn't even power up, suggesting that the problem might be with PCMCIA rather than the wireless card itself. 

I think I'll try reinstalling Ubuntu-Desktop which was uninstalled during the process.  In the meantime, if anyone has any suggestions as to what to do I'd sure appreciate it!

EDIT 1:  I just tried using an older 802.11b Orinico Silver card (Wavelan) and still don't have wireless.  On to restore Ubuntu-Desktop...

---

### Post by jeffus_il on 2008-02-22
Check the output of > dmesg to see if the kernel sees the card, if it is seen use > iwconfig to display the wireless device and post output here.

---

### Post by u-foka on 2008-02-22
Hy!

Now I looked around, and found, that ubuntustudio-audio is installing a new kernel surfixed: -rt
It is some patched (Ingo Molnar's full real time preemption patch) version of the kernel, and maybe not contain the driver you need for your wireless device...

But I think ubuntu doesn't installed the kernel you used before, sou you have to press esc at the grub screen at booting, and select a lastest generic kernel... it then you got your wlan back you can try if any ubuntu studio apps works well what you need ;)

---

### Post by SamMessing on 2008-03-01
Hey!

So I had a similar problem when I installed UbuntuStudio. I would run the command 

```
iwconfig
```

in a terminal and get back:

```
lo        no wireless extensions.
eth0        no wireless extensions.
```

eth1 is normally what I use for wireless. After look around I found this [howto]("http://ubuntuforums.org/showthread.php?t=681135&highlight=ubuntustudio+wireless"), which suggested going to System>Administartion>Restrictied Drivers Manager to make sure that the correct driver for wireless was enabled. When I cliked on it I got the following message:

```
You need to install the package linux-restricted-modules-2.6.22-14-rt for this to work properely.
```

So in a terminal I ran the following command:

```
sudo apt-get install linux-restricted-modules-2.6.22-14-rt
```

And after it finished I rebooted and everything was working great, as if there was never a problem with wireless to begin with. I suggest not running the command I did, but instead doing the same process, as you might need a different linux-restricted-modules package than I did, if you have  a different kernel version.

Hope this helps!

---

