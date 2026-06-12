---
title: "[Solved] Intel Wireless-N 2230 Ubuntu 10.04"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by Gabri22 on 2013-09-28
Hi there, I'm going to post my solution for getting Intel Wireless-N 2230 to work under Ubuntu 10.04.

First of all, I started trying the solution posted [here]("http://ubuntuforums.org/showthread.php?t=2069748") as follows:

> 
sudo su
make clean
     ./scripts/driver-select restore
     ./scripts/driver-select iwlwifi
     make
     make install


And this was the result after rebooting and "sudo modprobe iwlwifi": [http://imageshack.us/photo/my-images/5/wlry.png ]("http://imageshack.us/photo/my-images/5/wlry.png/")
(It doesn't work, and no rfkill output. The device seems to wake up but then, for no apparent reason, it gets disabled. I write this just in case the image link gets eventually broken).

So finally I had to try this drivers [iwlwifi-2030-ucode-18.168.6.1.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-2030-ucode-18.168.6.1.tgz").
All you have to do is:
 > 
1-Extract them at /lib/firmware. It will create a folder named  "iwlwifi-2030-ucode-18-168.6.1". 
2-Inside that folder you will find "iwlwifi-2030-6.ucode". Copy that file into /lib/firmware
Reload drivers:
3-sudo modprobe -r iwlwifi
4-sudo modprobe  iwlwifi


It should be working now.

I hope it helps.

Have a nice day.):P

---

### Post by chili555 on 2013-09-28
First of all, Ubuntu 10.04 is beyond its use-by date: [http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/](http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/) If it were me, I'd upgrade to 12.04 and I'm quite sure your 2230 would be working with no extra steps.

Second, as with many devices, Intel wireless cards are almost all covered by one driver. It is iwlagn in 10.04 and iwlwifi in later Ubuntu versions. The specifics of how to drive a specific device, your 2230 or my 6200 for example, are included in the firmware. Intel calls their firmware ucode:> iwlwifi-2030-[COLOR="#FF0000"]ucode[/COLOR]-18-168.6.1In your case, simply installing the matching firmware solved your case.

Now that you have a working wireless connection, I urge you to download and install 12.04.3 LTS.

---

### Post by Gabri22 on 2013-09-29
Thanks for the reply, but the weird thing is that I have got another laptop with the same wireless card and I tried the first solution (compat-wireless-2.6.32.16) and it worked as it did [here]("http://ubuntuforums.org/showthread.php?t=2069748")...

---

