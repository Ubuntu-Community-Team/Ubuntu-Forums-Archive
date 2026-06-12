---
title: "Is there a 64bit nVidia driver?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by bwallum on 2009-04-27
I had problems with flash and so moved to 64bit flash which works for me. I have also loaded 64bit Skype which is a bit clitchy but works. To get things working smoothly I removed ndiswrapper.

Now when I load the nVidia 180.44 driver I get an unstable system. It hangs when browsing.

I'm assuming that the problem lies with some incompatibility between the 64bit stuff and the nVidia driver. The standard vesa driver works fine but I can't use Stellarium (needs accelerated graphics) with the vesa driver and other graphics intensive software is very slow.

Can anybody help out with this, is there a 64bit version of the nVidia driver?

---

### Post by rajeev1204 on 2009-04-27
Of course there is.

If you are using a 32 bit OS , you can only use the 32 bit driver and for a 64 bit OS,you can only use the 64 bit nvidia driver .Its not the same for software though as you can install 32 bit apps on  a 64 bit system.
If you installed from synaptic, you are using the appropriate drivers for your system.

In a terminal type uname -a to tell which OS you have.



raj

---

### Post by Didius Falco on 2009-04-27
This is the result I get from the Nvidia driver download site for nVidia GeForce 7300 GS:

[http://www.nvidia.com/object/linux_display_amd64_180.51.html](http://www.nvidia.com/object/linux_display_amd64_180.51.html)

Here is the driver download search page:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by LowSky on 2009-04-27
no need to download it from nvdia's site, loading the driver from the repos will give you 64bit driver.

Infact if you are using 63bit ubuntu, it will choose the 64bit verisn of any program/driver if its availible.

---

### Post by bwallum on 2009-04-27
Thanks all for the help, special thanks to didius for the useful links.

I learnt that nVidia 64bit drivers have gone through two iterations more that the Ubuntu repos 180.44. We now have 180.51 and 185.18.04 (24th April 2009). These drivers only appear to be available in .run files which I understand need compiling (something I have not yet done but you can teach me!).

Feedback on the above would be useful. In view of the problems with 180.44 can I ask the Ubuntu devs to debianise the 180.51 and 185.18 drivers please?

EDIT
Thanks to ohzopants and SentientFluid, I have got the nVidia 185.18.04 driver running and all appears stable.

I have tried all your commands and also tried booting into recovery mode, which worked. For me the best route was:-

Download the .run file to Desktop. Right click on the file, go to the Permissions tag and check the box to run as executable.

Take note of the following instructions first because after the next step you will lose the gui.

Open a full screen consol (normal windowed terminal will NOT work) with ctrl-alt-F1

Stop the x server with```
sudo /etc/init.d/gdm stop
```change directory to Desktop with```
cd Desktop
```then run the file with
```
sudo sh NVIDIA-Linux-x86_64-185.18.04-pkg2.run
```Follow the prompts when the file runs and give it time between each option, it can be slow and nothing appears to be happening at times. Allow the installer to re-write your xorg.conf file and compile an nVidia kernel interface. When the installer completes and you return to the prompt, type```
sudo reboot
```and let the system reload to Desktop.

That's it, you should have all details and control of the driver in System>Preferences>NVIDIA X server settings. Note that your driver will NOT show in System>Administration>Hardware Drivers

Thanks again!
Bob

EDIT Released driver is now NVIDIA-Linux-x86_64-185.18.14.pkg2.run

---

