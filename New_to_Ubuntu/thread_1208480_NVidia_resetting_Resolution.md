---
title: "NVidia resetting Resolution"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by markios on 2009-07-09
Hi, 
 
I am a complete n00b on Unbuntu but pretty savvy none the less.
 
I am running a HP Pavillion dv6000 with the NVidia 7300 graphics card. 
 
My installation has gone ok and I have successfully installed all of the drivers for my wireless card etc and my Graphics card. 
 
Intially I was using the 180 version but noticed that when I rebooted the machine after setting the resolution and saving the data (and double checking) the xorg.conf file, the resolution resets to the 800X600.
 
Ive tried everything and have even downgraded the driver to the 173 with no avail. 
 
Basically every time I log on now im forced to go into the nvidia -settings and change the res to highest res 1280x800.
 
After rebooting ive checked the xorg.conf file and the settings are correct. 
 
Ive looked everywhere for an answer and have so far come up short. 
 
can anyone suggest anything else?

---

### Post by beastrace91 on 2009-07-09
Wanna post the contents of your xorg.conf file right after you reboot and it is in the 800x600 res (before you change it) and then also the contents after you force it to the correct res?

~Jeff

---

### Post by ptn107 on 2009-07-09
xorg.conf no longer stores your resolution information if your using the proprietary 180 drivers for Ubuntu.  You need to use the application nvidia-xconfig to set your resolution and other options.

---

### Post by CLomax on 2009-07-09
I'm sure that if you run nvidia-settings as root and set the resolution it sticks.

***sudo nvidia-settings***

---

### Post by zerolgk on 2009-07-09
I'm having the same problem. Even after doing gksudo nvidia-settings and saving the configs, it still load 800x600 after reboot or just logging off then on again.

---

### Post by CLomax on 2009-07-09
> **zerolgk said:**
> I'm having the same problem. Even after doing gksudo nvidia-settings and saving the configs, it still load 800x600 after reboot or just logging off then on again.

Have you tried tweaking your xorg.conf?

---

### Post by zerolgk on 2009-07-09
> **CLomax said:**
> Have you tried tweaking your xorg.conf?
Hey, thanks for quick response! Not yet. I've found some info saying that should work, but I haven't found any good instructions on how to do that yet. I should also mention that I've been using linux for less than twenty four hours, so my grasp isn't exactly firm yet.

---

### Post by running_rabbit07 on 2009-07-09
Unlike with Debian, when I loaded Ubuntu it immediately offered to install the 180 version. nvidia-settings will not let me in to change anything but when it installed it set the resolution very well after I restarted.

---

### Post by RedRat on 2009-07-09
markios
When you ask for help, please include the version of Ubuntu you are using. Ubuntu 8.04 does store info in the xorg.conf file, but the most recent Ubuntu 9.04 uses a different file. 

If you are using 8.04, I suggest that if you think you are having problems with the graphic driver that you install EnvyNG and run that, run it from the terminal as root,
sudo EnvyNG, it will give you the option of which Nvidia driver to install. Then run sudo nvidia-settings.

I do not yet run 9.04 so I can't pass any advice on that distro.

---

### Post by NOTAGEEK on 2009-07-09
I dont know if this applies to your 73 series card but i found this while snooping around...

you also dont mention your version and i got this from the 8.10 release notes...

bear in mind that i have zero saavy and am working with 9.04 that i installed just a handful of hours ago too...

i found this because i have the 9600gt card but i have no idea what it means so i bookmarked it...

HERE YOU GO HOPE IT MIGHT HELP

                                        [Home]("http://www.ubuntu.com/")
                                                  [B]8.10 Release Notes
[/B]

                                                                      
            **Contents**             
                          
[LIST=1]
[*][System Requirements]("http://www.ubuntu.com/getubuntu/releasenotes/810#System%20Requirements")
[*][Installation]("http://www.ubuntu.com/getubuntu/releasenotes/810#Installation")
[LIST=1]
[*][Hard disks potentially not shown when installing in Live CD mode]("http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode")
[*]["Free software only" option installs restricted software]("http://www.ubuntu.com/getubuntu/releasenotes/810#%22Free%20software%20only%22%20option%20installs%20restricted%20software")
[*][Slow start to "Select and install software" step in text-mode installer]("http://www.ubuntu.com/getubuntu/releasenotes/810#Slow%20start%20to%20%22Select%20and%20install%20software%22%20step%20in%20text-mode%20installer")
[*][oem-config fails to handle some languages properly]("http://www.ubuntu.com/getubuntu/releasenotes/810#oem-config%20fails%20to%20handle%20some%20languages%20properly")
[*][MID image requires a network for successful installation]("http://www.ubuntu.com/getubuntu/releasenotes/810#MID%20image%20requires%20a%20network%20for%20successful%20installation")
[*][Recommended packages installed by default]("http://www.ubuntu.com/getubuntu/releasenotes/810#Recommended%20packages%20installed%20by%20default")
[*][Password limitation with ecryptfs]("http://www.ubuntu.com/getubuntu/releasenotes/810#Password%20limitation%20with%20ecryptfs")
[*][PlayStation 3 installation issues]("http://www.ubuntu.com/getubuntu/releasenotes/810#PlayStation%203%20installation%20issues")
[/LIST]
 
[*][Upgrading]("http://www.ubuntu.com/getubuntu/releasenotes/810#Upgrading")
[LIST=1]
[*][nVidia "legacy" video support]("http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support")
[*][ATI "fglrx" video support]("http://www.ubuntu.com/getubuntu/releasenotes/810#ATI%20%22fglrx%22%20video%20support")
[*][X.Org Input Devices]("http://www.ubuntu.com/getubuntu/releasenotes/810#X.Org%20Input%20Devices")
[*][X.Org evdev xmodmap incompatibility]("http://www.ubuntu.com/getubuntu/releasenotes/810#X.Org%20evdev%20xmodmap%20incompatibility")
[*][UbuntuStudio real-time kernel support]("http://www.ubuntu.com/getubuntu/releasenotes/810#UbuntuStudio%20real-time%20kernel%20support")
[*][Toshiba laptop hotkey support]("http://www.ubuntu.com/getubuntu/releasenotes/810#Toshiba%20laptop%20hotkey%20support")
[*][Boot failures on systems with Intel D945 motherboards]("http://www.ubuntu.com/getubuntu/releasenotes/810#Boot%20failures%20on%20systems%20with%20Intel%20D945%20motherboards")
[*][Kubuntu KDE4 remix]("http://www.ubuntu.com/getubuntu/releasenotes/810#Kubuntu%20KDE4%20remix")
[LIST=1]
[*][Cannot login after upgrade from Kubuntu 8.04 KDE 4 Remix]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20login%20after%20upgrade%20from%20Kubuntu%208.04%20KDE%204%20Remix")
[/LIST]
 
[*][Support for ssl/blowfish-v0.2, version 2:0:1 not in encfs]("http://www.ubuntu.com/getubuntu/releasenotes/810#Support%20for%20ssl/blowfish-v0.2,%20version%202:0:1%20not%20in%20encfs")
[*][PlayStation 3 upgrade issues]("http://www.ubuntu.com/getubuntu/releasenotes/810#PlayStation%203%20upgrade%20issues")
[/LIST]
 
[*][Other known issues]("http://www.ubuntu.com/getubuntu/releasenotes/810#Other%20known%20issues")
[LIST=1]
[*][System lock-ups with Intel 4965 wireless]("http://www.ubuntu.com/getubuntu/releasenotes/810#System%20lock-ups%20with%20Intel%204965%20wireless")
[*][Cannot reactivate Intel 3945/4965 wireless if booting with killswitch enabled]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20reactivate%20Intel%203945/4965%20wireless%20if%20booting%20with%20killswitch%20enabled")
[*][Atheros ath5k wireless driver not enabled by default]("http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default")
[*][Limited support for Wacom tablet hotplugging]("http://www.ubuntu.com/getubuntu/releasenotes/810#Limited%20support%20for%20Wacom%20tablet%20hotplugging")
[*][iSCSI boot order]("http://www.ubuntu.com/getubuntu/releasenotes/810#iSCSI%20boot%20order")
[*][Cannot mount more than one iSCSI target]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20mount%20more%20than%20one%20iSCSI%20target")
[*][Wireless doesn't work after suspend with ath_pci driver]("http://www.ubuntu.com/getubuntu/releasenotes/810#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver")
[*][Systems installed from pre-release daily images may be missing some files]("http://www.ubuntu.com/getubuntu/releasenotes/810#Systems%20installed%20from%20pre-release%20daily%20images%20may%20be%20missing%20some%20files")
[*][Kubuntu Bluetooth support]("http://www.ubuntu.com/getubuntu/releasenotes/810#Kubuntu%20Bluetooth%20support")
[*][KNetworkManager cannot manage connections with static IPs]("http://www.ubuntu.com/getubuntu/releasenotes/810#KNetworkManager%20cannot%20manage%20connections%20with%20static%20IPs")
[*][Using usb-creator with 8.04.1 (Hardy) images]("http://www.ubuntu.com/getubuntu/releasenotes/810#Using%20usb-creator%20with%208.04.1%20%28Hardy%29%20images")
[*][Only US wireless channels enabled by default on Intel 3945]("http://www.ubuntu.com/getubuntu/releasenotes/810#Only%20US%20wireless%20channels%20enabled%20by%20default%20on%20Intel%203945")
[*][Cyrus SASL database created with incorrect permissions]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cyrus%20SASL%20database%20created%20with%20incorrect%20permissions")
[*][Access to Java Runtime Environment]("http://www.ubuntu.com/getubuntu/releasenotes/810#Access%20to%20Java%20Runtime%20Environment")
[*][CD eject problems]("http://www.ubuntu.com/getubuntu/releasenotes/810#CD%20eject%20problems")
[*][Hangs with desktop effects on Intel 830MG and 845G video cards]("http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards")
[*][PlayStation 3 issues]("http://www.ubuntu.com/getubuntu/releasenotes/810#PlayStation%203%20issues")
[/LIST]
                 
[/LIST]
             
                             
  These release notes document known issues with Ubuntu 8.10 and its variants.  

**nVidia "legacy" video support**

  The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration. 
  Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support [SSE]("http://en.wikipedia.org/wiki/Streaming_SIMD_Extensions") (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade.

---

