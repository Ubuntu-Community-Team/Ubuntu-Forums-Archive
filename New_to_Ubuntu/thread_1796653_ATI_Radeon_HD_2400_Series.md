---
title: "ATI Radeon HD 2400 Series"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by LinNew on 2011-07-04
HI

I am new to Linux .... always been a Windows junkie, but want to see what Linux is about. I installed Ubuntu 11.04 and the installation ran smoothly. I was asked to re-boot on completion of the installation which i did and then when it reloaded, after asking me to sign in, it froze. I suspect it has something to do with my graphics card because when i did a re-boot, this time in recovery mode and selected low graphics, all was fine and it worked pretty well. However, there does not seem to be any way to force it to boot up in low graphics all the time ? Or is there ? Or is there some other problem, possibly a different driver i can try. I see some of the posts indicate a general problem with ATI drivers, so i am not holding much hope of finding a suitable driver .... :(

---

### Post by mastablasta on 2011-07-04
after booting in low graphics mode did you install the proprietary hardware drivers (A.K.A AMD/ATI drivers)?

---

### Post by misterbiskits on 2011-07-04
> Or is there some other problem, possibly a different driver i can try. 
Check to see that AMD/ATI has a linux driver for your card (I think it does):
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
if so, 
Install the drivers manually:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)
In the future if you want to keep on top of updates, you will have to remove the old driver and install the update manually.

---

### Post by LinNew on 2011-07-05
Thanks Guys ... I will look try and find drivers and do the manual install :) Failing that is the only other solution a Nvidia card ?

---

### Post by mastablasta on 2011-07-05
yes and no. yes for better graphics and no, this ATI card should work fine with drivers provided by ATI (i think they have them). 
 
you should also be able to install them via additional drivers menu, however the ones on th esite might be newer ones. i think they spit out new onss before the Ubuntu comes out and then fixes every 3 months or so.

---

### Post by LinNew on 2011-07-09
> **misterbiskits said:**
> Check to see that AMD/ATI has a linux driver for your card (I think it does):
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
if so, 
Install the drivers manually:
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually)
In the future if you want to keep on top of updates, you will have to remove the old driver and install the update manually.

Ok ..so i tried this manually and didnt really get very far. I have no internet connectivity at this point as Linux does not recognize my 3G modem, so i downloaded the ATI installations manually on another machine. 

I started following the instructions from [http://wiki.cchtml.com/index.php/Ubu...ivers_manually](http://wiki.cchtml.com/index.php/Ubu...ivers_manually) but after trying to create the .deb package i got the following error :

==
Generating package: Ubuntu/natty
Resolving build dependencies...
Unable to resolve  debhelper  dh-modaliases libqtgui4 execstack.  Please manually install and try again.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 396: debclean: not found
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buil .....

(i have attached the full log)

I know i sound like a real dumb *** ... but where to from here?

---

### Post by LinNew on 2011-07-09
Guys,

Sorry i know its not related but where can  i get drivers for my ZTE MF190 3g Modem .... i have searched but cant seem to find any .. :(

---

### Post by waynefoutz on 2011-07-09
> **LinNew said:**
> Guys,

Sorry i know its not related but where can  i get drivers for my ZTE MF190 3g Modem .... i have searched but cant seem to find any .. :(

Look in Synaptic and see if usb-modeswitch is installed. That's usually the stumbling block for 3g modems, most of them have internal memory on them, and Ubuntu picks  them up as a pen drive instead of a modem.

Also, My two cents on the video drivers. I've NEVER had any luck installing ATI's drivers manually. 9 times out of 10 the drivers Ubuntu supplies are far better. Just click on the "hardware drivers" in the menus, and let Ubuntu take care of the installation. The stock open source Radeon drivers installed by default aren't all that bad either.

---

### Post by LinNew on 2011-07-09
> **waynefoutz said:**
> Look in Synaptic and see if usb-modeswitch is installed. That's usually the stumbling block for 3g modems, most of them have internal memory on them, and Ubuntu picks  them up as a pen drive instead of a modem.

Also, My two cents on the video drivers. I've NEVER had any luck installing ATI's drivers manually. 9 times out of 10 the drivers Ubuntu supplies are far better. Just click on the "hardware drivers" in the menus, and let Ubuntu take care of the installation. The stock open source Radeon drivers installed by default aren't all that bad either.

Hi waynefoutz

Sorry, but what is Synaptic ?? When in Linux, and i check the drivers in the additional drivers, the list is empty ...

man i am felling pretty stupid at the moment :(

---

### Post by waynefoutz on 2011-07-09
Synaptic package manager. It's a more technical version of software center. 

The drivers list is empty because you aren't connected to the internet yet. 

try going here:

[http://packages.ubuntu.com/search?keywords=usb-modeswitch]("http://packages.ubuntu.com/search?keywords=usb-modeswitch")

Download usb-modeswitch and usb-modeswitch-data. Get the right one for the version you're using. If you installed the latest one, get the two packages for Natty. Make sure you get the right version, amd64 for the 64 bit, i386 for 32 bit.

That should get your 3g modem working.

Once you are online, open up a terminal and type 

```
sudo apt-get update
``` 

You'll see a bunch of updates after you do that, go ahead and install them. You will also see the video ATI driver in the "hardware drivers" application (more than likely an alert will pop up by your clock telling you it found the video card and has drivers for it.)

It would be much easier if you could plug it into a router or something. Your first tak is to get it connected to the internet, once Ubuntu is connected, it will find the video driver for you.

---

### Post by misterbiskits on 2011-07-09
Sorry the manual install isn't working out for you.  You'll need the internet in order to do this.  
The method requires you to install dependencies:
```
sudo apt-get install build-essential cdbs fakeroot dh-make [COLOR=Red]debhelper[/COLOR] debconf libstdc++6 dkms [COLOR=Red]libqtgui4[/COLOR] wget [COLOR=Red]execstack[/COLOR] libelfg0 [COLOR=Red]dh-modaliases[/COLOR]
```Since there is no internet, the libraries can't install, and you get the error:
> **LinNew said:**
> 
Unable to resolve  [COLOR=Red]debhelper  dh-modaliases libqtgui4 execstack[/COLOR].  Please manually install and try again.

Regarding the debate on the method, letting ubuntu take care of the installation has never worked for me on any of 4 different RadeonHD cards.  This is why I have had to do it manually.  I have no idea which is "better" between the open source or the ati drivers.  
If you do get the machine connected and decide to try again, it might be a good idea to apply the couple of lines of code in the "Removing Catalyst/fglrx" section before you try installing the drivers again.  

It's a good idea to keep notes (Tomboy is great for that), mine look like this (Ubuntu 10.04):
> 
CHECK FOR DRIVER
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Manual ATI Driver Installation
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

1) Install the prerequisite packages:
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0

2) Download the latest Catalyst package.
cd ~/; mkdir catalyst11.6; cd catalyst11.6/
wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-6-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-6-x86.x86_64.run)

3) Create .deb packages and install .debs
sudo sh ati-driver-installer-11-6-x86.x86_64.run --buildpkg Ubuntu/lucid
sudo dpkg -i fglrx*.deb

4) Initialize all adapters (multiple heads)
sudo aticonfig --initial -f --adapter=all

5) Force use of the new xorg.conf
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
reboot
all should be working

Also, I am sure no one thinks you are dumb, we all learned at some time or other.

---

### Post by waynefoutz on 2011-07-09
misterbiskits, why not let the guy try it the default way first? He's a beginner, one step at a time.
 Right now, he can't do much of anything until it gets it connected to the internet. Having him install proprietary ATI drivers that aren't in the repositories is not where he should be starting this project. Your machine is most likely an exception, the fglrx drivers Ubuntu installs work fine 90% of the time.

---

### Post by misterbiskits on 2011-07-09
> **waynefoutz said:**
> He's a beginner, one step at a time.

Fair enough.  Hopefully he will have better luck than I have had (on like I said 4 different ATI adapters) with Ubuntu's "activate driver" button.  I can't recommend something that had never worked for me.   I hope it works for him, but should he wind up with garbled nonsense and artifacts on his screen he knows where to look from there.
Cheers.

---

### Post by waynefoutz on 2011-07-09
> **misterbiskits said:**
> Fair enough.  Hopefully he will have better luck than I have had (on like I said 4 different ATI adapters) with Ubuntu's "activate driver" button.  I can't recommend something that had never worked for me.   I hope it works for him, but should he wind up with garbled nonsense and artifacts on his screen he knows where to look from there.
Cheers.

Sorry, didn't mean to sound scolding, but my experience has been the the exact opposite, installing the divers from ATI's catalyst site usually breaks my video. The last time I can recall having any success was back on Ubuntu 7.10 and earlier.

---

### Post by misterbiskits on 2011-07-10
No worries, you're probably right in recommending he try it the easy-click way first.

---

### Post by LinNew on 2011-07-12
> **waynefoutz said:**
> Synaptic package manager. It's a more technical version of software center. 

The drivers list is empty because you aren't connected to the internet yet. 

try going here:

[http://packages.ubuntu.com/search?keywords=usb-modeswitch]("http://packages.ubuntu.com/search?keywords=usb-modeswitch")

Download usb-modeswitch and usb-modeswitch-data. Get the right one for the version you're using. If you installed the latest one, get the two packages for Natty. Make sure you get the right version, amd64 for the 64 bit, i386 for 32 bit.

That should get your 3g modem working.

Once you are online, open up a terminal and type 

```
sudo apt-get update
``` 

You'll see a bunch of updates after you do that, go ahead and install them. You will also see the video ATI driver in the "hardware drivers" application (more than likely an alert will pop up by your clock telling you it found the video card and has drivers for it.)

It would be much easier if you could plug it into a router or something. Your first tak is to get it connected to the internet, once Ubuntu is connected, it will find the video driver for you.

Hi

Thanks for the info ... so here is what i did :

1) i downloaded usb-modeswitch and usb-modeswitch-data. Wasnt sure if there was a special way of running them so i 'double clicked' the .deb files. Both seemed to already be installed as i was taken to a window which asked if i wanted to re-install them ... which i did.

2) i then plugged in the modem and nothing happened. i was expecting it to self install like it does on Windows but nothing. So, i found the Autorun.exe file and double clicked on it to try and install and got the following in an 'Archive' window :

Archive:  /media/Cell C/AutoRun.exe
[/media/Cell C/AutoRun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/Cell C/AutoRun.exe or
          /media/Cell C/AutoRun.exe.zip, and cannot find /media/Cell C/AutoRun.exe.ZIP, period.

Should i be doing something else :( ?

Again ... sorry for being so ignorant here :(

---

### Post by mastablasta on 2011-07-12
.exe files are windows executables. linux uses .run or Ubuntu uses .deb files. .exe files wont' work on linux. uless they are run via Wine, but in case of driver that is no option.
 
if the mentioned linux files are installed it means they need to be configured or you need to somehow tell the computer where the modem is exaclty.

---

### Post by LinNew on 2011-07-12
> **mastablasta said:**
> .exe files are windows executables. linux uses .run or Ubuntu uses .deb files. .exe files wont' work on linux. uless they are run via Wine, but in case of driver that is no option.
 
if the mentioned linux files are installed it means they need to be configured or you need to somehow tell the computer where the modem is exaclty.


Thanks mastablasta, now i know what the .deb/.run files are :) How do i 'install' this modem software then, or configure Ubuntu to use it?

---

### Post by mastablasta on 2011-07-12
well if you somehow manged to install usb-modeswitch and usb-modeswitch-data (or if this was already installed) then next step would be (if modem is still not working) to see first if device gets recognised by linux.
 
plug in the modem and type in terminal and post out put here of this command:
 
```
 
lsusb

```
 
this should list all USB devices. copy and paste the result here.
 
it's too bad you don't have a way to connect to internet via wired connection. it would make it a lot easier.

---

### Post by LinNew on 2011-07-12
Thanks mastablasta

i will check this tonight when i get home. I think it does recognize the device, because when it gets plugged in, it shows the correct company icon on the desktop.

---

### Post by LinNew on 2011-07-12
[QUOTE=mastablasta;11039502]well if you somehow manged to install usb-modeswitch and usb-modeswitch-data (or if this was already installed) then next step would be (if modem is still not working) to see first if device gets recognised by linux.
 
plug in the modem and type in terminal and post out put here of this command:
 
```
 
lsusb

```
 
this should list all USB devices. copy and paste the result here.
 
it's too bad you don't have a way to connect to internet via wired connection. it would make it a lot easier.

Hi mastablaster .... ok i went into terminal and typed lsusb and got the following :

mike@mike-P4M800PRO-M:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1241:1503 Belkin Keyboard
Bus 003 Device 003: ID 0458:002e KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bb4:0c02 High Tech Computer Corp. Dream / ADP1 / G1 Phone (Debug)
Bus 001 Device 003: ID 19d2:1224 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mike@mike-P4M800PRO-M:~$ 

I dont see the modem there ... :(

I have attached some of the log files .... i hope this can help in some way.

---

### Post by LinNew on 2011-07-13
> **LinNew said:**
> [QUOTE=mastablasta;11039502]well if you somehow manged to install usb-modeswitch and usb-modeswitch-data (or if this was already installed) then next step would be (if modem is still not working) to see first if device gets recognised by linux.
 
plug in the modem and type in terminal and post out put here of this command:
 
```
 
lsusb

```
 
this should list all USB devices. copy and paste the result here.
 
it's too bad you don't have a way to connect to internet via wired connection. it would make it a lot easier.

Hi mastablaster .... ok i went into terminal and typed lsusb and got the following :

mike@mike-P4M800PRO-M:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1241:1503 Belkin Keyboard
Bus 003 Device 003: ID 0458:002e KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bb4:0c02 High Tech Computer Corp. Dream / ADP1 / G1 Phone (Debug)
Bus 001 Device 003: ID 19d2:1224 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mike@mike-P4M800PRO-M:~$ 

I dont see the modem there ... :(

I have attached some of the log files .... i hope this can help in some way.

Any advice anyone or do i have to go back to .. *shudder* ... Windows :(

---

### Post by waynefoutz on 2011-07-16
> **LinNew said:**
> Thanks mastablasta

i will check this tonight when i get home. I think it does recognize the device, because when it gets plugged in, it shows the correct company icon on the desktop.

Network-manager should take care of the rest, if it's recognized. You should see an option for "New Mobile Broadband connection" in your list of available networks, up by your clock. You just click through the wizard and tell it what carrier it connects to.

---

