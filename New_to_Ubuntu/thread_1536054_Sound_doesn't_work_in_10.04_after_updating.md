---
title: "Sound doesn't work in 10.04 after updating"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by rs87424 on 2010-07-21
My sound was working fine for awhile but after an update it stopped.  Ubuntu seems to recognize my soundcard and everything seems to be unmuted but still no sound... I also did have a problem before with the headphones having this crackling noise and skype not working and I fixed that... but now nothing is working at all... I really need help on this one

---

### Post by Naderovski on 2010-07-21
Check the sound card's driver, or I guess you'd consider changing your sound card.
Have you got any other OS installed?
Good luck.

---

### Post by rs87424 on 2010-07-21
> **Naderovski said:**
> Check the sound card's driver, or I guess you'd consider changing your sound card.
Have you got any other OS installed?
Good luck.
I have windows vista installed and it is running alongside ubuntu... and how exactly would I check the sound card driver?  I am sort of new but some terminal commands I am not familiar with yet
also... my computer is an Acer Aspire 4810TZ I thought maybe that is relevant information

---

### Post by ubunterooster on 2010-07-21
see: 			                          			 			[Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by Naderovski on 2010-07-22
Ok. If you checked [ubunterooster]("http://ubuntuforums.org/member.php?u=1002708")'s link and you still couldn't solve your problem, then  boot to Windows and go on testing the sound card.

---

### Post by rs87424 on 2010-07-22
well I went to Windows and the sound works great... just like normal...

---

### Post by rs87424 on 2010-07-22
maybe its the driver... because I couldn't find the driver on the website... my sound chip is Intel 82801I (ICH9 family) USB2 EHCI Controller#2 Kernel Drivers in use:ehci_hcd

---

### Post by rs87424 on 2010-07-22
would this have anything to do with it?

```
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
```

---

### Post by lidex on 2010-07-22
First try removing your old config files:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**
If 'not found' don't worry.
No help? Need more info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by rs87424 on 2010-07-22
after putting in the first command to remove the old config files I received this message in the terminal: ```
rm: cannot remove `/home/ricky/.asound*': No such file or directory
rm: cannot remove `sudo': No such file or directory
rm: cannot remove `rm': No such file or directory
rm: cannot remove `/etc/asound.conf': No such file or directory

```

the next command I got these results* and my computer model and make is an **ACER ASPIRE 4810TZ**
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
computer:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                       1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-24-generic    2.6.32-24.201007200500                          Ubuntu-supplied Linux modules for version 2.
computer:~$ head -n 1 /proc/asound/card*/codec#*

```

---

### Post by lidex on 2010-07-22
> **rs87424 said:**
> after putting in the first command to remove the old config files I received this message in the terminal: ```
rm: cannot remove `/home/ricky/.asound*': No such file or directory
rm: cannot remove `sudo': No such file or directory
rm: cannot remove `rm': No such file or directory
rm: cannot remove `/etc/asound.conf': No such file or directory

```

the next command I got these results* and my computer model and make is an **ACER ASPIRE 4810TZ**
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
computer:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                       1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-24-generic    2.6.32-24.201007200500                          Ubuntu-supplied Linux modules for version 2.
computer:~$ head -n 1 /proc/asound/card*/codec#*

```

That was two commands, to be run separately. But don't worry about that now.
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by fehel001.303 on 2010-07-22
Go System> Preferences> Sound, then check hardware and see if you got an internal video card and if you have (and you are not using that one) then try selecting the other one, also check the profile of the audio card, normally its Analogue Stereo Duplex, and check if its got an output and input.

---

### Post by MatthewPlanchard on 2010-07-22
The first one is two lines.  Each line is a command.  Make sure you run them separately.

Edit:  Ah, I see that was already addressed.  My apologies.

---

### Post by rs87424 on 2010-07-22
my user file... would that be my home file folder in ubuntu or ACER>documents and settings>user file folder

this is the result I got from the terminal:
```
bash: utils_alsa-info.sh: No such file or directory

```
maybe I will try the other file and see what happens

---

### Post by rs87424 on 2010-07-22
> **fehel001.303 said:**
> Go System> Preferences> Sound, then check hardware and see if you got an internal video card and if you have (and you are not using that one) then try selecting the other one, also check the profile of the audio card, normally its Analogue Stereo Duplex, and check if its got an output and input.
I know what you are talking about... and I did have two or three recognized in there for the output as well as the hardware... and now I only have digital stereo HDMI as the only one listed

---

### Post by lidex on 2010-07-22
> **rs87424 said:**
> my user file... would that be my home file folder in ubuntu or ACER>documents and settings>user file folder

this is the result I got from the terminal:
```
bash: utils_alsa-info.sh: No such file or directory

```
maybe I will try the other file and see what happens

Your default download directory is ~/Downloads you could try changing to it in terminal then running the previous command.
```
cd ~/Downloads
```

---

### Post by MatthewPlanchard on 2010-07-22
Also, make sure you saved the alsa-info-script file that in lidex's sig to your home folder (/username/home/) before running the following command:

```
sudo bash utils_alsa-info.sh
```

As far as the earlier command went, we meant run the following:

```
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

as two separate commands.  You wouldn't have gotten the output you did if you had.

It's weird that the other audio options disappeared.  Maybe a fresh install of alsa and pulseaudio would reinstate them, allowing you to have sound again?

---

### Post by rs87424 on 2010-07-23
well every single thing I put into the terminal including those commands that were supposed to run separately say "no such file or directory" 
its a little frustrating 
I moved the file that was linked in your sig into different files and each time the same message was displayed no such file or directory

---

### Post by rs87424 on 2010-07-23
> **MatthewPlanchard said:**
> Also, make sure you saved the alsa-info-script file that in lidex's sig to your home folder (/username/home/) before running the following command:

```
sudo bash utils_alsa-info.sh
```

As far as the earlier command went, we meant run the following:

```
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

as two separate commands.  You wouldn't have gotten the output you did if you had.

It's weird that the other audio options disappeared.  Maybe a fresh install of alsa and pulseaudio would reinstate them, allowing you to have sound again?
I have a feeling you are right Matt... maybe I should just do that and clean up any bugs that seem to haunt my computer's sound every time I update

---

### Post by lidex on 2010-07-23
> **rs87424 said:**
> well every single thing I put into the terminal including those commands that were supposed to run separately say "no such file or directory" 
its a little frustrating 
I moved the file that was linked in your sig into different files and each time the same message was displayed no such file or directory
Don't worry about the config files, we're done with those.
To make this more foolproof do this. Right-click the alsa-info link in my sig. Select 'save link as'. In the combo box that comes up select 'Desktop' in the left column. Click the save button. Now open a terminal. Enter these commands, one-line-at-a-time, pressing <enter> for each:
```
cd ~/Desktop
```
```
sudo bash utils_alsa-info.sh
```
Use <Tab> to cycle through options in the terminal when needed.

---

### Post by rs87424 on 2010-07-23
> **lidex said:**
> Don't worry about the config files, we're done with those.
To make this more foolproof do this. Right-click the alsa-info link in my sig. Select 'save link as'. In the combo box that comes up select 'Desktop' in the left column. Click the save button. Now open a terminal. Enter these commands, one-line-at-a-time, pressing <enter> for each:
```
cd ~/Desktop
```
```
sudo bash utils_alsa-info.sh
```
Use <Tab> to cycle through options in the terminal when needed.
Sorry this is exactly what message I got and I followed your directions properly 
```
bash: utils_alsa-info.sh: No such file or directory
```

---

### Post by lidex on 2010-07-23
```
cd ~/Desktop
ls
```
Post result.

---

### Post by rs87424 on 2010-07-23
```
alsa-info.download
```

---

### Post by MatthewPlanchard on 2010-07-23
```
mv alsa-info.download alsa-info.sh
sudo chmod 755 alsa-info.sh
sudo bash alsa-info.sh
```

---

### Post by rs87424 on 2010-07-23
Here are the results I got from Matthew 
```
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=77755392d8101d8cc85a526e453455dd7c3bcd3a

Please inform the person helping you.


```

---

### Post by MatthewPlanchard on 2010-07-23
Cool!  Good job.  We are now officially out of my depth, so let's await more seasoned assistance. :popcorn:

---

### Post by lidex on 2010-07-24
Do you have onboard audio disabled in bios? Also what video driver are you using? Did you just upgrade that?

---

### Post by rs87424 on 2010-07-24
> **lidex said:**
> Do you have onboard audio disabled in bios? Also what video driver are you using? Did you just upgrade that?
I don't know how to answer you about the audio... I looked into the bios and I couldn't find the setting to enable or disable the audio because I didn't see anything that said onboard audio or audio settings at all and video driver I am also not sure about that... how would I check that?

---

### Post by lidex on 2010-07-24
Alsa is only picking up your hdmi device. Try an alsa upgrade via the alsa-upgrade link in my sig.

---

### Post by rs87424 on 2010-07-24
I downloaded the script file and went to 

```
 sudo ./AlsaUpgrade-1.0.23-2.sh -c
```

and this was the result:

```
*  alsa-driver-1.0.23 make failed

```

should I try again?

---

### Post by lidex on 2010-07-24
Yes, but install this first:
```
sudo apt-get install build-essential
```

Read through that entire post also.

---

### Post by rs87424 on 2010-07-24
I put in the code you mentioned and everything works I think but I did get this message at the end:
```
alsa-plugins-1.0.23 configure failed
```

---

### Post by rs87424 on 2010-07-25
the compile worked and when I go to the install this is the result:

```
*  alsa-utils-1.0.23 configure failed
```

---

### Post by lidex on 2010-07-25
You'll need to start over. First install the packages referenced here:
[http://ubuntuforums.org/showpost.php?p=9124024&postcount=722](http://ubuntuforums.org/showpost.php?p=9124024&postcount=722)

---

### Post by rs87424 on 2010-07-25
For some reason after I posted this in the forum it worked the compilation and the install... and after that I restarted... and nothing happened afterwards... strange... sorry I should have posted that but I was too sleepy

---

### Post by rs87424 on 2010-07-25
> **lidex said:**
> You'll need to start over. First install the packages referenced here:
[http://ubuntuforums.org/showpost.php?p=9124024&postcount=722](http://ubuntuforums.org/showpost.php?p=9124024&postcount=722)

I ran this script successfully, all of the packages were installed successfully

but still no sound

---

### Post by lidex on 2010-07-26
> **rs87424 said:**
> I ran this script successfully, all of the packages were installed successfully

but still no sound
OK then. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by rs87424 on 2010-07-26
```
bash: utils_alsa-info.sh: No such file or directory
```

I have tried this before I think

---

### Post by rs87424 on 2010-07-26
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```
Could there be a problem with this file?  I keep seeing error messages related to this file.

---

### Post by rs87424 on 2010-07-26
OK

I just got my audio to work...

I found that when I went to this thread:
[http://ubuntuforums.org/showthread.php?t=1477872&highlight=sound+problems&page=2](http://ubuntuforums.org/showthread.php?t=1477872&highlight=sound+problems&page=2)

I looked at the second page and found the install backports script and I did that... then when I rebooted everything seemed to be working great.. and also there was an application called the pulseaudio device chooser... I quit that application as well and everything went back to normal

---

### Post by MatthewPlanchard on 2010-07-26
Congratulations!  Please use the thread tools to mark the thread as "Solved" when you get a chance.

I'm glad you got it working again.

---

