---
title: "NDISwrapper and WiFi WPC 11 Ver 4 with Ububtu 7.04"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by sundial on 2007-06-14
I have a Fujitsu Lifebook laptop model E 6550 that ran Win2k and under Windows had an excellent connection to my WiFi access point using a Linksys WPC 11V4 PCMCIA card.  Over the last few weeks I installed several different versions of Linux on the system.  These include Ubuntu, Kubuntu both 6.06 and 7.04, Sabayon, and SUSE 10.02 in an attempt to see which works best for me.  I have settled on the Ubuntu 7.04 and that is now on the system.  I should add that each install was done on a disk that had been formatted fully using the installer for that version of Linux.  I did in fact use Linux Tools to cleaned the disk between the Sabayon install and the current attempts with Ubuntu..  

So what is the problem?  I cannot get the Wifi card to work on any of the four Ubuntu installs that I tried.  l.  I have tried the following cards;  Linksys WPC 11 v4,  and V3 (this should work out of the box) and a Lucent Orinco Gold card (16bit).  No card seems to work with Linux.  The WPC 11 v3, at least gets a flashing light indicating it is seeing the access point.  I have explored these wifi card problems and issues on the Networking Forum and followed the directions several were kind enough to give me all to no avail.

I tried to un-blacklist the native driver for the V4 card.  It seems to do nothing.  I tried to install the NDISwrapper and here I am stymied.  I have copied the directions and tried to follow them to no avail.  If I click on the files it opens a window for  “the Package Installer”, and I get a message saying Error; (Dependency is not satisfable: ndiswrapper common).  

If I try to use Synaptic to try to install I cannot get it to locate the files on the desktop.  I should add that the un-zipped files for NDISwrapper (1.47) are sitting on my desktop in a folder marked NDISWrapper 1.47.  If I try to get Synaptic to find the files they come up grayed out and if I try to get Synaptic to use the CD where I also have the files (tar) , it will not recognize the CD as a “repository”.

On the desktop are currently the following; folder titled; Ndiswrapper 1.47 (un-zipped files), A box like icon for ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb, and a second box icon with ndis5x-8180(173).zip.  This last box contains the .sys and .inf files for the driver for my card.

I am not a Newbie with the PC and windows, but I am a newbie with Linux.  I cannot understand most of the Linux jargon about using the terminal window to move around and to “Make and Install” programs.  I cannot even get the terminal window to complete a cd command to move to a different directory.

Can someone with experience walk me through this to help me get my NDISwrapper installed and install the .sys and .inf files for the V4 card that are also sitting on my desktop?  The kind of help I need is the exact code for executing commands to do the install.  Please, if you offer help, do not tell me to use “Make” without showing me the full command line.

I suspect that if I can work through getting my ndiswrapper set up, others reading this forum will also benefit from the specific instructions.

---

### Post by AAM on 2007-06-14
hell man, you don't need to run 'make' commands to get this done. That's not what the terminal is for with what you want to do!

get the ndiswrapper-common and ndiswrapper-utils-1.9 DEB files onto your desktop. Right click and on the individually and select the Gdebi installer option. That will get those installed. (you might find them on the installation CD also, put the disk in and see if it asks you if you want to open Synaptic!)

Copy the INF and SYS files into a home directory (not a zip file).

now you are ready to execute the commands and follow the instructions found previously. You are actually stuck BEFORE those instructions become relevant by the sounds of it. If the DEB thing doesn't work, get connect to an ethernet cable and do the Synaptic install that way.

I'll look back later to see if you need more help.

---

### Post by sundial on 2007-06-14
> **AAM said:**
> hell man, you don't need to run 'make' commands to get this done. That's not what the terminal is for with what you want to do!

get the ndiswrapper-common and ndiswrapper-utils-1.9 DEB files onto your desktop. Right click and on the individually and select the Gdebi installer option. That will get those installed. (you might find them on the installation CD also, put the disk in and see if it asks you if you want to open Synaptic!)

Copy the INF and SYS files into a home directory (not a zip file).

now you are ready to execute the commands and follow the instructions found previously. You are actually stuck BEFORE those instructions become relevant by the sounds of it. If the DEB thing doesn't work, get connect to an ethernet cable and do the Synaptic install that way.

I'll look back later to see if you need more help.

First let me thank you for getting back to me.  

It took a while to get ready to try what you suggested.  I did a new clean install of 7.04.  When I tried to click (rt) to open the utils package with Gdebi installer, i get the same response that the Dependency is not satisfiable.

All of the NDIS files and the utils (boxes) are now sitting on the desktop and are un-compressed.  What am I doing wrong?

---

### Post by kevdog on 2007-06-14
Dont fret -- everyone goes through this so its no big deal.  We will have you up and running shortly

First, open a terminal of console to type in commands from command line.  I know you want to avoid this, but its the only way I know how.  You are going to have to compile ndiswrapper from source, but you need gcc installed prior to doing this.

These are the first steps: If you can do these, then we will keep going from here.

First uninstall ndiswrapper, its not working anyway.

You can get the build-essentials package from the ubuntu cd (if you choose). Place CD in drive.
At command line:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

With build essential tools involved you are now ready to compile the sources.
You need to cd into the directory where you unzipped/untarred the sources.  Likely a command something like this:
cd ~/Desktop/ndiswrapper

then just type 
make distclean
make

We will install later, not too many commands right now

---

### Post by sundial on 2007-06-14
> **kevdog said:**
> Dont fret -- everyone goes through this so its no big deal.  We will have you up and running shortly

First, open a terminal of console to type in commands from command line.  I know you want to avoid this, but its the only way I know how.  You are going to have to compile ndiswrapper from source, but you need gcc installed prior to doing this.

These are the first steps: If you can do these, then we will keep going from here.

First uninstall ndiswrapper, its not working anyway.

You can get the build-essentials package from the ubuntu cd (if you choose). Place CD in drive.
At command line:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

With build essential tools involved you are now ready to compile the sources.
You need to cd into the directory where you unzipped/untarred the sources.  Likely a command something like this:
cd ~/Desktop/ndiswrapper

then just type 
make distclean
make

We will install later, not too many commands right now
Ah-Ha, it is doing something now.  

OK, what next?

---

### Post by kevdog on 2007-06-14
Ok great, 

First -- dont mean to be repetitive but make sure the ndiswrapper.deb files you installed previously (if you did) are uninstalled (Very important!)

Assuming the above

sudo make install

Ok ndiswrapper program is installed.

Verify installation with:
ndiswrapper -v

Shoot me the output in the next response!

Now lets move onto the driver.  Where did you get your driver??? if it wasnt from the ndiswrapper website, its probably not going to work with ndiswrapper.  If you got it from somewhere else then attach the results of the following:
lspci
lspci -n

Ok great.

---

### Post by sundial on 2007-06-14
> **kevdog said:**
> Ok great, 

First -- dont mean to be repetitive but make sure the ndiswrapper.deb files you installed previously (if you did) are uninstalled (Very important!)

Assuming the above

sudo make install

Ok ndiswrapper program is installed.

Verify installation with:
ndiswrapper -v

Shoot me the output in the next response!

Now lets move onto the driver.  Where did you get your driver??? if it wasnt from the ndiswrapper website, its probably not going to work with ndiswrapper.  If you got it from somewhere else then attach the results of the following:
lspci
lspci -n

Ok great.

First, the output of the make Install
When I check using the ndiswrapper -v I get the following:
file name               /lib/modules/2.6, 20-15 generic/misc/ndiswrapper.kp

If I recall correctly, i got the drives form a place I was sent to on the ndiswrapper site.  The driver is the one for my card. it is the rtl8180

Right now the sys and inf along with a text file are sitting on the desktop.

BTW, after we finish, I assume its ok to erase all these things form the desk top?
When should Iinsert my PCMCIA card?

---

### Post by sundial on 2007-06-14
KevDog

I should have mentioned that the laptop is not on line.  I am communicating with you via my desk unit, a PC running Win XP.  Consequently, i cannot extract the screens on the laptop and send them to you.
Sundial

---

### Post by kevdog on 2007-06-14
Ok

Im going to assume ndiswrapper is ok because you didnt provide the full output.  If you got the drivers from the ndiswrapper website then Im going to assume that is ok too!

You can delete everything, however I would keep the drivers in a separate folder -- its saves one step in case something goes wrong in the future.

Ok at command line:
go into desktop directory
cd ~/Desktop
sudo nidswrapper ****.inf  <----Substitude name of inf file.  Make sure .sys file is in same directory

Check if the driver was "wrapped" inside of ndiswapper:
ndiswrapper -l   

Should only have one driver listed, if there are two we have problems

Ok now lets insert ndiswrapper/drver combination into kernel:
sudo depmod -a 

Make sure there are no errors, then

sudo modprobe ndiswrapper

You can check if it was installed by using: dmesg and see if you get message about driver loaded or something similar

Issue command for ndiswrapper to start at startup:
sudo ndiswrapper -m

Ok by default ndiswrapper makes an interface name for your card named wlan0.  Its very likely right now your OS refers to your wireless card as eth0 or eth1.

What I would do at this time would be to power down computer, stick wireless card in, then restart.

Shoot me the output of the following:
ifconfig
cat /etc/iftab

We are 1 step away from everything working (on an unencrypted router connection  -- no wpa or wep)

---

### Post by sundial on 2007-06-14
> **kevdog said:**
> Ok

Im going to assume ndiswrapper is ok because you didnt provide the full output.  If you got the drivers from the ndiswrapper website then Im going to assume that is ok too!

You can delete everything, however I would keep the drivers in a separate folder -- its saves one step in case something goes wrong in the future.

Ok at command line:
go into desktop directory
cd ~/Desktop
sudo nidswrapper ****.inf  <----Substitude name of inf file.  Make sure .sys file is in same directory

Check if the driver was "wrapped" inside of ndiswapper:
ndiswrapper -l   

Should only have one driver listed, if there are two we have problems

Ok now lets insert ndiswrapper/drver combination into kernel:
sudo depmod -a 

Make sure there are no errors, then

sudo modprobe ndiswrapper

You can check if it was installed by using: dmesg and see if you get message about driver loaded or something similar

Issue command for ndiswrapper to start at startup:
sudo ndiswrapper -m

Ok by default ndiswrapper makes an interface name for your card named wlan0.  Its very likely right now your OS refers to your wireless card as eth0 or eth1.

What I would do at this time would be to power down computer, stick wireless card in, then restart.

Shoot me the output of the following:
ifconfig
cat /etc/iftab

We are 1 step away from everything working (on an unencrypted router connection  -- no wpa or wep)

ifconfig results:
lo link encap:Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: :: 1/128 scope host
UPLOOPBACK RUNNING MTU:16436  Metric:1
RX packets:2 errors:0 dropped:0 overrun:0 frame:0
TX packets:2 errors:0 dropped:0 overrun:0 carrier:0
collisions:0 txquelen:0
RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

results cat /etc/iftab
#  This file assigns persistent names to network interfaces
#  See iftab(5) for syntax

Thats it for these two commands.

Is it Ok?

---

### Post by sundial on 2007-06-14
> **sundial said:**
> ifconfig results:
lo link encap:Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: :: 1/128 scope host
UPLOOPBACK RUNNING MTU:16436  Metric:1
RX packets:2 errors:0 dropped:0 overrun:0 frame:0
TX packets:2 errors:0 dropped:0 overrun:0 carrier:0
collisions:0 txquelen:0
RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

results cat /etc/iftab
#  This file assigns persistent names to network interfaces
#  See iftab(5) for syntax

Thats it for these two commands.

Is it Ok?

I should have added the following
I did not get a response to the command "ndiswrapper -|  what returned was a ">"

I am not sure if the driver loaded.

---

### Post by kevdog on 2007-06-14
A little bit confused at this point...

ndiswrapper -l  (as in list)

Driver should be mentioned when you do this.

What is result of:
cat /etc/network/interfaces

---

### Post by sundial on 2007-06-14
> **kevdog said:**
> A little bit confused at this point...

ndiswrapper -l  (as in list)

Driver should be mentioned when you do this.

What is result of:
cat /etc/network/interfaces

I mis understood the command when i do the ndiswrapper -l iget   " ls:  /etc/ndiswrapper: No such file of directory"

The result of th cat command is as shown in my earlier message.
also only the power light is on on the PCMCIA card the connection light  is off.

---

### Post by sundial on 2007-06-14
Kevdog
What time zone are you in?  I am in the Eastern US and the time is now almost 5:30 PM.  I will need to be off line for some period of time tonight but can pick this up later tonight or tomorrow.

I must thank you for the excellent help.  I have spent days trying to figure out how to set up this driver and got nowhere.  You were able to do more in a few messages that all of my other efforts over many hours and over many days.

Thanks,
Sundial

---

### Post by kevdog on 2007-06-14
Ok -- lets back up a bit.

Im assuming you performed the 
sudo make install

command while in the directory where you compiled all the sources.
Can you first post the full output -- I know there will be a lot to type but of the command:
ndiswrapper -v

Its going to be about 5 lines of output.

Im sorry but I dont think you posted your interfaces file earlier.
cat /etc/network/interfaces

We can pick this up where ever you like.  Things like this always happen.  I give you a bunch of commands, it seems like the other person is cruising along until something doesnt work.  Its likely a step was skipped and it wasnt recognized until later.

While you are at it, just run the command
sudo updatedb

We will need the output later if there are future problems.

---

### Post by sundial on 2007-06-14
> **kevdog said:**
> Ok -- lets back up a bit.

Im assuming you performed the 
sudo make install

command while in the directory where you compiled all the sources.
Can you first post the full output -- I know there will be a lot to type but of the command:
ndiswrapper -v

Its going to be about 5 lines of output.

Im sorry but I dont think you posted your interfaces file earlier.
cat /etc/network/interfaces

We can pick this up where ever you like.  Things like this always happen.  I give you a bunch of commands, it seems like the other person is cruising along until something doesnt work.  Its likely a step was skipped and it wasnt recognized until later.

While you are at it, just run the command
sudo updatedb

We will need the output later if there are future problems.

I did the updatedb and the system asked for my password then sat doing nothing for some time then gave me a open line for entering commands.  I cannot tell if it did anything.

The response to ndiswrapper is the following

utils version: 1.9 , util version needed by module: 1.9
module details
filename  /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:  1.47
vermagic:  2.6.20-15-generic SMP mod_unload 586

---

### Post by kevdog on 2007-06-14
Ok, it looks like ndiswrapper is installed and compiled correctly.

It must be a problem with the driver.

Can you point me to the link where you got the driver??

---

### Post by sundial on 2007-06-14
> **kevdog said:**
> Ok, it looks like ndiswrapper is installed and compiled correctly.

It must be a problem with the driver.

Can you point me to the link where you got the driver??

I think the driver came from here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

It is different form the driver I used.  The name of the zipped file I used was NDIS5x-8180(173) and i thought i got it from the same list on the NDISwrapper web site.

I will be off line now for a few hours.
Sundial

---

### Post by kevdog on 2007-06-14
Ok so I bet we have the wrong driver

On your computer do:

lspci

Look at the output ---  Somewhere it should describe you network card -- it should be one line. 
Can you type that line for me -- its important because if we dont have the right driver, nothing is going to work.

---

### Post by sundial on 2007-06-14
> **kevdog said:**
> Ok so I bet we have the wrong driver

On your computer do:

lspci

Look at the output ---  Somewhere it should describe you network card -- it should be one line. 
Can you type that line for me -- its important because if we dont have the right driver, nothing is going to work.

Back again

The lspci show that the PCMCIA card is a Realtek Semiconductor Co Ltd Rtl8189L 802.11b MAC (rev20)

I thought this is the same as the driver I was using.

Sundial

---

### Post by sundial on 2007-06-14
> **sundial said:**
> Back again

The lspci show that the PCMCIA card is a Realtek Semiconductor Co Ltd Rtl8189L 802.11b MAC (rev20)

I thought this is the same as the driver I was using.

Sundial

TYPO on the RTL it is RTL 8180  last digit is a 0, not 9.

---

### Post by kevdog on 2007-06-14
OK you need to help me -- you need to type the exact line including all the numbers that describe your wireless card when issuing the lspci command.

Also on the line that describes your card, it begins with a set of numbers:  Here is my exact line for an example:
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I want you to take the leading numbers, 06:00.0 in my case and then match it to the line when issuing the command lspci -n  - Here is my example:

06:00.0 0280: 14e4:4320 (rev 03)

Using my example, its the 14e4:4320 (rev 03) is what I am after.

I need to know the exact lines in your case (its a pain to type, but this is going to help us get the driver)

---

### Post by sundial on 2007-06-14
> **kevdog said:**
> OK you need to help me -- you need to type the exact line including all the numbers that describe your wireless card when issuing the lspci command.

Also on the line that describes your card, it begins with a set of numbers:  Here is my exact line for an example:
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I want you to take the leading numbers, 06:00.0 in my case and then match it to the line when issuing the command lspci -n  - Here is my example:

06:00.0 0280: 14e4:4320 (rev 03)

Using my example, its the 14e4:4320 (rev 03) is what I am after.

I need to know the exact lines in your case (its a pain to type, but this is going to help us get the driver)

The last line is the one that says anything about the PCMCIA card it reads as follows:
02:00.0 Ethernet controller: Realtek Semiconductor Co. Ltd.  RTL8180L  802.11b MAC (rev 20)

When I enter Lspci -n the line with 02:00.0 shows the following:
02:00.0 0200:  10c:8180  (rev 20)

I assume that is what you are looking for.

Sundial

---

### Post by kevdog on 2007-06-14
Ok, this is going to be a touchy -- Im not sure if there is a driver for your card -- here is what ndiswrapper states:

#
Card: Linksys WPC11 v.4

    *
      Chipset: Realtek RTL8180L
    *
      pciid: 10ec:8180 (rev 20)
    *
      Driver: Don’t use driver that ships with card. Use driver for RTL8180L for Windows XP from [http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180) (Outdated) Also [http://www.opendrivers.com/freedownload/211939/realtek-rtl8180l-wireless-driver-3.30.163.312-windows-download.html](http://www.opendrivers.com/freedownload/211939/realtek-rtl8180l-wireless-driver-3.30.163.312-windows-download.html)
    *
      Other:The Realtek driver mentioned above works only with the 16KB stack kernels. I got mine for Fedora Core 3 from Linuxant.


I have no idea if ubuntu linux kernel uses 16Kb stack.

I explored the first link -- the url had changed and this is the page -- try downloading the xp driver.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

The second link leads here -- and the driver seems to be a different version:
[http://www.opendrivers.com/freedownload/211939/realtek-rtl8180l-wireless-driver-3.30.163.312-windows-download.html](http://www.opendrivers.com/freedownload/211939/realtek-rtl8180l-wireless-driver-3.30.163.312-windows-download.html)

Lets try the first link I guess.
Instead of putting on desktop...lets cleanup installation process.  From command line:
cd ~
mkdir temp
cd temp
mkdir realtek
cd realtek

Ok unzip files into ~/temp/realtek

Wrap driver inside ndiswrapper:
ndiswrapper -i NET8180.INF

Check to see if was success
ndiswrapper -l

---

### Post by sundial on 2007-06-14
> **kevdog said:**
> Ok, this is going to be a touchy -- Im not sure if there is a driver for your card -- here is what ndiswrapper states:

#
Card: Linksys WPC11 v.4

    *
      Chipset: Realtek RTL8180L
    *
      pciid: 10ec:8180 (rev 20)
    *
      Driver: Don’t use driver that ships with card. Use driver for RTL8180L for Windows XP from [http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180) (Outdated) Also [http://www.opendrivers.com/freedownload/211939/realtek-rtl8180l-wireless-driver-3.30.163.312-windows-download.html](http://www.opendrivers.com/freedownload/211939/realtek-rtl8180l-wireless-driver-3.30.163.312-windows-download.html)
    *
      Other:The Realtek driver mentioned above works only with the 16KB stack kernels. I got mine for Fedora Core 3 from Linuxant.


 

I have no idea if ubuntu linux kernel uses 16Kb stack.

I explored the first link -- the url had changed and this is the page -- try downloading the xp driver.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

The second link leads here -- and the driver seems to be a different version:
[http://www.opendrivers.com/freedownload/211939/realtek-rtl8180l-wireless-driver-3.30.163.312-windows-download.html](http://www.opendrivers.com/freedownload/211939/realtek-rtl8180l-wireless-driver-3.30.163.312-windows-download.html)

Lets try the first link I guess.
Instead of putting on desktop...lets cleanup installation process.  From command line:
cd ~
mkdir temp
cd temp
mkdir realtek
cd realtek

Ok unzip files into ~/temp/realtek

Wrap driver inside ndiswrapper:
ndiswrapper -i NET8180.INF

Check to see if was success
ndiswrapper -l

I tried the first link and cannot find a driver.  The page lists the RTL 8180L and when i click on step 2, it cycles back to the dsame page.

I went to the second page shown in your message. Is the Linux driver useful?  I believe this is where I go the driver I used. The driver I installed is the ndis one shown on the site as the one for XP.

I am at a loss for what to do now.  

Sundial

---

### Post by kevdog on 2007-06-14
I looked at the linux driver -- its for Fedora --- so I dont think it will work for Debian disto's like Ubuntu

Try the link I gave you, in your last response just click on it.  I just did this.  It took me to a page were it listed a bunch of drivers for windows.  Across for the WinXp line, just hit go #1.

Im confused.  Because I just did this again.

---

### Post by kevdog on 2007-06-14
Try this link if desperate:

[http://download.opendrivers.com/uploaddrv/network/realtek/rtlsetup-8180(330).zip](http://download.opendrivers.com/uploaddrv/network/realtek/rtlsetup-8180(330).zip)

---

### Post by sundial on 2007-06-14
> **kevdog said:**
> I looked at the linux driver -- its for Fedora --- so I dont think it will work for Debian disto's like Ubuntu

Try the link I gave you, in your last response just click on it.  I just did this.  It took me to a page were it listed a bunch of drivers for windows.  Across for the WinXp line, just hit go #1.

Im confused.  Because I just did this again.

Kevdog

I think that is the driver I have and installed.  Either that or I am missing something.  I opened the file at the site and it matches exactly the date and size of the files I installed.

What is the RTLSETUP 8180?  The file is very large and is taking forever to download.

---

### Post by sundial on 2007-06-14
> **sundial said:**
> Kevdog

I think that is the driver I have and installed.  Either that or I am missing something.  I opened the file at the site and it matches exactly the date and size of the files I installed.

What is the RTLSETUP 8180?  The file is very large and is taking forever to download.

Kevdog
Thanks for the help today.   Its getting late here and I need to call it quits for the night.  I will be back on line tomorrow.  If you have other suggestions, please post them and I will try to carry them out.

Sundial

---

### Post by kevdog on 2007-06-15
What happens if you just try to re-install the driver you have??  I dont think ndiswrapper would have a problem even if it were the wrong driver.  I would think we would see a problem later after inserting the driver into the Linux kernel and then trying to use it to communicate with the wireless card.

Try again.
With what ever driver you have:
sudo ndiswrapper -i xxxxx.inf

Then check installation
ndiswrapper -l

---

### Post by sundial on 2007-06-15
> **kevdog said:**
> What happens if you just try to re-install the driver you have??  I dont think ndiswrapper would have a problem even if it were the wrong driver.  I would think we would see a problem later after inserting the driver into the Linux kernel and then trying to use it to communicate with the wireless card.

Try again.
With what ever driver you have:
sudo ndiswrapper -i xxxxx.inf

Then check installation
ndiswrapper -l

Kevdog
I tried to reinstall the same driver and the response was that the driver is installed.  When I did a ndiswrapper -l, the response is:  net8180 : invalid driver!

Is the driver installed or is it not?

Is there a device manager like windows where I can see what drivers are installed?

Sundial

---

### Post by kevdog on 2007-06-15
Lets just try one more thing, the driver may truly be invalid

cd /etc/ndiswraper

sudo rm -R *

Make sure then nothing is in the directory

ls

No directories of files should be listed.

Change back into the directory where the driver files are stored
cd ~/temp/drivers (for example)

Then try to reinstall driver
sudo ndiswrapper -i   ******.inf

Check with ndiswrapper -l

---

### Post by sundial on 2007-06-15
> **kevdog said:**
> Lets just try one more thing, the driver may truly be invalid

cd /etc/ndiswraper

sudo rm -R *

Make sure then nothing is in the directory

ls

No directories of files should be listed.

Change back into the directory where the driver files are stored
cd ~/temp/drivers (for example)

Then try to reinstall driver
sudo ndiswrapper -i   ******.inf

Check with ndiswrapper -l


I followed these directions and removed the 8180 form the ndis wrapper directory.  that went ok and when I did a ls, it showed that the file was gone.

I then went to install the driver again.

Here is what is got back:
install /manage windows driver for ndiswrapper

usage NDISwrapper OPTIONS
(this fololws with a list of command options for installing the first is for  -i infile)

I do not get a sense that the 8180 inf was installed.

sundial

---

### Post by kevdog on 2007-06-15
You are probably right --so we've pinned it down to a driver problem.

On my desktop are two zip files right now with possible drivers for your card.
ndis5x-8180(173).zip
rtlsetup-8180(330).zip

Do you know the name of the zip file you downloaded??

If not I can possibly email you these two zip files -- Again yesterday we were having a problem finding the correct driver file -- I suspect the one we are working with probably will not work.  Hopefully the other file will.

---

### Post by sundial on 2007-06-15
> **kevdog said:**
> You are probably right --so we've pinned it down to a driver problem.

On my desktop are two zip files right now with possible drivers for your card.
ndis5x-8180(173).zip
rtlsetup-8180(330).zip

Do you know the name of the zip file you downloaded??

If not I can possibly email you these two zip files -- Again yesterday we were having a problem finding the correct driver file -- I suspect the one we are working with probably will not work.  Hopefully the other file will.

Yes it is the ndis5x-8180(173)

---

### Post by kevdog on 2007-06-15
Ok do you have access to the second file?  I think it was from the second link from the post aways back.

---

### Post by sundial on 2007-06-15
> **kevdog said:**
> Ok do you have access to the second file?  I think it was from the second link from the post aways back.

Yes  I copied over the SYS INF and CAT files for the XP.  These are now on my desktop on the laptop system waiting for your directions on how to install them.

---

### Post by kevdog on 2007-06-15
The files contained in the (330) version at least for me are:

net8180.cat
net8180.inf
rtl8180.sys

Make sure these are on your desktop or in a folder.
Make sure that the old .inf, .cat, .sys files from the (173) version are deleted or off the desktop.

Assuming they are on your desktop:
cd ~/Desktop

ndiswrapper -i NET8180.INF

---

### Post by sundial on 2007-06-15
> **kevdog said:**
> The files contained in the (330) version at least for me are:

net8180.cat
net8180.inf
rtl8180.sys

Make sure these are on your desktop or in a folder.
Make sure that the old .inf, .cat, .sys files from the (173) version are deleted or off the desktop.

Assuming they are on your desktop:
cd ~/Desktop

ndiswrapper -i NET8180.INF

Response is couldn't create /etc/ndiswrapper/net8180: Permission denied at /usr/sbin/ndiswrapper line 188

Kevdog, I need to be off line for while.  I will likely get bac to this late afternoon today.
again thanks 

Sundial

---

### Post by kevdog on 2007-06-15
Sorry type this instead:

sudo ndiswrapper -i NET8180.INF

---

### Post by sundial on 2007-06-15
> **sundial said:**
> Response is couldn't create /etc/ndiswrapper/net8180: Permission denied at /usr/sbin/ndiswrapper line 188

Kevdog, I need to be off line for while.  I will likely get bac to this late afternoon today.
again thanks 

Sundial

I tried to do what you asked, and the following resulted;

installing net8180
couldn't open NET8180.INF; No such file or directory at /usr/sbin/ndiswrapper line 217

Is this becasue the INF file is not in the directory where NDISwrapper is located?  If so, how can I get it to see the inf file on the desktop where it is now.  Or, must I move the files to another directory?

Sundial

---

### Post by kevdog on 2007-06-15
Im really starting to run out of ideas on this one.  What I would do is to re-unzip the files into a different directory like:
~/temp/driver

or something

I would change into that directory
cd ~/temp/driver

and then run command
sudo ndiswrapper -i ***.inf

I have to say if this doesnt work, im out of ideas.  Ndiswrapper only gives two sites to get the driver from, and right now I have both packages.  If either driver package doesnt work, then I really dont know what to tell you.  Possibly type
dmesg
This is the system log, maybe it can give you some more insight.  What you might want to do, is to download another driver for a different card and see if you can install it.  If you can, it just proves that everything is OK with ndiswrapper.

---

### Post by kevdog on 2007-06-15
Im getting the feeling you are doing something really wrong.  I unzipped the ndis5x-8180(173).zip file myself.  I then tried to install the driver:

sudo ndiswrapper -i NET8180.INF

and everything worked -- as far as the installation:

lsbcmnds : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
net8180 : driver installed

Are you sure you are doing everything correctly.  I have a feeling you are missing a step.

---

### Post by sundial on 2007-06-21
> **kevdog said:**
> Im getting the feeling you are doing something really wrong.  I unzipped the ndis5x-8180(173).zip file myself.  I then tried to install the driver:

sudo ndiswrapper -i NET8180.INF

and everything worked -- as far as the installation:

lsbcmnds : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
net8180 : driver installed

Are you sure you are doing everything correctly.  I have a feeling you are missing a step.

Kevdog:

Last week I got tied up with work stuff and could not get back to you to thank your for all of the support and help you gave me.  I had a business associate who has a Unix background try to fix the problem and he to could not get the NDISwrapper and the driver working.  What we did find was that the driver was apparently in some fashion associated with the NDISwrapper, but not functional.  At any rate, i have reinstalled Ubuntu using the older 6.06 version and I will try to use the other card I have, a WPC 11 v3 card and the Wicd that some people have apparently had good luck with.  I will not be able to get to that challenge until later this week and I will post the results here once I have a chance to test it all out.  BTW, An odd thing happened after I did the new install of 6.06.  The WPC 11 v3 card showed connection  (both lights were on) then after the reboot, only the power light was on.   Could be some hardware issues in my laptop.
Thanks again, 
Sundial

---

### Post by bensor on 2007-06-21
kevdog:
another newbie here.  I am following the procedure in the following site:
[http://bnmr.triumf.ca/~zaher/Presario_2197CA/#Wireless:](http://bnmr.triumf.ca/~zaher/Presario_2197CA/#Wireless:)

everything apears to work until I get to: (My labtop is Presario 2100)  I am using ndiswrapper-1.47.tar.gz 
to:

make
make install

then hell breaks loose with errors!


also when I continue to go to 
ndiswrapper -i bcmwl5.inf

it cannot locate ndiswrapper

I really appreciate your help!

BTW I have no network connection and brought over the files using scandisk.

Ben

---

### Post by killdragon on 2007-06-21
Hi, sorry I'm late to this party. But I have the card working just by unblacklisting the driver and though
    
         other post's have learned that you need to add a extra digit to the ESSID name. 


        ex. ESSID = linksys                to  ESSID = linksysz

        this is working with out nisdwrapper.

        it is also working with WEP on.

---

### Post by triptex on 2007-06-21
I am also following this thread to get my card running, 

I am using the same card and general setup this thread was started by. 

> root@triptex-laptop:/home/triptex# ndiswrapper -l
net8180 : driver installed
        device (10EC:8180) present (alternate driver: r818x)

Here is the output from ndiswraper. as you can see I have the driver installed. The problem I have is that the card does light up but is not detected in my network connections. 

> root@triptex-laptop:/home/triptex# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I had the card running before with the linuxant driver loader. But I didnt feel like actually paying for the service ;)
I think the problem now is with my ndiswraper version. 

> root@triptex-laptop:/home/triptex# ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586 

Ill keep looking and ill upgrade my ndiswraper too. If anyone has any hints..... much appreciated.

---

### Post by bensor on 2007-06-22
OK I think I got ndiswrapper installed by:

[I]2.2.1. Feisty Fawn (7.04) and Edgy Eft (6.10)
For 7.04 Feisty Fawn 

 [http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common) 

 [http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9) 

 [http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk) 


Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order: 

  sudo dpkg -i ndiswrapper-common_*.deb

  sudo dpkg -i ndiswrapper-utils*.deb

  sudo dpkg -i --force-depends ndisgtk_*.deb

 [/I] 

But now when I try
ndiswrapper -i bcmwl5.inf
I get
*couldn't create /ect/ndiswrapper/bcmwl5:Permission denied at /usr/sbin/ndiswrapper-1.9 line 146*

What am I doing wrong?

---

### Post by kevdog on 2007-06-22
Bensor

The correct syntax of the command is 
sudo ndiswrapper -i XXXXXXX <-- Put in name of inf file here.

Triptex --
You have two problems.  I would probably uninstall your driver, something like:
sudo ndiswrapper -r net8180

or simply go to /etc/ndiswrapper  and then
sudo rm -R *

Then uninstall ndiswrapper.  I think its best for you to compile ndiswrapper from the source files.  If you dont know how to do this, go back to the beginning of this thread, its all explained.  After reinstallation, if you check
ndiswrapper -v
You should get a listing that doesnt have even a hint of an error or something that would lead you to believe there is a problem.
Then reinstall your driver -- you did this correctly.  You then need to insert ndiswrapper into the kernel.  Ndiswrapper makes a default interface name of wlan0, so you may need to modify both your /etc/iftab and /etc/network/interfaces file to reflect that you have a wlan0.  I will help you with this if you want.

---

### Post by triptex on 2007-06-22
Thanks Kevdog.... I'll be on later tonight trying to make this all work .. I'll uninstall ndiswrapper and try to re-compile it. after that works (hoping it works) ill check out the info on inserting that into the kernel.

---

### Post by kevdog on 2007-06-22
Way too many people in this thread with different problems -- hopefully I dont get confused.

Bensor
Hopefully installing ndiswrapper from repository, or deb files work for you, because I could never make it work for me.  The reason you could not compile in the first place (all those errors), is because you likely dont have the build-essential packagae installed.

If you have a working internet connection (wired) on the computer type:
sudo aptitude install build-essential

If you do not but have the installation Cd - place cd in drive then:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

You can then try reinstalling ndiswrapper from source.
If you change to the directory where the sources are located:
sudo make uninstall
make distclean
make
sudo make install

Then check if ndiswrapper is installed correctly
ndiswrapper -v
The output - should not even suggest an error or a problem.  If you even get a suggestion something is wrong -- it is!

---

### Post by triptex on 2007-06-22
> **kevdog said:**
> Way too many people in this thread with different problems -- hopefully I dont get confused.



Well to make you life easier I managed to get it all set up. I re-compiled ndiswrapper and followed the instructions in "INSTALL" ran "modeprobe ndiswrapper" and Im connected right now.

Thanks.

---

### Post by Zeke46 on 2007-06-24
Never mind, I found the Wireless Windows Driver Application, and used the website [here]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") to do it.  It works now!!

---

### Post by bensor on 2007-06-24
> **kevdog said:**
> Way too many people in this thread with different problems -- hopefully I dont get confused.

Bensor
Hopefully installing ndiswrapper from repository, or deb files work for you, because I could never make it work for me.  The reason you could not compile in the first place (all those errors), is because you likely dont have the build-essential packagae installed.

If you have a working internet connection (wired) on the computer type:
sudo aptitude install build-essential

If you do not but have the installation Cd - place cd in drive then:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

You can then try reinstalling ndiswrapper from source.
If you change to the directory where the sources are located:
sudo make uninstall
make distclean
make
sudo make install

Then check if ndiswrapper is installed correctly
ndiswrapper -v
The output - should not even suggest an error or a problem.  If you even get a suggestion something is wrong -- it is!

Thanks so much kevdog...
It appeas that you are right on.. since I can't get to work. 

So I tried what you suggested and after I:
sudo apt-cdrom add
sudo aptitude update

I get Err [http://security.ubuntu.com](http://security.ubuntu.com) fiesty....

I am trying to make a new disk from:
carrol.cac.psu.edu
I have a feeling that the orginal disk might have some problems?
but thanks for all your advice..
since I was about to give up after trying the same thing ove and over.

Hopefully if i get it to work it''l be worth it!

---

