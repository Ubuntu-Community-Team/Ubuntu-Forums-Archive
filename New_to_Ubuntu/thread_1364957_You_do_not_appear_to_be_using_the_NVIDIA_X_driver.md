---
title: "You do not appear to be using the NVIDIA X driver"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by wordmaster on 2009-12-26
I used the synaptics loader to load ALSA trying to get a USB mike to work. Until I did that, most everything was working fine. I picked everything to do with ALSA and after it all loaded, it said to restart.

I restarted and it would not let me get anything but low graphics, said nvidia was not loaded, so far have not been able to get it to load nvidia and now I find that Pegasus Mail under Wine is not working. Don't know what else I am going to find messed up. 

When I try to go the the vid setup I get"You do not appear to be using the NVIDIA X driver" and it tells me to run nvidia - xconfig, but this does nothing.

Is there some way I can get back to where I was prior to loading ALSA? Or anyway to fix what it  has messed up?

Than you kindly for any help you can give.

---

### Post by taurus on 2009-12-26
Look in System -> Administration -> Hardware Drivers and see if your nvidia graphic card is on the list.  If it is, then install a driver (recommended) for it and reboot.

---

### Post by wordmaster on 2009-12-26
OK, did that, said it was downloading and installing nvidia driver, but nothing happened. Restarted and got the same error on boot that nvidia was not loaded and could run only on low vid. Checked to run this time only on low vid. 800x600 is all I can get up to.

---

### Post by taurus on 2009-12-26
Which nvidia graphic card do you have and which version of driver did you install?

---

### Post by wordmaster on 2009-12-26
I have the 7050 and installed the 185 that was recommended by the Administration/hardware drivers. After downloading and installing it still says this driver is not activated. If I again click "activate" it goes through a 1 second or so thing like it did for a longer time the first time, then just comes back to the same original screen showing the driver and not activated.

---

### Post by lidex on 2009-12-26
wordmaster:

Try this:
[http://ubuntuforums.org/showpost.php?p=8059635&postcount=6]("http://ubuntuforums.org/showpost.php?p=8059635&postcount=6")

---

### Post by wordmaster on 2009-12-26
tried that and still no joy. Any idea what loading all the ALSA stuff did to mess everything up?

---

### Post by lidex on 2009-12-26
So you installed those packages through that ppa and rebooted and they still aren't available?

Run these commands in a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm /etc/X11/xorg.conf

```
and reboot

---

### Post by wordmaster on 2009-12-26
Did that and no change.

---

### Post by presence1960 on 2009-12-27
> **wordmaster said:**
> it tells me to run ```
nvidia - xconfig
```, but this does nothing.



Maybe you mistyped the command on your post. The command is ```
nvidia-xconfig
```
no space between nividia & -, no space between - & xconfig

---

### Post by lidex on 2009-12-27
OK.
Post the output of these commands please:
```
lspci
sudo lshw -C video
dmesg | grep -i nvidia
```

```
gedit /etc/X11/xorg.conf
```

And could you go into synaptic and search nvidia and see exactly what packages are installed, including xorg-nv?

---

### Post by wordmaster on 2009-12-27
OK, here is the output and thank you for all the help.

p@p-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7050 PV / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
01:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
01:07.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
p@p-desktop:~$ sudo lshw -C video
[sudo] password for p: 
  *-display UNCLAIMED     
       description: VGA compatible controller


















       product: C68 [GeForce 7050 PV / nForce 630a]
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:de000000-deffffff memory:c0000000-cfffffff(prefetchable) memory:dd000000-ddffffff memory:dffc0000-dffdffff(prefetchable)



# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier     "Configured Monitor"
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
	Option         "NoLogo" "True"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "keyboard"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by lidex on 2009-12-27
Run this command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and reboot.

---

### Post by lidex on 2009-12-27
> And could you go into synaptic and search nvidia and see exactly what packages are installed, including xorg-nv?

Please post here

---

### Post by wordmaster on 2010-01-01
Well, instead of posting all the nvidia things I found, I thought it might help to undo all I had done when I installed all the ALSA modules. I used the synaptics function to find all installed ALSA modules and I uninstalled all of them in the hope that I could go back to where I was before installing them brought on all the troubles.

After uninstalling, it said to reboot. I did, and after the same nvidia errors came up, it did not go to a gui, instead, I now only have a command line.

I tried startx and it gave errors and said there was no x installed. 

How can I get my gui back and hopefully, now that ALSA is gone, get the nvidia drivers to work again?

Thank you kindly for your help. Yes, I know, I should have done what you said....but instead I had a bright idea...

---

### Post by lidex on 2010-01-01
When you get to the command line, try this command:
```
apt-get install ubuntu-desktop
```

---

### Post by wordmaster on 2010-01-01
Tried that and no joy. got errors, ran with sudo in front, some stuff seemed to install, others did not, more errors and main problem seemed to be the nvidia module was not loaded.

Tried sudo apt-get install nvidia and got module not found. How can I get it to install the nvidia stuff?

---

### Post by lidex on 2010-01-01
```
sudo apt-get install nvidia-glx-180 nvidia-180-modaliases nvidia-settings
```

Then:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

**Reboot**

---

### Post by wordmaster on 2010-01-01
Thank you lidex. I used lynx from a command line, found your answer, applied it and finally am back with a desktop gui.

However, I still get the ubuntu running in low res mode and am unable to get it to take the nvidia drivers and allow the high res modes.

Any help appreciated.

---

### Post by lidex on 2010-01-01
Let's see if the video adapter is still unclaimed:
```
sudo lshw -C display
```

And try this one again:
```
sudo nvidia-xconfig
```

---

### Post by wordmaster on 2010-01-02
OK, here is what I got: 
*-display UNCLAIMED     
       description: VGA compatible controller
       product: C68 [GeForce 7050 PV / nForce 630a]
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:de000000-deffffff memory:c0000000-cfffffff(prefetchable) memory:dd000000-ddffffff memory:dffc0000-dffdffff(prefetchable)
p@p-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by wordmaster on 2010-01-02
After the above I ran the following with the following response:

p@p-desktop:~$ sudo apt-get install nvidia-glx-180 nvidia-180-modaliases nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-180 is already the newest version.
nvidia-180-modaliases is already the newest version.
nvidia-settings is already the newest version.
nvidia-settings set to manually installed.
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libfreebob0 libclxclient3 libwildmidi0 libmpich1.0gf
  libqt4-opengl rev-plugins guile-1.8 dvgrab texlive-base-bin-doc kword-data
  lilypond-doc gmerlin-data libdc1394-22 lilypond-data debhelper swh-plugins
  module-assistant texlive-base libxine1-x intltool-debian libxvidcore4
  wine-gecko kdebase-runtime-data-common libsoundtouch1c2 python-evince
  libdiscid0 mplayer-skins libsvga1 libgfortran3 lmodern kdebase-runtime
  libqt4-sql-mysql libqt4-dbus libxine1-misc-plugins ocaml-base-nox
  kdelibs-data kdelibs5 libxcb-xv0 libqt4-qt3support texlive-common
  libalsaplayer0 libdca0 libdns50 libopenspc0 libknotificationitem1 po-debconf
  liblualib50 libcddb2 libass3 kde-icons-oxygen libxine1-bin koffice-data
  libexiv2-5 debconf-utils python-gtksourceview texlive-base-bin
  libswt-gtk-3.4-java liblzma0 libxosd2 libmail-sendmail-perl ruby1.8 dvipdfmx
  guile-1.6-libs libx264-67 python-gnomedesktop libsoprano4 amb-plugins
  gettext python-urwid libmp3lame0 ruby libenca0 kdebase-runtime-bin-kde4
  libqt4-webkit gcj-4.4-base cmt vco-plugins libcelt0 kdelibs5-data cvs
  libfltk1.1 libitext-java libavahi-qt3-1 libgcj-common python-gnomeprint
  oss-compat libxcb-shape0 libgavl1 python-metacity libyate1.3.0 freepats
  libclthreads2 camlp4 libwv2-2 libqthreads-12 liblzo2-2 libffado1 libqt4-sql
  sfftw2 libc6-amd64 libqt4-svg python-mediaprofiles lilypond
  libstreamanalyzer0 libsox-fmt-base yate libkate1 libplasma3 libcdaudio1
  libmimic0 uuid-dev xmms2-core ledit phonon-backend-xine libqt4-designer
  beast python-bugbuddy ocaml-interp libxml++2.6-2 python-totem-plparser
  kdelibs-bin libqt4-phonon python-evolution mpg123 libncurses5-dev
  libmpg123-0 libstreams0 html2text libdirac0c2a libmodplug0c2 exiv2
  python-wnck kernel-package libpri1.4 winbind php5-cli liblua50 libruby1.8
  python-nautilusburn libqt4-script libsox1a libquicktime1 ladcca2 fxload
  libxcb-shm0 soprano-daemon libswt-cairo-gtk-3.4-jni kdebase-runtime-data
  libguile-ltdl-1 texlive-doc-base ocaml-nox libmpcdec3 php5-common tex-common
  libsys-hostname-long-perl libpqxx-2.6.9ldbl libofa0 libmms0 libiptcdata0
  texinfo python-gtop libxine1-console libswt-gtk-3.4-jni libfaac0
  libmusicbrainz3-6 libfaad0 libswt-mozilla-gtk-3.4-jni libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nouveau-kernel-source (0.0.15+git20090823-0ubuntu1) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: nouveau-0.0.15+git20090823
You cannot add the same module/version combo more than once.
dpkg: error processing nouveau-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 3
Errors were encountered while processing:
 nouveau-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code

---

### Post by lidex on 2010-01-02
Did you reboot after "sudo nvidia-xconfig" command? And did it work?
there was no reason to install "sudo apt-get install nvidia-glx-180 nvidia-180-modaliases nvidia-settings", that was done previously.

What is the output of:
```
uname -a
```
```
lsb_release -a
```

---

### Post by wordmaster on 2010-01-02
Yes, I rebooted, and no, it didn't work. Here is the output:

p@p-desktop:~$ uname -a
Linux p-desktop 2.6.31-16-generic-pae #53-Ubuntu SMP Tue Dec 8 05:20:21 UTC 2009 i686 GNU/Linux
p@p-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic


I have also found that none of my programs under wine will work. When I go to the exe files and properties,it says open with archive manager. What should it say to open with in wine?

---

### Post by lidex on 2010-01-02
I don't know what you did to your system previously but it's pretty mucked up. You need alsa, and that's not what's causing your video problems. Likely it's nouveau. That needs to go. I would search synaptic for anything related and purge it. Then re-install alsa. This should be the basic install: ```
sudo apt-get install alsa-oss libasound2-plugins alsa-utilities alsa-base linux-sound-base libasound2 lib32asound2
```   **Then reboot. **

Did you recently uninstall some kde apps or the kubuntu-desktop? Do you have audio right now?

---

### Post by lidex on 2010-01-02
> **wordmaster said:**
> 
I have also found that none of my programs under wine will work. When I go to the exe files and properties,it says open with archive manager. What should it say to open with in wine?

One thing at a time. Need to get your video and audio together first. I just noticed this: > 0 upgraded, 0 newly installed, 0 to remove and ***20 not upgraded*** After re-installing alsa, update your system before you reboot:

```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

---

### Post by wordmaster on 2010-01-02
OK, I removed nouveau. 180 and 185 would still not load so using system/administration/hardware drivers, I activated 173. That finally worked and I am now at high res.

The only thing I did between everything working and loads of problems was to install alsa. However, I did it through synaptics and checked everything to do with alsa after a search.

I do have sound now. It seems to be working fine.

The only thing still giving problems are my wine programs. The most important of which is Pegasus Mail where all my email is at.

Under "open with" all my .exe files have "archive manager" this does not sound right. Under ubuntu, what should a .exe file open with?

---

### Post by charlier653 on 2010-01-02
Have you configured wine yet?

---

### Post by wordmaster on 2010-01-02
Prior to the alsa problem, everything ran fine under wine. It has been set up and running all along until the problem. Now none of the programs will start and when I run properties I see that the .exe files are set to open with archive manager. I have not tried reloading or reconfiguring wine.

---

### Post by charlier653 on 2010-01-02
That may solve the problem. Don't know. Still a new user myself.

---

### Post by wordmaster on 2010-01-02
I really don't know how to reload or reconfigure wine without possibly causeing a lot of new problems. Can anyone help?

---

### Post by charlier653 on 2010-01-02
Only thing I would be able to suggest is use synaptic to remove wine and all libs/dependencies, then reinstall.

---

### Post by lidex on 2010-01-02
Try to stay away from experimental programs/packages.

As for wine, I have never used it, but you can find some good info here:
[https://help.ubuntu.com/community/Wine]("https://help.ubuntu.com/community/Wine")


*[COLOR="Gray"]wordmaster: Please mark this thread as solved and if you continue to have problems with wine, post another thread in the appropriate area so you can get the help you need.[/COLOR]* ;-)

---

### Post by bobloblaw86 on 2010-01-02
I am having very similar problems to this after doing a fresh install of 9.10 and then adding several programs from the Ubuntu software center. Should I just revert to 173?

---

### Post by lidex on 2010-01-03
bobloblaw86,
Run these commands in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Go to "Hardware Drivers" and deactivate your driver (if activated). Close that. Go to synaptic and search "nvidia" and remove any packages with a number other than 173 in the package name. Now (still in synaptic) install all the packages with 173 in the package name as well as nvidia-settings.

**Reboot**. Now go to "Hardware Drivers" and enable 173.

---

### Post by bobloblaw86 on 2010-01-03
thank you lidex worked perfectly.

---

### Post by Rugiero on 2010-06-05
> **lidex said:**
> Run this command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and reboot.


Thanks a lot, im running 10.04 dv2945se laptop 
:guitar:

---

