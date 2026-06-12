---
title: "Graphics driver / monitor usage"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Destructor on 2009-05-24
Hi,

I've just installed Ubuntu as a dual boot OS on an HP compaq nx9105. It is my intention, if I can get Ubuntu working without issue, to eventually reinstall as a single OS PC- that OS being Ubuntu obviously!

However I primarily use this PC to run video to my tv. I've been doing this on Windows through a cable and treating the tv as a second monitor.

If I click 'System/Administration/Hardware Drivers' I can see that the 'Nvidia accelerated graphics driver 9version 96) (recommended)' is greyed out. I have hit 'install' on this but when I reboot, my primary monitor (the one attached to the laptop) deactivates- I can hear that Ubuntu has started, but I see nothing- the monitor is not active. I can only restore it by running Ubuntu in safe mode and running the graphics autofix. 

So the Nvidia driver is still uninstalled/greyed out. 

If I click 'System/Preferences/Display' it says:

**'It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?'**

If I click 'Yes' it then says:

**'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. '**

But I don't know what this means. If I insert that command into the terminal as directed, I get this message:

[B]Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.


ERROR: Unable to write to directory '/etc/X11'.[/B]

If I click 'No' to the questions 'Systems/Preferences/Display' I get a dialogue box called 'Display Preferences' that consists primarily of a pink box marked 'Unknown'. This box also appears in the top left corner of the screen at all times.

If I activate the tv and try to get the display to operate, it just flickers black- it seems unstable. However that's a different issue for a little later down the track, right now I just want to get the driver to recognize my primary monitor.

So I'm at a bit of a loss as to how to get my gfx card to interact with my monitors correctly- any advice would be helpful.

Thanks!

---

### Post by presence1960 on 2009-05-24
Look under System > Administration > NVIDIA X Server Settings. If NVIDIA X Server Settings is not listed then open a terminal and run > sudo apt-get install nvidia-settings or use Synaptic Package manager to install.

You can also try installing the nvidia drivers by installing Envyng, Go to Synaptic and install envyng-core and envyng-qt. After install in 9.04 Envy is in Applications > System Tools > Envyng. Envy will install your proprietary graphic driver provided there is one available for your model video card.

Edit: Install Envy first then do the other thing...sorry I misread your post.

---

### Post by Destructor on 2009-05-25
> **presence1960 said:**
> Look under System > Administration > NVIDIA X Server Settings. If NVIDIA X Server Settings is not listed then open a terminal and run  or use Synaptic Package manager to install.

Thanks, I have the Nvidia X server settings installed. However it's not immediately evident to me how to get my secondary monitor (the tv) to activate. I've tried to intuit what to do but it ended up disabling my laptop monitor and I had to reset the video settings from the GRUB boot menu and reinstall. So I am a bit stumped, how do I activate the secondary monitor? It seems to work automatically in Windows just by hitting Fn+F4

---

### Post by Destructor on 2009-05-25
Additionally, if I set the second screen up as a 'Seperate X screen', it asks me to save the X configuration file. If I try to do this, it gives me the message:

> Failed to parse existing X config file '/etc/X11/xorg.conf'!

If I hit OK, it closes the program. I have been able to get the tv monitor to display portions of the screen by fiddling around, so a signal can definitely get through, but it's always been just a section of the screen split off from my primary one (this is labelled 'Twinview') and is not usable as a monitor.

If I can get this problem fixed and my wifi up and running, I will no longer need Windows. As it is, I don't seem to be able to get Ubuntu to replicate these basic functions, I could really do with some advice on this.

---

### Post by Destructor on 2009-06-02
Is there some kind of user guide to getting a second monitor running? I have been unable to make ay progress with this issue. I can get the TV displaying, say, a quarter of the screen's real estate, but it is not useful for anything, or displayed at the correct resolution. Is there a way to reinstall the nVidia program?

---

