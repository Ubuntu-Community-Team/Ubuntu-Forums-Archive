---
title: "Anyone else having recent problems with wifi not working after laptop suspend/resume?"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by meldroc on 2007-03-04
I have an Asus A8Js laptop, running an up-to-date Edgy, and it has wifi using the ipw3945 driver.

I have it rigged to go into suspend mode when I close the lid.  Up until recently it worked almost every time.  Now, it only works roughly three out of four times, and upon failure, knetworkmanager claims "No network devices found" when I click on its icon.  When I try restarting knetworkmanager, as well as the NetworkManager and NetworkManagerDispatcher daemons, same thing.  Wifi stops responding, and the only way to make it work again is to reboot, which annoys me to no end.

How do I make wifi with suspend/resume of my laptop reliable.  As in works every single time, and comes back up every single time without exception.  I hate waiting for reboots.

---

### Post by meldroc on 2007-03-04
Bump.  Anyone have any ideas?

---

### Post by meldroc on 2007-03-05
Bump again.  It happened again this morning.  Why can't suspend and resume and wifi be reliable?

---

### Post by alastair on 2007-03-09
I currently lose wifi on resume from suspend. I'm investigating.

But a way back, without a reboot, is to unload and reload the wlan driver e.g. for me (in a shell) :

sudo rmmod ipw3945
sudo modprobe ipw3945

and the wlan is back.

---

### Post by zvezdogled on 2007-03-09
i have wifi on eth2 by default. But after waking up from suspend, it changes to eth1.

---

### Post by meldroc on 2007-03-11
> **alastair said:**
> I currently lose wifi on resume from suspend. I'm investigating.

But a way back, without a reboot, is to unload and reload the wlan driver e.g. for me (in a shell) :

sudo rmmod ipw3945
sudo modprobe ipw3945

and the wlan is back.

I already do that (and got annoyed enough to build a small shell script to do that quickly.)  It works, sometimes.  But not always.  Occasionally, the wifi's so wigged out I have to reboot.

That and restarting knetworkmanager, NetworkManager and NetworkManagerDispatcher also frequently gets wifi working again after a suspend/resume.

---

### Post by lbmounse on 2007-03-16
I'm currently having trouble with Dapper not even detecting my wlan after suspend. 
It does not show up in the network manager, none of it's LED's light.

I've tried to uninstall and reinstall the ndis driver, but to no avail.
Only rebooting has brought wifi back.

I do not have any problems suspending when using a wired connection.

---

### Post by clconway on 2007-03-18
I am having a similar problem. I have a Inspiron 6400 with ipw3945 wifi and an nVidia GeForce video card. It worked beautifully until yesterday. I occasionally had to rmmod/insmod after Suspend, but that would at least always work.

As of now, my laptop refuses to Suspend. It goes so far as to turn off the screen, then stops. I have to Ctrl-Alt-F1 then Ctrl-Alt-F7 to get the screen to wake up again and, when I come back, the wifi is dead. If I try the rmmod/insmod trick, it hangs on insmod. It also hangs if I open a new terminal and try lsmod. If I try to Shutdown at that point, it hangs. The only way to get back is a hard reboot.

Here's a conceivably relevant line from syslog:
Mar 18 13:40:27 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on eth1: No such device 

The weirdest thing about this is I haven't done any system updates in almost 2 weeks. The last update (7 March) was mozilla-thunderbird/tcpdump, so it's hardly likely they were responsible.

Another tidbit (this is possibly irrelevant, but I know I've had trouble with the interaction between my nVidia card and wifi in the past): I had trouble with Suspend after a recent update to nvidia-glx, so I have pinned that version to 1.0.8776+2.6.17.7-11.1. This was as of 3 March.

My kernel packages are:
linux-headers-2.6.17-11-generic     2.6.17.1-11.35
linux-image-2.6.17-11-generic      2.6.17.1-11.35
linux-restricted-modules-2.6.17-11-generic 2.6.17.7-11.2

---

### Post by clconway on 2007-03-18
This may also be relevant: my screen blanks at approximately the moment that the wifi connection is established at startup. Is there some kind of conflict between my video and wifi?

---

### Post by clconway on 2007-03-18
Installing the proprietary nvidia driver as [suggested here]("http://ubuntuforums.org/showthread.php?t=354704") seems to have fixed my problem. I apologize for hijacking this thread!

---

### Post by klato on 2007-03-19
I got the same problem.  Wifi craps out after suspend/resume.  xorg.conf says I'm using "nvidia" as my video driver.  Is that the proprietary one?

---

### Post by clconway on 2007-03-20
Yes, but the ubuntu package nvidia-glx installs an older version of the proprietary driver. You can download and install a more recent driver here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by klato on 2007-03-20
Ahh ok...will give this a shot when I get home today =)

---

### Post by clconway on 2007-04-12
The exact same problem re-appeared after I did a system update yesterday, installing linux-image-2.6.17-11-386 2.6.17.1-11.37 et al. I'm going to try re-installing the nvidia driver.

---

### Post by clconway on 2007-04-12
Yeah, that worked. If you install the nvidia driver outside of apt, you've got to re-install it when the kernel packages get upgraded.

---

### Post by keith11 on 2007-04-23
I am facing the same problem and I have also filed a bug on launchpad, but it has been two days and no one has responded yet. I am wondering if this is normal; it has been two days and no one is taking care of the bug.

I wanted to know if I have the right version of NVidia drivers for my NVidia GeForce FX Go 5200. How do i check that? As far as I remember I installed a driver called nvidia-glx-new from Automatix2. Any help or comments will be greatly appreciated. Thanks.

Keith.

---

### Post by clconway on 2007-04-23
Keith, I recommend you try downloading and installing the driver yourself from this URL: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
This is the only thing that has worked for me. There's something wrong with both the stock Ubuntu and the Automatix nvidia-glx packages.

---

### Post by keith11 on 2007-04-23
Thanks for your suggestions. I am skeptical about the drivers from NVidia though as it doesn't say nvidia-glx or something on those lines. Do you know any command by which  can verify that I do have the latest version? Thanks.

Keith.

---

### Post by H.E. Pennypacker on 2007-05-02
I am having the same problem, and I don't have an NVIDIA card.

---

### Post by clconway on 2007-05-02
Keith, try running nvidia-settings. That will give you the driver version on the splash screen. Currently, I am rocking with the feisty repo nvidia-glx, version 1.0.9631+2.6.20.5-15.20. No more custom install.

Pennypacker, sorry for your trouble. What kind of graphics card do you have? Do you have an Intel wifi chip? Are you still running Dapper? You might consider upgrading... the wifi and suspend/resume support improved in both edgy and feisty.

---

### Post by meldroc on 2007-05-09
I just upgraded my A8Js (the same one in the OP in this thread) to Feisty.  I guess the combination of newer Nvidia drivers, newer wi-fi drivers & networkmanager, and new suspend2 code seems to do the trick - it comes out of suspend very quickly now, and the wi-fi snaps to and automagically gets on the nearest wi-fi point.

Thanks, Feisty developers!

Beryl still misbehaves if I try to suspend and resume - I suspect the nvidia drivers don't handle suspend quite as well when 3-d acceleration is active.

---

