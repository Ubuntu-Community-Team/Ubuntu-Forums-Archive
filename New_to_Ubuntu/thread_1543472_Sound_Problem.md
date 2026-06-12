---
title: "Sound Problem"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2010-08-01
when i last updated my packages using synaptic, since then sound is not coming...please help..

---

### Post by viditgoyal3009 on 2010-08-01
y is it dat never my problem got solved in this forum???

---

### Post by thegod_slayer on 2010-08-01
i had this problem once.
the problem is that the updates you are doing are meant to replace the old alsa sound drivers and pulse audio drivers with the new once.
but what it does is it just deletes the old ones without replacing them with the new ones.
so i stopped updating my laptop.
believe me no such problem occurs if your ubuntu is not updated.
and there may be one more reason i found on net.
don't install the proprietary driver under the hardware drivers tab.
so just make a fresh install don't update and enjoy.

---

### Post by lidex on 2010-08-01
Can you post the output of these terminal commands for me please:
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

### Post by tekybrit on 2010-08-02
I have no sound with LUbuntu & never have since installed less than a month ago, but sound is fine with Windows 7. Can anyone figure out what my problem is from the info below.

john@touchsmart:~$ uname -a
Linux touchsmart 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux

john@touchsmart:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

john@touchsmart:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA

john@touchsmart:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC888

---

### Post by orethrius on 2010-08-02
Alt+F2, gnome-alsamixer.  If something's muted (particularly Master, Headphone, and PCM) then unmute it.  If that doesn't work - or no audio devices show up - then a driver issue is at play.

Yes, I *know* this is a simple fix, but it took me three *months* to find the *original* alsamixer the first time.  Oh how I wish somebody had pointed that one out long ago. ;)

---

### Post by tekybrit on 2010-08-02
I had not installed gnome-alsamixer, but thanks to your tip, have now.
Still got the problem of no sound from internal speakers.

---

### Post by lidex on 2010-08-02
> **tekybrit said:**
> I had not installed gnome-alsamixer, but thanks to your tip, have now.
Still got the problem of no sound from internal speakers.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by tekybrit on 2010-08-02
Your ALSA information is located at [http://www.alsa-project.org/db/?f=f6b43644ae572a535632721cbbc27ac0b3630996](http://www.alsa-project.org/db/?f=f6b43644ae572a535632721cbbc27ac0b3630996)

---

### Post by tekybrit on 2010-08-02
Should ESound Daemon be running?

---

### Post by lidex on 2010-08-02
> **tekybrit said:**
> Should ESound Daemon be running?
No, only pulse. You only need one soundserver.

---

### Post by lidex on 2010-08-02
*tekybrit*
I would suggest upgrading alsa at this point. Use the upgrade link in my sig. If you have alsa-backports installed remove it first.

What is the model number of this pc?

---

### Post by tekybrit on 2010-08-07
My PC is

HP TOUCHSMART 600-1105XT 23.0" 1080P 2.2GHZ DESKTOP PC

Which means I am probably in the wrong thread (am still trying to understand everything)

Unfortunately I have not learnt enough yet to understand how to use the "link in your sig"

Also I do not know how to check if I have got "alsa-backports installed"

I really appreciate the guidance you have given me.

---

### Post by tekybrit on 2010-08-07
This is as far as I got

1. download the script and save it somewhere

      I saved it in my download folder

2. cd <your-download-dir>

  john@touchsmart:~$ cd Downloads
john@touchsmart:~/Downloads$ ls
alsa-driver-1.0.23.tar-1

3. tar xvf AlsaUpgrade-1.0.23-2.tar

john@touchsmart:~/Downloads$ tar xvf AlsaUpgrade-1.0.23-2.tar
tar: AlsaUpgrade-1.0.23-2.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
john@touchsmart:~/Downloads$ 

What is xvf?
Did I download the wrong script?

---

### Post by laskarhack on 2010-08-07
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)
i have SAME PROBLEM....

I haven't a sound in my MP3 or other..
I use VAIO VPCEA22EG 

this is the output..


 $ uname -a
Linux azis-exploiter 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
laskarhack@azis-exploiter:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
laskarhack@azis-exploiter:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-21-generic 2.6.32-21.11                                    Ubuntu supplied Linux modules for version 2.
laskarhack@azis-exploiter:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

---

### Post by lidex on 2010-08-07
> **tekybrit said:**
> This is as far as I got

1. download the script and save it somewhere

      I saved it in my download folder

2. cd <your-download-dir>

  john@touchsmart:~$ cd Downloads
john@touchsmart:~/Downloads$ ls
alsa-driver-1.0.23.tar-1

3. tar xvf AlsaUpgrade-1.0.23-2.tar

john@touchsmart:~/Downloads$ tar xvf AlsaUpgrade-1.0.23-2.tar
tar: AlsaUpgrade-1.0.23-2.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
john@touchsmart:~/Downloads$ 

What is xvf?
Did I download the wrong script?

Here is the direct download link:
[http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001](http://ubuntuforums.org/attachment.php?attachmentid=156468&d=1273598001)
Follow the instructions as posted. You don't have backports installed so don't worry about that.
You may need this also - it won't do anything if already installed:
```
sudo aptitude install build-essential
```

---

### Post by lidex on 2010-08-07
> **laskarhack said:**
> i have SAME PROBLEM....

I haven't a sound in my MP3 or other..
I use VAIO VPCEA22EG 

this is the output..


 $ uname -a
Linux azis-exploiter 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
laskarhack@azis-exploiter:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
laskarhack@azis-exploiter:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-21-generic 2.6.32-21.11                                    Ubuntu supplied Linux modules for version 2.
laskarhack@azis-exploiter:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

Update your system first;
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Now this:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. On the output tab choose the correct device.

---

### Post by tekybrit on 2010-08-07
Sorry, still no sound from speakers, have not tried headphones or microphone.
Speaker test goes through the motions, but no sound, umuted & levels up.

john@touchsmart:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
john@touchsmart:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug  7 2010 for kernel 2.6.32-24-generic (SMP).

john@touchsmart:~$ speaker-test -Dplughw:0,0 -c2

speaker-test 1.0.23

Playback device is plughw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.630471
 0 - Front Left
 1 - Front Right
Time per period = 5.970293
 0 - Front Left

---

### Post by lidex on 2010-08-07
Replace auto with touchsmart in alsa-base.conf

---

### Post by tekybrit on 2010-08-07
I think I have messed something up.
Seeing your reply to laskarhack, I thought 
options snd-hda-intel model=autowould help me, it seems I was wrong because now I have Device resource busy come up!
Also I was playing with the hardware sound preferences.
I do not know for the profile what I should select
    Analog Stereo Input
    Digital Stereo Duplex (IEC958)
    Digital Stereo (IEC958) Output + Analog Stereo Input
    Analog Stereo Output
    Analog Stereo Duplex


john@touchsmart:~$ speaker-test -Dplughw:0,0 -c2

speaker-test 1.0.23

Playback device is plughw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right

---

### Post by lidex on 2010-08-07
> **tekybrit said:**
> I think I have messed something up.
Seeing your reply to laskarhack, I thought 
options snd-hda-intel model=autowould help me, it seems I was wrong because now I have Device resource busy come up!
Also I was playing with the hardware sound preferences.
I do not know for the profile what I should select
    Analog Stereo Input
    Digital Stereo Duplex (IEC958)
    Digital Stereo (IEC958) Output + Analog Stereo Input
    Analog Stereo Output
    Analog Stereo Duplex


john@touchsmart:~$ speaker-test -Dplughw:0,0 -c2

speaker-test 1.0.23

Playback device is plughw:0,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
I'm getting a little confused myself. You should be using the touchsmart model.
For now use the analog stereo duplex profile.

---

### Post by tekybrit on 2010-08-07
I Replaced auto with touchsmart in alsa-base.con

now speaker test runs without error, but no sound still.

---

### Post by tekybrit on 2010-08-07
I have sound from the headphone output and the microphone jack works fine, but still no internal speakers.
Rhythmbox Music Player exits a fraction of a second after being selected from the Applications menu.
So I used synaptic to get Alsaplayer, which works fine, albeit just through the headphones.

Having read other threads, I know several other HP Touchsmart users have had problems getting the internal speakers working.

---

### Post by tekybrit on 2010-08-07
Forgot to mention that  in GNOME ALSA MIXER the following volume (and where appropriate balance) controls all affect the headphone output.
Master, Headphone & PCM

---

### Post by tekybrit on 2010-08-07
I selected the Sound Preferences Dialog from System>Preferences>Sound.
Then turned off the profile, which just makes the dialogs volume & balance controls inoperative, but they work again when I select "Internal Audio" (Internal Audio is the only visible device).

The GNOME ALSA Mixer controls work whatever I do with the Sound Preferences Dialog.

---

### Post by tekybrit on 2010-08-07
I selected the Output tab of Sound Preferences Dialog.
Setting the connector to Speakers, Headphones or Output has no effect, but the balance control directly above it does.

The plot thickens.

---

### Post by lidex on 2010-08-08
I'd like to see these with your current configuration:
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by tekybrit on 2010-08-08
```

```john@touchsmart:~$ dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'[    9.796713] Console: switching to colour frame buffer device 240x67
[   11.038839] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   11.038891] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   11.039506] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   11.039511] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[   11.039514] hda_intel: Disable MSI for Nvidia chipset
[   11.039539] HDA Intel 0000:00:08.0: setting latency timer to 64
[   11.648039] hda_codec: ALC888: SKU not ready 0x411111f0
[   11.656035] hda_codec: ALC888: BIOS auto-probing.
[   11.856113] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input6
[   12.788342] eth0: no link during initialization.
john@touchsmart:~$ sudo dmidecode -t bios
[sudo] password for john: 
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: 5.12   
    Release Date: 11/05/2009
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 8.15

Handle 0x000C, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

john@touchsmart:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: PEGATRON CORPORATION
    Product Name: E60
    Version: 1.02
    Serial Number: 103050610001988
    Asset Tag:                                 
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis:                                 
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x000A, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description:

---

### Post by lidex on 2010-08-09
*tekybrit:*
Remove the line you added to alsa-base.conf and replace it with this:
```
options snd-hda-intel probe_mask=1
```
**Reboot**
Your codec is actually ALC888S

EDIT: May have stumbled onto something here. If the above doesn't work, substitute this line:
```
options snd-hda-intel model=mobile
```
Reference:
[http://www.touchsmartdevzone.com/article/2327/How-to-make-Ubuntu-Linux-work-on-a-TouchSmart-IQ506/](http://www.touchsmartdevzone.com/article/2327/How-to-make-Ubuntu-Linux-work-on-a-TouchSmart-IQ506/)

---

### Post by tekybrit on 2010-08-09
Sorry, still no luck.

But I notice now that after robooting with either of the suggested edits to alsa-base.conf GNOME ALSA Mixer volume for speakers is set to lowest level, I do not know if this was the case before.
Raising the volume does not give sound to the speakers.

Something else I have observed is that under windows 7 unplugging the headphones turns on the speakers and of course plugging in the headphones turns off the speakers, in either case a message appears on the screen to say that the headphones have been plugged or unplugged.
The HP Touchsmart 600 has volume control buttons on the keyboard and on the right hand side of the screen, of course these do not work under Ubuntu, not that I am even worried about that.

---

### Post by lidex on 2010-08-09
Check the HP website for a bios update.
Download the LiveCD of maverick testing and see if sound works with it:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by faibistes on 2011-03-10
bump
Same problem here, Ubuntu Maverick, HP Touchsmart 600 1210de. No sound from internal speakers.

---

### Post by faibistes on 2013-02-19
bumpy

](*,)

Ubuntu 12.10

---

### Post by oldos2er on 2013-02-19
Please start a new thread.

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

