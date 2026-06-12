---
title: "Quirky Wireless Problems -Kubuntu"
date: 2005-08-26
forum: Networking &amp; Wireless
---

### Post by hbweb500 on 2005-08-26
First off, I am running Kubuntu 5.10 on a Dell Celeron 2.4ghz with a D-LINK DWL-G510 wireless pci card.

I have installed wireless cards before by using ndiswrapper, so I knew what to do (I think). I installed the card, ndiswrapper listed it as being correct for the hardware, and I thought I was finished.

Wrong.

I modprobe'd ndiswrapper and tried ifconfig. The card wasnt listed. I ran iwconfig, and it was. There was a note, something about the driver being compiled with version 17 of the wireless extensions instead of 18. Nothing pings, not even my wireless network computers, however iwconfig lists the ESSID of my network and the speed, etc...

I go into the KControlPanel and navigate to the network settings. There in the box it shows the two available networks: eth0 and wlan0, but both are grayed out. A red X is next to both, showing they are disabled. 

Whenever I click "Administrator Mode" and the bottom and enter my root password, the control panel momentarily gains the red border (as it should), and then returns to the index page. I go back to network settings, and it is not in admin mode. This could just be due to my newness with Ubuntu and its root priviledge setup...


Thank you for your time and help,
Jeff

---

### Post by hbweb500 on 2005-08-26
Ok, never mind, this has been resolved. To all of those who want to know what I did:

First I ran 'ifconfig wlan0 192.168.2.2' to set a static network ip. Then I ran 'sudo kcontrol' to gain root priviledges in the control center, went over to network settings, and configured.

---

### Post by jasmuz on 2005-10-04
Hello there!

Wich revision of the D-Link DWL-G510 are you running? A or B?

I have the A revision, a Marvell Chipset and i have no idea how to make it work,  could you help?

---

