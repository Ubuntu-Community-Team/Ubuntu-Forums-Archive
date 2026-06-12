---
title: "Can't change resolution: NVIDIA 425M"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by TwoG on 2010-10-04
So the title pretty much says it all. I just installed Ubuntu on my new Vaio VPCF136FM/B. There are a few other problems, but I want to get this out of the way first.

When I try to go to System > Preferences > Monitors I get a pop-up that says this.

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

If I select No it takes me to a screen where I can't change my refresh rate, or my resolution. Its stuck on 61hz and 800x600.

If I select Yes it opens NVIDIA X Server Settings and tells me this.

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.



Not 100% what to do here. I'm very new to Linux, and any help would be greatly appreciated. Thank you.

---

### Post by Zero++ on 2010-10-04
open the command line and type;
sudo nvidia-xconfig

You can also load third party drivers from the Administrator>Hardware Drivers menu in the GUI

Once those are installed you should get a good resolution.

---

### Post by TwoG on 2010-10-04
Tells me command not found. It prompts me for the password first, and then tells me command not found.

I also cant get my touch pad to work or sound.

---

### Post by professor76 on 2010-10-04
I have the same problem on a Sony vpcf137. The nvidia controller 425m appears a new one and the default resolution sticks to 800X600.

I tried installing the latest drivers for nvidia from the repos and the x-swat ppa, but after these drivers are installed, even login prompt won't showup. The screen just hangs at the ubuntu loading screen.

The terminals are not accessible either

---

### Post by ibizatunes on 2010-10-04
go to application > accessories > terminal
copy and paste this into the command line
```
sudo nvidia-xconfig
```
and that will allow you to run as root and configure x

btw which version of ubuntu are you running?

---

### Post by realzippy on 2010-10-04
> **ibizatunes said:**
> go to application > accessories > terminal
copy and paste this into the command line
```
sudo nvidia-xconfig
```
and that will allow you to run as root and configure x

btw which version of ubuntu are you running?


...read thread before answering.
OP tried that (see post #2/3),he does not have any nvidia-driver installed correctly,
so nvidia-xconfig will not run.
According to the nvidia homepage there is no driver listed for the 425m.
Wait a few days.

---

### Post by ibizatunes on 2010-10-04
ok missed that bit

---

### Post by realzippy on 2010-10-04
When the kernel module is missing e.g.,or something else gets wrong during nvidia installation,nvidia-settings gets installed but
the driver does not run.Then nvidia-settings "says":
**You do not appear to be using the NVIDIA X driver**

---

### Post by realzippy on 2010-10-04
..try this:
```

sudo apt-get install linux-headers-$(uname -r)
```
and reboot.Then again run:
```
sudo nvidia-xconfig
```

---

### Post by TwoG on 2010-10-04
> **realzippy said:**
> ..try this:
```

sudo apt-get install linux-headers-$(uname -r)
```
and reboot.Then again run:
```
sudo nvidia-xconfig
```

Tried the first code and it says 

bash: syntax error near unexpected token `('


Sorry if I'm typing it incorrectly, like I said before, I am very new to Linux.

And to answer a previous post. I'm using 64 bit 10.04

---

### Post by realzippy on 2010-10-04
???
..there is no typo in the command.Have you copied & pasted it into your terminal or typed it yourself (then I guess you mistyped something..)

---

### Post by TwoG on 2010-10-04
> **realzippy said:**
> ???
..there is no typo in the command.Have you copied & pasted it into your terminal???

Copy and pasted, and it ran just fine. So I rebooted and tried the 

sudo nvidia-xconfig it says command not found.

---

### Post by realzippy on 2010-10-04
ran fine means:
It installed the kernel headers
or did it claim:
linux-headers-2.6.32-xx is already the newest version...
and did install nothing?

Which nvidia-driver is installed according to System/Administration/HardwareDrivers ?

---

### Post by TwoG on 2010-10-04
> **realzippy said:**
> ran fine means:
It installed the kernel headers
or did it claim:
linux-headers-2.6.32-xx is already the newest version...
and did install nothing?

Which nvidia-driver is installed according to System/Administration/HardwareDrivers ?
Well this is what I got in terminal after running the first code you gave me.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.32-25-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-24-generic linux-headers-2.6.32-24
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Also, after checking the hardware I get this. There are no drivers proprietary drivers installed it says.

---

### Post by realzippy on 2010-10-04
How did you try to install the nvidia-driver?

---

### Post by TwoG on 2010-10-04
> **realzippy said:**
> How did you try to install the nvidia-driver?

I haven't. I don't know how to go about doing that.

---

### Post by realzippy on 2010-10-04
????????...usually nvidia-settings is not installed,only when installing the nvidia driver.
So you have not attempted to install a nvidia-driver nor nvidia-settings?Strange,
but anyway who cares.Sorry for misunderstanding.
So *is* there a nvidia-driver offered in system/administration/hardwaredrivers?

---

### Post by TwoG on 2010-10-04
> **realzippy said:**
> ????????...usually nvidia-settings is not installed,only when installing the nvidia driver.
So you have not attempted to install a nvidia-driver nor nvidia-settings?Strange,
but anyway who cares.Sorry for misunderstanding.
So *is* there a nvidia-driver offered in system/administration/hardwaredrivers?

There is no driver offered.

---

### Post by realzippy on 2010-10-04
Yep,would be surprising since the 425M is not listed even on the nvidia linux driver section.You could install the 256.xx driver manually
hoping that it works or email to nvidia asking *if* 256.53 would work with 425M...
Bad thing is that the display driver tool also refuses to work with your graphics chip,so setting up a better resolution with nouveau (the free driver which is running now) by xrandr might not work also,but you can try:
```
xrandr
```
and post it's output.

---

### Post by TwoG on 2010-10-04
> **realzippy said:**
> Yep,would be surprising since the 425M is not listed even on the nvidia linux driver section.You could install the 256.xx driver manually
hoping that it works or email to nvidia asking *if* 256.53 would work with 425M...
Bad thing is that the display driver tool also refuses to work with your graphics chip,so setting up a better resolution with nouveau (the free driver which is running now) by xrandr might not work also,but you can try:
```
xrandr
```and post it's output.

Okay I'll try that. However I have no idea how to go about installing that driver on Linux.

This is what I get when I run xrandr

Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0

---

### Post by realzippy on 2010-10-04
There should be many [HowTos]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html") out there according manually installing nvidia drivers on 10.04..
..basically you had to disable nouveau and run a nvidia install script,no big deal.
Back to xrandr,
now try:

```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```

```
xrandr --addmode default "1600x900_60.00"
```

```
xrandr --output default --mode "1600x900_60.00"
```

...but would suprise me if it works.

---

