---
title: "wi fi wireless troubles"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by censer2002 on 2011-07-12
ok i know i need drivers but i keep finding diff drivers everywhere and  where do i install them once i have them i have no wired connection so i  would have to put them on a usb or view them somehow in ubuntu i have a  ralink RT5390 and i think the chipset is RTL8101E/RTL8102E any help  would be great a link to the drivers where to put them when i&#65279; got them  anything will help

---

### Post by MG&amp;TL on 2011-07-12
Ok, if you've done this and it didn't work, apologies, but someone has to check.

Go to 'additional drivers':

Under 10.10 or earlier Administration> additional drivers.

Under 11.04 search(press windows or <super> key) for 'additional' , it will pick it up. (it looks like a circuit board with a padlock)

Once you're in there, it may (or may not) tell you that you have drivers to install. If so, install them, then reboot as instructed. Drivers should then work. This is the recommended way of doing it, if you've already done this, sorry. :)

---

### Post by MG&amp;TL on 2011-07-12
Of course, if they don't, and I'm afraid about 1/3 of the time they don't, you have an issue, post a separate thread giving CLEAR data about your hardware, and someone will help you. They always do, welcome to the forum btw.

---

### Post by grahammechanical on 2011-07-12
As you do not have a wired connection then the previous suggest won't be any good. Here is a link to the troubleshooting guide.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Somewhere in there is a section on how to install drivers when you do not have an Internet connection. I think that you need to tell Update Manager to look at your CD/DVD drive for the files instead of on the Internet. With Update manager open I think you select Settings, then Other software, then Add volume

Regards.

---

### Post by wep940 on 2011-07-12
If you can at least boot, please do the following:
 
[LIST]
[*]open a terminal window (applications/accessories/terminal)
[*]
[*]type lspci >dwe.txt <press enter>  This should redirect the output of the lspci command to a file, in this case dwe.txt in your default folder.  Please note only 1 ">" redirect symbol on this command as we are creating the file.
[*]
[*]type lsusb >> dwe.txt <press enter>  This should redirect the output of the lsusb command and append it to the file containing the results of the lspci command.  Please note that on this command there are 2 redirect symbols (>>) to append to the file
[/LIST]Now create a post back here and attach the dwe.txt file to it.  In that way we can be sure of the chipset and give you valid advice.  I know some of those chipsets don't require finding a driver - at least 1 of them is just a modprobe to insert the correct kernel module, others require just creating a dummy config file with nothing in it.

---

### Post by MG&amp;TL on 2011-07-13
Apologies:
a) I misread the post. Sorry.
b) I found a site once that told me to look there, but I checked the site, but it's actually wrong and unrelated. Ooops.

Sorry again. I hate causing confusion. :(

---

### Post by censer2002 on 2011-07-13
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Ralink corp. Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by censer2002 on 2011-07-13
Thanks for being so helpful everyone  i hope what i have posted per wep's request helps us resolve my problem

---

### Post by westie457 on 2011-07-13
May i make a radical suggestion here? 

If you have a mobile phone with internet access you can set up a Mobile Broadband connection to download the Ralink Drivers as a .tar package. I am sure someone would help with installing these if you are unsure of the process.

---

### Post by censer2002 on 2011-07-13
also this is the link i was given from someone on youtube [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)       it is a link to some drivers i downloaded the second one from the top in the list i have them on my ubuntu desktop now what do i do with them ??? or is this what i need to do at all ??? or did i download the correct drivers ??? because i seen drivers that are different from realtek that i found from google listed under this number RTL8101E/RTL8102E instead of what ralink has drivers listed under this number RT5390 also here is the link to the youtube video that mentioned earlier [http://www.youtube.com/watch?v=ydrb4_fiPJo](http://www.youtube.com/watch?v=ydrb4_fiPJo)

---

### Post by bkratz on 2011-07-13
> **westie457 said:**
> May i make a radical suggestion here? 

If you have a mobile phone with internet access you can set up a Mobile Broadband connection to download the Ralink Drivers as a .tar package. I am sure someone would help with installing these if you are unsure of the process.



You might also want to read through this thread for info.

[http://ubuntuforums.org/showthread.php?t=1751685](http://ubuntuforums.org/showthread.php?t=1751685)

---

### Post by westie457 on 2011-07-13
Have just found this

[http://ubuntuforums.org/showthread.php?t=1751685](http://ubuntuforums.org/showthread.php?t=1751685)

It may not be the correct solution but it should give you some clues for what you need.

---

### Post by censer2002 on 2011-07-13
i believe i have those drivers refer to my post just after yours and i can get files to ubuntu by just downloading them in windows and switching partitions then getting them from where ever i put them when i downloaded them in windows so if that is the case then i just need to know where to put them

---

### Post by westie457 on 2011-07-13
> **censer2002 said:**
> i believe i have those drivers refer to my post just after yours and i can get files to ubuntu by just downloading them in windows and switching partitions then getting them from where ever i put them when i downloaded them in windows so if that is the case then i just need to know where to put them

Here is a guide on what to do [http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

Also you will to get a package called build-essential.

---

### Post by censer2002 on 2011-07-13
is this something that could help me if so which one [http://en.wikipedia.org/wiki/Comparison_of_open_source_wireless_drivers#Status](http://en.wikipedia.org/wiki/Comparison_of_open_source_wireless_drivers#Status)

---

### Post by Peter09 on 2011-07-14
I have just installed this driver on my wifes pavilion g6. The card is very new and the drivers are not in the Ubuntu firmware yet.
 
I am not sure where you are with this but this link is the one that I followed.
 
[http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)
 
NOTE- look at my edit at the bottom before running the make.

[LIST=1]
[*]> [LIST=1]
[*]Download the driver from ralinktech.com --> Software --> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]cd to the 2010_xxx extracted directory
[*]cd os/linux/
[*]Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified)
[*]Go back to the 2010_xx directory
[*]run command 'make'
[*]Make sure 'make compile' exists without errors. I got an error "too many arguments to format" towards the end of the compile but it did compile successfully eventually. And so I ignored the errors. You would see ***errors*** if the compile is not successful. In which, something went wrong and you may need to tweak the makefile or config.mk files before compile is successful.
[*]**run command 'make install' as root. This is not listed in the README_STA_pci file that comes with downloaded driver zip file. This takes of copying the file to /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt5390sta.ko. running depmod, creating /etc/Wireless/... folder.**
[*]Edit the /etc/modules and add the line at the end of this file
rt5390sta
[*]Edit the file /etc/modprobe.d/blacklist.conf and add the below line to it...
blacklist rt2800pci
[*]Reboot and you should see an ra0 interface when you run the command 'ifconfig'
[*]You may have to run '/etc/init.d/network-manager restart' command to have it show in the first go.
[*]Once, the wireless icon shows up, look for your wireless SSID and there you go surfing :smile:
[/LIST]
[/LIST]Note the kernel reference numbers will be different if you are using a different kernel.
Note line 9 which is in bold - this did not work for me as it seems to try to use the wrong driver so:
 
 
Copy the file rt5390sta.ko to **/lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt5390/rt5390sta.ko**
 
You will need to create the rt5390 folder.
then 
 
```
sudo depmod
```
and
```
modprobe rt5390
```
 
should fireup your wireless.
 
It looks complex but if you follow by rote it should be ok, look for errors and come back if you see any.
 
EDIT:
>  
Forgot that you need to apply patches:
 
*Hi edwin_aldrin,*
 
*To open an RPM package, just download it then double-click on it as you would do with any TAR or ZIP. It will be opened and you will see the contents. You will see a TAR with the driver code from Ralink and a set of patches. Just extract the contents of the RPM to some directory of your choice. Then, extract the driver code TAR in that directory and your directory should look like*
 
*#cd myDir*
*#ls*
*driverCodeDir*
*patch1.patch*
*patch2.patch*
*...*
*patchN.patch*
 
*then change to the driver code directory and apply the patches as follows*
*#cd driverCodeDir*
*#patch -p0 <../patch1.patch*
*#patch -p0 <../patch2.patch*
*..*
*#patch -p0 <../patchN.patch*
 
*To know the order in which you need to apply the patches, look at the rt5390sta.spec file lines 38-44. If you are using 10.10 32-bit apply all patches except rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch. For 10.10 64-bit, apply all patches.*

 
All of this is in the thread I referenced.

---

### Post by westie457 on 2011-07-14
@ Peter09

+1 for that. This is more or less exactly the advice I was going to give.

Could not remember all the details as only did this once over a year ago.

---

### Post by Peter09 on 2011-07-14
Also - its worth doing all of this in your home directory somewhere as when there is a kernel update you may need to do it again. However all you need to do is run the make and do the copy - which is quick and easy. So don't delete the directory when you have finished.

---

### Post by censer2002 on 2011-07-15
could u give any further info like to steps 3 and 4 im a total noob at this and i really want to learn it i know cd means change directory but thats about it it i dont even know how to get started really

---

### Post by censer2002 on 2011-07-15
would this help me connect to wireless ? [http://www.amazon.com/Alfa-AWUS036H-802-11b-Wireless-Original/dp/B002BFMZR8/ref=pd_sxp_f_i](http://www.amazon.com/Alfa-AWUS036H-802-11b-Wireless-Original/dp/B002BFMZR8/ref=pd_sxp_f_i)

---

### Post by Peter09 on 2011-07-15
cd is a terminal command to change directory.

```
cd <path to change to>
```

---

### Post by censer2002 on 2011-07-15
yes but what is that 2010 part and the _ underscore and the rest is xxx out

---

### Post by Peter09 on 2011-07-16
If you look in the directory where you extracted the driver you will see a directory called that. Its a long name so it has been shortened.

---

### Post by censer2002 on 2011-07-16
ok thanks  what i did was i downloaded the drivers on my windows partition and put them where i could find them moved them in their folder to my unity desktop still in their folder i dont remember if it was a zip file or what but its accessible on the desktop all i got to do is click on it i need to figure out what to do from there i doubt there is but i was wondering if there was some way that i could place the drivers when im in my windows partition where linux could find them if that would be easier

---

### Post by censer2002 on 2011-07-17
ok i have another question if i make a directory and put my drivers in it how does my computer know to look there for the drivers to run my wireless card and what is this about apply patches ???

---

### Post by wep940 on 2011-07-18
The installation process for a driver will install it in the proper ubuntu system folder.  If you had to compile from source code, the "make install" is what installs the driver you just compiled, again in the proper ubuntu system folder.

---

### Post by censer2002 on 2011-07-18
i have my drivers in the single folder that they unzipped into labeled ralink_drivers in downloads in my home folder do i open the single folder with files and drivers and etc and other folders inside of that and make each file ,drivers etc individually by itself so nothing is inside a folder or anything at all and have all of this in downloads i think the install command is apt-get or sudo  apt-get depending on if i am in root or not when i go to downloads in the terminal the only thing that it shows being in there is ralink_drivers because the folder isnt open i assume and i can get no further

---

### Post by wep940 on 2011-07-20
Since you have unzipped the files, you need to look in the ralink_drivers everything was placed in.  There should be a readme or README or something along those lines.  If indeed this was source code, the normal procedure may apply:
 
- open a terminal window (applications/accessories/terminal)
 
- type:
 
cd Downloads/ralink_drivers <press enter>
 
./configure <press enter>
 
make <press enter>
 
sudo make install <press enter>
 
If you haven't done so already, be sure to install the build-essential package before attempting this.
 
BTW - I assume that when you unzipped the files it placed the expanded files in the ralink_drivers folder and that there are also subfolders there.  If you merely copied them yourself you may need to start over.

---

