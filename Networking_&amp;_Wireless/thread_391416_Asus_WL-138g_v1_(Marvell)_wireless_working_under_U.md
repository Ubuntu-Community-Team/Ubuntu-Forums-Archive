---
title: "Asus WL-138g v1 (Marvell) wireless working under Ubuntu 6.10 AMD64 with WPA"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by Jouke74 on 2007-03-23
* This may also work for other cards; change the Asus windows driver into your cards windows driver.
* Problem is you need an internet connection to get all the stuff (1&2).
* I assume you don't have a problem using Gnome-network-manager.
* I am not taking any responsibility for any damage to your files or system.
* I started using Linux two months ago, so I am NOT an expert.
* This **won't** work on Dapper (crashes system even with native driver removed).


**1.** Download the following Windows 64 bit driver package from Asus or mirror, note that this is not the most recent 64bit driver, and it may therefore be difficult to find it. 

	> WIFI_V2712_64bit.zip

Extract the following 4 files from this driver to your home (or any other) directory.

	> Mrv8knt.inf
	> MRV8K50.sys
	> MRV8K51.sys
	> MRV8Kx64.sys


**2.** Download **ndisgtk_0.6-0ubuntu1_all.deb** from 
[COLOR="Red"]
[http://packages.ubuntu.com/edgy/net/]("http://packages.ubuntu.com/edgy/net/")
[/COLOR]
and save it also in your home (or any other) directory.


**3.** Start Ubuntu 6.10 Edgy Eft AMD64 if you're not there already.


**4.** Open Synaptic Package manger

Install the following software packages from the original Ubuntu CD:

	> ndiswrapper utils 1.5
	> ndiswrapper utils 1.8
	> network-manager
	> Gnome-network-manager

Check if the following packages are installed:

	> ndiswrapper-common
        > wpa_supplicant
	> Python 2.4
	> Python-glade2
	> Python-gtdk2


**5.** Open a command terminal and do the following (you can use tab to finish typing the file name):

[SIZE="4"]sudo dpkg -i ndisgtk_0.6-0ubuntu1_all.deb[/SIZE]	

This will install the graphical Ndiswrapper frontend.


**6.** From the administration menu select Wireless Networks which is now added.

Select add driver. 

Navigate to the Home directory where you placed the INF file.

Click on the Mrv8knt.inf file and let the program install the Windows driver. Afterwards it should say that the hardware is present.


**7.** Edit the modules file to include ndiswrapper at startup:

[SIZE="4"]sudo gedit /etc/modules[/SIZE]

Subsequently add plain **ndiswrapper** at the bottom of the file.  

Close and save the file. 


**8.** Edit the /etc/network/interfaces file. Here it becomes a bit tricky, because I configured the system to let the gnome-network-manager take care of all the connections. However, if you have a working wired connection you might loose the settings for it.

[SIZE="4"]sudo cp /etc/network/interfaces /etc/network/interfaces.orig[/SIZE]

Makes a precautionary backup.

[SIZE="4"]sudo gedit /etc/network/interfaces[/SIZE]

Now clean out the file except for the loopback interface so it looks like this:

[SIZE="3"]		# This file describes the network interfaces available on your system
		# and how to activate them. For more information, see interfaces(5).
	
		# The loopback network interface
		auto lo
		iface lo inet loopback

[/SIZE]

Save this file.

Alternatively you can use the Networking option in the menu and make sure that all network devices are unconfigured. Here you can also check if your Asus wireless card is now present.


**9.** For some reason the nm-applet = gnome-network-manager needs the icon cache to be resfreshed, otherwise it may crash with the error "could not find some required resources" at the next reboot. In order to do this type the following in the terminal:

[SIZE="4"]sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/[/SIZE]


**10.** Reboot Ubuntu


**11.** If everything goes well you should see now the gnome-network-manager starting to work after you log in. It's the small monitor in the right corner of the screen. Click on this monitor and there should be you wired connections as well as all wireless networks in your area.

Click on the network to which you want to connect.

Fill in your password and select which protocol to use (WPA / WEP etc).

And let it connect to the network (might take a bit of time).

After the first connection the network manager will ask for a master password for the keyring. I presume it uses this to safeguard all saved passwords you use to connect to different networks. So type a password here. From now on, if you reboot again, it will ask for the keyring password in addition to your normal login password. I don't really have a problem with that, but you might want to check out the forum to look for a way of integrating this at boot.

Thanks for all the people who put the puzzle pieces over this forum, I simply made the puzzle....

[SIZE="4"]JJH[/SIZE]

---

