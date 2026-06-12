---
title: "Using a wireless linksys WGA54G"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by LieToPurify3 on 2007-06-04
I just installed Xubuntu onto my old Thinkpad 770z.  I have this linksys adapter that is supposed to be for playstation, but it works fine as a wireless bridge on my old desktop.  I just think i need to figure out how to get a driver on here.  The computer is old, so it doesn't have an ethernet port.  I had to convert the ethernet to USB with an adapter.  Any help would be appreciated.  Thank you!

---

### Post by kevdog on 2007-06-04
Please post the output of:

lspci 
and 
lspci -n

This will tell us the actual chipset of the device you are working with.
Do you have another computer with an internet connection to download files and then transfer the files to ubuntu via usb stick???

---

### Post by LieToPurify3 on 2007-06-04
Yes, I do have another computer and a usb stick to transfer.  I found an old wireless card that you insert too.  so i'll post my answers for both of them and if its not any trouble, maybe you can tell me how to install the driver for that too.  But shouldn't i be using lsusb since the wireless bridge is plugged into a usb port?

Wireless usb Bridge : 

lspci:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)

00:02.0 CardBus bridge: Texas Instruments PCI1251A

00:02.1 CardBus bridge: Texas Instruments PCI1251A

00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)

01:00.0 VGA compatible controller: Trident Microsystems Cyber 9397DVD (rev f3)

lspci -n:
00:00.0 0600: 8086:7190 (rev 03)

00:01.0 0604: 8086:7191 (rev 03)

00:02.0 0607: 104c:ac1d

00:02.1 0607: 104c:ac1d

00:06.0 0401: 1013:6001 (rev 01)

00:07.0 0680: 8086:7110 (rev 02)

00:07.1 0101: 8086:7111 (rev 01)

00:07.2 0c03: 8086:7112 (rev 01)

00:07.3 0680: 8086:7113 (rev 02)

01:00.0 0300: 1023:939a (rev f3)

Now the USB bridge but with lsusb:
Bus 001 Device 005: ID 0506:03e8 3Com Corp. 3C19250 Ethernet [klsi]

Bus 001 Device 001: ID 0000:0000  



--------------------------
The linksys card with lspci:
lspci:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)

00:02.0 CardBus bridge: Texas Instruments PCI1251A

00:02.1 CardBus bridge: Texas Instruments PCI1251A

00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)

01:00.0 VGA compatible controller: Trident Microsystems Cyber 9397DVD (rev f3)

06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)



and with lspci -n:
00:00.0 0600: 8086:7190 (rev 03)

00:01.0 0604: 8086:7191 (rev 03)

00:02.0 0607: 104c:ac1d

00:02.1 0607: 104c:ac1d

00:06.0 0401: 1013:6001 (rev 01)

00:07.0 0680: 8086:7110 (rev 02)

00:07.1 0101: 8086:7111 (rev 01)

00:07.2 0c03: 8086:7112 (rev 01)

00:07.3 0680: 8086:7113 (rev 02)

01:00.0 0300: 1023:939a (rev f3)

06:00.0 0280: 14e4:4320 (rev 03)



Thank you so much!

---

### Post by kevdog on 2007-06-04
Sorry about that -- you were absolutely right about the lsusb thing -- Ive got to be more careful.

Ok so the chipset contained in you usb wireless device is:
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Ok -- because you have a USB wireless controller -- you will definitely need to use the ndiswrapper approach.
bcm43xx although much easier is only for pci cards.

I looked up if the card is supported on the ndiswrapper website and this is what I found:

#
Card: Linksys WMP54G v3, 54mbps

    *
      Chipset: Broadcom BCM94306
    *
      pciid: 14e4:4320
    *
      Driver: The current Linksys driver [ftp://ftp.linksys.com/pub/network/WMP54Gv4_20040415.exe](ftp://ftp.linksys.com/pub/network/WMP54Gv4_20040415.exe) does work well with Ndiswrapper 1.0rc1. Use the driver in WMP54Gv4_20040415/Drivers/WMP54Gv2/bcmwl5.inf.
    *
      Other: Debian Sarge, linux kernel 2.6.9, SMP, Ndiswrapper 1.0rc1 manual compile. WPA works with wpa_supplicant supplied with Debian (0.2.5), both broadcast and non-broadcast ssid.

#


Ok so it looks like it will work.

A couple of things.  Here is the ndiswrapper website -- please consult it because I do not have all the answers and it is very well documented between the installation section, list section, and troubleshooting section: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/)

When I used ndiswrapper for my notebook, I guess I went above and beyond and compiled ndiswrapper from svn.  If you dont know what that is, you can always download the tarball, but this still needs to be compiled.  If this doesnt work, I think ndiswrapper may be installed by default with the ubuntu installation.

One way to check is to simply type
ndiswrapper -v
on the command line.  Make sure that in the output, the version of the utils package is appropriate, based on the output, or I think you could have problems.  I did, this is the reason I needed to install ndiswrapper from svn.  If ndiswrapper is included in the installation -- I hope it was compiled with USB support -- I dont know if it was or it wasnt.  I know when I compiled from source there was an option when using the make command.  I guess you could always proceed, and if something doesnt work, you may be forced to compile.

If you choose to compile from either the tarball or svn package you will need the:
build-essentials package, g++ libraries, and possibly the svn package.

Please either verify you have the "appropriate ndiswrapper package" and download the driver as referenced above or in the list section on the ndiswrapper website. 

Write back if you have any questions.

---

### Post by LieToPurify3 on 2007-06-04
Ok, so I typed ndiswrapper -v into the terminal and it said that it couldn't find any versions of it.  So I went to the link you gave me and downloaded it onto my usb drive and then transferred it to my laptop running xubuntu.  I also transferred the linksys driver and extracted the ndiswrapper folder.  I'm not sure what to do now.   I'm pretty much completely new to linux/ubuntu.  I really appreciate the help!

PS i also have a card i just found that i think has a "3Com" chipset.  any idea what that is?  If you have time, can you explain what exactly you're doing here so that I can learn and not have to ask next time?  I'm running linux because I want to learn more about programming and networking.

Also, where do I see what wireless networks my laptop is picking up on and choose one of them?

---

### Post by kevdog on 2007-06-05
Background - ndiswrapper is a program to my knowledge that makes windows drivers work in linux.  

In order to install your network card, you basically have to install a card driver (just like in windows).

At this point, you have  (I think) downloaded the source files for ndiswrapper, and the windows driver for your card.  

We could run into some problems at this point because I dont know if your installation has the necessary g++ (c++) libraries to install the ndiswrapper package into an executable file.

At the command line, go into the ndiswrapper directory (where ever you extracted it), and then just type make.
If you get a bunch of errors then we have a problem -- ie compilation from source would nearly be impossible (not totally).

In this case you might want to download a pre-compiled ndiswrapper executable.  Ubuntu (like debian), distributes executables in packages known as .deb files.

Just to ensure you dont have ndiswrapper installed
sudo updatedb
locate ndiswrapper

If nothing shows up (other than in the directories where you unzipped the tar ball) you without a doubt do not have ndiswrapper installed on your system (I thought it was installed by default - but could be wrong).

***Warning Ive never done this step but found it on other posts
If you installed ubuntu from desktop cd or alternate cd, I think the ndiswrapper package, along with build-essentials package may be on the cd.  In order to install packages from cd, insert cd-rom then at command line:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper
#Following line optional
sudo aptitude install build-essential

I believe after doing the above, ndiswrapper should be installed on the system.  Again 
ndiswrapper -v
to see if this works.

Hopefully you get this far -- the rest is not as bad!

---

### Post by LieToPurify3 on 2007-06-05
I'm not sure I completely understand the meaning of what I'm seeing in the terminal, but I'm sure I'll learn.  When i typed ndiswrapper -v, it was fine for a while, and then gave me a bunch of errors and then asked for my password and finally gave me one last line that did not include any errors.

---

### Post by kevdog on 2007-06-05
Something isnt right.  Did you install from CD??

When I type ndiswrapper -v I get:
utils version: '1.9' utils version needed by module: '1.9'
module details:
filename: /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version: 1.45
vermagic: 2.6.20-16-generic SMP mod_unload 586

---

### Post by LieToPurify3 on 2007-06-05
When i tried before, i noticed the CD wans't spinning. I'm trying again now and it is spinning. Hopefully it works now.  Do you have aim or anything?

---

### Post by LieToPurify3 on 2007-06-05
after I type "sudo apt-cdrom add", it tells me it is mounting the disk, reading it, then it says feisty main restricted, and unmounts the cd-rom.  It then tells me to repeat this process for the rest of the cd's in my set.

---

### Post by LieToPurify3 on 2007-06-05
Actually, when you gave me the link to download ndiswrapper, I only knew how to extract it on my desktop.  So it never actually installed anything.  What do I do after I extract it?  I tried running the only file I could in the folder and nothing happened.

---

### Post by kevdog on 2007-06-05
Do you have the alternate or desktop CD??   Again Ive never installed from CD, so Im a little out in the dark here why its not working, Ill have to google around or check in the forums on how to install packages from ubuntu cd.

As far as the tarball extraction, this only extracted the source files -- which then need to be compiled to executables.  You need the build-essential package to compile -- but again this is on the damn CD.

---

### Post by kevdog on 2007-06-05
Here is a link that might help you.  
[http://monkeyblog.org/ubuntu/installing/#add_cd](http://monkeyblog.org/ubuntu/installing/#add_cd)

It uses Synaptic (a GUI based program) to add CD as a program repository.  Then do a search for ndiswrapper. Hopefully you can install package.

---

### Post by kevdog on 2007-06-05
Yet another method, download the utils and common packages from here: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=feisty&release=all)

Transfer to ubuntu computer.

At command line:
gdebi-gtk

Use this program to install the common then utils package.  This program will check for dependencies.  If it says unmet dependencies there is a problem.

---

### Post by kevdog on 2007-06-05
I'll catch up with you tomorrow if you need help -- going to be for now!

---

### Post by LieToPurify3 on 2007-06-06
I tried downloading that file and bringing it to my laptop.  I extracted it and then typed gdebi-gtk in the terminal, and one of the lines it gave me said "GtkWarning: gdk_window_set_cursor: assertion 'GDK_IS_WINDOW (window)' failed
self.window_main.set_sensitive(False)
Then, it opened a window titled "Package Installer", but everything except "File" and "Help" was greyed out and there was nothing I could select under the Description tab even if it wasn't greyed out.

---

### Post by LieToPurify3 on 2007-06-06
Right now, I'm trying that other link you gave me that uses Synaptic to install ndiswraper.  I searched ndiswrapper and it came up with ndiswrapper-common, and ndiswrapper-utils-1.9.  Ill try to install both right now just in case. If you want, I can pm you my email

---

### Post by kevdog on 2007-06-06
Although I dont mind being emailed, you will find out the purpose of this forum is to document problems and resolutions for others.  Ive only been using ubuntu for about 3 months and have found the info presented in these forums to be invaluable.  Its great sometimes to see the evolution of problems that are exactly the same as yours.

---

### Post by LieToPurify3 on 2007-06-06
Yeah, I realized that right after I sent that.  Anyway, I tried the other link using the Synaptic program, and both installed fine.  But I was lost after that.  Do you think this could just be a problem with me having Xubuntu?

---

### Post by kevdog on 2007-06-06
I havent used Xbuntu a ton, so I cant speak to its features, but ndiswrapper should work on all 3 version of ubuntu (K,U,X).  

So I assmue you now have the ndiswrapper executable installed??

What is the output of: ndiswrapper -v??

---

### Post by LieToPurify3 on 2007-06-06
for some reason it gives me: 
utils Error: no version specified!
driver version:            1.38
vermagic:          2.6.10-15-generic SMP mod_unload 586

---

### Post by kevdog on 2007-06-06
I kept getting the same error when I downloaded from the repositories -- hence the reason I eventually compiled from source.

Compiling from source is very easy -- and it at least sounds like you have an internet connection somewhere (or where else did you get the ndiswrapper-common package from). 

Just to add a little complexity to the matter to compile from source you need 3 things or packages:
1. The ndiswrapper tarball -- I believe you have this
2. The build-essential package
3. Update linux headers -- which is yet another package.

Presuming you can download on the computer you are trying to get the wireless working on:

Modify the sources.list file to allow for the downloading of additional required utilities...

```


sudo nano /etc/apt/sources.list

```

...by uncommenting (removing the # next to) the following entries in the sources.list file...

```

deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe

```

...then saving the file.

Then dowload and install build-essentials package
```

sudo aptitude update 
sudo aptitude install build-essential

```

For the headers:

Identify your kernel version, using...
```

uname -r

```

...which should output something similar to...

```

2.6.17-10-generic

```

...and update your linux headers, using the output from uname -r, as indicated:

```

sudo aptitude install linux-headers-2.6.17-10-generic 
sudo ln -s /usr/src/linux-2.6.17-10-generic /lib/modules/2.6.17-10-generic/build

```

If you dont have an internet connection, the build-essential package can be downloaded here:
[http://packages.debian.org/stable/devel/build-essential](http://packages.debian.org/stable/devel/build-essential)

Ill look to see if I can find the header package somewhere!

---

### Post by LieToPurify3 on 2007-06-06
I am using a Macbook to post in these forums.  The only pc I am running linux on is my other laptop, which we are trying to get an internet connection running on.  I have the WGA54G which is ethernet but converted to USB to use on the laptop since it doesnt have an ethernet port, and I also have the WPC54GS card.  BOth of which are linksys, but neither of which will give me a connection to the internet due to the driver problem we're having.  So will what you just said work?

---

### Post by kevdog on 2007-06-06
My linux notebook runs the wpc54gs card.  Look you have this card there is a much easier way to get it going.  The bcm43xx cutter drivers.  Basically you download to files from the internet, install them and then everything works.  The only downside with the bcm drivers is that the max speed of your card is going to be 11 Mb/s rather than 54 Mb/s.  I just recently found this out, hence the reason for the switch over to ndiswrapper.  But one thing it did give me on the laptop was a working internet connection to download everything first, and then install the ndiswrapper files.  

Let me know what you want to do.  I really like Ubuntu but getting a working internet connection via ndiswrapper is a pain in a$$.  Why the package designers didnt think of this, I dont have a clue.  All the instructions tell you to download certain files, and then install the drivers, etc....  I guess if I could download all the packages I wouldnt have to set up an internet connection...because it would be already working.

One last thing I thought of since we last spoke, is that I have compiled the ndiswrapper package from svn.  (The process for installing from source files, is first to compile the sources, then install them.  If our kernels our the same version, I could simply zip up the compiled files, attach them to a future post, whereby all you would have to do is unzip, and then install them.  I guess this would save a lot of headache!!!

---

### Post by kevdog on 2007-06-06
To determine your kernel number:

uname -r

---

### Post by LieToPurify3 on 2007-06-06
my kernel number is: 
2.6.20-15-generic

---

### Post by kevdog on 2007-06-06
Ok, my kernel is 2.6.20-16-generic

All is not lost however, Im going to see how I can boot back into the previous kernel and then compile against these headers.

Give me about an hour or two, I should have everything compiled for you.

---

### Post by LieToPurify3 on 2007-06-06
thanks so much.  do you know if the airport card for a mac is supported? will that be a pain in the *** too?

---

### Post by kevdog on 2007-06-06
Just one question before I go off on a wild goose chase.  Just to confirm your computer ->USB port->usb/ethernet adapter->wireless gaming console.

I relooked at the usb/ethernet adapter you listed -- at least the chipset 3Com Corp. 3C19250 Ethernet.

It seems that drivers for this device should be built in -- ie plug and play or hotplug ready.  

[http://linux-hotplug.sourceforge.net/kernel/kernel.html](http://linux-hotplug.sourceforge.net/kernel/kernel.html)



As far as your gaming console, the linksys website states it doesnt need any drivers.


If your setup is what I think it is, what happens when you hook everything up and then boot into xbuntu??

---

### Post by LieToPurify3 on 2007-06-06
Lets just forget about the "gaming" adapter, since I dont see a way of installing it since it is meant to be plugged in via ethernet which would need no drivers, and i have it plugged in wiht a USB adapter.  The WPC54GS card seems to be our best bet.  I also have this 3Com Lan PC Card, but I'm not really sure what that is.  The WPC54GS card has a Broadcom Corporation BCM4306 chipset.

---

### Post by kevdog on 2007-06-06
Ok -- I hope this works
ndiswrapper 1.46 compiled against linux kernel 2.6.20-15-generic headers.

Please make sure that you uninstall the ndiswrapper packages that you earlier installed.

Extract with
tar -zxvf ndiswrapper-1.46.tar.gz

Go into extracted directory, then:
sudo make install

Hopefully the package will be installed.

Verify the installation

ndiswrapper -v

Download site:
[ftp://gohilton.com](ftp://gohilton.com)
user:anonymous

---

### Post by LieToPurify3 on 2007-06-07
Ok, I used synaptic package manager to remove ndiswrapper, downloaded the file you gave me and brought it to my laptop on my usb drive, and then installed it.  When I verify the installation, I get:
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename: /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version: 1.38
vermagic: 2.6.20-15-generic SMP mod_unload 586

You may need to upgrade driver and/or utils to latest versions available at [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

---

### Post by kevdog on 2007-06-07
Couple things -- because I thought the utils version was included in the install

What if you type

/usr/sbin/ndiswrapper -v

What is the output??

I attempted to just proceed at this point.  Do you have the driver for the wireless card??? Visit the ndiswrapper site,goto documentation, find list, and then search for your card.  Download the driver that they provide for your card.  If unsuccessful, since I have the same card, I will upload the driver to the ftp site so you can download it.

---

### Post by LieToPurify3 on 2007-06-07
When I input that command, it gives me the same output that ndiswrapper -v gave me.  I downloaded the driver for the card and put it on my laptop.  How do I install it?

---

### Post by kevdog on 2007-06-07
Great -- hopefully we are moving along :)

I believe your driver package should have a .inf file and a .sys file (among other files).  Go into the directoy where these two files are located. They must be together in the same directory.

Type
sudo ndiswrapper -i filename.inf 

(Again substitute the filename for whatever you have)

This copies all necessary files to /etc/ndiswrapper and creates the config files for your card.  Verify by running

ndiswrapper -l
Should say something like:
lsbcmnds : driver installed
        device (14E4:4320) present

Now we need to load module into kernel
sudo depmod -a

Make sure there are no errors -- if there are, there is a problem.  Then

sudo modprobe ndiswrapper
If you get no error the driver should be loaded.

Ok, nearly there.  By default ndiswrapper sets up a wlan0 interface.  This may or may not be the interface name of your card.  If believe you can find out what your system calls the card by typing:
ifconfig
It should list something like eth0 or wlan0, among other interfaces.   If it is wlan0, great.  If not, we need to change a few things.

First issue command:
sudo ndiswrapper -m

There are two files (if your interface is not named wlan0), that you need to edit as root.
/etc/network/interfaces --> Change, for example, everywhere it says eth0 to wlan0 (assuming eth0 is the interface name)
/etc/iftab -> Change, for example, eth0 to wlan0 (assuming eth0 is the interface name).

That should be it in a nutshell.  Reboot computer and let me know what happens!

---

### Post by LieToPurify3 on 2007-06-08
You said I should have a .exe file and a .inf file.  THe files I have are SETUP.EXE, and lsbcmnds.inf.  So I should type "sudo ndiswrapper -i SETUP.EXE"?

---

### Post by LieToPurify3 on 2007-06-10
?

---

### Post by kevdog on 2007-06-10
You should have a .sys and .inf file.  

Hmmm.

Can you point me either to the link or name of your driver file??

---

### Post by LieToPurify3 on 2007-06-12
[http://network.free-driver-download.com/Linksys/14888/Linksys-WPC54GS-Wireless-G-Notebook-Adapter-with-SpeedBooster-v1.0-Driver-3.50.21.html](http://network.free-driver-download.com/Linksys/14888/Linksys-WPC54GS-Wireless-G-Notebook-Adapter-with-SpeedBooster-v1.0-Driver-3.50.21.html)

---

### Post by kevdog on 2007-06-13
I found a set of drivers for you, with the WPC54GS card.  I need to know what revision the chipset is.

Again with the card plugged in what is 
lspci
lspci -n

Thanks and sorry about delay

---

### Post by LieToPurify3 on 2007-06-13
No problem, I've been away from my computer for a day or two also.  
lspci : 00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1251A
00:02.1 CardBus bridge: Texas Instruments PCI1251A
00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: Trident Microsystems Cyber 9397DVD (rev f3)
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

lspci -n:  00:00.0 0600: 8086:7190 (rev 03)
00:01.0 0604: 8086:7191 (rev 03)
00:02.0 0607: 104c:ac1d
00:02.1 0607: 104c:ac1d
00:06.0 0401: 1013:6001 (rev 01)
00:07.0 0680: 8086:7110 (rev 02)
00:07.1 0101: 8086:7111 (rev 01)
00:07.2 0c03: 8086:7112 (rev 01)
00:07.3 0680: 8086:7113 (rev 02)
01:00.0 0300: 1023:939a (rev f3)
02:00.0 0280: 14e4:4320 (rev 03)

---

### Post by LieToPurify3 on 2007-06-14
.

---

### Post by kevdog on 2007-06-14
I need to get back to you later.

Can you again just tell me the name and model of the linksys card please!

---

### Post by LieToPurify3 on 2007-06-14
You said it was the same as yours.  WPC54GS.  Take your time.  Thanks for helping :D

---

### Post by kevdog on 2007-06-14
Ive reviewed the post and first of all, even though I tried to give you a compiled version of ndiswrapper, I dont think it is going to work.

Lets start at the beginning and do the following, it shouldnt take too long.
1. Stick you Ubuntu CD in the disc drive
2. Type the following:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

3. Lets redownload the ndiswrapper tarball at sourceforge (you are going to have to do this on your mac and transfer to usb stick): [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.47.tar.gz?modtime=1181699252&big_mirror=0](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.47.tar.gz?modtime=1181699252&big_mirror=0)

4. Ok lets set up some things for compilation so we are on the same page.  Working from command line:
cd ~
mkdir temp
cd temp
mkdir ndiswrapper

Copy the tarball from USB stick to ~/temp/ndiswrapper
cd ndiswraper

There should be the ndiswrapper-1.47.tar.gz file in this directory
Lets extract the tarball
tar -zxvf ndiswrapper-version.tar.gz

Ok change to the directory containing the sources
cd ndiswrapper-1.47

5. Lets compile the sources
make distclean
make

6. Lets now install the program
sudo make install

Lets check to make sure what we did is OK:
ndiswrapper -v

Please post output.

Hopefully if everything worked the above should have taken 5 minutes or less.

---

### Post by cablejimmy on 2007-08-03
If you have it plugged into an ethernet port, all you have to do is
```
sudo dhclient
```
Type in your password, then it works perfectly.

---

### Post by cablejimmy on 2007-08-03
I mean with a WGA54G.

---

