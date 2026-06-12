---
title: "Easy Broadcom BCM4312 Activation - No Internet Needed"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by TBABill on 2011-05-26
I'm posting this in absolute beginner in the hopes it may help some new user(s) with a fresh Ubuntu installation. I will post some caveats because:
 
1. I did not test on Kubuntu, Xubuntu, etc., only Ubuntu
2. I do not know if this will work for all BCM43xx cards that use the STA (wl) driver, but it works for my BCM4312.
 
 
When I install Ubuntu I always do so from the live session. My first step is to get my wireless going and to enable the STA driver for the BCM4312, it's as simple as:
 
1. Do NOT connect to ethernet. You can connect and get the same result, but then you are not installing the firmware and driver directly from the LiveCD.
 
2. When the restricted driver icon appears, click install driver and follow the prompts to activate the STA driver. Or you can immediately go to Additional Drivers and enable it without waiting on a prompt to do so from the system.
 
3. When the system prompts you that it must restart to enable the device, DO NOT RESTART! You are in a live session and a restart will simply start a fresh live session and it will not remember anything from the previous session.
 
4. Instead of restarting, simply open a terminal and ```
sudo modprobe wl
``` 
 
5. Wait a few moments (up to about a minute I think) and then you should see wireless networks from the network icon on the upper panel. 
 
6. Enter any passwords for network security that are required and enjoy. 
 
Once you have wireless enabled on your system you can begin the installation process. By doing so the system enables the wireless on the fresh install and once you restart the machine you should have an already working wireless device. Plus you can still install all updates, restricted codecs, etc. during install.
 
This info is offered via Ubuntu Help ([https://help.ubuntu.com](https://help.ubuntu.com)), but it does NOT identify the fact that you can just modprobe the driver and begin using it within the live session, and it does not identify the fact that if it is enabled during the install from a live session it will already be enabled on the machine once installation is complete. This should permit a user to fully test their Live session without relying on ethernet if the STA driver is required.
 
Hopefully this will help someone new to Ubuntu.

---

### Post by laidback on 2011-05-26
Great, I just tried this on my daughters new Acer 5742Z, Intel P6100, 3GB ram with HD graphics. It would run 11.04 live CD with internet connection but with 10.04LTS I couldn't get the internet to work. Other posts talk of the driver issue but don't mention the modprobe wl command, which seems to be the key for a live session.

Many thanks

Laidback

---

