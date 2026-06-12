---
title: "Sound, Internal Microphone, Skype &amp; Rhythmbox Issues with ACER Aspire &amp; Lucid Lynx"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by CaronMargarete on 2010-06-13
Hi, would like to request help with a few issues I'm experiencing. I  love ubuntu but I do not understand a lot of the tech-talk so please  keep information clear and instructions specific.

**System:** ACER Aspire 4535
**Release:** Lucid Lynx

[SIZE=3]**1. Sound**[/SIZE]
**Problem:**

[LIST]
[*]I have to have gnome alsa mixer open to operate the sound.
[*]When I start my laptop the volume is all the way down (not muted)  and my keyboard sound buttons are not recognised at all.
[*]Sound plays even with headphones plugged in.
[*]**Skype** isn't recognising sound at all.
[*]I do not have a sound icon on my panel
[*]There's sound in Rhythmbox but not on Firefox
[/LIST]
[B]Research:
[/B]Tried to follow the Sound Troubleshooting documentation without  success. Will happily run commands but I think [this link]("http://www.alsa-project.org/db/?f=3db943ca8222d5a13034eed97e8ee1dad2107c24") might tell a tech-savvy wizard a lot. 


[SIZE=3]**2. Internal Microphone**[/SIZE]
**Problem:** Not recognised.

**Research:**
Looked for threads that might help but none seemed to lead me in the  right direction. Am trying to use the mic with **skype** without  success, plugging in a headphone makes no difference.


[SIZE=3]**3. Rhythmbox**[/SIZE]
**Problem: **When I first open the program seems to freeze. I can  scan artists/ songs but if I select one to play, or try to change the  volume nothing happens for about 2-3mins until it unfreezes, after which  it will run fine.

**Research:**
Cannot find specific help with the program freezing, only the  visualisations which I don't use.

---

### Post by lidex on 2010-06-14
Is this an upgrade or new install?
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

### Post by CaronMargarete on 2010-06-14
Thanks for looking into this for me Lidex.

**Make/ Model: **ACER Aspire 4535 laptop. 
**Upgrade: **Lucid Lynx- upgrade from Karmic Koala. I did have some problems with the upgrade, mostly because my system froze and I can't be sure it finished accurately.

**Requested information:**

```

caz@Jamie:~$ uname -a
Linux Jamie 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux 
```

```
caz@Jamie:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
```

```
caz@Jamie:~$ dpkg -l | grep "alsa"
ii  alsa-base                                       1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                        1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                                      1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                      4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                 0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                              0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                                    0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                            1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
```

```
 caz@Jamie:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI  
```

Thanks again, let me know what else you may need.

---

### Post by lidex on 2010-06-14
An upgrade can leave some cruft. Try this first. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

No help? Bring alsa up to date using the alsa-upgrade link in my sig.

---

### Post by CaronMargarete on 2010-06-15
> **lidex said:**
> An upgrade can leave some cruft. Try this first. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```Logout/in.

No help? Bring alsa up to date using the alsa-upgrade link in my sig.

Tried...
```
caz@Jamie:~$ rm -r ~/.pulse ~/.asound*
rm: cannot remove `/home/caz/.asound*': No such file or directory
```

Didn't do the second code because I'm assuming it is dependant on the first... Ideas?

Thanks for your help & patience...

---

### Post by CaronMargarete on 2010-06-15
> **lidex said:**
> An upgrade can leave some cruft. Try this first.  Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```Logout/in.

No help? Bring alsa up to date using the alsa-upgrade link in my  sig.

Tried...
```
caz@Jamie:~$ rm -r ~/.pulse ~/.asound*
rm: cannot remove `/home/caz/.asound*': No such file or directory
```Then tried the 2nd code:
```

caz@Jamie:~$ sudo rm /etc/asound.conf
rm: cannot remove `/etc/asound.conf': No such file or directory

```I've actually seen this ALSA Upgrade info before and have tried to follow the instructions but because of my lack of knowledge  and the seemingly sparse details I wasn't sure of a few things:

> Short Alsa-Upgrade script install instructions:
 1. download the script and save it somewhere
 2. cd <your-download-dir>
 3. tar xvf AlsaUpgrade-1.0.23-2.tar
 4. sudo ./AlsaUpgrade-1.0.23-2.sh -d
 5. sudo ./AlsaUpgrade-1.0.23-2.sh -c
 6. sudo ./AlsaUpgrade-1.0.23-2.sh -i
 7. sudo shutdown -r 0
 Logging: I recommend to log all the upgrade steps, e.g. 
 script -a -c "./AlsaUpgrade-1.0.23-2.sh -d"  /tmp/Alsa_1.0.23-2_upgrade_download.log 
 You'll find a log file /tmp/Alsa_1.0.23-2_upgrade_download.log as soon  as the script is finished.
 You need to run this procedure for every single step. Choose whatever  logfile names.Which script alsa-info.tar or AlsaUpgrade-1.0.23-2.tar? I've downloaded both and saved them in an easy place.

What does *2. cd <your-download-dir>* & *3. tar xvf AlsaUpgrade-1.0.23-2.tar* actually require me to do?

I assume that #4 - #7 are terminal commands, correct?

The logging stuff has gone right over my head. Sorry.

Thank you for your continued help and patience! I really appreciate it!

---

### Post by CaronMargarete on 2010-06-18
ALSA seems to have maintained a 'memory' for the sound now but the highest volume isn't anywhere near as loud as this laptop is capable of. I have windows partitioned and it is louder through windows than ubuntu.
Ideas?

Also, I am wondering about the mic and rhythmbox issues I'm having. Does anyone know what I can try???

---

### Post by lidex on 2010-06-18
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by CaronMargarete on 2010-06-19
> **lidex said:**
> Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

```
caz@Jamie:~$ sudo apt-get install gnome-alsamixer
[sudo] password for caz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-alsamixer is already the newest version.
The following packages were automatically installed and are no longer required:
  libfreebob0 libopal3.6.4 libxml++2.6-2 libgda-4.0-common libqt4-phonon
  libxklavier15 libicu40 latex-xft-fonts libgda-4.0-4 libknotificationitem1
  libcompress-bzip2-perl libgupnp-1.0-2 xulrunner-1.9.1-gnome-support libdns53
  libindicate-gtk1 gnome-blackjack libiso9660-5 libass3 qt3-assistant
  python-gda libexiv2-5 python-gdl libcln5 librasqal1 python2.5 libisccc50
  liblzma0 libpt2.6.4-plugins libindicate3 libx264-67 python-gtksourceview
  linux-backports-modules-2.6.31-20-generic python-gksu2 libgdl-1-common
  kde-icons-oxygen python-nautilusburn liblwres50 libcelt0 qcad-doc
  raptor-utils xulrunner-1.9.1 qcad-data python-gtkmozembed libntfs-3g54
  libbind9-50 libffado1 python-gtkspell libgdata5 qt3-doc libpt2.6.4
  libisccfg50 rhino redland-utils firefox-3.5-gnome-support libisc50
  libjline-java libgssdp-1.0-1 libgdl-1-3 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

What was this meant to do?

---

### Post by lidex on 2010-06-19
Gnome-alsamixer is not in the default ubuntu install. That command was to install it if needed. Obviously you have it already. The terminal is also telling you that some packages that are no longer required can be removed using this command:
```
sudo apt-get autoremove
```

---

### Post by nab on 2010-06-20
I had a simular problem on my Acer Aspire 1810tz:

**Skype**:
It was changing my audio settings, especially the mic settings.

So I had to disable them:
-> options -> sound devices -> uncheck box for allowing Skype to automatically adjust mixer levels.

**Mic**
Ubuntu thought it was an stereo mic. So there are two solutions:

First Quick and Dirty:
Click on the "speaker" icon in the upper right hand corner of the screen and start the Audio setting. There make sure no device is muted.
In output set the balance to mono (left or right) and put level to about 90%.
In input set the level also to 90% and the bar to show the mic activity should now move.

Second solution:
I installed pavucontrol with Synaptic and started it in a terminal.
In output devices I set the front left to 90% and the front right to 10%. (This way the mic doesn't cancel the signal out) You have to play with the buttons to be allowed to change both value independently.

**Rhythmbox**
I only have a short time lag, but it never really bothered me.



If that is not helping: you will have to follow the Comprehensive Sound Problem Solutions Guide: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by lkjoel on 2010-06-21
Click on [Fix your sound!]("https://help.ubuntu.com/community/OpenSound") on my sig. That should fix it.

---

### Post by Vege 4wd on 2010-07-02
Hi Lkjoel.
       Checked out the link. Will that work with lucid?

---

### Post by restless on 2010-07-14
upgrade worked a treat for me..

THANK YOU!!

---

### Post by CaronMargarete on 2011-02-07
Not sure if it's better to kick this off with a new thread or not but hate to double up threads. I still have this problem with my mic, only now I've completely reformatted and used a live cd to load a fresh version of Lucid Lynx.

To refresh what I did initially here are the original commands that @Lidex asked for.
[FONT=Arial][SIZE=1]
[/SIZE][/FONT]>                                                    [FONT=Arial][SIZE=1]Is this an upgrade or new install?
Can you post the output of these terminal commands for me please:
[/SIZE][/FONT]      [FONT=Arial][SIZE=1]Code:[/SIZE][/FONT]
 ```
    uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 

```[FONT=Arial][SIZE=1]
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**[/SIZE][/FONT] [FONT=Arial][SIZE=1]
Please post text output using code tags (the # in toolbar)[/SIZE][/FONT]
                                                                              [FONT=Arial][SIZE=1]                 __________________
[ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")[/SIZE][/FONT][FONT=Arial][SIZE=1]|[Boot Info Script]("http://bootinfoscript.sourceforge.net/")|[Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")|[Pulse Audio]("http://ubuntuforums.org/showthread.php?t=789578")|[Ubuntu-Bug Audio]("https://wiki.ubuntu.com/DebuggingSoundProblems")[/SIZE][/FONT]             
                                                            
```
caronmargarete@caronmargarete:~$ uname -a
Linux caronmargarete 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux
caronmargarete@caronmargarete:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
caronmargarete@caronmargarete:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
ii  libsox-fmt-alsa                      14.3.0-1.1build1                                SoX alsa format I/O library
caronmargarete@caronmargarete:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC888

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
caronmargarete@caronmargarete:~$ 
```So if we can start here can someone please tell me where I need to go next. I'm not comfortable preempting the rest of lidex's information without knowing I'm on the right track. 

Thanks in advance for keeping your language in layman's terms for me to understand too...

---

### Post by lidex on 2011-02-09
Are you able to get mic input using 'Sound Recorder'?
> ...run alsamixer then tab over to the [Capture] View and change the 'Input Source' (not 'Input Source 1') to the 'Front Mic'. This is not enabled by default. 

Next. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Still no joy try editing alsa-base.conf:
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by CaronMargarete on 2011-02-11
> **lidex said:**
> Are you able to get mic input using 'Sound Recorder'?

Quote:
 	 	 		 			 				...run alsamixer then tab over to the [Capture] View and change the  'Input Source' (not 'Input Source 1') to the 'Front Mic'. This is not  enabled by default. 			 		


No I'm not getting mic input through the sound recorder.
I have needed to install gnome-alsamixer before attempting what you've recommended however what you describe does not look the same as what I have. 

Can you explain for me what I need to do before I continue with the rest of what you've said?

---

### Post by CaronMargarete on 2011-02-11
> **lidex said:**
> 
Next. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Still no joy try editing alsa-base.conf:
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

I went ahead and did as you've recommended because it only looked like updates and no major changes:

```
 
caronmargarete@caronmargarete:~$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
[sudo] password for caronmargarete: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5
gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com
gpg: key 72B194E5: public key "Launchpad Ubuntu Audio Dev team PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
caronmargarete@caronmargarete:~$ sudo apt-get update
Get:1 http://au.archive.ubuntu.com lucid Release.gpg [189B]                    
Get:2 http://au.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_AU [1,813B]
Get:3 http://au.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_AU [2,407B]
Ign http://au.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_AU
Get:4 http://au.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_AU [91.6kB]
Get:5 http://archive.canonical.com lucid Release.gpg [198B]                    
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_AU       
Get:6 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Ign http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ lucid/main Translation-en_AU
Get:7 http://security.ubuntu.com lucid-security Release.gpg [198B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_AU   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_AU
Get:8 http://au.archive.ubuntu.com lucid-updates Release.gpg [198B]            
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_AU  
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com lucid Release                                 
Get:9 http://au.archive.ubuntu.com lucid-updates Release [44.7kB]              
Hit http://au.archive.ubuntu.com lucid/main Packages                           
Hit http://au.archive.ubuntu.com lucid/restricted Packages                     
Get:10 http://archive.canonical.com lucid Release [8,215B]                     
Hit http://au.archive.ubuntu.com lucid/main Sources                            
Hit http://au.archive.ubuntu.com lucid/restricted Sources                      
Hit http://au.archive.ubuntu.com lucid/universe Packages                       
Hit http://au.archive.ubuntu.com lucid/universe Sources                        
Hit http://au.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://au.archive.ubuntu.com lucid/multiverse Sources                      
Get:11 http://au.archive.ubuntu.com lucid-updates/main Packages [447kB]        
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_AU
Get:12 http://security.ubuntu.com lucid-security Release [44.7kB]              
Get:13 http://ppa.launchpad.net lucid Release [14.0kB]                         
Get:14 http://au.archive.ubuntu.com lucid-updates/restricted Packages [3,267B] 
Get:15 http://au.archive.ubuntu.com lucid-updates/main Sources [178kB]         
Get:16 http://archive.canonical.com lucid/partner Packages [11.8kB]            
Get:17 http://au.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]  
Get:18 http://au.archive.ubuntu.com lucid-updates/universe Packages [183kB]    
Get:19 http://ppa.launchpad.net lucid/main Packages [5,527B]                   
Get:20 http://security.ubuntu.com lucid-security/main Packages [142kB]         
Get:21 http://au.archive.ubuntu.com lucid-updates/universe Sources [65.5kB]
Get:22 http://au.archive.ubuntu.com lucid-updates/multiverse Packages [8,346B] 
Get:23 http://au.archive.ubuntu.com lucid-updates/multiverse Sources [4,369B]  
Get:24 http://security.ubuntu.com lucid-security/restricted Packages [14B]     
Get:25 http://security.ubuntu.com lucid-security/main Sources [44.2kB]
Get:26 http://security.ubuntu.com lucid-security/restricted Sources [14B]      
Get:27 http://security.ubuntu.com lucid-security/universe Packages [62.2kB]    
Get:28 http://security.ubuntu.com lucid-security/universe Sources [18.3kB]     
Get:29 http://security.ubuntu.com lucid-security/multiverse Packages [1,856B]  
Get:30 http://security.ubuntu.com lucid-security/multiverse Sources [651B]     
Fetched 1,387kB in 7s (193kB/s)                                                
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
caronmargarete@caronmargarete:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.40.0 libboost-thread1.40.0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-alsa-driver-modules-2.6.32-28-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,968kB of archives.
After this operation, 9,294kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ lucid/main linux-alsa-driver-modules-2.6.32-28-generic 2.6.32-28.201102101600 [1,968kB]
Fetched 1,968kB in 9s (209kB/s)                                                
Selecting previously deselected package linux-alsa-driver-modules-2.6.32-28-generic.
(Reading database ... 154128 files and directories currently installed.)
Unpacking linux-alsa-driver-modules-2.6.32-28-generic (from .../linux-alsa-driver-modules-2.6.32-28-generic_2.6.32-28.201102101600_amd64.deb) ...
Setting up linux-alsa-driver-modules-2.6.32-28-generic (2.6.32-28.201102101600) ...
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic

```

Now the alsamixer looks different but still not really as you describe. I played with it a bit and did more tests in skype to no avail. 

When I do a test call through skype it does everything and I hear everything fine but when it goes to replay the recording it doesn't. It just beeps immediately as though nothing at all was recording even though I spoke for the 8 or so seconds it needed. 

I'll now wait for your reply before doing anything more. Thanks for your continued support lidex.

---

### Post by lidex on 2011-02-15
Enter ```
alsamixer
``` in a terminal. Press the <Tab> key to select 'capture' view. Use the L/R arrow keys to navigate to 'input source' and the Up/Dn keys to toggle that value to 'front mic'

---

### Post by CaronMargarete on 2011-02-19
> **lidex said:**
> Enter ```
alsamixer
``` in a terminal. Press the <Tab> key to select 'capture' view. Use the L/R arrow keys to navigate to 'input source' and the Up/Dn keys to toggle that value to 'front mic'

Hi lidex, I have done as you recommended however I do not have front mic only line/ mic/ internal mic. I went back to an earlier post where you said:

> 
**Reboot**
Check your levels in alsamixer.
 	Code:
 	 alsamixer 
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct  soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.


I've attached some screen shots of what I have. Everything looks maxed out except master, which I've found cannot be maxed because it gives a lot of air static. 

I looked at sound preferences and while making test calls through skype found that the input was muted. I first tested the mic/ internal mic settings and both allowed me to make a recording but upon playback gave silence. When I unmuted the input I could also make a recording but the playback was a lot of static. So... I'm left a little unsure what I should do. Feeling as though we're close though.

Are we at a point where I should try your last piece of advice? I don't really understand what this does but willing to give it a go.

> 
Still no joy try editing alsa-base.conf:
 	Code:
 	echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf 
 **Reboot**


Ideas?

---

### Post by lidex on 2011-02-20
What about the input tab of 'sound preferences'?

---

### Post by CaronMargarete on 2011-02-22
> **lidex said:**
> What about the input tab of 'sound preferences'?

Lidex, I'm not sure I know what you're referring to. Another screen shot. In sound pref if I move the volume of the mic up I get air. If I modify the capture and mic boost in gnome I also get air. So I'm not sure what the problem is. Each time I recorded via skype test call this time it didn't record at all. It's as though Ubuntu isn't recognising the mic of my laptop. 

Ideas?

---

### Post by CaronMargarete on 2011-03-11
Has anyone else heard of the ACER Aspire 4535 not recognising the mic? Lidex has given me loads to go on but I keep getting air or nothing at all... ideas?

---

### Post by lidex on 2011-03-17
> **CaronMargarete said:**
> Has anyone else heard of the ACER Aspire 4535 not recognising the mic? Lidex has given me loads to go on but I keep getting air or nothing at all... ideas?

> The microphone works good, albeit with the mic boost. There is some feedback, but I think that it is the problem with my mixer settings.
To get it to work, I had to run alsamixer then tab over to the [Capture] View and change the 'Input Source' (not 'Input Source 1') to the 'Front Mic'. This is not enabled by default. 
Reference:
[http://www.linlap.com/wiki/acer+aspire+4530](http://www.linlap.com/wiki/acer+aspire+4530)

---

### Post by CaronMargarete on 2011-03-17
Thanks Lidex, I appreciate you posting this however, it is not new information that we haven't already covered. 

I changed it to Front Mic, and once recorded got static sound instead of my own voice. So we're still a step short and I don't know how to fix it. In the post it mentions 'mixer settings' but I wouldn't know how to fix or even adjust these.

Ideas?

---

