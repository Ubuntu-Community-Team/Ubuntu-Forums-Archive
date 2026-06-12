---
title: "No sound after Ubuntu 9.10 Update (Intel ICH9)"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Mongoose088 on 2010-05-04
Hello all,

I've been having a rough update from 9.04 to 9.10. I have no sound after updating to 9.10 (Not a clean install, I updated from the update manager).

Here's the relevant output of lspci:
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


```

I've been searching the forums, and my problem seems to be in this file:
/etc/modprobe.d/alsa-base.conf

Here is its output:

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
# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=10 power_save_controller=N

#options snd-hda-intel model=3stack

```

I should note that those last two commented options were attempts at fixing the problem, both of which did not work.

Also, here is the output of the command "aplay -l"
aplay: device_list:223: no soundcards found...

EDIT: I can actually hear sound clearly when I listen to certain audio streams online! However, I have no control over the volume, and plugging in my headphones has no effect. It still comes out of the speakers. aplay still shows no sound card, so I assume it's running on some kind of "generic output".

Thanks.

---

### Post by Jon Monreal on 2010-05-04
From [http://ubuntuforums.org/showthread.php?t=1036508:](http://ubuntuforums.org/showthread.php?t=1036508:)
>  just tried the following on my Aspire 8930G...Kubuntu 8.10

Edit/reduce alsa-base (the last few lines beginning "options...") to  just this:

options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto 

and reboot...

Sound works beautifully... hope this helps...

To do this, you will need to type in the terminal
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
and press enter.

If you need additional help doing this, please feel free to ask.

---

### Post by Mongoose088 on 2010-05-04
Hi Jon,

Unfortunately the posted solution didn't fix the problem.

My alsa-base.conf file has been commented down to the final 3 lines as described. But "aplay -l" still shows that no cards have been found. Do you have any other solutions?

Thanks for your help!

---

### Post by Jon Monreal on 2010-05-04
Try going to a terminal (Applications>Terminal), type
```
alsa reload
```
and press enter, and see if it works for you then.

---

### Post by Mongoose088 on 2010-05-04
It seems the problem goes deeper.

First, the command given wouldn't run because it didn't have the directory /var/run/alsa. So I created it, and re ran the command:
```

tom@tom-1320:~$ sudo alsa reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/tom/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

```

^It would seem the command isn't doing much of anything at all.
---

Now, I was also looking through the Ubuntu Documentation, and I think I've isolated my problem:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I get stopped right at the section titled :
Do you have the sound modules installed?

Nothing comes up after using the command:
find /lib/modules/`uname -r` | grep snd

So I use the following command, but receive a packaging error:
```

tom@tom-1320:~$ sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-18-generic"
Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-18-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0  newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done


```

I feel like the issues might be with sound modules.

Thank you for your quick assistance so far.

---

### Post by lidex on 2010-05-05
Please remove any custom entries from alsa-base.conf and reboot. Now do this. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by Mongoose088 on 2010-05-05
Sorry Lidex, I wasn't able to try your posted solution. I simply updated to 10.04 to solve the problem. Moderators, feel free to close the thread.

Thank you for all the people who tried to help!

---

### Post by lidex on 2010-05-05
Not a problem, got your solution, right? That's why we're here. And please don't capitalize my username, it makes me feel important. ;)
Enjoy.

---

