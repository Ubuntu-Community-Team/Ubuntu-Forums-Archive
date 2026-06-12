---
title: "Not using Nvidia X driver"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by llmunro on 2011-01-31
Hi all,

I thought maybe I could just let the Nvidia thing alone and it wouldn't bother me, but it really is getting annoying.

After I installed the Nvidia driver (which is activated), the computer stopped consistently booting the GUI, meaning that I now nearly always have to boot in recovery mode and reconfigure the display and then reboot.  I also am unable to enable desktop effects.  When I open the NVIDIA X Server settings, I get this:


You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I have tried running nvidia-xconfig as root, which hasn't solved the problem.  I know that this has been brought up before on the forum, but it seems like there's no one solution to solve this.

Any suggestions would be mightily appreciated.

Thanks much.
Best,
Lisa

---

### Post by realzippy on 2011-01-31
Which graphics-card do you use?

Can you post your nvidia bug report as attachment?
Open terminal,run:
```
sudo nvidia-bug-report.sh

```
..file will be in your /home folder.

---

### Post by llmunro on 2011-01-31
Hi,

Thanks for the help!

I have attached the bug report here.

Thanks much.

Best,
Lisa

---

### Post by realzippy on 2011-01-31
It is a laptop?

Read in the bug report:
*[    19.596] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,*

Looks like nvidia optimus technology (Hybrid graphics:Nvidia and Intel).
To verify this,open a terminal and run:

```
lspci | grep VGA
```

Please post the output.
The terminal can be found at Applications menu -> Accessories -> Terminal.

---

### Post by llmunro on 2011-01-31
Hi,

Here's what I get:


lisa@lisa-Samsung:~$ 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Control


Thanks much for the help.

Best,
Lisa

ETA: Yes, a laptop.

---

### Post by realzippy on 2011-01-31
Nothing else?
So you do not have a nvidia-graphics card,you run Intel graphics..
**?**


Edit:
Which laptop exactly?

---

### Post by llmunro on 2011-01-31
Nope. Nothing else.

So, if I'm using Intel graphics rather than NVIDIA, what do I need to do about the NVIDIA driver that seems to be causing all sorts of problems?

The laptop is a Samsung Q430.

Thanks.
L.

---

### Post by jd2012 on 2011-01-31
> **realzippy said:**
> Nothing else?
So you do not have a nvidia-graphics card,you run Intel graphics..
**?**


I have sorta the same deal, In windows I use Nvidia drivers, W/ Nvidia control panel ect, but in:
```

sudo lspci | grep VGA

```I get:

VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)


Im using an Asus K50 line.

---

### Post by realzippy on 2011-01-31
> **llmunro said:**
> Nope. Nothing else.

So, if I'm using Intel graphics rather than NVIDIA, what do I need to do about the NVIDIA driver that seems to be causing all sorts of problems?

The laptop is a Samsung Q430.

Thanks.
L.

Google says that samsung q430 has also a nvidia 310m graphics card.
So you have 2 graphic cards,think that the nvidia card might be disabled in the BIOS?
Do you also run windows?
if,does the nvidia card work there?

---

### Post by realzippy on 2011-01-31
> **jd2012 said:**
> I have sorta the same deal, In windows I use Nvidia drivers, W/ Nvidia control panel ect, but in:
```

sudo lspci | grep VGA

```I get:

VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)


Im using an Asus K50 line.

Do you have a switch in the BIOS?

---

### Post by llmunro on 2011-01-31
I regret to say that despite the fact that the official description of my Samsung laptop is that it has a NVIDIA driver, the BIOS only lists the Intel driver.

Is there any hope of making an Intel driver play nicely with Ubuntu?

Thanks.
Lisa

---

### Post by jd2012 on 2011-01-31
> **realzippy said:**
> Do you have a switch in the BIOS?

Hi, ):P

Im not sure can you elaborate slightly? 

Thx

---

### Post by llmunro on 2011-02-02
So, if I have an Intel graphics card, it seems to me that trying to use the NVIDIA driver is probably not the best idea.  Is there an Intel drive that can be (easily?) installed?

Thanks.
Lisa

---

### Post by realzippy on 2011-02-02
Normally the intel graphics core works fine.

Wondering why System/administration/HardwareDrivers offers a nvidia driver and
*lspci | grep VGA* showing no nvidia card.

You are sure there is no way to change graphics in the BIOS?

---

### Post by llmunro on 2011-02-16
Hi,

This remains unsolved for me.  I've checked the BIOS several times and there's nothing to change as far as graphics.

Still unable to enable desktop effects, although everything else seems to be working.

Ideas?

Best,
Lisa

---

### Post by realzippy on 2011-02-17
Open a terminal,type
```
ccsm
```

compizconfigsettingsmanager opens,enable eg "wobbly windows".
Does this work?Drag any opened window and move it...

---

### Post by llmunro on 2011-02-17
Hi,

Opened up Compiz and checked box for wobbly windows, but no luck.  When I look in System>Preferences>Appearance>Effects and try to change from No effects to some degree of effects, I get the message that desktop effects could not be enabled.

I can only assume this has to do with the mystery of the graphics card and the nvidia driver.

Best,
Lisa

---

### Post by realzippy on 2011-02-17
Is it [this]("http://reviews.cnet.com/laptops/samsung-q430-11/4505-3121_7-34121948.html?tag=rnav") laptop?

---

### Post by llmunro on 2011-02-17
I don't know if this is the same model, but this is the one I have:

[http://www.amazon.com/Samsung-14-Inch-Laptop-Aluminum-surface/dp/B0043B7WDK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1297982745&sr=8-1](http://www.amazon.com/Samsung-14-Inch-Laptop-Aluminum-surface/dp/B0043B7WDK/ref=sr_1_1?ie=UTF8&s=electronics&qid=1297982745&sr=8-1)

Thanks.

---

### Post by TechWiz2100 on 2011-02-17
May not apply to your laptops in particular but sometimes in BIOS theres a tab for PCI or Southbridge (you can also look around for other similar things) and it sometimes has an option for default graphics device.

Intel I think is usually "integrated" and other dedicated cards would be PCI so maybe setting default from integrated to PCI/AGP or what have you would force the nVidia to the front as default graphics chipset.

Just poke around your BIOS a bit and look for something that is similar to default graphics device and mess with those settings. I know a lot of people are having issues with multi-cards but thats how I usually force certain cards on the laptops I do repairs on and it also works for desktop graphics troubleshooting.

---

### Post by realzippy on 2011-02-18
..that is confusing.
Please start an Ubuntu LiveCD,when it has completely booted again run:

```
lspci | grep VGA
```

It had to show something similar to:

```
me@mine:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1)

```

If there are not 2 graphic devices shown,there **has** to be kinda "switch" in the BIOS.

Please also check if compiz runs on the live CD,
do not enable compiz with rightclick-desktop-aso,since there is a bug.
Enable compiz via ccsm,wobbly windows...

---

### Post by llmunro on 2011-02-19
This is indeed confusing, although I tried running the live CD tonight and this may have more answers.

Running from the live CD, when I put lspci | grep VGA into the terminal, I get the same Intel graphics card:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Nothing about Nvidia.

The Nvidia driver isn't installed or activated on the live CD.  I can, however, get wobbly windows by enabling desktop effects via Preferences>Appearance>Visual Effects.  Just for kicks, I tried installing/activating the Nvidia driver, although I didn't restart the computer to finish the installation.  After doing so, I checked the Nvidia X Server Settings, which again reports that I'm not using the Nvidia X driver.

I'm not quite sure what to do at this point.  Uninstall the Nvidia driver and call it good?

Ideas?

ETA: I'm marking this as solved, because on a whim, I decided to uninstall the Nvidia driver, just to see what would happen.  And, after restarting, I have desktop effects back! I love these wobbly windows! :D

Thanks to all for the help.
Good night!
Lisa

---

### Post by realzippy on 2011-02-20
OMG.
Thought:

*...reconfigure the display and then reboot* (your 1rst post)

..would mean you have uninstalled the nvidia-driver already.
My mistake.The installed nvidia driver disables KMS
(Kernel-mode-setting) for the graphics device,so the Intel driver
was not loaded,and you booted with the minimal vesa driver...
Anyway,glad you made it.BTW,the Intel driver runs desktop effects
pretty well,so there is no need for the nvidia-driver.Also
your battery capacity would decrease noticeable..
Did the laptop come with Windows7 preinstalled,and does the nvidia card work in W7?

*I love these wobbly windows!* 

Me too.Also try the desktop cube with nice animated equirectangular
skydome image...

---

### Post by llmunro on 2011-02-20
Thanks for all of the help and patience while I figured this out! My favorite thing about Ubuntu is that I get to learn something new every day. 
Yes, Windows came pre-installed, but I rarely use it.  The Windows side of things also says that its using the Intel card, although there's seems to be a way to activate Nvidia settings at certain times. (It seems confusing.)

I'm so glad this is fixed.  Using my lappy is way more fun with desktop effects AND it always surprises people who doubt the power of the mighty Ubuntu! :)

---

### Post by agntsgotnosecret on 2011-03-14
"Wondering why System/administration/HardwareDrivers offers a nvidia driver and
*lspci | grep VGA* showing no nvidia card."

-- That's because the nVidia card is showing as "3D controller" and not "VGA":

02:00.0 3D controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
        Subsystem: Samsung Electronics Co Ltd Device c094
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at bc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at be000000 (64-bit, prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Expansion ROM at bd000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [b4] Vendor Specific Information: Len=14 <?>
        Capabilities: [100] Virtual Channel
        Capabilities: [128] Power Budgeting <?>
        Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nouveau, nvidiafb

I believe I have the exact same laptop (Q430-JU01) as the OP -- I also have the exact same issue and it's really bugging me!

Installed Ubuntu 10.10 (64-bit), updated via apt-get, and I then enabled the nVidia drivers.

The reason X cannot be started upon installing the nVidia drivers and rebooting is due to the 'xorg.conf' that is generated -- for some reason, 'nvidia-xconfig' generates a xorg.conf that fails to load the display. The failure to load the display via nVidia could also be due to the fact that lspci shows the the nVidia chipset as the "3D controller" and not a "VGA" adapter -- perhaps someone can shed some light on this?

The only way to get X started for me again is to move the generated 'xorg.conf' out of /etc/X11 and boot using the Intel graphics.

This is the error I get when trying to start X via nVidia's generated 'xorg.conf':

[    22.959] (II) LoadModule: "nvidia"
[    22.959] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    22.960] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.960]    compiled for 4.0.2, module version = 1.0.0
[    22.960]    Module class: X.Org Video Driver
[    22.960] (II) NVIDIA dlloader X Driver  260.19.44  Sun Feb 27 22:42:21 PST 2011
[    22.960] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    22.960] (--) using VT number 8

[    22.963] (EE) No devices detected.
[    22.963] 
Fatal server error:
[    22.963] no screens found
[    22.963] 
Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    22.963] Please also check the log file at "/var/log/Xorg.1.log" for additional information.

If anyone could shed some light on this issue that would be great!

---

### Post by agntsgotnosecret on 2011-03-14
Just a note: lspci is reporting that IRQ 16 is being reserved by both the Wireless LAN device and the nVidia GeForce 310M -- could that be the issue?

Also, nouveau seems to be coming into play here...

Mar 14 07:58:45 q430 kernel: [    9.472929] nouveau 0000:02:00.0: power state changed by ACPI to D0
Mar 14 07:58:45 q430 kernel: [    9.472978] nouveau 0000:02:00.0: power state changed by ACPI to D0
Mar 14 07:58:45 q430 kernel: [    9.472988] nouveau 0000:02:00.0: enabling device (0104 -> 0107)
Mar 14 07:58:45 q430 kernel: [    9.472998] nouveau 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 14 07:58:45 q430 kernel: [    9.473009] nouveau 0000:02:00.0: setting latency timer to 64
Mar 14 07:58:45 q430 kernel: [    9.476137] [drm] nouveau 0000:02:00.0: Detected an NV50 generation card (0x0a8800b1)
Mar 14 07:58:45 q430 kernel: [    9.482963] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PRAMIN
Mar 14 07:58:45 q430 kernel: [    9.482988] [drm] nouveau 0000:02:00.0: ... BIOS signature not found
Mar 14 07:58:45 q430 kernel: [    9.482989] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PROM
Mar 14 07:58:45 q430 kernel: [    9.483000] [drm] nouveau 0000:02:00.0: ... BIOS signature not found
Mar 14 07:58:45 q430 kernel: [    9.483001] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PCIROM
Mar 14 07:58:45 q430 kernel: [    9.483135] nouveau 0000:02:00.0: Invalid ROM contents
Mar 14 07:58:45 q430 kernel: [    9.483283] [drm] nouveau 0000:02:00.0: ... BIOS signature not found
Mar 14 07:58:45 q430 kernel: [    9.483284] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from ACPI
Mar 14 07:58:45 q430 kernel: [    9.483286] [drm] nouveau 0000:02:00.0: ... BIOS signature not found
Mar 14 07:58:45 q430 kernel: [    9.483287] [drm] nouveau 0000:02:00.0: No valid BIOS image found
Mar 14 07:58:45 q430 kernel: [    9.483464] nouveau 0000:02:00.0: PCI INT A disabled

I had tried following the manual install instructions for nVidia drivers (blacklist.conf, etc.) to no avail. Whether nouveau is loaded or not, the graphics card fails to be initialized.

I tried changing the IRQ on wlan0 via ifconfig to no avail as well. 

Are there any ways to change the IRQ for the nVidia card?

---

