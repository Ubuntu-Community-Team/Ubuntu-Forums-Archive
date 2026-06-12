---
title: "Trouble regarding NVIDIA graphics drivers"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by retard182 on 2009-05-27
Hi!
I have a NVIDIA 6200LE and an Intel motherboard.

I have been using Windows for quite a while now and then decided to try Ubuntu. I installed Jaunty but cannot get the resolution to go above 640x480.

At first it had a default resolution of 800x600, then I installed latest Nvidia graphics drivers(v 180.51)  after which the resolution became 640x480 and would not go any higher. I tried almost everything mentioned in any forum regarding this but I cannot get this to work. 

I have uploaded the /etc/X11/xorg.conf file for your review.

Please help me. Any help is extremely appreciated.

---

### Post by overdrank on 2009-05-27
Hi and welcome, are you able to use the nvidia-settings to adjust your resolution. Using the alt, F2 keys and enter the command ```
gksu nvidia-settings
``` and try to adjust the resolution.

---

### Post by retard182 on 2009-05-28
> **overdrank said:**
> Hi and welcome, are you able to use the nvidia-settings to adjust your resolution. Using the alt, F2 keys and enter the command ```
gksu nvidia-settings
``` and try to adjust the resolution.

Thanks.

Yes, I did that and first it prompted me to run sudo nvidia-xconfig. I did that and restarted X only to find that it gave all sorts of errors. It said that X settings are not compatible and I need to reconfigure. After reconfiguring, it said that another X server is already running and it will use another (shell?) to run the X server on. And then it promptly brought me back to my 800x600 resolution.  Earlier I used to run 1280x1024 at 60 Hz on Windows. Then I tried running the command you wrote above again only to get that same error again.

I don't know if there are any compatibility issues or anything but I really need to get this working in the next 2 days or so since after that I won't be having access to Internet.

Please help.

---

### Post by Jazzy_Jeff on 2009-05-28
How did you install the graphics driver? Did you download it or did you goto System > Administration > Hardware Drivers?

---

### Post by appier on 2009-05-28
It has been while since I encountered this, so my explanation may be a bit rusty.  I am currently using the NVIDIA driver for a card I installed, and I had the same problem you are describing.  When selecting the display option under administration, I would receive a warning advising me to use NIVIDIA's proprietary tool.  No matter what I did from manually editing the Xorg files to running NVIDIA-settings under sudo, etc., I could not get the display resolution change to stick after logging out.  One time, I just pressed cancel and changed the resolution without using NVIDIA-settings, and then the settings seemed to take.

Someone with more experience will probably be able to give a better explanation for what I have just described.  

Hope this helps!

---

### Post by retard182 on 2009-05-28
> **Jazzy_Jeff said:**
> How did you install the graphics driver? Did you download it or did you goto System > Administration > Hardware Drivers?

I manually downloaded and installed it.
Using the System > Administration > Hardware Drivers route always caused the download to stay at 0%.

---

### Post by retard182 on 2009-05-28
> **appier said:**
> It has been while since I encountered this, so my explanation may be a bit rusty.  I am currently using the NVIDIA driver for a card I installed, and I had the same problem you are describing.  When selecting the display option under administration, I would receive a warning advising me to use NIVIDIA's proprietary tool.  No matter what I did from manually editing the Xorg files to running NVIDIA-settings under sudo, etc., I could not get the display resolution change to stick after logging out.  One time, I just pressed cancel and changed the resolution without using NVIDIA-settings, and then the settings seemed to take.

Someone with more experience will probably be able to give a better explanation for what I have just described.  

Hope this helps!

Actually that does not help either. Using Nvidia drivers puts my system at 640x480 resolution. Not using those drivers gives me a resolution of 800x600 only. In the change resolution option I only get two resolutions : 800x600 and 640x480.

I have tried generating modelines, using xrandr and editing xorg.conf but nothing seems to work. :(

---

### Post by freesitebuilder on 2009-05-28
My card is older, but I had similar problems especially using the Nvidia settings tool (System > Admin > Nvidia Xserver). Using System > Preferences > Display worked much better, saved the settings between sessions, and stopped everything moving around the panel which was driving me mad!

---

### Post by 4Orbs on 2009-05-28
If you manually installed the latest driver, and you are certain that it installed successfully... you should NOT try to activate the driver afterwards from the Hardware Drivers Mgr. The Hardware Drivers Mgr does not work with a manually installed driver. My guess is that you installed the driver after you had changed your resolution settings (you should have kept your resolution set to default or auto before installing the driver, even if its not your desired resolution). 

Your xorg.conf file gives no indication that the driver was ever installed (which could be the result of your telling the installer to not write the new changes to the xorg.conf... thus you still have the generic default xorg.conf file). But, again, if you are certain that the driver installed successfully, you might try this.

1. Log into your account in Low Graphics Mode, don't worry about the errors (x already running) or the 640 resolution.

2. Open the nVidia Settings Mgr as root by entering in the terminal:
```
gksudo nvidia-settings
```

3. If you don't have available the desired resolution in the nVidia Settings Mgr, then set both the resolution and refresh rate to "Auto" and click the "Apply" button. Your resolution may or may not change after clicking.

4. Now click on the "Save" button to save the settings to the xorg.conf file and be sure the popup window shows the correct location for the file: /etc/X11/xorg.conf then close the nVidia Settings Mgr.

5. Reboot (you'll probably get an error message, or you might just get the Login window, regardless where it ends up be sure to reboot.

6. Log in after rebooting and check your nVidia Settings Mgr to see if you now have more resolution options available. If so you can change to the desired resolution (as root), save the newer changes again by clicking the "Save" button.

7. Reboot and log in to the desired, successful resolution alteration.

If this doesn't fix it, we'll try something else.

---

### Post by retard182 on 2009-05-28
@4Orbs

Step 1. Went as expected.
Step 2. Told me that "You do not appear to be using NVIDIA X Driver. Please edit your X configuration file(just run nvidia-xconfig as root) and restart the X server." Also the window opened had no options related to resolution or refresh rate. I did as it told me to but nothing changed.
Also, I never found any option to set resolution/refresh-rate to auto.

Please understand that I am new to Linux and may be doing something horribly wrong. Please help me solve my problem. I am extremely thankful to everybody who tried to help.

---

### Post by 67GTA on 2009-05-28
Run ```
sudo nvidia-xconfig
``` in a terminal. This should set up your xorg.conf file to use the nvidia driver. Reboot.

---

### Post by 4Orbs on 2009-05-28
Did you install Ubuntu by using Wubi (inside Windows), or did you install it to a real partition on the hard drive?

---

