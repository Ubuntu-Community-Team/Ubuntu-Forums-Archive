---
title: "Got Jaunty Studio and Nvidia problems?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by psy-moon on 2009-05-11
You are not alone..
I'm new to ubuntu, Ive had some success installing Jaunty Jackalope inside a windows rig using the wubi installer.

 A bit of fiddling with Nvidia drivers to get my old fx5200 dual monitor to work like it does in windows XP.
 So I decide to take the next step and clear some drive space for a proper install of ubuntu studio.
 I had a bit of trouble with GRUB, but that is down to the layout of my drives.
 So, my windows MBR remains intact on the first IDE drive Ubuntu is in on a partition on a serial ata drive. (BIOS reads it as SCSI) , GRUB is on the first partion of that drive.
 Tell BIOS to boot SCSI, jobdone.
Now I have ubuntu studio installed and running,
 I'm recomended to install propriatory drivers for the nvidia card so I click ok. the driver is downloaded and installed but does not load. When I reboot I see the nvidia driver FAILS to load and have no GUI.
Now after a couple of days following threads here there and every where I think I am beging to understand whats wrong.
The latest nvidia driver 180 does not support my old card.
The legacy nvidia drivers do not seem to function in the ubuntu studio low latency kernel though they seemed to work ok on the standard Jaunty kernel.
I think I read that it is possible to compile the legacy driver using headers for the kernel used in ubuntu studio but this seems to be over my head as I could not take it on board. Can anyone illucidate or point to a beginers guide?:guitar:

---

### Post by cariboo on 2009-05-11
Use synaptic to rmove all traces of the nvidia driver, make sure build-essential is installed.

[list]
[*] Download the driver from [here]("http:///www.nvidia.com/object/unix.html")
[*] Go to a console, press Ctrl-Alt-F1
[*] Make the downloaded file executeable
```
chmod +x ~/Desktop/*run
```
this assumes the file is on your desktop.
[*]kill gdm
```
sudo /etc/init.d/gdm stop
```
[*] run the file
```
sudo ~/Desktop/*run
```
answer yes to all the questions
[*] once the driver has compiled, restart gdm
```
sudo /etc/init.d/gdm start
```
if everything went all right you should be back at the desktop
[/list]

---

### Post by psy-moon on 2009-05-12
Hi there,
 thanks for the reply I followed the instructions;
 awesome! now I see what makes linux so adaptable.
 unfortunately the compile failed.
 The log file seems to suggest that I am missing a couple of header files,
 I have checked that I have "linux-headers-2.6.28-3-rt_2.6.28-3.12_i386.deb"
 the package manager says the same version is already installed;
 so I don't know what gives!
 should I reinstall the kernel header package and try again?
I have attached the installer log in case it helps.

Post script. 
Ok I tried reinstalling the kernel header package. Clearly this was not the problem as the compile still reports an error.

I have resorted to plan B 

Whilst I was at the ubuntu studio download server I also grabbed the iso for 8.1 hardy.
I have removed the Jaunty install and replaced it with Hardy. I guess the older version is better suited to my clunky old rig as I now have my two CRTs displaying an extended desktop at 2560x1024 
that's 1280x1024 each. great!

---

