---
title: "Wireless not detected"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by oconnorpaulq on 2010-06-27
Installed Ubuntu 10.04 Lucid Lynx using WUBI on Dell Dimension B110 running Windows XP service pack 3.
Wireless adapter is Linksys WUSB11 version 2.6 (USB dongle). 
Network manager icon is present in upper right corner with exclamation point (disconnected), no wireless network listed. Trying "Edit Connections, Wireless, try adding SSID and WEP key, no luck.
Following the wireless troubleshooting instructions in Ubuntu help, tried lshw -C network and don't get any indication of the wireless device. 

System -> Administration -> Hardware Drivers get error message "Downloading package indexes failed" then empty hardware drivers window saying No proprietary drivers are in use on this system.

iwconfig returns 
  lo     no wireless extensions
  eth0 no wireless extensions

Machine does not have access to wired ethernet.

Booting into windows, wireless is OK as usual.

Any suggestions? Would like to move from WinXP to Linux but can't get far without network.

---

### Post by GlazedWicker on 2010-06-27
Sounds like you're going to have to get access to a wired connection somehow in order to download the proper wireless drivers.

---

### Post by anewguy on 2010-06-27
If you don't have access to the internet (e.g, you have no way to hard wire a connection to the router), we can try the Windows XP drivers.  I posted reply on a similar wireless question and using drivers last week, so I'll just copy that in here now - maybe it will help you.

There are many, many posts on the forum for wireless adapter help, but a basic strategy would be:

(1) Check for restricted driver:

- connect your computer via a hard wired connection to the internet

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo apt-get update <press enter>

After this completes, close the terminal window, then go to System/Administration/Hardware Drivers and see if a driver is listed there. If so, enable the driver (I would also just reboot after this).

(2) If a hard wired connection is not an option, or if you tried but no driver showed in System/Administration/Hardware Drivers, your next step would be to try ndiswrapper. There are 3 main things needed for this: ndiswrapper and its utility, the Windows XP driver files (.inf and .sys) for the adapter, and ndisgtk. The following is how to install ndiswrapper, the ndiswrapper utilities, ndisgtk, and install the driver using these tools. Please note you will need to locate the Windows XP driver files for your adapter first.

- copy your Windows XP driver files (.inf and .sys files) to your desktop

- spin up the Ubuntu LiveCD you installed from. When a message comes up about a CD with packages being found, just cancel out of it.

- via "Places", open the LiveCD in the file browser

- navigate to the pool/main/n folder. You should see 2 folders here: 1 for ndiswrapper and 1 for ndisgtk. Ndiswrapper must be installed first, so do the following:

    * navigate to the ndiswrapper folder
    * double click on the ndiswrapper-common file to start its installation
    * when ndiswrapper has finished installing, double click on the ndiswrapper utilities file to start installing it
    * navigate back one folder to the pool/main/n folder again, then click on the ndisgtk folder
    * double click on the ndisgtk file to starts its installation


- go to System/Administration/Windows Wireless Drivers. This will start ndisgtk (it's gui'd front end to ndiswrapper).

- if anything shows in ndisgtk, delete it so the "slate is clean"

- click add and point it to the Windows XP driver .inf file on your desktop. This should install the driver.

As with anything, there are exceptions. Some may require some special configuration of the wireless connection via such things as iwconfig, etc.. Some laptops also have a key (or set of key combinations) that physically turn the wireless adapter off or on - you have to be sure you have it on. Sometimes other things crop up - when they do just post back to the forum and people will try to help you.


Now for a couple things common to all:

- know your routers configuration - you will need to know such things as:

    * The network (ESSID) name, especially if your router is "hiding" the network by not broadcasting the name.
    * What type of security is being implemented - WEP, WPA, WPA2, etc.
    * The network key if security is being implemented
    * Is MAC filtering enabled - if so, you'll need to add the adapters MAC address to the table in the router or you will never connect to it


- right click on the network manager icon and be sure "Enable Wireless" is checked

- check in network manager for wireless networks. If you can see available wireless networks your adapter is now working. Please note that if the only network(s) available in your area are "hidden" (the router is not broadcasting a network name), you will not see them in network manager. You must manually add the new connection via network manager.


dave ;)

---

### Post by oconnorpaulq on 2010-06-30
Tried with no luck to access the adapter by installing atmel-firmware.deb. It's supposed to automatically upgrade the firmware in the adapter's chipset.  This failed, bringing up a window saying "breaks existing package - linux-firmware conflict".

Next got a long ethernet cable and hooked the machine up to a wired connection. Booted into linux, no wireless icon at all, tried System/Administration/Hardware Drivers, nothing shows up in the list.

Next step was to use Synaptics Package Manager to install ndiswrapper, the ndiswrapper utilities, and ndisgtk. Downloaded the latest Windows drivers, brought them over to the Linux filesystem. Before running ndisgtk I downloaded and installed atmel-firmware again. Ran  System/Administration/"Windows Wireless Drivers" (I guess this is ndisgtk) and it asked me to browse to the driver location. I pointed it at the .inf file but it failed to complete, complaining that not all files were found. 

Next I went back into Windows and installed the updated driver for the WUSB11 v2.6.

Then back into Ubuntu, still nothing in System/Administration/Hardware Drivers list. Once again went to "Windows Wireless Drivers", this time the window opened, then turned grey after 10 seconds and stayed that way, no further progress. I had to Force Close the window. 

Also of note: I tried running lusb and ndiswrapper -l from the terminal window. Both commands hung up, no error message, had to force close the terminal. 

With all these commands ending in hung windows, I am puzzled and may resort to uninstalling/reinstalling Ubuntu.

---

### Post by anewguy on 2010-06-30
One thing I can tell you - you have to have either your hard wired connection or your wireless connection.  While you are connected to the net via the hard wired connection your wireless will not work.

Not sure I understood clearly about the updated Windows driver.  Installing it in Windows has no effect on Ubuntu - you need to load a driver in Ubuntu, either via a download of a valid Linux driver (preferable) or as a last resort via ndiswrapper/ndisgtk.

Dave

---

