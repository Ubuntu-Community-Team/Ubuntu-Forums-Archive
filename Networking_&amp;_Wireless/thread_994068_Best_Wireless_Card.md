---
title: "Best Wireless Card?"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by josesanders on 2008-11-26
I want to build a desktop for a remote area of my apartment (where I'm not able to run an ethernet cable), so I wanted some advice about cards that just work right away with a fresh installation.

I've seen this:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
but in my experience, these lists don't usually accurately reflect what works.

I don't know much about wireless speeds, but I do plan to use this for a MythTV frontend, so it will need to be fast enough to stream video from my MythTV backend machine.

---

### Post by CholericKoala on 2008-11-26
Mine doesnt work right away, so I have to use ndiswrapper for mine, but that takes less than 5 minutes to set up.

I have the Linksys WMP300N.  Mainly I like it because it has 3 separate antennas and has a stinking long range.  [Link]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&pagename=Linksys%2FCommon%2FVisitorWrapper&cid=1144763512962")

---

### Post by mag1strate on 2008-11-26
I use mainly NETGEAR products because they are very easy to use! The only problem is that since none of the companies have linux support you have to use ndiswrapper. I use the WN121T, it has very good range. Here are a couple links that will help you set it up if you choose to buy it!

[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

(This Forum link gives the link to the .inf and .sys files, so you don't have to find them on your own!):
[http://ubuntuforums.org/showthread.php?t=537281](http://ubuntuforums.org/showthread.php?t=537281)

(I don't have the link to this page, but I shall copy and paste it for you!)

:)**1. Introduction**:)
Even if your wireless network card does not have a native Linux driver, you may still be able to get it working with ndiswrapper. Ndiswrapper is a Linux module which allows Ubuntu to use the Windows driver for wireless cards (in most cases). 
 These instructions apply only when using the x86 Alternate CD. If you are running Ubuntu for AMD64, please see NdiswrapperOnAMD64 for instructions. These instructions do not apply to Ubuntu for Power PC (PPC) and the Ubuntu Desktop CDs. 
•	If you do not know the name of the chipset which your wifi card uses, issue the lspci command in a terminal; it should be listed there. In order to see if your chipset is known to work with the ndiswrapper module, find your card in the list here. The link may even provide you with useful tips on how to get your specific card to work, as well as providing a link to the working Windows drivers. 
**2. Installation**•	Ubuntu comes with the necessary ndiswrapper module pre-installed, but it needs the ndiswrapper-utils package to get it working. There is also a graphical interface to using ndiswrapper which you can use. Note: Starting with Ubuntu 6.06 (Dapper), ndiswrapper-utils is included on the standard installation CD. You can install the package from the CD and skip to section 2.2... 
**2.1. Installing Packages (With Internet access on the Ubuntu computer)**
If you already have Internet access via some other method while logged into Ubuntu: 
1. Ensure the multiverse and universe repositories are enabled; see AddingRepositoriesHowto 
2. Install the ndisgtk package from the Ubuntu repositories. If you don't know how to install applications then you can read this guide. 
**2.2. Installing Packages (With Internet access on another computer)**•	If you do not have a working Internet connection, you can use another computer which is connected to the Internet to download the following packages (See note about bug below). There is method to use Synaptic to generate a download script to simplify this procedure. 
**2.2.1. Currently Supported Releases**
1.	For 8.04 Hardy Heron 
a.	[http://packages.ubuntu.com/hardy/misc/ndiswrapper-common](http://packages.ubuntu.com/hardy/misc/ndiswrapper-common) 
b.	[http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9) 
c.	[http://packages.ubuntu.com/hardy/net/ndisgtk](http://packages.ubuntu.com/hardy/net/ndisgtk) 
2.	For 7.10 Gutsy Gibbon 
a.	[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common) 
b.	[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9) 
c.	[http://packages.ubuntu.com/gutsy/net/ndisgtk](http://packages.ubuntu.com/gutsy/net/ndisgtk) 
3.	For 7.04 Feisty Fawn 
a.	[http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common) 
b.	[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)
c.	[http://packages.ubuntu.com/feisty/net/ndisgtk](http://packages.ubuntu.com/feisty/net/ndisgtk) 
4.	For 6.06 Dapper Drake 
a.	[http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils)
b.	[http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk) 
Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order: 
  sudo dpkg -i ndiswrapper-common_*.deb
  sudo dpkg -i ndiswrapper-utils*.deb
  sudo dpkg -i --force-depends ndisgtk_*.deb
 Note: There is a known bug in the Debian package, detailed in this thread. If you install from these packages, the kernel module may not get installed, so you may get the error FATAL: Module ndiswrapper not found when you run modprobe ndiswrapper. To avoid this problem, it's best to compile from the source available at [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/). This is fairly simple but requires the build-essentials package to be installed. You can install this offline using apt-cdrom from the command line or the synaptic package manager with the ubuntu install CD. 
 The commands listed above are a general example of how to install a .deb package from the command line. You need to be in the directory where the files were copied to. If you are new to the terminal, consider reading BasicCommands. 
**2.2.2. Older Releases**
1.	For 6.10 Edgy Eft 
a.	[http://packages.ubuntu.com/edgy/misc/ndiswrapper-common](http://packages.ubuntu.com/edgy/misc/ndiswrapper-common) 
b.	[http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-](http://packages.ubuntu.com/edgy/misc/ndiswrapper-utils-)**1.8 **
c.	[http://packages.ubuntu.com/edgy/net/ndisgtk](http://packages.ubuntu.com/edgy/net/ndisgtk) 
2.	For 5.10 Breezy Badger 
a.	[http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils](http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils) 
b.	[http://packages.ubuntu.com/breezy/net/ndisgtk](http://packages.ubuntu.com/breezy/net/ndisgtk) 
Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order: 
•	  sudo dpkg -i ndiswrapper-utils_*.deb
  sudo dpkg -i ndisgtk_*.deb
 The commands listed above are a general example of how to install a .deb package from the command line. You need to be in the directory where the files were copied to. If you are new to the terminal, consider reading BasicCommands. 
NOTE: in Edgy, you must install the ndiswrapper-utils-1.8 package instead of just ndiswrapper-utils. and then proceed with installation using the command ndiswrapper-1.8 instead of ndiswrapper. See [https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983) for bug report. and [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy) for help installing. 
**2.3. Installing Packages (Without Internet access)**•	Without an Internet connection, you can still install ndiswrapper-utils from the Desktop CD. If you installed from that, the repository in which ndiswrapper-utils is found is on the CD, but not within the live session. You need to boot into your new Ubuntu installation and then reinsert the Desktop CD. You will be asked if you want to add the packages on the CD to your list of repositories. 
If you installed using the Dapper Alternate CD, those packages except ndisgtk are included on it. 
Put the CD into the drive, click System > Administration > Synaptic Package Manager and search for ndis. If you don't know how to install applications, read this guide. 
3. Configuration
**3.1. Disable Free Drivers**
Firstly, all releases since Ubuntu 6.06 have the open source bcm43xx driver, which was replaced in 8.04 by b43 and b43legacy, see WifiDocs/Driver/bcm43xx. If this driver doesn't work for you, then you should disable it, because it will conflict with ndiswrapper. To disable it, add blacklist bcm43xx lines for each driver to the modprobe blacklist. 
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
(Or just edit the /etc/modprobe.d/blacklist file and add blacklist bcm43xx, blacklist b43, blacklist b43legacy and blacklist ssb to the end of the file.) Note: This only effects what is loaded at startup, so you will have to reboot to have the bcm43xx drivers disabled. If you have an atheros based card, remember to blacklist not only ath_pci, but also ath_hal, since ndiswrapper won't work if ath_hal is still loaded. 
 To get this working with a D-link DWL-G122 USB wireless device, we had to blacklist rt2500usb as well, then restart. Our big clue came when the device's "Connection Information" kept saying rt2500usb was the driver even though we had followed all the instructions on this page. 
**3.2. Identifying Wireless Adapter**•	 Important: Be careful when using the drivers from the CD included with the wireless card. They may work and you can try them, but you could experience kernel crashes and other serious problems if the driver on your CD has not been tested with ndiswrapper. 
•	You should download a tested Windows XP driver which is suitable for your card from the ndiswrapper list. 
**3.2.1. PCI Wireless Adapter**
1.	Open a Terminal (Applications | Accessories | Terminal), type lspci and press the return/enter key. 
2.	Look through the output of the lspci command for an entry for your wireless card. 
3.	Once you have identified your card, note down the contents of the first column, which should look like 0000:00:0c.0. 
4.	Now, type lspci -n into the Terminal and press return. 
5.	Find the PCI ID for your device. Your device will be referred to in the output of the command by the identifier which you just made a note of, e.g. 0000:00:0c.0. The PCI (chipset) ID will be in the third column of the output and will be in the form 104c:8400. 
**3.2.2. USB Wireless Adapter**
1.	Open a Terminal (Applications | Accessories | Terminal), type lsusb and press the return/enter key. 
2.	Look through the output of the lsusb command for an entry for your wireless adapter. 
3.	Once you have identified your adapter, note down the contents of the chipset ID, this will be in the form 104c:8400. 
**3.3. Downloading Windows Drivers**
1.	Retrieve the Windows driver corresponding to your chipset: Use the ID information you have just found and the ndiswrapper list to find and download the correct windows driver files for your wireless adapter, or one which is very similar (same chipset ID). 
2.	Unpack the Windows driver by using the unzip, cabextract and/or unshield tools (run from the Terminal), and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). You may first need to install cabextract and unshield. 
3.	If there are multiple INF/SYS files, look in the ndiswrapper list to see if there are any hints about which of them should be used. 
4.	Make sure that the INF file, SYS file and any BIN files are all put into one directory. 
**3.4. Installing Windows driver**
**3.4.1. Installing Windows driver using ndisgtk (ndiswrapper graphical interface)**•	If you chose to install ndisgtk, the graphical interface for ndiswrapper, after installation click on System | Administration | Windows wireless drivers and follow the instructions on-screen. For an idea of what to expect, some screenshots of ndisgtk can be found here. 
If this works, and you have a network connection, then you can skip to Automatically loading at Startup - ndisgtk will load the driver if it installs correctly. 
**3.4.2. Installing Windows driver using command line**
In a Terminal, run the following command: 
•	  sudo ndiswrapper -i ~/drivers/drivername.inf
(assuming the driver is in a directory in your home folder called drivers, and is named drivername.inf) 
ndiswrapper then copies the .inf and sys files into /etc/ndiswrapper/.... Don't forget that the filename you type in is case-sensitive. 
**3.4.2.1. Check to make sure the driver was installed correctly**•	Run the following command from a Terminal: 
  ndiswrapper -l
If the driver is installed correctly, you should see the following output: 
  Installed ndis drivers:
  {name of driver} driver present, hardware present
or 
  {name of driver} : driver installed
       device ({Chipset ID}) present
If you don't see this message: 
a.	Try a different driver such as the drivers for Windows 2000, or another driver matching the PCI ID on the ndiswrapper list. 
b.	This document has a troubleshooting section which may provide an answer. 
c.	Look for additional help. Read HowToGetHelp for more information. 
**3.5. Load the new driver module**•	If ndiswrapper correctly associates the driver to the wireless adapter, you are now ready to load the driver into memory, and try to establish a network connection. Open a Terminal and run the following commands: 
•	  sudo depmod -a
  sudo modprobe ndiswrapper
Then, also in a Terminal, check for error messages: 
  tail /var/log/messages
Alternatively, open a Terminal and try the commands ifconfig and iwconfig. Your wireless card should appear with an interface name of wlan0. If it doesn't appear here, then the driver is not working properly. If no errors are given, you should now be able to configure the network connection. 
**3.6. Configuring Wireless Network Settings****3.6.1. Configuring Wireless Network Settings using nm-applet **(GNOME front end for Network Manager)
•	If this applet is installed, it makes wireless network connection to multiple networks (roaming) easier - this is useful if you use your laptop to connect to wireless networks at more than one location. 
1.	Open the Networking Admin tool (System | Administration | Networking), select the Wireless connection and click Properties, ensure the Enable roaming mode checkbox is ticked. 
2.	Click the Network Manager icon (computers icon in the top right corner of system tray), your network ESSID should be shown in the drop-down list. Select your network by clicking on it. 
3.	If the Network requires any further configuration (eg WEP key), a dialog should appear, select the correct settings and paste in your key. 
4.	The Network Manager applet uses Keyring Manager to store your passwords - so a second dialog will open after this, asking to create a master password for the keyring manager. Note that you will be requested to enter the Master Keyring password each time you logon - there is a solution to avoid entering a password each time here. 
5.	Your Wireless Network should now be configured - skip to Automatically loading at Startup 
 Using this method of configuration with the TNET1450 driver, the wireless network kept dropping packets and the wireless connection stopped responding after a few minutes - if you encounter similar problems use the network-admin method below. 
 nm-applet does not use the standard NetworkAdmin file /etc/network/interfaces to store the Wireless Network settings, so you will not be able to use ifup and ifdown commands to start / stop the Network adapter. Starting / Stopping ndiswrapper (sudo modprobe ndiswrapper / sudo modprobe -r ndiswrapper) can be used instead. This may make it harder to diagnose connection problems. 
 nm-applet requires an entry in /etc/modules to start ndiswrapper on system startup. However this setting needs to be removed if using manual configuration (network-admin), as ndiswrapper will be started by network-admin by the alias command in /etc/modprobe.d/ndiswrapper only 
**3.6.2. Configuring Wireless Network Settings using network-admin (Network Admin)**This is an alternative, more native method to using the GNOME nm-applet. 
1.	Open the Networking Admin tool (System | Administration | Networking), select the Wireless connection and click Properties, ensure the Enable roaming mode checkbox is unticked. 
2.	In the Network Name box, select / type the ESSID of your network 
3.	In the Password type box, select whether your network password is Hex (eg. 208AB43..) or Ascii (eg. secret) 
4.	In the Password box, Type / paste your network password 
5.	In the Connection Configuration, select the Network configuration type - this is normally DHCP. 
6.	If your network is configured using Static IP addresses, fill in the IP address of the computer, Subnet mask and Gateway IP address. 
7.	Click OK to apply these settings - they will be stored to file /etc/network/interfaces 
8.	For completeness, In the Network Settings dialog click Save and type a memorable name for the network you have configured. This can be used to manually select between multiple networks. 
9.	Your Wireless Network should now be configured - skip to Automatically loading at Startup 
•	Note: During startup, the system will activate the Network Admin settings kept in the file /etc/network/interfaces, where the Networking tool saves its settings. 
•	You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages: 
o	  sudo ifdown wlan0
o	  sudo ifup wlan0
You may diagnose the network adapter status with commands: 
o	  ifconfig
o	  iwconfig
o	  
o	  dmesg
o	  tail /etc/var/messages
**3.6.3. Configuring Wireless Network Settings using command line**
If the above methods did not produce a working Wireless Network connection, you can Edit the Network Interfaces file by hand and diagnose your network using the command line. 
•	You can discover settings with iwconfig beyond those on offer with the Networking tool. Also, the order of the wireless settings can be very important. If you discover that issuing iwconfig commands in a certain order on the command line is necessary, make sure the file asserts the settings in the same order. 
Test /etc/network/interfaces by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages: 
o	  sudo ifdown wlan0
o	  sudo ifup wlan0
You may diagnose the network adapter status with commands: 
  ifconfig
  iwconfig
  
  dmesg
  tail /etc/var/messages
Note: During startup, the system will activate the Network Admin settings kept in the file /etc/network/interfaces, where the Networking tool saves its settings. 
For information on getting WPA to work, read the WPAHowto. 
**3.7. Automatically loading at start-up**
If everything works, you need to tell your system to load the module when the system starts-up. Depending on the method of network manager you are using, will require a different setup 
•	Configure ndiswrapper for use with the Network Admin settings - this adds an Alias to associate wlan0 to ndiswrapper in modprobe.d 
o	  sudo ndiswrapper -m
**3.7.1. Network Manager applet only**
•	If you are using the nm-applet to configure Wireless Network, ndiswrapper will not be started by the network manager alias setting. Ensure the ndiswrapper module is loaded at system startup: 
Edit /etc/modules file to add an entry for ndiswrapper at the end of the file In Ubuntu, 
o	  gksudo gedit /etc/modules
In Kubuntu, 
o	  kdesu kate /etc/modules
and add the word ndiswrapper to the end of this file and save it. 
 nm-applet requires entry in /etc/modules to start ndiswrapper on system startup. However this setting should be removed if using manual configuration (network-admin), as ndiswrapper will be started by network-admin alias command in /etc/modprobe.d/ndiswrapper and having the entry in etc/modules may cause the wireless network driver to not start properly 
 It is strongly recommended that you make a backup copy of the /etc/modules file before manually editing it. 
**4. Troubleshooting**•	If you cannot get a working driver, you may want to consider compiling and using the latest ndiswrapper release. Ubuntu Breezy comes with v1.1, and as of Jan 2006 v1.8 is the stable release. 
•	Can not modprobe ndiswrapper, fatal error given. 
o	This error is usually given when ndiswrapper is compiled and installed. You have a bad installation or you didn't remove the module that came with Ubuntu. You need to uninstall ndiswrapper and make sure you remove the ndiswrapper module that came with Ubuntu. Instructions on how to uninstall ndiswrapper can be found here 
•	If you cannot connect, make sure eth0 (or any other network interface that may be in use) is down/deactivated. The command to take eth0 down is: 
sudo killall dhclient
sudo ifconfig eth0 down
**4.1. Some common errors**•	Tried to install driver from CD-ROM 
o	The files need to be on your hard drive, they can not be loaded from the cd-rom 
•	Not all files are copied over to the hard drive 
o	Not all files from the drive are needed. You basically need a .inf and a .sys file. Some drivers also use a .bin file but there shouldn't be any other file type needed. 
•	Too many driver files copied to folder 
o	You should only have 1 .inf and 1 .sys file in the directory on your hard drive. 
•	Can't get driver.inf file to install - file not found 
o	You have to be in the directory where the .inf file is or specify the full path to the file. 
•	Another driver loads and binds to the device 
o	Sometimes ndiswrapper is used prematurely. There may be a native driver that comes with Ubuntu which is taking the primary driver position and conflicting with ndiswrapper. For more information on this, go to the WifiDocs/WirelessTroubleShootingGuide and view the step on device drivers and ndiswrapper. 
**5. Compiling the latest version of ndiswrapper**This section is based on an ndiswrapper wiki page, and was copied from the Ubuntu Forums. The original post can be found here. Please discuss any problems or errors you experience there. 
•	It is recommended that you first remove any sign of ndiswrapper from your computer. There is a module which installs by default with Ubuntu. To remove this, from a Terminal run the following commands: 
o	  sudo modprobe -r ndiswrapper
o	  sudo apt-get --purge remove ndiswrapper-utils
o	  sudo rm -r /etc/ndiswrapper/
o	  sudo rm -r /etc/modprobe.d/ndiswrapper
o	  sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
 Before you begin to compile your own ndiswrapper, please note that whenever you update your kernel you will need to recompile. However, it shouldn't be necessary to remove the previous traces of ndiswrapper, as detailed above when you reinstall. 
**5.1. Install kernel headers**
•	From a Terminal, run: 
  sudo apt-get install linux-headers-$(uname -r)
and run the following for the dependencies: 
  sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
**5.2. Download and unpack the current version**•	You can find the current version of ndiswrapper here. Using the Terminal, change to the directory where you saved the downloaded file and run the following commands: 
•	  tar xvfz ndiswrapper-[current version].tar.gz
  cd ndiswrapper-[current version]
•	With the second command, replace [current version] with the actual version of the file you downloaded. 
**5.3. Install Ndiswrapper**•	The most current version of ndiswrapper (since at least version 1.19) can no longer be compiled into a .deb package. There is a way around this, however. Just do the following while in your ndiswrapper directory (see above): 
•	  sudo make uninstall
  sudo make
It is advised that your run in fakeroot for the following: 
  fakeroot
  sudo make install
If any errors occur during these steps, please try installing again. It may be required for you to run in fakeroot during the entire process. When everything has installed without error, return to the install section of this document to finish setting up ndiswrapper. 
**5.4. Build deb packages and install (works only for older versions of ndiswrapper)** Please note: This is technically outdated material. However, in certain circumstances it may be required that you use an older version of ndiswrapper to get your wireless card working. If for some reason you can not get the above steps working, then download a version before 1.16 for the following to apply. 
•	Run the following from the Terminal: 
•	  fakeroot debian/rules binary-modules
•	  fakeroot debian/rules binary-utils
•	  cd ..
  sudo dpkg -i ndiswrapper-modules-[your kernel]_[current version]-1_i386.deb ndiswrapper-utils_[current version]-1_i386.deb
Now go back to the Configuration section of this document to set up and use your newly installed ndiswrapper package. 



Hope this helps!:)

---

### Post by Idefix82 on 2008-11-26
> **mag1strate said:**
> I use mainly NETGEAR products because they are very easy to use! The only problem is that since none of the companies have linux support you have to use ndiswrapper. 

That's not true at all. For example many Ralink chip sets seem to work out of the box. This site might be helpful:[http://www.linuxemporium.co.uk/products/wireless/]("http://www.linuxemporium.co.uk/products/wireless/")

---

### Post by mag1strate on 2008-11-26
Wow I didn't know about those cards, Thanks for telling me, now I won't make the mistake of giving false info! Thanks Again!

---

### Post by josesanders on 2008-11-26
Idefix82,

That seems to be what I'm looking for.  Thanks

---

