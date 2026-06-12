---
title: "Ubuntu and WPA encryption"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by mevets on 2006-11-30
I'm having trouble connecting to the internet with Dapper. It recognizes my notebook's internal wifi.

I have been going to System > Administration > Network Settings. The wireless connection is active and I then goto it's properties. There it finds serveral SSIDs of networks including my own. It asks for a WEP key, but I know for certain WPA (AES) is the encryption used for my network. From there I press ok and it takes a very long time to "Activate interface eth1".

Does my problem stem from the fact it wants a WEP key or am I possibly doing something else wrong?

---

### Post by Spin Doctor on 2006-11-30
Mevets,

Did you read this how-to about WPA and wireless?

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

In my system, with a DLINK DWL g650+, I could never get it to work with Dapper, but I upgraded to Edgy and then it works...however with ndiswrapper and network manager...

---

### Post by Hrothgar on 2006-12-01
> **Spin Doctor said:**
> Mevets,

Did you read this how-to about WPA and wireless?

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

In my system, with a DLINK DWL g650+, I could never get it to work with Dapper, but I upgraded to Edgy and then it works...however with ndiswrapper and network manager...

I have the same card as you. Actually mine is not the plus version. It worked fine in breezy with the madwifi drivers and I just upgraded to edgy and it worked out of the box once I installed the restricted modules. My problem is i can connect to the net but knetworkmanager cant find any network hardware not even the wired.

---

### Post by mevets on 2006-12-02
Thanks,

I read the docs and I downloaded the package. I let the package manager install it. From here I don't know what I should do. Also, I'm not sure by installing using the package manager I should continue work in the terminal. Any clues?

---

### Post by Spin Doctor on 2006-12-03
Did u get network manager to startup?

Read the following additional info:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by tripstar on 2006-12-09
> **mevets said:**
> n my system, with a DLINK DWL g650+, I could never get it to work with Dapper, but I upgraded to Edgy and then it works...however with ndiswrapper and network manager..

I just got a hold of Ubuntu 6.10. I had been using Suse Linux 10.0. I'm using the DWL-G650 hardware ver B5, firmware version 2.54. The adapter worked perfectly under Suse 10.0. It is not working under Ubuntu. I have the network icon. I right click on the icon and get the "Settings for interface ath0" window. When I click the "up-down" arrow on "Password type" select box, the only choices are Hexadecimal and Plain. No WPA.

I re-downloaded the network-manager-gnome app, in case I had the incorrect version. The result is the same. So, (1)Do I have the Edgy version or not? And (2)if it IS the Edgy version, do I still have to download and install the firmware and the driver for this card? (3)If the firmware and driver are already present, what the heck am I doing wrong?:confused:

---

### Post by fredj on 2006-12-11
The ordinary network configuration tool cannot do WPA.
You need to edit the /etc/network/interfaces file and comment
out the lines that refer to your wireless card. Then install
network-manager and network-manager-gnome. Then restart and use
the systray icon to configure and connect to wpa wireless
networks.

---

### Post by mevets on 2006-12-15
hey, thanks for the clue in on having to comment the file out. What is the character to comment lines out though?

---

### Post by Spin Doctor on 2006-12-21
> What is the character to comment lines out though?Use ## infront of the lines you want to comment out.

---

