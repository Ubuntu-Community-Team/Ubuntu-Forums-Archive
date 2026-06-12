---
title: "Wireless Issues-o-plenty"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by packetcreeper on 2008-01-20
Let me preface this by saying that I've followed several howtos on this site, as well as, spent gobs of time scouring Google over the course of 2 weeks or so. And all to no avail.

I'm sure I've managed to screw up some files and/or configurations, and I've reached the point where I simply can't stare at any more of these tutorials or threads. If anyone can help or point me in the right direction, I'd be eternally grateful.

Here's some info...

**Laptop**: Acer Aspire 3680 running Ubuntu 7.10 (kernel 2.6.22-14-386), platform i686, Intel Celeron 1.73ghz, 512MB RAM

**Wireless Router**: Linksys Wireless-G WRT54GS  **Setup**: broadcasting the SSID, channel 10, WPA (1) encryption, TKIP algorithm, DHCP enabled.

************************************************************************************************************

I first began trying to use a wireless card I'd purchased that was reported to work "out of the box". This was the Netgear WG511T (Made in China version). After installing ndiswrapper and trying both the Win2K and WinXP drivers (neither of which worked), I gave up on that.

I've also tried WiFi-radar...which also proved unsuccessful.

I followed this guide - [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539), but it didn't work for me.

In the end, I gave up trying to make the Netgear WG511T work in Gutsy. I've since turned to the internal wireless in an attempt to connect.

If I follow this guide - [http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154), I can actually connect wirelessly _when using the LiveCD only_. This tells me there's a driver loaded for my internal wireless card and it is functioning properly.

If I return to my hdd installation of Gutsy Gibbon, I am unable to connect. I've altered the /etc/network/interfaces file as per the tutorial, but I can't start NetworkManager in Gnome (I removed the panel applet shortly after installing the os). Typing 'nm-applet' in the terminal has no effect. I also tried adding NetworkManager as a panel icon, but that also proved unsuccessful. I uninstalled and reinstalled NetworkManager for Gnome via SPM. Still, no dice.

If I need to post any outputs here, please let me know. I hope someone will be able to help - I'm pretty frustrated and discouraged.

---

### Post by packetcreeper on 2008-01-20
oh well, was hoping for some direction. looks like i'll be wiping my hdd today. :(

---

### Post by Greg Mueller on 2008-01-20
I don't blame you this is insane.

---

### Post by Greg Mueller on 2008-01-20
packetcreeper

After going through most of the BS you have been I followed the instructions here


> If you are having problems connecting to a wireless network with networkManager try this:

1.) Boot from a LiveCD of the version of Ubuntu that you use (this works for Kubuntu, too). Note: You should boot from the LiveCD to eliminate any problems you may have caused by altering settings inadvertently in the network manager in a hard drive installation. This is easy to do.

2.) Click on the Networkmanager icon in the taskbar (upper right of screen in Ubuntu, lower right in Kubuntu).

3.) A panel should open up showing choices for program preferences, and a list of available wireless networks. These networks are displayed by name (essid) in a line with a bar graph showing signal strength. Click on the network's (bar graph) line that you would like to connect to. If the network requires a password, a password dialog will open up and you should fill in the password to connect. (Note: be sure to select the right type for your router's encryption method WPA, WEP-128 bit, WEP-64 bit, passphrase or hex, etc)


and it worked

Maybe if you see some success you can go futher with it
This place needs a BS filter

the full thread is here
[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

After spending a couple of days beating my head against the wall this all worked in 2 minutes   :-x

---

### Post by Greg Mueller on 2008-01-20
I am now typing through my wireless connection
I took out the install disk and rebooted to my previous install.
As the instructions said I right clicked on the two monitors in the task bar. Both Enable Networking and Enable Wireless were checked. I unchecked Enable Wireless and then I rechecked it. It then began to work.

I hope you get yours working

---

