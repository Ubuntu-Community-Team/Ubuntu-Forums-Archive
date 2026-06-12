---
title: "Display settings can not adjust"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by nalakau on 2010-01-25
Hi,
 
I'm using ubuntu 9.10 / windows XP. I can not adjust my display setting in ubuntu. it shows huge icons & fonts. When I try to adjust display settings it shows monitor not identified. I'm using nvidia Geforce 5500 AGP graphic card. Pls help to overcome this problem.

---

### Post by hemimaniac on 2010-01-25
You should head to the nvidia.com website and download the latest driver for your rig.

once that is done pop open a terminal and do 

sudo telinit 3
su: <pass>
cd <path/to/wherethe/file/is>
sh ./NVidia_<name>.run
reboot

---

### Post by nalakau on 2010-01-25
Thanks for your advice but I can not download drivers from nvidia site. Attached the screenshot for your reference.

---

### Post by realzippy on 2010-01-25
For your (old) card you have to use the 173.driver...

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.22/NVIDIA-Linux-x86-173.14.22-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.22/NVIDIA-Linux-x86-173.14.22-pkg1.run)


But can't you install it with System/Administration/Hardware Drivers ?

---

### Post by nalakau on 2010-01-25
I installed from System/Administration/Hardware Drivers but it did not work. anyway I download the drivers from the link. I don't have any idea of run that drivers.  even I don't have any idea in working with the terminal. I do not wont to take my step back I need to go ahead with ubuntu. Pls assist.

---

### Post by hemimaniac on 2010-01-25
the directions for the driver you've just downloaded will be the same as the ones posted earlier.

open a terminal
use the following commands

cmd
sudo telinit 3  <- it will appear to restart but it is just dropping to a lesser display mode
cmd
cd /home/username/location/ <- this will be where the file was downloaded eg /home/nalakau/downloads/ (tab complete works to file out the directory after first couple of letters are typed, REMEMBER linux is case sensitive so Downloads would be entered as Downloads)

cmd
sudo sh ./NVIDIA-Linux-x86-173.14.22-pkg1.run < this will allow the pkg to be executed and install, use tab and arrow keys to navigate through the options, and at the end select yes for letting it configure you're x-server
cmd 
reboot

upon restart it will load (should) the nvidia driver and in terminal you can do 
gksudo /usr/bin/nvidia-settings

then the nvidia settings will open up and you can make your adjustments, then simply click save to configuration file upon completion.

Alternatively you could go menu > administration then drag the nvidia icon to the desktop, right click on it and select properties and edit the command with gksudo_ ( _indicates a space ) save, then launch it like a regular desktop launcher.

---

