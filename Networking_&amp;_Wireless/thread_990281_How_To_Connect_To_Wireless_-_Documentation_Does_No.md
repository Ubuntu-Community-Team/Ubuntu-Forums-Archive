---
title: "How To Connect To Wireless - Documentation Does Not Work"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by jereece on 2008-11-22
I have an Acer Extensa 5620-4025 and am trying Ubuntu 8.10 on it.  I am a nubie to Linux.  I read the directions [here]("https://help.ubuntu.com/8.10/internet/C/wireless-connecting.html"), but 

1) It says to go to System &#8594; Administration &#8594; Network, but all I see is System &#8594; Administration &#8594; Network Tools which I see nothing to help.

2) When I click the Network Manager icon in the task bar, I see no wireless networks.  All I see is *Wired Netowrk and Auto eth0 and both are grayed out.  There also is VPN Connections.  

I went into System > Admin > Hardware Drivers and the driver for my Atherous wireless card is listed Activated and Currently In Use. 

I went into System > Preferences > Network Connections and manually set up my wireless network using my SSID, set the Security to WPA and entered my network password.  Nothing happened, so I rebooted.  Still no connection.

So does anyone have any suggestions on how to get wireless networking to work?

Thanks,
Jim

---

### Post by Joe2Shoe on 2008-11-22
Jim,
Find the name of your wifi card (it's usually listed on the bottom of your laptop as a 'wireless divice' or 'wifi device').
Go to System/Administration/Hardware Drivers, and see if your wireless card's drivers are listed.
If so, click on it, then click the 'activate' button below.
Reboot if required (do it anyway).
Good luck.
Joe2Shoe.

---

### Post by Joe2Shoe on 2008-11-22
Jim, sorry I did not read the rest of your message, so ignore my previous post.

Here's my 'configuration' settings.

Right-click your 'wifi' icon (top-right of the screen).
Click "Edit Connections".
Under the "Wireless" tab, click your network's name, then click "Edit'.

Under the "Wireless" tab
Connect automatically: is checked
System setting: is not checked
SSID: name of my network
Mode: Infrastructure
BSSID: blank
MAC address: blank
MTU: automatic

Under the "Wireless Security" tab
Security: WPA & WPA2 Personal
Password: my network's password

Under the "IPv4 Settings" tab
Method: Automatic (DHCP) or "Automatic DHCP (with address only"), whichever works)

Under "Address" section
Address: my IP Address
Netmask: 24
Gateway: 0.0.0.0

DNS Servers: my DNS Server Address
Search Domains: blank

Hope this helps.
Joe2Shoe.

---

### Post by Joe2Shoe on 2008-11-22
Jim,
I took me over a year to figure how to get my wireless working.
If you are using Ubuntu v8.10, you must enable all the repositories to be able to download the needed drivers.
Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

AFTER doing this, the drivers for my Broadcom BCM4306 rev. 02 wifi card were downloaded/installed, and now works!

Good luck.
Joe2Shoe.

---

### Post by jereece on 2008-11-22
I do not see a 'wifi' icon.  In the upper right corner of the desktop, I see the battery power icon, a Network icon, speakers, date/time and then a start button with Jim on it.  When I right click on the Network icon, it has "Enable Netowrking" which is checked and Edit Connections which is what I went to to set up my wireless network.  If I left click on this icon, I get "Wired Network", "Auto eht0" (both grayed out) and VPN Connections.  There is no "wifi" icon.

---

### Post by Joe2Shoe on 2008-11-22
Jim,
Right-click on "Edit connections".
Then follow my instructions, if they are not grayed out.

---

### Post by Joe2Shoe on 2008-11-22
Jim, do this, if it lets you.

Right-click your 'wifi' icon (top-right of the screen).
Click "Edit Connections".
Under the "Wireless" tab, click your network's name, then click "Edit'.

Under the "Wireless" tab
Connect automatically: is checked
System setting: is not checked
SSID: name of my network
Mode: Infrastructure
BSSID: blank
MAC address: blank
MTU: automatic

Under the "Wireless Security" tab
Security: WPA & WPA2 Personal (or whatever encryption you selected)
Password: my network's password

Under the "IPv4 Settings" tab
Method: Automatic (DHCP) or "Automatic DHCP (with address only"), whichever works)

---

### Post by jereece on 2008-11-22
I did all of the above and rebooted.  Still no wireless connection.  Is there not a feature that will look for wireless networks and then allow you to pick one and connect?  If Hardware Drivers shows the driver for my Atherous wireless card is listed Activated and Currently In Use, I would think I should be able to see what wireless networks were available somewhere.

---

### Post by Joe2Shoe on 2008-11-22
I had the same problem; my driver was listed and activated, but would not work until I downloaded all the files from the repositories.  Once I did that and rebooted, my wireless connection worked.

---

### Post by eks on 2008-11-22
If you have an Atheros card and is running Intrepid, take a look at this:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by jereece on 2008-11-22
I downloaded all the updates (~69 total) rebooted and still no wireless connection.  I followed the instructions on [https://help.ubuntu.com/community/Wi...Driver/Atheros](https://help.ubuntu.com/community/Wi...Driver/Atheros), then rebooted and still no wireless. 

Any other ideas?

---

### Post by jereece on 2008-11-22
This finally solved my wireless driver problem - [https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)

I did not realize that Ubuntu could use Windows drivers. 

Why would Ubuntu tell me the driver was installed and active when in reality it was not?  

So far it looks like everything else is working so maybe the wireless glitch will get worked out.

I do appreciate your efforts to help me.

Jim

---

### Post by Joe2Shoe on 2008-11-22
I see.  That's why your driver wasn't listed in Hardware Devices.
Glad you go it sorted out.
Yeah!!!!!!!!
Joe2Shoe.

---

### Post by vuthy.com on 2008-11-28
> **Joe2Shoe said:**
> Jim,
I took me over a year to figure how to get my wireless working.
If you are using Ubuntu v8.10, you must enable all the repositories to be able to download the needed drivers.
Go to System/Administration/Synaptic Package Manager.
Enter password [...]

Thanks Joe.  I was having the same issue and this is exactly what I needed to do.  After the reboot, I activated the newly listed driver for my wireless card and then the options to connect and find networks showed up.

Thanks again! :)

---

### Post by Lostin60's on 2008-11-30
GREAT POST JOE!! I had tried a million things to get my card working. I followed the advice in this post, and when I re-booted I had wireless.  Didn't even need to configue anything.  It goes to show you the importance of regular updating. BTW Joe, if you have not posted this as a stand alone thread, rather than a reply, you really should. Again, a great post.

---

