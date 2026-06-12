---
title: "ubuntu screen size inside virtualbox virtual machine"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by mowaffak on 2010-01-02
Dear every body, I am a 24 hour old ubuntu user. I installed it as a guest OS inside Virtual machine created by Virtual box. The host OS is Windows 7 home premium. I have the following problems for which I am seeking your help;
First, upon starting the virtual machine, the screen size is much smaller than the full screen size with no way to enlarge. I need to find a way to enlarge the guest Ubuntu screen to fit the full screem. This one problem. The second problem is that when ubuntu completes launching a message telling me the screen colors need to be changed from 16 to 32 bit color mode. I tried to do the change through the display preferences but I could not find the required options. Finally, The reason I am putting ubuntu in use is to get my HP printer laserjet 1000 to work (has no driver for Windows 7). So will Ubuntu recognise the hardware and installs the necessary driver automatically or will need me to do something??

Thank you for help and advice.

---

### Post by 3rdalbum on 2010-01-02
1. You need to install the Virtualbox Guest Additions in Ubuntu so it can use the Virtualbox video driver, and achieve a higher resolution. You can find instructions in the manual at [www.virtualbox.org](www.virtualbox.org)

2. The screen colours message is displayed by Virtualbox itself, right? Installing the Guest Additions in Ubuntu should provide this as well.

3. You will need to tell Virtualbox to "pass through" the USB device to the guest OS. Then Ubuntu will discover it (all distros contain the HP printing and scanning driver) and you can use it straight away. Once again, USB passthrough is covered in the Virtualbox manual (or should be pretty self-explanatory to set up anyway).

---

### Post by Dennis N on 2010-01-02
As stated in the reply above, install the guest additions:

In the VirtualBox window menu:

```
Devices > Install Guest Additions
```

After the installation process ends, you will need to restart the guest os. Then you can resize the window as desired or run full screen (Rt-Ctrl + F). You also have seamless mouse integration - it won't be captured in the VB window.

---

