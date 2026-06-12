---
title: "Lost prefered display"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by nnjond on 2009-10-23
Hi,
Can anyone help me? To cut a lng story shrt, It seems an update conflicted with my display driver. My pc now boots without incident but I've lost my scrn res and am now  looking at a 800X600 display. I have followed these intructions to solve the prob, but now i'm stuck.

nnjond@nnjond-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
nnjond@nnjond-desktop:~$ 


nnjond@nnjond-desktop:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
[sudo] password for nnjond: 
nnjond@nnjond-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20091023071026
nnjond@nnjond-desktop:~$ sudo apt-get install build-essential pkg-config linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
pkg-config is already the newest version.
linux-headers-2.6.28-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
nnjond@nnjond-desktop:~$ If you run Ubuntu and have an NViDIA card, you more than likely used the 'Hardware Drivers' utility to install them. This can lead to conflicts later down the line, as New drivers/Old drivers will cause API conflicts that will prevent X from starting. So you are required to uninstall/remove any nvidia modules and references before beginning. Code: 
bash: If: command not found
nnjond@nnjond-desktop:~$ 
nnjond@nnjond-desktop:~$ sudo apt-get --purge remove nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
Package nvidia-glx-legacy is not installed, so not removed
Package nvidia-glx-new is not installed, so not removed
The following packages will be REMOVED
  nvidia-settings*
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
After this operation, 1933kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 261690 files and directories currently installed.)
Removing nvidia-settings ...
Purging configuration files for nvidia-settings ...
Processing triggers for menu ...
Processing triggers for man-db ...
nnjond@nnjond-desktop:~$ dpkg -l | grep nvidia
ii  nvidia-173-kernel-source                   173.14.16-0ubuntu1                                         NVIDIA binary kernel module source
ii  nvidia-glx-173                             173.14.16-0ubuntu1                                         NVIDIA binary Xorg driver
nnjond@nnjond-desktop:~$ sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  nvidia-173-kernel-source{p} nvidia-glx-173{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 7 not upgraded.
Need to get 0B of archives. After unpacking 32.1MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 261665 files and directories currently installed.)
Removing nvidia-glx-173 ...
Purging configuration files for nvidia-glx-173 ...
Removing nvidia-173-kernel-source ...
Removing all DKMS Modules
Done.
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

nnjond@nnjond-desktop:~$ Download Drivers
bash: Download: command not found
nnjond@nnjond-desktop:~$ 
nnjond@nnjond-desktop:~$ Depending on your OS architechture, you will need to get the right one for your kernel.
bash: Depending: command not found
nnjond@nnjond-desktop:~$ 
nnjond@nnjond-desktop:~$ If you are on 32bit Ubuntu, run: 
bash: If: command not found
nnjond@nnjond-desktop:~$ 
nnjond@nnjond-desktop:~$ wget [ftp://download.nvidia.com/XFree86/Linux-x86/185.18.31/NVIDIA-Linux-x86-185.18.31-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/185.18.31/NVIDIA-Linux-x86-185.18.31-pkg1.run) -O NVIDIA-Linux-185.18.pkg.run
--2009-10-23 07:22:17--  [ftp://download.nvidia.com/XFree86/Linux-x86/185.18.31/NVIDIA-Linux-x86-185.18.31-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/185.18.31/NVIDIA-Linux-x86-185.18.31-pkg1.run)
           => `NVIDIA-Linux-185.18.pkg.run'
Resolving download.nvidia.com... 213.248.114.243
Connecting to download.nvidia.com|213.248.114.243|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /XFree86/Linux-x86/185.18.31 ... done.
==> SIZE NVIDIA-Linux-x86-185.18.31-pkg1.run ... 22665711
==> PASV ... done.    ==> RETR NVIDIA-Linux-x86-185.18.31-pkg1.run ... done.
Length: 22665711 (22M)

100%[===================================>] 22,665,711   667K/s   in 33s     

2009-10-23 07:22:51 (671 KB/s) - `NVIDIA-Linux-185.18.pkg.run' saved [22665711]

nnjond@nnjond-desktop:~$ sudo install NVIDIA-Linux-185.18.pkg.run /usr/src
nnjond@nnjond-desktop:~$ 
nnjond@nnjond-desktop:~$ sudo ln -fs /usr/src/NVIDIA-Linux-185.18.pkg.run /usr/src/nvidia-driver
nnjond@nnjond-desktop:~$ 
nnjond@nnjond-desktop:~$ The nvidia-driver symlink will be needed for later + post installation configuration. (?)
bash: syntax error near unexpected token `('
nnjond@nnjond-desktop:~$ 
nnjond@nnjond-desktop:~$ 

Kill X

Now, it's time to stop X and the gdm (or kdm for Kubuntu Users) This requires that you logout and switch to another tty console ( Ctrl+Alt+F1 ).

Login to the shell, and kill gdm: 

sudo /etc/init.d/gdm stop

sudo killall Xorg

At this point, this is returned:

No process killed

I continue to follow the instructions:



Installing NViDIA

Afterwards, its time to install the drivers. Code:

sudo sh /usr/src/nvidia-driver

This leads me to:

ERROR: Unable to load kernal module 'nvidia.ko


If all had gone well, i would have cont...


Follow the instructions, and everything should run smoothly. A few points that I'd like to reassure first though:

    *
      Don't worry about pre-compiled binaries, just let the script compile the drivers itself.


    *
      When asked, double check to ensure you select 'NO' when the NViDIA installer asks to reconfigure the xorg.conf file.
    *
      We don't want to change the xorg.conf file just yet, at least not until we are back in X.

Once finished, it is now time to reboot: 

sudo reboot


Before you Initiate the Driver

Now, since NViDIA didn't reconfigure the xorg.conf file, you will boot into the VESA drivers. To setup the xorg.conf file for nvidia, login, open a terminal, and run: Code: 

sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
sudo nvidia-xconfig


Note: You may see this being outputted into the console

Using X configuration file: ”/etc/X11/xorg.conf”.

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf. Device section “Configured Video Device” must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup' New X configuration file written to '/etc/X11/xorg.conf' Ubuntu uses an automagically configured xorg.conf file, and nvidia-xconfig flags it only as a parser warning, and serves only as a warning. This does not affect the outputted xorg.conf file generated by the nvidia script, and you blissfully ignore it.

Now, not everyone may experience a smooth transition, and there are a number of small problems that you may run into that need addressing first. The most common one probably being a non-existent module listed in the xorg.conf file.

And if you have had a successful transition, and everything works. The first thing you may notice is a nice new NViDIA splash logo that you probably want to be removed too. If you get this, just run the following: Code: 

sudo sed -i '/Section\s*.Screen./a\    Option         "NoLogo" "True"' /etc/X11/xorg.conf


X Time

And that is it! To reload into your new nvidia drivers, close all running applications and logout/login again. If you are running Ubuntu Hardy/Intrepid, this can be done by pressing Ctrl+Alt+Backspace. If you are running Ubuntu Jaunty, then you'll have to manually logout, or in some cases, reboot your machine in order for the new driver to load and work.

Keep in sync with kernel updates Now with custom compiled nvidia modules, you'll have to ensure that the drivers get recompiled whenever a new kernel gets released. For reference on how to do this, follow this thread to set it up: 

    *
      [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

But, for clarification, open a new file named update-nvidia 

gedit update-nvidia


Paste in the script listed in the thread, save and quit. Then run: 


sudo mkdir -p /etc/kernel/postinst.d
sudo install update-nvidia /etc/kernel/postinst.d


to install the script.

---

