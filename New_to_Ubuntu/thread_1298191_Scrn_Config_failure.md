---
title: "Scrn Config failure"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by nnjond on 2009-10-22
Hi,

I was prompted to restart after update,  3 failures occured :

# (EE) NVIDIA(0)) failed to load...  kernal
#
# (EE)..                             SCRNs found but none have useable config

Never had this prob befor?

---

### Post by aesis05401 on 2009-10-22
Hello, if you can get to a console I think you can follow the instructions in the guide to get running again:  [http://gwos.org/udsf/doku.php/hardware:nvidia](http://gwos.org/udsf/doku.php/hardware:nvidia)

Can you take a look at the link and post back?

Edit: Additionally, it would help to know your card model, OS, and what sort of upgrade you were doing.

---

### Post by nnjond on 2009-10-22
Hi, Thanks for your help.

Ubuntu prompted me to install 39m of upgrades, but i didn't look to see what they were. Then it asked me to restart. It highlit 3-4 failures when booting.

I follwed that pge with code as well as i could; have uninstalled stuff etc. Now it boots with out incident but my my res is still rudimentry.

Sorry i cant remember the code which ids my vcard,  My os is 9.04.

---

### Post by aesis05401 on 2009-10-22
> **nnjond said:**
> Hi, Thanks for your help.

Ubuntu prompted me to install 39m of upgrades, but i didn't look to see what they were. Then it asked me to restart. It highlit 3-4 failures when booting.

I follwed that pge with code as well as i could; have uninstalled stuff etc. Now it boots with out incident but my my res is still rudimentry.

Sorry i cant remember the code which ids my vcard,  My os is 9.04.

 The boot errors no longer appear?

For the hardware try opening a terminal and typing 
```

lspci

```

Post the output here to show us your chipsets.

---

### Post by nnjond on 2009-10-22
Boots without incident.


lspci
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

---

### Post by aesis05401 on 2009-10-22
Ok, we should be almost there. This thread is for an earlier Ubuntu version, but same chipset and should help finish the recovery: [https://answers.launchpad.net/ubuntu/+source/xorg/+question/33571](https://answers.launchpad.net/ubuntu/+source/xorg/+question/33571)

Either getting nvidia-settings package or the right glx package should get your resolution back.

Please post back either way.

---

### Post by nnjond on 2009-10-22
Thanks again. I've been led to this point:

nnjond@nnjond-desktop:~$ nvidia-xconfig
The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-glx-173
 * nvidia-glx-180
 * nvidia-glx-96
Try: sudo apt-get install <selected package>
bash: nvidia-xconfig: command not found
nnjond@nnjond-desktop:~$ nvidia-glx-new
bash: nvidia-glx-new: command not found
nnjond@nnjond-desktop:~$ install nvidia-glx-new
install: missing destination file operand after `nvidia-glx-new'
Try `install --help' for more information.
nnjond@nnjond-desktop:~$  nvidia-glx-173
bash: nvidia-glx-173: command not found
nnjond@nnjond-desktop:~$ install  nvidia-glx-173
install: missing destination file operand after `nvidia-glx-173'
Try `install --help' for more information.
nnjond@nnjond-desktop:~$

---

### Post by nnjond on 2009-10-22
Let me try to clarify my position:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?."

Y

 "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

I think i need to know the code for "run"

---

### Post by aesis05401 on 2009-10-22
Hello,

The correct installation command is:
```

sudo apt-get install <package>

```But have you already tried nvidia-settings?

Edit: Using sudo apt-get install will install your package in a manner that will allow you to run it by typing the name... however you may want to type 'man <package-name>' to get some background before running any utility. 

Additionally, sudo apt-cache search <package> allows you to search for packages.

---

### Post by nnjond on 2009-10-22
I have installed nvidia-settings and have sudo aptitude installed one of the packages.  Should i install the other 2 to see if that will work ?

"Edit: Using sudo apt-get install will install your package in a manner that will allow you to run it by typing the name... however you may want to type 'man <package-name>' to get some background before running any utility."

??? What background would i need to know?

---

### Post by aesis05401 on 2009-10-22
No.  The document I linked starts by having you purge those files... then downloading the updated packages, building, installing, configuring.  

So when you got to the nvidia-xconfig step you received the error... I am a bit confused.  The driver package you downloaded with the wget command should have pulled down everything you needed.

Did you receive any errors when downloading and installing the drivers?

Edit: The background I refer to is the instructions on how to use the programs.  'man' jsut stands for manual and man-pages hold many answers to life's little questions.

---

### Post by nnjond on 2009-10-23
I think I've started from the beginning again and come up with 2 errors but don't know what to do about it. here is my account:

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

Then I'm returned:

"No process killed"                         

Is this a problem? I cont...

Installing NViDIA

Afterwards, its time to install the drivers. Code: 

sudo sh /usr/src/nvidia-driver

                                            I cont untill...

ERROR: Unable to load kernal moduale 'nvidia.ko'

---

