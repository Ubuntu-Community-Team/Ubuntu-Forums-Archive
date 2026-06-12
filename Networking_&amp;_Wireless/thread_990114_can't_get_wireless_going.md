---
title: "can't get wireless going"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by rosswell59 on 2008-11-22
I installed ubuntu 8.04 on my everex gbook and it seems to be seeing the hardware and installed the proper driver. It didn't have any icon at the top for networking so I added one I believe to be correct but It doesn't show my wireless router. I can go to Administration>networking manager and I can see the router and enter my password on the manual configuration only but I'm still not connected to the internet. I tried all of the troubleshooting tips in the help browser and could only conclude that I indeed was not connecting to the router.

Ross

---

### Post by Olivier2371 on 2008-11-22
What is the chipset of your wireless adapter?

---

### Post by rosswell59 on 2008-11-22
Atheros AR5005G Wireless Network Adapter 802.11b/g

---

### Post by Joe2Shoe on 2008-11-22
ross,
Go to System/Administration/Hardware Drivers and see if your wifi card's drivers are listed there.
If so, click on the driver listed, then click the 'activate' button below.
Reboot.
Try connecting again.
Good luck,
Joe2Shoe.

---

### Post by Joe2Shoe on 2008-11-22
Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper.  This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install ndisgtk (System/Administration/Synaptic Package Manager).
   3. Open ndisgtk (System/Administration/Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.


[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', even though you have great signal strength, it isn't.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.

---

### Post by rosswell59 on 2008-11-22
Joe,
I show that the driver is loaded and active.

---

### Post by Olivier2371 on 2008-11-22
So is it working?

I found a link for drivers.
[http://linuxwireless.org/en/users/Drivers]("http://linuxwireless.org/en/users/Drivers")

---

### Post by rosswell59 on 2008-11-23
No, and I don't know why. My old os had an icon at the top which autodeteced the wireless network and it was just a matter of putting in my security password. I'm not getting that with the two newer installs I have tried. To make matters worse, I thought it might work better if I just did upgrade with my working os and it was rendered unbootable. The factory restoration disk that came with the computer is bad so I have no working internet on that computer.

---

### Post by Joe2Shoe on 2008-11-23
ross, try this configuration, it works on my 8.04 and 8.10 laptops.

HOW TO EDIT CONFIGURATIONS OF WIFI CARD:



In the top-right of the screen, right-click the "Network Manager" icon (the signal strength bar).

Left-click on "Edit Connections".



Click the "Wireless" tab

Click your network's name, then click "Edit".



Connect automatically: is Checked

System setting: is not Checked



Under the "Wireless" tab

SSID: name of network

Mode: Infrastructure

BSSID: blank

MAC address: blank

MTU: automatic



Under the "Wireless Security" tab

Security: WPA & WPA2 Personal (or whatever type of encryption you used on your wireless router).

Password: xxxx



Under the "IPv4 Settings" tab

Method: Automatic (DHCP) or Automatic (DHCP Address only)



Save/Exit.

Try connecting again.


Good luck,
Joe2Shoe.

---

