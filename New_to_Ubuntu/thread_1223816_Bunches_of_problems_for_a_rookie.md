---
title: "Bunches of problems for a rookie"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by cfishburn on 2009-07-26
Hi everybody,
I have a few items I hope the community can help with. I have been
suffering with these problems for several months, but just haven't had the
time to sit down and ask. 
1) When I attempt to get updates, the following message appears:
E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.

What should I enter in the command line? And how do I report the problem.

2) After I downloaded the latest Ubuntu(last fall I believe), I couldn't download pictures from my camera. The program can't find it.

3) I have no sound.

4) Made the mistake of buying a Kodak ESP 5. Now understand that it is not supported by Ubuntu. Ouch.

5) I have a Pentium 4 Gateway that's 4 years old and need to configure it to accept camcorder images. Understand that the best way to go is firewire
protocol. Exactly what would I need. Camera is a Cannon and accepts firewire and usb.
:confused:

Need help. I am a refugee from Microsoft and really don't want to go back
but my wife is really an end user of pictures and sound and is starting to talk Vista. Help.

---

### Post by halitech on 2009-07-26
1. open a termianal and run
```
sudo dpkg --configure -a
```

nothing to report, something on your system stopped the update and just needs to be completed.

2.with the camera not plugged in, run
```
lsusb
```
plug the camera in, wait about 45 seconds and run lsusb again

3. in the terminal, run ```
lspci
``` ```
aplay -l
``` and post the results here

4. guessing maybe this goes along with 2?

5. do you have a firewire card currently installed? might just need to go usb and transfer the data that way.

---

### Post by roger_1960 on 2009-07-26
Hi

for No 1 you need to enter in a terminal

> dpkg --configure -a

---

### Post by cfishburn on 2009-07-26
Thanks halitech. Ran suggestion for first problem and got this:
dpkg: error processing flashplugin-nonfree (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 flashplugin-nonfree
Now what?

---

### Post by cfishburn on 2009-07-26
Halitech, this is result of lapci

cfishburn@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0a.0 Communication controller: U.S. Robotics USR5660A (USR265660A, USR5660A-BP) 56K PCI Faxmodem (rev 01)
02:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)

What's next

---

### Post by cfishburn on 2009-07-26
This just keeps getting more interesting. Just reran updates and got
the following. (these were the JAVA updates)

E: /var/cache/apt/archives/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb: subprocess new pre-removal script returned error exit status 127

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tzdata/tzdata-java_2009b-0ubuntu0.8.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/t/tzdata/tzdata-java_2009b-0ubuntu0.8.04_all.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009b-0ubuntu0.8.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009b-0ubuntu0.8.04_all.deb)
  404 Not Found [IP: 91.189.88.45 80]


What a mess
cfishburn

---

### Post by halitech on 2009-07-26
try
```
sudo apt-get reinstall flashplugin-nonfree
```

until you get the error taken care of for flashplugin, nothing else is going to work properly in regards to installing things.

Re lspci: I don't see any mention of a firewire card so guessing usb is your only current option. It also looks like you have a SB Live card that should be working fine.

---

### Post by cfishburn on 2009-07-26
Here's aplay results:

cfishburn@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Live [SBLive! Value [CT4871]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SBLive! Value [CT4871]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SBLive! Value [CT4871]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by cfishburn on 2009-07-26
Thanks halitech,
Copied your code and pasted it into command line, got:

 Invalid operation reinstall

What now?

---

### Post by halitech on 2009-07-26
try this
```
sudo apt-get remove flashplugin-nonfree && sudo apt-get install flashplugin-nonfree
``` and see if it works that way

---

### Post by cfishburn on 2009-07-26
Opps, probably help if I told you what code I copied.

sudo apt-get reinstall flashplugin-nonfree 

Then I got the invalid operation message.

cfishburn

---

### Post by cfishburn on 2009-07-26
Just ran new code. Reply is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libisc32 linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by halitech on 2009-07-26
do you have synaptic open right now? if you do, close it and run the command again

---

### Post by cfishburn on 2009-07-26
I did have upgrade manager open, closed it ran code again and result is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libisc32 linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by cfishburn on 2009-07-26
halitech,
I have to run a quick errand, be back in about 30 minutes.I'll catch up with you then.

Thanks for your help
cfishburn

---

### Post by halitech on 2009-07-26
try this
```
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
```

---

### Post by cfishburn on 2009-07-26
Ok, back to it. Ran new code. This is the reply:

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 234059 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: unable to remove /etc/alternatives/firefox-flashplugin: Inappropriate ioctl for device
dpkg: error processing flashplugin-nonfree (--remove):
 subprocess pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree

---

### Post by halitech on 2009-07-26
let's try this info

[http://ubuntuforums.org/showthread.php?t=455541](http://ubuntuforums.org/showthread.php?t=455541)

post 4 states:
> If you have tried everything else, a last resort is this.

1. Backup your /var/lib/dpkg/status file NB You MUST do this first, becuase if you lose this file, your system is hosed.

2. In a terminal, type in the following command: sudo gedit /var/lib/dpkg/status

3. The errant package seems to ardour, is this correct? If so, do a search for it in the opened file.

4. When you have located it, CAREFULLY delete all references to it.

5. Save the file and re-boot.

Hopefully, all should go well, as Synaptic is no longer aware of this package and although it hasn't actually been deleted, over time, it will be over-written.


change ardour to flashplugin-nonfree

---

### Post by cfishburn on 2009-07-27
Halitech,
I do not understand the reference to "ardour". Should I delete all
references, back up the files and reboot, or are you telling me to 
simply replace "ardour" with "flashplugin-nonfree"?
cfishburn

---

### Post by halitech on 2009-07-27
follow the instructions as far as opening files but replace ardour with flashplugin-nonfree

---

### Post by cfishburn on 2009-07-28
Hi Halitech,
This will display my ignorance of Linux. How would you suggest I back up the file. Use cp from command line or the Simple Backup package I have or some other method and is there a naming convention I should use to insure
I can restore the file if something goes wrong.  
And thanks for all your help so far.
cfishburn

---

### Post by halitech on 2009-07-28
easiest and fastest would be to copy it from the terminal

```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.old
```

hopefully nothing will go wrong *crosses fingers*

---

### Post by ager-wick on 2009-10-30
Just posted this solution, which takes any rookie through how to solve issues when a package refuses to be installed uninstalled or configured. It is inspired by the replies to this post, but I've elaborted a bit more to make it rookie-friendly.
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/365392/comments/10](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/365392/comments/10)

---

