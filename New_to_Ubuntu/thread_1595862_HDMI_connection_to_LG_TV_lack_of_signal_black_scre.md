---
title: "HDMI connection to LG TV lack of signal: black screen after ubuntu 10.04 loading"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by lvmarat on 2010-10-13
I have nettop computer (Asus eeeBox eb1012, 

Intel Atom N330, ION Nvidia card, 2MB RAM, Ubuntu 10.04 OS, 64-bit). I would like to connect it to LG TV 26LE5300 with HDMI and use as HDPC. 

 
VGA connection is working fine. But on HDMI connection TV failed to 

recognize the computer. In fact I see computer boot up normally and for a 

few second I can even see the desktop, but then monitor is turn off and I 

see only black screen.

There is HDMI-HDMI connection to my computer. I used HDMI1 output 

and selected it in the menu setting of the TV as HDMI-PC. I upgraded nVidia graphic card driver (current version 256.53) in my computer, and nVidia card does recognizes the monitor (VGA connection). Here is the data from nVidia X-server Display configuration:

Display        LG Electronics LG TV 1360 x 768
Model          LG Electronics LGTV (CRT-0 on GPU-0)
Resolution    Auto

X Server Information:
Operating system       Linux-x86_64
Nvidia driver version:   256.53
Display name      marat-desktop:0.0
Server version number: 11.0
server vendor string        The X.Org Foundation
Server vendor version:   1.7.6 (10706000)
NV-CONTROL Version      1.23
screens                          1

X Screen information:

Screen number 0
Display name      marat-desktop:0.0
Dimensions        1360 x 768
Resolution          30 x 30 dots per inch
Depth                24
GPUs:                 ION (GPU0)
Displays:            LG Electronics LGTV (CRT-0)
Recovered GPU Errors: 0
Stereo mode: Unknown

GPU0
Graphic Processor Ion
Cuda cores          16
vBios version  62.79.60.00.00
memory              512 MB
M.interface          64 bit
Bus type               integrated
Bus ID:                PCI:2:0:0
PCI device ID:       0x087d
PCI vendor ID      0x10de
IRQ:                   22
X Screens:         Screen 0
Display Devices:     LG Electronics LG TV (CRT-0)

Interestingly, when I choose Monitors in System>Preferences menu of 

my Desktop it shows:

It appears your graphics driver does not support the necessary 

extensions to use this tool. Do you want to use your graphics driver 

vendor's tool instead?


If I select "Yes", the  Nvidia X Server Setting window is promped.

I checked HDMI cable and HDMI inputs in TV. Everything looking OK, and 

TV recognizes my DVD player via HDMI. The problem only with PC. I 

hooked the PC using the same HDMI cable to Sony TV 40EX, and it 

immediately recognizes the PC.
I also tried Win-F8 (suggested by Asus) and Win-F4 keys but it doesn't 

work. 

Here is the way I connected my PC to TV:
1.Connect HDMI cable.
2.Turn on PC
3. Turn on TV and choose HDMI1-PC input.
PC start to boot, Os is loaded, I see desktop and after 3 seconds the 

monitor is turn off (black screen) and lost the signal (No signal info on 

screen).

I think the LG TV for some reason doesn't recognize the Nvidia card via 

HDMI input. I'd  be appreciate for any suggestion.

Does this problem is similar to so called X splash/Plymouth problem?

Thank you.
Marat

---

### Post by supergillis on 2010-10-29
I have the same problem but with ATI Mobility Radeon HD 3400 Series... Help would be appreciated.

Gillis

---

### Post by sandyd on 2010-10-29
> **supergillis said:**
> I have the same problem but with ATI Mobility Radeon HD 3400 Series... Help would be appreciated.

Gillis

works here.
the only thing was that I needed two monitors.
One attached to VGA to configure it while the other monitor was off.

try that.
------------------------------

and the mobility radeon HD3400 works, im typing from a mobility radeon HD 3650 (fglrx).

I find that the propreity drivers generally have better support for this kind of setup. (you also might want to turn off the laptop screen in the ATI settings manager after youve installed fglrx if you have t done so already)

---

### Post by vyom.neeraj on 2010-10-30
Hi people,

Im still new to Ubuntu and also this forum. However, I have the same prob with my setup as well. 

Im using Ubuntu 10.10 on my Asus G1S-A1 laptop. I am trying to connect it to my sony 720p TV using HDMI cable. I have the Nvidia drivers (dloaded from System > Administration > Additional Drivers) which are current recommended by Ubuntu. I tried to set it up using the Nvidia panel, but not been successful. I dont get any video, no idea about audio at this point. 

If anyone has a solution, please post.

---

### Post by spvo on 2010-10-31
lvmarat,

I've had a similar problem and finally figured out something that would fix the video.  I wrote about what I did to fix it on this thread [http://ubuntuforums.org/showthread.php?t=1604896]("http://ubuntuforums.org/showthread.php?t=1604896").  Hope it helps.

---

