---
title: "[SOLVED] No scanning extensions"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by schaef22 on 2007-10-22
I have been googling, yahooing, and searching these forums but can't find the answer to my prolems.  I am having some issues setting up my wifi on Ubuntu newest release 7.10.  I have installed ndiswrapper, and when I type ndiswrapper -l I recieve a message saying bcmwl5 installed, device present, so I know ndiswrapper is installed.  I have followed the rest of the instructions for linking it to my driver R140747.EXE.  The problem comes when I type the iwconfig command.  When I do this I recieve a message stating lo no wireless extensions  eth0 no wireless extensions.  I don't understand why its not picking up a wlan0???? My wifi light is on on my laptop, and when I go to System --> Admin --> Networking, I don't see a Wireless network configuration.  So for some reason its not picking up my wifi and I don't understand it!!!!  I'm getting pretty frustrated with this.  I have a Dell Insprion 1501 with a 1390 Wireless Card.  Any help anyone has would be greatly appreciated.  Sorry for no screenshots and this message isn't neat and easy to read like others.

---

### Post by spd106 on 2007-10-22
According to the [list]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDell") of supported cards you should really want to go with the [bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") driver through the System -> Admin -> Restricted Drivers Manager.

Then if this doesn't work try [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by schaef22 on 2007-10-22
Thanks for your input.  When I go to do that I click on enable then confirm that I want to enable it, and I get an error saying:  The software source for the package bcm43xx-fwcutter
 is not enabled.  I thought this was because I blacklisted it during my ndiswrapper install, following instructions on this mesage board led me to do that, but I took the bcm43xx driver off the blacklist file and I still get this error message saying it can't be enabled.  I haven't tried logging in as root yet, to try this.  How might I type a sudo command in the terminal to enable this.  Thanks again.

---

### Post by schaef22 on 2007-10-22
Well I apologize for my stupidity, I forgot that after you edit the blacklist file, you need to reboot it to for the changes to take affect.  Well I did that and now its working fine.  Thanks again.  I'm a litle bit of a noob with Linux, I feel like I know enough, but definately still learning.

---

