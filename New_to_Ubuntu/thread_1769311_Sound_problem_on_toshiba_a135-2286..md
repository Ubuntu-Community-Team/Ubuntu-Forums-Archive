---
title: "Sound problem on toshiba a135-2286."
date: 2011-05-27
forum: New to Ubuntu
---

### Post by JulioGee on 2011-05-27
I have a toshiba A135-2286 running ubuntu 11.04 nutty.
it works great. but just one problem my sound doesnt work.
there is no hardware listed in my sound preferences.
on output it says simutaneous output and rtp multicast.
and my input doesnt have anything in it either.
i've tried everything i can find on google.
heres my alsa info [http://www.alsa-project.org/db/?f=23821ef7190dd92cf33e5633a531d1a29644574a](http://www.alsa-project.org/db/?f=23821ef7190dd92cf33e5633a531d1a29644574a)

---

### Post by lidex on 2011-05-27
You have been busy. Those tweaks you made could well be causing your problem. We'll need to reset to default. 
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*
Next post these outputs:
```
cat /etc/modprobe.d/alsa-base.conf
```
```
ls /etc/modprobe.d/
```
```
dpkg -l | grep "alsa"
```

---

### Post by JulioGee on 2011-05-28
I did all of them.

---

### Post by JulioGee on 2011-05-28
and on the first one it just said no such file or directory

---

### Post by lidex on 2011-05-28
I need you to copy and paste the terminal output from those last three commands into your next post. For each block of text, highlight and press the # above to enclose in code tags.

---

### Post by JulioGee on 2011-05-28
#1
        [LEFT]rm -r ~/.pulse ~/.asound* ~/.pulse-cookie [/LEFT]
    [LEFT]rm: cannot remove `/home/juliogee/.pulse': No such file or directory[/LEFT]
    [LEFT]rm: cannot remove `/home/juliogee/.asound*': No such file or directory[/LEFT]
    [LEFT]juliogee@juliogee-Satellite-A135:~$ sudo rm /etc/asound.conf[/LEFT]
    [LEFT][sudo] password for juliogee: [/LEFT]
    [LEFT]rm: cannot remove `/etc/asound.conf': No such file or director




#2
[LEFT]
[/LEFT]
    [LEFT]ls /etc/modprobe.d/[/LEFT]
    [LEFT]alsa-base                   blacklist-modem.conf[/LEFT]
    [LEFT]blacklist-ath_pci.conf      blacklist-oss.conf[/LEFT]
    [LEFT]blacklist.conf              blacklist-rare-network.conf[/LEFT]
    [LEFT]blacklist-firewire.conf     blacklist-watchdog.conf[/LEFT]
    [LEFT]blacklist-framebuffer.conf[/LEFT]
    [LEFT]juliogee@juliogee-Satellite-A135:~$ [/LEFT]





#3



dpkg -l | grep "alsa"[/LEFT]
    [LEFT]ii  alsa-base                                         1.0.24+dfsg-0ubuntu1                       ALSA driver configuration files[/LEFT]
    [LEFT]ii  alsa-source                                       1.0.24+dfsg-0ubuntu1                       ALSA driver sources[/LEFT]
    [LEFT]ii  alsa-utils                                        1.0.24.2-0ubuntu6                          Utilities for configuring and using ALSA[/LEFT]
    [LEFT]rc  alsamixergui                                      0.9.0rc2-1-9                               graphical soundcard mixer for ALSA soundcard driver[/LEFT]
    [LEFT]ii  bluez-alsa                                        4.91-0ubuntu1                              Bluetooth ALSA support[/LEFT]
    [LEFT]ii  gnome-alsamixer                                   0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME[/LEFT]
    [LEFT]ii  gstreamer0.10-alsa                                0.10.32-1ubuntu5                           GStreamer plugin for ALSA[/LEFT]
    [LEFT]rc  libclalsadrv2                                     2.0.0-3                                    ALSA driver C++ access library[/LEFT]
    [LEFT]juliogee@juliogee-Satellite-A135:~$ [/LEFT]

---

### Post by lidex on 2011-05-31
Those are the commands, not the command output. You have to run them in -the terminal- by pressing enter.

---

### Post by JulioGee on 2011-05-31
.

---

### Post by JulioGee on 2011-05-31
#1

uliogee@juliogee-Satellite-A135:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
juliogee@juliogee-Satellite-A135:~$ 


#2

ls /etc/modprobe.d/
alsa-base.conf          blacklist-firewire.conf     blacklist-rare-network.conf
alsa-base.save          blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist-ath_pci.conf  blacklist-modem.conf
blacklist.conf          blacklist-oss.conf

#3

juliogee@juliogee-Satellite-A135:~$ dpkg -l | grep "alsa"
ii  alsa-base                                         1.0.24+dfsg-0ubuntu1                       ALSA driver configuration files
ii  alsa-oss                                          1.0.17-4                                   ALSA wrapper for OSS applications
ii  alsa-source                                       1.0.24+dfsg-0ubuntu1                       ALSA driver sources
ii  alsa-utils                                        1.0.24.2-0ubuntu6                          Utilities for configuring and using ALSA
ii  alsamixergui                                      0.9.0rc2-1-9                               graphical soundcard mixer for ALSA soundcard driver
ii  bluez-alsa                                        4.91-0ubuntu1                              Bluetooth ALSA support
rc  gnome-alsamixer                                   0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                0.10.32-1ubuntu5                           GStreamer plugin for ALSA
rc  libclalsadrv2                                     2.0.0-3                                    ALSA driver C++ access library
juliogee@juliogee-Satellite-A135:~$ ;

---

### Post by lidex on 2011-05-31
Yes sir.
I'll need you to remove a file:
```
sudo rm /etc/modprobe.d/alsa-base.save
```
Now re-install alsa:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

Next, after rebooting, run the alsa-info script again.
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by JulioGee on 2011-05-31
Heres the updated alsa info.


[http://www.alsa-project.org/db/?f=bec1d3687f7931218fa57e0b1065016c1b9ef05f](http://www.alsa-project.org/db/?f=bec1d3687f7931218fa57e0b1065016c1b9ef05f)

---

### Post by lidex on 2011-05-31
Now it's looking the way I expect it to except still no soundcard recognized. Is there a chance it was disabled in bios? 
I'd check that just to be sure. Post the output of this command please:
```
sudo lshw -C multimedia
```

Also try booting into an earlier kernel.

---

### Post by JulioGee on 2011-05-31
This is what that codes output is..

PCI (sysfs)

---

### Post by lidex on 2011-05-31
So either you didn't wait long enough for the command to complete or it is not detected at the hardware level. Make sure it is enabled in your bios.

---

### Post by JulioGee on 2011-06-01
How do i enable it in my bios?
i' have looked in my bios and cant find anything that is audio related?

---

### Post by lidex on 2011-06-01
What are these terminal results:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

If you dual-boot windows, load windows and see if you have sound, then restart into ubuntu. 
Another trick is to suspend and resume.

---

### Post by JulioGee on 2011-06-01
Here is the output.

[sudo] password for juliogee: 
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: TOSHIBA
    Version: V1.30
    Release Date: 08/02/2007
    Address: 0xE4D20
    Runtime Size: 111328 bytes
    ROM Size: 1024 kB
    Characteristics:
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        IEEE 1394 boot is supported
        Smart battery is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 1.48
    Firmware Revision: 1.48

juliogee@juliogee-Satellite-A135:~$

---

### Post by marcoftheknight on 2011-06-01
Hey Julio,


Just one suggestion would be to run this code again and wait for the output:

sudo lshw -C multimedia

Thanks




To LIDEX about the past:

[QUOTE=lidex;10884117]Yes sir.
I'll need you to remove a file:
```
sudo rm /etc/modprobe.d/alsa-base.save
```Now re-install alsa:
Just curious are you purging the file because its easier to start fresh then to figure out what has been messed up? don't answer if your to lazy :)

---

### Post by lidex on 2011-06-01
That's a relatively old bios, you may want to check for an update, but what about the output of the second command?

---

### Post by lidex on 2011-06-01
> **marcoftheknight said:**
> [QUOTE=lidex;10884117]Yes sir.
I'll need you to remove a file:
```
sudo rm /etc/modprobe.d/alsa-base.save
```Now re-install alsa:


Hey,

Just curious are you purging the file because its easier to start fresh then to figure out what has been messed up? 

Thanks

Yeah, kinda. The real purpose here is that anything in /etc/modprobe.d/ is read by alsa, so any old configurations in that file will affect how it parses the codec.

---

### Post by JulioGee on 2011-06-01
I've been doing everything you tell me.
Do i purge by putting in that comand?
and this is what i get when i try to remove that file using that code.

juliogee@juliogee-Satellite-A135:~$ sudo rm /etc/modprobe.d/alsa-base.save
rm: cannot remove `/etc/modprobe.d/alsa-base.save': No such file or directory
juliogee@juliogee-Satellite-A135:~$

---

### Post by lidex on 2011-06-01
No, you're doing fine. That file is gone, hence the error. I want you to post the output of:
```
sudo dmidecode -t baseboard
```
And try booting into windows and/or a suspend/resume cycle.

---

### Post by JulioGee on 2011-06-01
Here is the output.

juliogee@juliogee-Satellite-A135:~$ sudo dmidecode -t baseboard
[sudo] password for juliogee: 
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: TOSHIBA
    Product Name: IAYAA
    Version: 1.00
    Serial Number: 0123456789AB

Handle 0x000F, DMI type 10, 8 bytes
On Board Device 1 Information
    Type: Sound
    Status: Disabled
    Description: Realtek ACL861
On Board Device 2 Information
    Type: Ethernet
    Status: Disabled
    Description: Realtek RTL8100L

juliogee@juliogee-Satellite-A135:~$

---

### Post by lidex on 2011-06-02
In your bios look for 'On Board Device' section.

---

### Post by JulioGee on 2011-06-02
I have looked serveral times but i cant seem to find anything in the bios about on board devices.

---

### Post by lidex on 2011-06-02
Try just resetting bios to default:
[http://www.ehow.com/how_5118092_reset-toshiba-bios.html](http://www.ehow.com/how_5118092_reset-toshiba-bios.html)

---

### Post by JulioGee on 2011-06-02
I have already tried to reset to default settings.

---

### Post by lidex on 2011-06-02
Does the sound work in windows or other distro?
Does it work with a previous kernel?
If no then probably hardware issue.

---

### Post by JulioGee on 2011-06-04
The sound does work in vista.

---

