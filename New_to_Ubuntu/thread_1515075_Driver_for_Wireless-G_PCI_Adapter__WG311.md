---
title: "Driver for Wireless-G PCI Adapter  WG311"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by montana68 on 2010-06-21
I am trying to get a driver for Wireless-G PCI Adapter WG311, Netgear. I have looked on the forum and found an explanation but could not understand it. I am a newbie and don't understand to much.

---

### Post by ieee488 on 2010-06-22
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) has the explanation

if that is not something you can do, then either buy a device that is supported "out of the box" or forget about Ubuntu

---

### Post by Warren North on 2010-06-22
> **ieee488 said:**
> [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) has the explanation

if that is not something you can do, then either buy a device that is supported "out of the box" or forget about Ubuntu

Ouch,
But what you can do is try to install it and see if Ubuntu detects it.
I discovered that Ubuntu can detect devices and make them work but in windows you have to install driver. My cable modem with usb does not work without a driver in windows but works without do anything in Ubuntu.
Do give up on Ubuntu. I there are enough users out there that should have the same problem and get it fixed. Other option is try another distro using a live cd and see if that helps. 
I went ahead and got a printer that work with ubuntu and gave up on my Canon ip1700 pixma.
Good Luck

---

### Post by ieee488 on 2010-06-22
How can install it if he doesn't understand it?  Which is what he is claiming.

Learning to use Ubuntu takes some effort. 

Apparently, there are different versions of that card. He'll need to determine which one he has first before he can do anything.

---

### Post by Warren North on 2010-06-22
I know that link that was sent above may help, it appears to have a lot of info and he may have to use terminal to put the commands in to get those packages installed. 
Thanks

---

### Post by Bucky Ball on 2010-06-22
Plug in an ethernet cable, if you haven't already, and get all updates. Plug in your adapter while the cable is in, give it a few minutes.

Also, System->Administration->Hardware Drivers. Is there anything in there disabled?

---

### Post by fresnofred on 2010-06-23
easiest fix is to go on ebay and buy and install an airlink101 super-g wifi card.  it works right away with ubuntu (g-card wont work only super-g).  no drivers needed.

---

### Post by anewguy on 2010-06-23
> **fresnofred said:**
> easiest fix is to go on ebay and buy and install an airlink101 super-g wifi card.  it works right away with ubuntu (g-card wont work only super-g).  no drivers needed.

For a lot of users, purchasing another piece of hardware, even if relatively inexpensive, is not an option.  Besides, if you already have the hardware there are usually ways to make it work.  One of those ways is listed in the link pointed to by ieee488's link -> ndiswrapper.  For those who may not know, ndiswrapper allows you to use Windows XP drivers in Linux for your wireless device.  There is still a large number of adapters for which there is no native Linux driver, and no restricted driver (what people are having you look for when they have you hardwire, do an apt-get update, then check in hardware drivers to see if there is a driver listed).  Large strides have been made for the Broadcom chipset adapters, and most of the people pointing people to the restricted drivers are doing so for Broadcom chipset adapters.

But the biggest problem may also be that these things aren't always obvious to the new user, even with the thousands of posts on this forum about getting wireless working.

There are many, many posts on the forum for wireless adapter help, but a basic strategy would be:

(1) Check for restricted driver:

- connect your computer via a hard wired connection to the internet

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo apt-get update <press enter>

After this completes, close the terminal window, then go to System/Administration/Hardware Drivers and see if a driver is listed there.  If so, enable the driver (I would also just reboot after this).

(2) If a hard wired connection is not an option, or if you tried but no driver showed in System/Administration/Hardware Drivers, your next step would be to try ndiswrapper.  There are 3 main things needed for this: ndiswrapper and its utility, the Windows XP driver files (.inf and .sys) for the adapter, and ndisgtk.  The following is how to install ndiswrapper, the ndiswrapper utilities, ndisgtk, and install the driver using these tools.  Please note you will need to locate the Windows XP driver files for your adapter first.

- copy your Windows XP driver files (.inf and .sys files) to your desktop

- spin up the Ubuntu LiveCD you installed from.  When a message comes up about a CD with packages being found, just cancel out of it.

- via "Places", open the LiveCD in the file browser

- navigate to the pool/main/n folder.  You should see 2 folders here: 1  for ndiswrapper and 1 for ndisgtk.  Ndiswrapper must be installed first, so do the following:
[LIST]
[*]navigate to the ndiswrapper folder
[*]double click on the ndiswrapper-common file to start its installation
[*]when ndiswrapper has finished installing, double click on the ndiswrapper utilities file to start installing it
[*]navigate back one folder to the pool/main/n folder again, then click on the ndisgtk folder
[*]double click on the ndisgtk file to starts its installation
[/LIST]

- go to System/Administration/Windows Wireless Drivers.  This will start ndisgtk (it's gui'd front end to ndiswrapper).

- if anything shows in ndisgtk, delete it so the "slate is clean"

- click add and point it to the Windows XP driver .inf file on your desktop.  This should install the driver.

As with anything, there are exceptions.  Some may require some special configuration of the wireless connection via such things as iwconfig, etc..  Some laptops also have a key (or set of key combinations) that physically turn the wireless adapter off or on - you have to be sure you have it on.  Sometimes other things crop up - when they do just post back to the forum and people will try to help you.


Now for a couple things common to all:

- know your routers configuration - you will need to know such things as:
[list][*]The network (ESSID) name, especially if your router is "hiding" the network by not broadcasting the name.
[*]What type of security is being implemented - WEP, WPA, WPA2, etc.
[*]The network key if security is being implemented
[*]Is MAC filtering enabled - if so, you'll need to add the adapters MAC address to the table in the router or you will never connect to it
[/list]

- right click on the network manager icon and be sure "Enable Wireless" is checked

- check in network manager for wireless networks.  If you can see available wireless networks your adapter is now working.  Please note that if the only network(s) available in your area are "hidden" (the router is not broadcasting a network name), you will not see them in network manager.  You must manually add the new connection via network manager.


Now, for the OP - if your adapter is the WG311V3 you can use ndiswrapper and the Windows drivers (let me know if you need those).  I have that adapter so I know it will work.  Just don't assume it's the V3 - you'll need to check for that as there is more than 1 version of that card.  One thing I have noticed with this adapter, and it seems to be a common complaint about the WG311 especially in Linux, is that the signal doesn't seem as strong - for me thats with Windows XP or Linux.  I have an Acer Aspire One netbook with a different built-in adapter in it, and it sees the signal strength as much stronger.

Any questions - please post back!


Dave ;)

---

### Post by anewguy on 2010-06-23
I also should have included the following for those people looking to get a wireless adapter or perhaps a laptop with built-in wireless that you intend run Ubuntu on.

[This]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") list shows the wireless adapters that work with Ubuntu and to what degree.

Dave ;)

---

### Post by messiah89 on 2010-07-13
Hello, I have this similar WG311v3 wifi card and it works on both Lubuntu and XP. In Lubuntu I used ndiswrapper with XP drivers and it worked fine but in Ubuntu 9.10 it detects networks and it tried to connect but after a minute or so it gives up.
Does anyone know how to solve this?

---

### Post by jlpage on 2010-08-18
Hi.

Also trying to use a Netgear wg311v3 pci card.  I followed all of the instructions above.  I now have two problems:  1) ndiswrapper says "hardware present:  no" and 2) no "enable wireless" checkbox appears on the Network Manager dropdown menu.  Any ideas?  Thanks!!

---

### Post by anewguy on 2010-08-18
> **jlpage said:**
> Hi.

Also trying to use a Netgear wg311v3 pci card.  I followed all of the instructions above.  I now have two problems:  1) ndiswrapper says "hardware present:  no" and 2) no "enable wireless" checkbox appears on the Network Manager dropdown menu.  Any ideas?  Thanks!!


Hopefully you used ndisgtk as the GUI'd front end to ndiswrapper.  If so, open it (System/Administration/Windows Wireless Drivers) and delete any devices that show.  Then add your driver again and check network manager.

If you didn't use ndisgtk, you have just a little more work to do - it's easy, just more typing:

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo ndiswrapper -l <press enter) That's a lower case "L", not a one.  The lower case "L" tells ndiswrapper to list any know devices.  This will include devices which may not work due to some error when adding it.

For each device returned above:

sudo ndiswrapper -e xxxxxxx <press enter> where xxxxxxx should be the device name return on the list

Once the list is empty, I would strongly suggest installing ndisgtk as the GUI'd front-end to ndiswrapper - it takes a lot of hassles out of things.  It can be found on the installation media (like the LiveCD) in the /pool/main/n/ndisgtk folder.  Double-click on the file there to install it.  After installation it can be activated via:  System/Administration/Windows Wireless Drivers

Do an add, and point it to the the .inf file for your driver.

I have the WG311v3 PCI card and have used it fine in Ubuntu.  I installed the driver using ndiswrapper/ndisgtk.

Dave ;)

---

