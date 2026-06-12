---
title: "Help required in installing Linksys WUSB11V26.."
date: 2005-07-05
forum: Networking &amp; Wireless
---

### Post by ncrr on 2005-07-05
I am trying to install the Linksys WUSB11V26 external USB adapter with Ubunto 5.04, and have no luck. I tried using ndiswrapper and the Windows driver for the Linksys WUSB11V26 (netusb.inf) but that did not help. The other Realtek based wired PCI NIC is working fine. Any help or pointers will be appreciated.

Thanks,

---

### Post by ncrr on 2005-07-07
The ATMEL firmware did not work for me with my Linksys WUSB11V26. It took me two days to figure it out and I finally managed to get a Linksys WUSB11V26 working with Hoary Hedghog 5.04. I installed the ndiswrapper-utils, downloaded the Windows 98 drivers for this Wireless USB from Linksys Support website, and was able to get it working. Here are the steps:

1. sudo apt-get install ndiswrapper-utils (to install the ndiswrapper-utils)

Download the driver from Linksys.Be sure to download the drivers. Do this on a Windows machne if possible since this is an exe file and creates its own directories. Go to the folder where the drivers were extracted and copy this folder to a folder in your Desktop on Ubuntu.

Open a terminal and do:

cd /home/USERNAME/Desktop/Drivers (or any other folder you have created)
sudo ndiswrapper -i NETUSB.INF
sudo ndiswrapper -l
(This should list the driver)

sudo -m netusb

edit the file /etc/network/interfaces as follows:
# iface eth0 inet dhcp (My PCI wired card is disabled here)
auto wlan0
iface wlan0 inet dhcp (I use DHCP on my network)
wireless_keymode restricted
wireless_key XXXXXXXXXXX (Replace with your Wireless Key)
wireless_essid XXXXXXXX (Replace with your SSID from Router)

Shutdown; conect your WUSB11v26 and you should be set.

I am thrilled that I finally got this working. I was almost beginning to give up.
 :grin:

---

