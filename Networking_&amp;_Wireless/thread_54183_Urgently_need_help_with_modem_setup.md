---
title: "Urgently need help with modem setup"
date: 2005-08-03
forum: Networking &amp; Wireless
---

### Post by mingus on 2005-08-03
I need assistance please with getting a modem fully installed.  I have near zero experience with this in Linux.

The modem is a SmartLink smartpci562, per the scanModem utility

I installed the 2.9.9a driver modules per the Unofficial Start Guide:
sudo dpkg -i sl-modem-modules-*.deb
sudo apt-get install sl-modem-daemon

The installation indicated the device to be /dev/modem with a symlink pointing to /dev/ttySL0

After reboot, lspci reported:
0000:00:12.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
The Ubuntu Device Manager also shows the modem 

lsmod shows no modem related modules.

System/Administration/Networking returned the error:
"could not enable the interface ppp0"

At this point, I was very cautious, not wanting to bork anything up.  I don't know the diffs between wvdial vs pppconfig, and the deb install package refers to /etc/default/sl-modem-daemon as the initialization script where parms such as in wvdial.conf are also entered.  

Trying wvdial returns:
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

At system shutdown, there is the message:
"Shutting down the SmartLink modem normally . . . no slmodemd daemon running"

At system startup, there is a message that flashes shortly after ALSA, but too fast to read and it does not appear anywhere in the logs that I could find.  It appears to start with:
"Loading SmartLink . . . "

ls /dev/modem shows that file to be there; however
ls /dev/ttySL0 reports no file found

Using BUM, the service "sl-modem-daemon" is listed, but shows it to *not* be running.  Asking BUM to start the service returns a "service started" message but the indicator light does not change to green, and no changes observed elsewhere.

BTW, this system also has a 10/100 ethernet card.  I removed the cable so that it is not started at boot, but did not deactivate the device itself.

Thanks very much in advance.

---

### Post by wvslkr on 2005-08-03
Hi Mingus.  
Don't know if this has any bearing, but I don't understand what ttySL0 is.  Any modem setup I have seen ties to a serial port.  I would think ttyS0.  Other than that I am at a loss.

GL to you. :)

---

### Post by amohanty on 2005-08-03
I think the module is called lt_modem

try:
>> locate lt_modem
If you cannot find it probably the driver module is not installed.

If you can
>> modprobe lt_modem
and
>> modprobe lt_serial

If they return anything (ie print anything to console) then they are not loaded.
You can add lt_modem to /etc/modules.

Also I hink the drivers are available as source of smlink.com

HTH
AM

---

### Post by mingus on 2005-08-03
Thx guys, but no help.  ttySL0 is correct for the SmartLink modem.  The lt_modem is for the lucent-based modems, not the smartlink chipset.

Checking other threads, I saw a ref to a module named "slamr" that should be loaded.  I found the module in /lib/modules/..... but modinfo and modprobe does not recognize it(???).

It seems that the module and driver installation is not complete, although dpkg indicates it is and I can find all the files such as the slmodemd script.

Any ideas?  

azz, you're expert on these modems, suggestions?

EDIT:  May have found a solution - at least, the modem is now being recognized.  Thread #35056 Post #4 says:

*I made it work today, using ALSA instead of sl-modem-module. It was done by editing the /etc/default/sl-modem-daemon file at the line device. Changing auto for hw:0 (or hw:1, test both) you make alsa control the modem. By doing this I've made wvdial work with /dev/modem.*

The scanModem file slmodem.txt refs packages that are newer than those in the repository (and supposedly, also newer code than the smlink download) that use this ALSA technique.  Mind-numbing to sort it out, though.

Tomorrow I'll go to work on (hopefully) getting the dialing to work.  Spent a *lotta* time reviewing the threads, and jeez, what a bloody nightmare.  Getting these modems to work are a major drawback for regular users moving to linux.

---

### Post by az on 2005-08-04
The precompiled modules are for the 386 kernel.  Is that what you are running?

If that is not the case, you need to compile your own modules.  It is pretty straightforward.

Install the sl-modem-source package and untar the tarball it puts in /usr/src

You can make make install it or run the

debian/rules binary-modules

command to build a deb package for the modules.

If this is not the case, you can go to the smartlink website and get the latest source and build that.  The most recent chipsets from smartlink require the latest source.  It is released under a different licence and does not permit it's use for other compatible chipsets - which is why I is not packaged in Ubuntu.

Also, you can try using the alsa module, 

sudo dpkg-reconfigure sl-modem-daemon

That toggles between the alsa module and the slamr module.  I am no more help than what is written in the redme files when it comes to the intel810xm alsa modules, since it never worked for my hardware.

---

### Post by mingus on 2005-08-04
azz, thx a bunch for the reply.  Yes, using 386 kernel.  With the fix I found (above) the device is at least now being recognized.  That post seems to suggest that what he did in the sl-modem-daemon file may be the same tweak as the dpkg toggle you refer to.  Will investigate further tomorrow.

---

### Post by Matchless on 2005-08-05
Hi,
    Did you generate the config file and modify? Here is an example. If you need more details I can post the whole procedure, but it is a bit long. I have just set up a couple of Smartlink Modems on Hoary PC's this past week and they work well! The basics are, ensure that your linux kernel headers are installed, install with Synaptic, if not, then install the driver package, must be 2.9.9a or higher for the latest kernel 2.6.10-5-386 anf then install the sl-modem-daemon from the repositories with Synaptic.
A quick test is to reboot your PC and do a "modprobe slamr" and check if successfull.

Do the following to setup the wvdial dialler for testing and configuring. This also creates the /etc/wvdial.conf
sudo wvdialconf   /etc/wvdial.conf
The wvdial requires that you edit the  /etc/wvdial.conf as follows, adding in your personal information and a line Carrier Check = no. Example of file below:

[Dialer Defaults]
Modem = /dev/ttySLT0
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
# if there is problem with dial tone acquisition, add into the above line:
#    X3
# meaning "dial without waiting"
ISDN = 0
Modem Type = Analog Modem
Phone = 0800123456
Username = peterpan
# for MSN.net, use instead
#  Username = MSN/Your_Login_Name   
Password = bandylegs
# if useing the SmartLink slmodem drivers, uncomment Carrier Check = no:
Carrier Check = no

The lines above beginning with " # " are Comments not read as code.
Remove the " # " to activate a line. Save the file and then try getting on line from the terminal with:
sudo wvdial

Watch the results in the console screen. Sudo fg wvdial. Then Ctrl+c will stop wvdial.
If wvdial works you can try configuring kppp dialer and try that, but a script file will be needed to start the modem daemon and stop it so that the console is not needed to be left open. To do this install the sl-modem-daemon as shown in the next step by using Synaptic. Use the "Query Modem" part in Kppp to check id your modem is recognised and setup.

Hope this helps
Regards
Matchless

---

### Post by mingus on 2005-08-05
Matchless -

Thanks very much.  An issue came up and I haven't been able to get back to this; will do tomorrow.  I did install sl-modem-daemon and sl-modem-modules-2.6.10-5-386 version 2.9.9a.  The device was not recognized yet the driver was attempting to load at boot/unload at shutdown.  When I tried the fix in post #4 of:

[http://www.ubuntuforums.org/showthread.php?t=35056](http://www.ubuntuforums.org/showthread.php?t=35056)

which apparently toggled the driver from slamr to alsa, the device was recognized.

The driver now shows being successfully started and shutdown.  

What is strange is that both before and after making the change to the /etc/default/sl-modem-daemon, the modinfo command does not see slamr, but the driver file is definitely there at /lib/modules/2.6.10-5-386/misc.  That is what led me to look for the alsa alternative.

I plan to use gnome-ppp.  If the modem doesn't cleanly initialize and close down without having to get into a terminal, I'll be in trouble - I'm doing this for another W$-like user.

---

### Post by az on 2005-08-05
Can you not load the slamr module by hand?  I know the install script does not run a depmod -a, but that is fixed the next time you reboot.

What happens when you modprobe slamr?

The daemon is starting at boot time, that is what you are seeing in dmesg.  Whether it detects a device or not is diplayed.  If you use the alsa module (snd-intel8x0m) you pretty much have to configure it as an alsa device, and I think that is not done automagically.

sl-modem-daemon creates a symlink between the device and /dev/modem, so gnome-ppp should see it without any problems.

---

### Post by mingus on 2005-08-05
Thx azz, for the help.

*Can you not load the slamr module by hand?  I know the install script does not run a depmod -a, but that is fixed the next time you reboot.  What happens when you modprobe slamr?*

It returns a "module not found" error.  The module file is however on disk.

*The daemon is starting at boot time, that is what you are seeing in dmesg.  Whether it detects a device or not is diplayed.  If you use the alsa module (snd-intel8x0m) you pretty much have to configure it as an alsa device, and I think that is not done automagically.*

Yes, it appears to be starting now at boot.  However, none of the logs show it (for that matter, msgs like "starting Alsa" is not in the logs, either).  Before I tweaked the sl-modem-daemon config file, I could not start the daemon.  Now BUM shows the daemon as running.  Wvdial recognizes the device (/dev/modem aka ttySL0) now.  I haven't done anything other than that tweak.  I also notice that the alsa module snd-intel8x0 is loaded, in addition to the driver for the actual CS sound device in this system.

*sl-modem-daemon creates a symlink between the device and /dev/modem, so gnome-ppp should see it without any problems.*

That's what I'm hoping, since the driver seems to be running now.  I'll test over the week-end.

---

### Post by mingus on 2005-08-12
fwiw, maybe of use to others struggling with the smartlink modem . . .

The problem was the known bug re a lock being put on the port preventing the modem from being accessed.  The fix is "ungrab winmodem", a program that must be downloaded from the linmodem site, compiled, and added to /etc/modules in front of slamr which must also be manually added (the Alsa alternative is inserted into the kernel and loads automatically).  Note that this fix only works for the 2.9.9x drivers (the Ubuntu version is 9a, the linmodem site has up to 9e but it must be compiled) - it does not work with the 2.10 version on the smartlink website.  The driver that came with the modem on CD (recently purchased) was several years old, 2.7 - and does not seem to work with the 2.6 kernel.

This would not have been all that difficult to navigate thru were it not for conflicting or even misleading information.  Scanmodem is very useful to diagnose the chipset and point to a driver, but its instruction files are problematic.  Definitely not for newbs.

What was most helpful, along with forum posts, was reading the /etc/init.d script and configuration files.  The script shows the logic used when the driver is loaded at boot to determine whether the smartlink proprietary slamr driver should be used vs an Alsa driver.  If slamr cannot be modprobed, then the Alsa driver is used.  However, slamr will not load unless ungrab-winmodem executes first, hence forcing Alsa to load every time until the fix is installed. This is why "dpkg-reconfigure sl-modem-daemon" toggling of Alsa to slamr would not work or as noted above, also will prevent the newest 2.10 driver to work in some cases.  The Alsa alternative was not possible on this system due to a sound card device conflict.

The config file is called from the script; I didn't find documented anywhere.  It is /etc/default/sl-modem-daemon, and is read by /etc/init.d/sl-modem-daemon at boot.  If Alsa is being used the device value should be changed from "auto" to the hardware port not assigned to the sound card, usually "1".  On some systems, "slamr0" or "slamr" should be specified rather than auto.  There are other parms avail in this file.

The dialers also make a difference, although I don't know why.  wvdial returns a "modem not responding" error on this smartlink and also on an external Amigo conextant controllerless modem I used for comparison testing.  pppconfig with pon also does not work.  But Gnome PPP works nicely, just be careful to set the correct modem speed - Gnome PPP wants to default to 460800 but that will degrade modem performance, so it's important to force the 115200.

A last discovery is that this modem is performing noticeably slower than the external hardware serial modem, very inexpensive unit with a Conextant chipset.  I haven't determined yet whether this is a config issue or simply an inherent diff in the two devices.

Thx again to those who gave a hand to my prev request for assistance.

---

