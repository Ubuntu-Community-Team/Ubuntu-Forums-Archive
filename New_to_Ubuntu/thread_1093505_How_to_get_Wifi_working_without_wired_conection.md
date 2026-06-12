---
title: "How to get Wifi working without wired conection?"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by isendel123 on 2009-03-11
Hi everyone. I've been searching for 2 days now with no luck at all the different things i have tried. I have had to uninstall and install again about 30 times already lol. My question is:
How do I get my wifi working without a wired connection?

-I have UBUNTU 8.04 installed and WindowsXP as well (same laptop).
-I only have 1 pc and it's the only one that has internet connection (only through windows).
-I have a Pendrive in case I need to download anything from the web and then install it in UBUNTU after rebooting into it.
-I DO NOT have wired connection (ethernet cable) to internet only WIFI so i won't be able to input any of the commands that try downloading things automatically into UBUNTU system.
-I have a Broadcom WLAN 1390 card from DELL 1720 laptop which uses BCMWL5 driver.

I'd really love to see what UBUNTU has to offer but there is no way I can do so if my WIFI won't work since every update has to be done through the internet and i have no access from UBUNTU.

---

### Post by RJ12 on 2009-03-11
I dont know if this can properly answer your question as I am a begginer in Ubuntu to. The way I have my setup is a virtual machine. I use virtualbox and my main connetion for my windows xp is also wireless and it works perfectly if your willing to reinstall ubuntu one last time this is perfect unless you have bad hardware but I have 700 something mb of RAM and it works fine.

---

### Post by lindsay7 on 2009-03-11
The way I understand you is your laptop his one hard drive, you have windows and Ubuntu installed and they will both bootup. You can connect to the internet with windows with your wireless card but you can not connect to the internet with Ubuntu with your wireless card, and that is your problem. Correct?\

If that is it, here is a link to get you going,  [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6869313](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6869313)

---

### Post by KIAaze on 2009-03-11
I found 2 tutorials for your wireless card which seem pretty similar:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

Since you only have internet under windows, here's what you'll have to do instead of using apt-get:
[LIST]
[*]Open synaptic 
[*]Click on File->Generate package download script 
[*]Save the script on the USB key
[*]Reboot into Windows and open the script with a text editor
[*]Download all the .deb packages to your USB key using the links from the script.
[*]Reboot into Ubuntu
[*]Open synaptic and click on File->Add downloaded packages
[/LIST]
Adapted from: [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

Note: While you're in Windows downloading the packages, don't forget to also download the driver as indicated in the tutorials! ;)
Here's the link for the driver: [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)

@RJ12:
Please provide support through the forums instead of by e-mail.
This will allow other users to profit from this help as well.

@isendel123
Avoid getting support per e-mail. I don't want to question RJ12's honesty, but getting public support through the forums reduces the risks of being given [malicious commands]("http://ubuntuforums.org/announcement.php?f=326") by "evil" users since others will notice them and warn you as well as report those users to the moderators.
And as said previously, other users can profit from it. :)

---

### Post by isendel123 on 2009-03-11
HI again. Geez thanks so much guys for all the help but unfortunatley some of the suggestions won't work for me.

Lindsay thx very much but the site that you suggested ([http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6869313](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6869313)) says this: 
"EDIT: BTW, This method requires you to be plugged into a network cable. Once everything gets installed, your good to go." 
So it won't apply to me since I have no wired connection. I cannot Run update manager (System/Administration/Update Manager) cuz it won't update anything without a connection.

KIAaze so far the information you have given me seems to be the most helpful. I had already read both of those tutorials b4 but I told my self that it would not help since they both assumed there was physical access to the router or a wired connection. But you also gave me an alternative of using apt-get commands which is exactly what I was looking for. Thx so much KIAaze. I'm gonna try it right away. I'm already doing a fresh install of Ubuntu 8.10. I'll let you know what happens :S

---

### Post by mudguts on 2009-03-11
What I found worked for me was downloading the windows driver (*.inf) and pointing the device towards it.

When you plug in the card, do you get a notice in the top bar pointing out a driver issue?

I just unpacked the drivers on a windows box then moved over the *.inf file to a new folder in my documents.

I use the D-link WNA-2330 and it works well.

Are there lights on your card?  how do they blink when in the windows environment?  do they do they same in Ubuntu?

---

### Post by lkraemer on 2009-03-11
isendel123,
Why don't you try this:

Open a terminal window:

```

lshw -C network
ndiswrapper -l

```

Then post the output displayed by both.

If there are drivers loaded, as shown by ndiswrapper -l, open a
Terminal window and remove all by:
```

sudo ndiswrapper -r b43
sudo ndiswrapper -r b44
......
......

```
These are examples only, your may be different.

If there are no drivers loaded open a Terminal window and do:
```

sudo ndiswrapper -i /path/to/bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper

```

If you have an open router do the following in a Terminal Window:
```

iwconfig

```

This will tell you the Wifi's identification....wlan0, ath0, wifi0, etc.

Assume your ID is wlan0...so substitute wlan0 everywhere there is a
<interface> in the code below.  Turn on your Wifi switch if there is one,
or use CNTL F2 or whatever keystrokes enable your Wifi.  Insert your
essid (UPPERCASE or lowercase specific)

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>

```

You should be able to surf.


ref URL:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

If you are using WEP or WPA or WPA2 see URL above.

another ref URL:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)

You may have to blacklist some drivers, but hopefully not at this point.

lkraemer

---

### Post by isendel123 on 2009-03-11
> **KIAaze said:**
> I found 2 tutorials for your wireless card which seem pretty similar:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

Since you only have internet under windows, here's what you'll have to do instead of using apt-get:
[LIST]
[*]Open synaptic 
[*]Click on File->Generate package download script 
[*]Save the script on the USB key
[*]Reboot into Windows and open the script with a text editor
[*]Download all the .deb packages to your USB key using the links from the script.
[*]Reboot into Ubuntu
[*]Open synaptic and click on File->Add downloaded packages
[/LIST]
Adapted from: [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

Note: While you're in Windows downloading the packages, don't forget to also download the driver as indicated in the tutorials! ;)
Here's the link for the driver: [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)

@RJ12:
Please provide support through the forums instead of by e-mail.
This will allow other users to profit from this help as well.

@isendel123
Avoid getting support per e-mail. I don't want to question RJ12's honesty, but getting public support through the forums reduces the risks of being given [malicious commands]("http://ubuntuforums.org/announcement.php?f=326") by "evil" users since others will notice them and warn you as well as report those users to the moderators.
And as said previously, other users can profit from it. :)


After saving the file i reboot windows. When I open the file to see what is in it this is what it shows:  #!/bin/sh
As if it didn't save any package info.

---

### Post by isendel123 on 2009-03-11
> **lkraemer said:**
> isendel123,
Why don't you try this:

Open a terminal window:

```

lshw -C network
ndiswrapper -l

```

Then post the output displayed by both.

If there are drivers loaded, as shown by ndiswrapper -l, open a
Terminal window and remove all by:
```

sudo ndiswrapper -r b43
sudo ndiswrapper -r b44
......
......

```
These are examples only, your may be different.

If there are no drivers loaded open a Terminal window and do:
```

sudo ndiswrapper -i /path/to/bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper

```

If you have an open router do the following in a Terminal Window:
```

iwconfig

```

This will tell you the Wifi's identification....wlan0, ath0, wifi0, etc.

Assume your ID is wlan0...so substitute wlan0 everywhere there is a
<interface> in the code below.  Turn on your Wifi switch if there is one,
or use CNTL F2 or whatever keystrokes enable your Wifi.  Insert your
essid (UPPERCASE or lowercase specific)

[/CODE]
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
[/CODE]

You should be able to surf.


ref URL:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

If you are using WEP or WPA or WPA2 see URL above.

another ref URL:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)

You may have to blacklist some drivers, but hopefully not at this point.

lkraemer



Hi there :)
I followed your suggestion and this is what i got so I didn't go any further.

lkraemer
isendel@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  

*-network               description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation        physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz       capabilities: bus_master cap_list       configuration: driver=b43-pci-bridge latency=0 module=ssb
  

*-network       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ac:07:aa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  

*-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:4c:4b:7b:d1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:8c:29:b1:3f:6e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



isendel@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
isendel@ubuntu:~$ 

The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

---

### Post by lkraemer on 2009-03-11
OK, I assumed that ndiswrapper would be installed.

Go to SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER
Search for ndiswrapper.  It should find ndiswrapper-common.
Mark it for install, and apply the change.

Then try my previous post starting at:
ndiswrapper -l

You have a Broadcom BCM4311 Wifi Card as wlan0.


lkraemer

---

### Post by KIAaze on 2009-03-11
> **isendel123 said:**
> After saving the file i reboot windows. When I open the file to see what is in it this is what it shows:  #!/bin/sh
As if it didn't save any package info.
Oops, my mistake.
Forgot to mention you have to select the packages you want to install in synaptic before generating the package download script. ;)
In your case, that would be the "ndiswrapper" package of course.

I'll have to fix that in the wiki too when I have some time.

---

### Post by isendel123 on 2009-03-11
Hi again :) I really want to say thx so much for all your support. I will do as u say and let u know right away what happens. By the way my ubunto didn't come with ndiswrapper. I downloaded my UBUNTU directly from their main site and its version 8.10. So I had to downloaded the ndiswrapper from windows and then get it into UBUNTU with a pendrive and have it installed.

---

### Post by isendel123 on 2009-03-11
> **lkraemer said:**
> isendel123,
Why don't you try this:

Open a terminal window:

```

lshw -C network
ndiswrapper -l

```

Then post the output displayed by both.

If there are drivers loaded, as shown by ndiswrapper -l, open a
Terminal window and remove all by:
```

sudo ndiswrapper -r b43
sudo ndiswrapper -r b44
......
......

```
These are examples only, your may be different.

If there are no drivers loaded open a Terminal window and do:
```

sudo ndiswrapper -i /path/to/bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper

```

If you have an open router do the following in a Terminal Window:
```

iwconfig

```

This will tell you the Wifi's identification....wlan0, ath0, wifi0, etc.

Assume your ID is wlan0...so substitute wlan0 everywhere there is a
<interface> in the code below.  Turn on your Wifi switch if there is one,
or use CNTL F2 or whatever keystrokes enable your Wifi.  Insert your
essid (UPPERCASE or lowercase specific)

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>

```

You should be able to surf.


ref URL:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

If you are using WEP or WPA or WPA2 see URL above.

another ref URL:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)

You may have to blacklist some drivers, but hopefully not at this point.

lkraemer

Everthing went well until I used the command:

sudo ifconfig wlan0 up

SIOCSIFFLAGS: No such file or directory

By the way my WIFI light never turned on. Not after using all of the commands.  :(

---

### Post by isendel123 on 2009-03-12
> **RJ12 said:**
> I dont know if this can properly answer your question as I am a begginer in Ubuntu to. The way I have my setup is a virtual machine. I use virtualbox and my main connetion for my windows xp is also wireless and it works perfectly if your willing to reinstall ubuntu one last time this is perfect unless you have bad hardware but I have 700 something mb of RAM and it works fine email me at [email]russjr08@hotmail.com[/email] for any other questions

Hi there :)  
Thx for the info but there is no way for me (not a way that I know of) to download any upgrades for the Virtualbox package from Ubuntu. If there could be a way to download everything (virtualbox packages) from windows and then simply install it in UBUNTU that would be great. The idea behind all this would be to upgrade UBUNTU and then use it as the main OS and not have to run both OS at all times. Only Ubuntu. :)

---

### Post by KIAaze on 2009-03-12
> **isendel123 said:**
> Hi there :)  
Thx for the info but there is no way for me (not a way that I know of) to download any upgrades for the Virtualbox package from Ubuntu. If there could be a way to download everything (virtualbox packages) from windows and then simply install it in UBUNTU that would be great. The idea behind all this would be to upgrade UBUNTU and then use it as the main OS and not have to run both OS at all times. Only Ubuntu. :)

I think you misunderstood what he meant.
He doesn't use a dual-boot. He installed Ubuntu inside VirtualBox on Windows.
This way Ubuntu uses the Windows internet connection.
At least that's what I understood.

Here's a tutorial on how to do it:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Otherwise, VirtualBox can easily be installed on Ubuntu without internet connection using the method I gave you. Then you can install Windows in VirtualBox on Ubuntu for example.
But first you should get wireless access, which is more important.

---

### Post by isendel123 on 2009-03-12
> **KIAaze said:**
> I think you misunderstood what he meant.
He doesn't use a dual-boot. He installed Ubuntu inside VirtualBox on Windows.
This way Ubuntu uses the Windows internet connection.
At least that's what I understood.

Here's a tutorial on how to do it:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Otherwise, VirtualBox can easily be installed on Ubuntu without internet connection using the method I gave you. Then you can install Windows in VirtualBox on Ubuntu for example.
But first you should get wireless access, which is more important.


You know u couldn't be more right.  :)  First what comes first, WIFI. I was fooling around with the Virtualbox and had Ubuntu installed. Obviously i had Wifi working since the virtualbox was installed in Windows. i tried running 3 important commands that i can't run if i Boot from UBUNTU and was thinking if there was a way to get all those updates directly from those commands into a flash drive (pen drive). Then have UBUNTU search in the flash instead of the web. That would solve all my problems. :D

---

### Post by KIAaze on 2009-03-12
You can use the Ubuntu CD as source for apt-get:
[https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD](https://help.ubuntu.com/community/Repositories/Ubuntu#CD-ROM/DVD)

---

### Post by mikechant on 2009-03-12
Just out of interest, why can't you get a wired connection? Nearly all PCs and wireless routers come with standard RJ-45 wired network connectors.
The thing is, even if you do get wireless working, it's always useful to have the option of a wired connection - for example, in case a software update breaks your wireless connection sometime in the future.

---

### Post by lkraemer on 2009-03-12
ok,
when you did the:

sudo ndiswrapper -i /path/to/bcmwl5.inf

Did you have the bcml5.sys file located in the same folder as
the bcmwl5.inf along with all the other drivers that make up the
Windows Broadcom folder?  Somehow the firmware is not being found,
meaning to me that you only copied one file from windows to a path
in Ubuntu.  Am I correct?

ref:
[http://lists.berlios.de/pipermail/bcm43xx-dev/2006-January/001084.html](http://lists.berlios.de/pipermail/bcm43xx-dev/2006-January/001084.html)

(I had this error (the SIOCSIFFLAGS error) when the firmware had been
extracted to the wrong directory. To fix this I made /lib/firmware a
symbolic link to /lib/hotplug/firmware and re-extracted the firmware
using fwcutter. i.e.:
ln -s /lib/hotplug/firmware /lib/firmware
YOU WON"T NEED TO DO THIS)

If so, do the following:
copy the Windows folder containing all the Broadcom files to a folder in Ubuntu.

Then do the following in a Terminal window:
```

ndiswrapper -r bcmwl5
ndiswrapper -l
modprobe -r ndiswrapper

```
Make sure no drivers are shown.
```

ndiswrapper -i /Broadcomfolder/bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper

```

Post the output of:
```

ndiswrapper -l

```

Then continue with my previous post.

lkraemer

---

### Post by RJ12 on 2009-03-12
Sorry about the whole email support thing as I am new to the forums:(

---

### Post by RJ12 on 2009-03-12
> **KIAaze said:**
> I think you misunderstood what he meant.
He doesn't use a dual-boot. He installed Ubuntu inside VirtualBox on Windows.
This way Ubuntu uses the Windows internet connection.
At least that's what I understood.

Here's a tutorial on how to do it:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Otherwise, VirtualBox can easily be installed on Ubuntu without internet connection using the method I gave you. Then you can install Windows in VirtualBox on Ubuntu for example.
But first you should get wireless access, which is more important.
Thanks thats what I meant and thats what I do but be careful and check your hardware before you do this so Ubuntu dosent run to slow. Other than thats its perfect since it uses the Windows internet connection.

---

### Post by KIAaze on 2009-03-12
> **RJ12 said:**
> Sorry about the whole email support thing as I am new to the forums:(
No problem. :)
And I forgot to mention it, but: posting your e-mail address on the net will likely also increase the spam you receive... You might want to remove it. ;)

---

### Post by isendel123 on 2009-03-12
So far nothing has worked.  :(

---

### Post by isendel123 on 2009-03-13
> **mikechant said:**
> Just out of interest, why can't you get a wired connection? Nearly all PCs and wireless routers come with standard RJ-45 wired network connectors.
The thing is, even if you do get wireless working, it's always useful to have the option of a wired connection - for example, in case a software update breaks your wireless connection sometime in the future.


Can't get to it b/c the owner that runs this place doesn't want us to know where it is. Not to mention let us have access to it. I rent the place.   :(

---

### Post by isendel123 on 2009-03-13
> **lkraemer said:**
> ok,
when you did the:

sudo ndiswrapper -i /path/to/bcmwl5.inf

Did you have the bcml5.sys file located in the same folder as
the bcmwl5.inf along with all the other drivers that make up the
Windows Broadcom folder?  Somehow the firmware is not being found,
meaning to me that you only copied one file from windows to a path
in Ubuntu.  Am I correct?

ref:
[http://lists.berlios.de/pipermail/bcm43xx-dev/2006-January/001084.html](http://lists.berlios.de/pipermail/bcm43xx-dev/2006-January/001084.html)

(I had this error (the SIOCSIFFLAGS error) when the firmware had been
extracted to the wrong directory. To fix this I made /lib/firmware a
symbolic link to /lib/hotplug/firmware and re-extracted the firmware
using fwcutter. i.e.:
ln -s /lib/hotplug/firmware /lib/firmware
YOU WON"T NEED TO DO THIS)

If so, do the following:
copy the Windows folder containing all the Broadcom files to a folder in Ubuntu.

Then do the following in a Terminal window:
```

ndiswrapper -r bcmwl5
ndiswrapper -l
modprobe -r ndiswrapper

```
Make sure no drivers are shown.
```

ndiswrapper -i /Broadcomfolder/bcmwl5.inf
sudo depmod -a
sudo modprobe ndiswrapper

```

Post the output of:
```

ndiswrapper -l

```

Then continue with my previous post.

lkraemer


Hi again. you have been of great help my friend. I'm still working on the wifi issue. You asked me a question and the answer is no. I did move the whole thing including the .sys and also other files in it. But there is something i just realised. In Windows, the folder that contains the drivers also has other folders that have other bcmwl5 files. There are 5 folders in it:
Driver, Driver_jpn, Driver_row, Driver_us, X64. There are also files (not folders) in the folder that has all 5 folders in it. None of which has a bcmwl5.sys nor .inf.
What would your advice be?

---

### Post by lkraemer on 2009-03-13
The best thing to do is SEARCH for bcmwl5.inf using Windows search, assuming that your Windows Wifi Driver is really bcmwl5.inf.  Then when
that specific file is found, look for the bcmwl5.sys file in the same folder.  You must have the bcmwl5.sys for ndiswrapper to work in Linux.
But the easiest thing to do is just grab the whole folder where bcmwl5.inf
is located, and copy those files to Linux.

Look at this:
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

It will help you copy the requested files to a USB Memory stick and then
be able to install the files for Ubuntu.  His program doesn't support other
Distro's yet.

Once you have the bcmwl5.sys file copied to your Linux system, you should
proceed again with my post that states remove bcmwl5 with ndiswrapper and then re-install it.

lkraemer

---

### Post by BOZG on 2009-03-13
I'm not sure if your card uses the same chip set but I'd suggest having a look at this site: [http://www.omattos.com/omattos/broadcom/](http://www.omattos.com/omattos/broadcom/)

Download the tarball at [http://www.omattos.com/omattos/broadcom/b43-all-fw.tar.gz](http://www.omattos.com/omattos/broadcom/b43-all-fw.tar.gz) through Windows and copy it to a USB drive or a CD. Unzip the archive and open the folder "b43-all-fw" and copy the two folders "b43" and "b43legacy" to /lib/firmware and reboot.  As I said, I'm not sure if it's the same chip set as I've seen a couple of references to different chips but it's worth a try.

---

### Post by isendel123 on 2009-03-13
> **lkraemer said:**
> The best thing to do is SEARCH for bcmwl5.inf using Windows search, assuming that your Windows Wifi Driver is really bcmwl5.inf.  Then when
that specific file is found, look for the bcmwl5.sys file in the same folder.  You must have the bcmwl5.sys for ndiswrapper to work in Linux.
But the easiest thing to do is just grab the whole folder where bcmwl5.inf
is located, and copy those files to Linux.

Look at this:
[http://keryx.betaserver.org/](http://keryx.betaserver.org/)

It will help you copy the requested files to a USB Memory stick and then
be able to install the files for Ubuntu.  His program doesn't support other
Distro's yet.

Once you have the bcmwl5.sys file copied to your Linux system, you should
proceed again with my post that states remove bcmwl5 with ndiswrapper and then re-install it.

lkraemer


Hi. I just installed it again and went through all of your suggested procedures double checking that the folder with all its files was copied into the OS. I can tell that the driver is loaded when I use ndiswrapper -l. Says driver bcmwl5 and hardware present etc. The only issue or error so far is when i use the command to bring the interface up. Keeps saying the same thing it said b4.

---

### Post by isendel123 on 2009-03-13
> **BOZG said:**
> I'm not sure if your card uses the same chip set but I'd suggest having a look at this site: [http://www.omattos.com/omattos/broadcom/](http://www.omattos.com/omattos/broadcom/)

Download the tarball at [http://www.omattos.com/omattos/broadcom/b43-all-fw.tar.gz](http://www.omattos.com/omattos/broadcom/b43-all-fw.tar.gz) through Windows and copy it to a USB drive or a CD. Unzip the archive and open the folder "b43-all-fw" and copy the two folders "b43" and "b43legacy" to /lib/firmware and reboot.  As I said, I'm not sure if it's the same chip set as I've seen a couple of references to different chips but it's worth a try.


Sure pale. Why not give it a try? :) In the worst scenario I'll simply install ubuntu again. Thx again.  ;)

---

### Post by isendel123 on 2009-03-13
> **BOZG said:**
> I'm not sure if your card uses the same chip set but I'd suggest having a look at this site: [http://www.omattos.com/omattos/broadcom/](http://www.omattos.com/omattos/broadcom/)

Download the tarball at [http://www.omattos.com/omattos/broadcom/b43-all-fw.tar.gz](http://www.omattos.com/omattos/broadcom/b43-all-fw.tar.gz) through Windows and copy it to a USB drive or a CD. Unzip the archive and open the folder "b43-all-fw" and copy the two folders "b43" and "b43legacy" to /lib/firmware and reboot.  As I said, I'm not sure if it's the same chip set as I've seen a couple of references to different chips but it's worth a try.

Awesome. All I did was a fresh install of Ubuntu and then simply extract those files into  /lib/firmware folder. It will obviously ask u to have the appropriate permission for it. I used the command "nautilus" for it from terminal and then rebooted. It's all working now. There might be millions trying UBUNTU having the same issue I had. I am glad I didn't quit trying but certainly that is a big "wall" for new users (noobs like me) to climb. One reason why Windows is still "up and running" is that it's made for dumb ppl. And most don't like to troubleshooting at all.

I'd have to say that this forum has been extremely useful and has very friendly ppl trying to help. Very thankful for all the help and support from all you guys. Very very thankful. The only way I can pay back is helping others the same way you helped me.

---

### Post by BOZG on 2009-03-15
> **isendel123 said:**
> Awesome. All I did was a fresh install of Ubuntu and then simply extract those files into  /lib/firmware folder. It will obviously ask u to have the appropriate permission for it. I used the command "nautilus" for it from terminal and then rebooted. It's all working now. There might be millions trying UBUNTU having the same issue I had. I am glad I didn't quit trying but certainly that is a big "wall" for new users (noobs like me) to climb. One reason why Windows is still "up and running" is that it's made for dumb ppl. And most don't like to troubleshooting at all.

I'd have to say that this forum has been extremely useful and has very friendly ppl trying to help. Very thankful for all the help and support from all you guys. Very very thankful. The only way I can pay back is helping others the same way you helped me.


Glad to see it worked!  Now if only I could get my wireless cards to work on Kubuntu! :P

---

### Post by Linux000 on 2009-03-15
In case it still isn't working, I have a dell Latitude D830 with the Brodacom 1390 card, and I could never get it to work in 8.04, the ndiswrapper messed my system and everything, upgrade to 8.10, it has a message that will pop-up on your first boot telling you it has found proprietary drivers for a system component, all you do is install them and you are done:D

---

### Post by BOZG on 2009-03-16
> **Linux000 said:**
> In case it still isn't working, I have a dell Latitude D830 with the Brodacom 1390 card, and I could never get it to work in 8.04, the ndiswrapper messed my system and everything, upgrade to 8.10, it has a message that will pop-up on your first boot telling you it has found proprietary drivers for a system component, all you do is install them and you are done:D

Out of interest, did you do a fresh install followed by installing all available updates before you enabled proprietary drivers or were able to enable the drives before any updates?  I recently installed Ubuntu on a Latitude C600 and could only enable the proprietary drivers after updating everything first.

---

