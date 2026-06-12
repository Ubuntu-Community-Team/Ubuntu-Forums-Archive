---
title: "Success: Linksys WPC45G v4 PCMCIA wireless card and WEP with ndiswrapper"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by sdegrace on 2007-05-16
I've been having tremendous trouble getting the Linksys WPC54G v4 PCMCIA wireless card to work on my Presario 2100 under Feisty Fawn using ndiswrapper. NOTE: this is NOT a Broadcom chipset, this is INPROCOMM. I am using Feisty Fawn with the aim of demonstrating that all my hardware works using only the LiveCD before attempting an install. I made this work on LiveCD only, with no need to reboot or even restart networking.

After struggling I was able to make it consistently connect to my Linksys wireless router as long as I did not use any security settings. However, I was not prepared to run with absolutely no security. I am using only WEP as I am prepared to accept a network which is not secure - this is with the goal of allowing my friends easy and flexible access while keeping out casual snoopers and moochers, which is fine in my neighborhood.

As it turned out, the problem was the choice of drivers. The driver that the ndiswrapper list says to use is the wlipnds.inf driver from Linksys which it gives a link to. This driver does not fully work. The right driver is neti2220.inf, available from [this site]("http://www.laptopvideo2go.com/forum/index.php?showtopic=7172&hl=ipn2220"). When I use this driver my WEP worked without a hitch. This is the process I followed:

1. Booted up Ubuntu connected to my router wired.
2. From Synaptic searched for ndis and installed ndiswrapper-utils-1.9
3. Opened a terminal. Did sudo -i for convenience, you can just sudo all these commands individually.
4. ifdown eth0
   Not going to use it anymore, kill it early.
5. mkdir /mnt/win
   This step is just because I had the drivers downloaded in Windows and saved on the hard drive. Obviously do this part differently depending on where you put your drivers, if you dled them in Ubuntu etc.
6. mount /dev/hda1 /mnt/win
7. ndiswrapper -i /mnt/win/INPROCOMM/neti2220.inf
8. ndiswrapper -l
   I see that my driver is installed and the hardware is detected.
9. modprobe ndiswrapper
10. iwconfig
   Just to look at what we have
11. ifconfig
   Ditto.
12. ifdown wlan0
   For thoroughness.
   **For the following, use info for your network obtained above:**
13. iwconfig mode Managed
14. iwconfig channel 8
15. iwconfig essid MY_LAN
16. iwconfig key MY_KEY
17. ifup wlan0

Connects nice, seems stable. Working good so far. Hope this info is helpful to someone!

Stephen

---

### Post by booticon on 2007-05-17
Is ndiswrapper mandatory for network adapters? I ask because lspci shows that my WPC54G v3 (Broadcomm) is installed in a fresh install of Feisty.

---

### Post by sdegrace on 2007-05-17
It depends. There is a non-ndiswrapper driver for Broadcomm cards. That doesn't help me, however - to the best of my knowledge, there is no driver for the IPROCOMM chipset in v4, and from what I have been able to discover this may be partly due to them going out of business or something - anyway, info was very hard to find. ndiswrapper works for me, though :). My understanding is that ndiswrapper is the measure of last resort, and it does allow some hardware to be used that otherwise could not be supported.

---

### Post by sdegrace on 2007-05-22
Just to follow up, I finally did wipe WinXP and install Ubuntu on my Presario 2100 laptop. It went well and I'm really pleased with the outcome. I managed to set up wireless so that it works really flawlessly. For anyone with a similar setup, here are the additional steps I followed to allow wireless to start seamlessly at startup and to have a nice graphcal interface to control it (I never did get network-manager-gnome, the default network manager, to work). There may be other ways, but this works:

1. Open a terminal. Either get a root shell by typing sudo -i, or be nicer and preceeding the commands below with sudo.

2. ndiswrapper -m

3. echo ndiswrapper >> /etc/modules

4. Go to Applications -> Add/Remove Programs, set to All Open Source, and search fo wifi. Install wifi-radar.

5. Go to Applications -> Internet -> Wifi-radar. In Wifi-radar click Disconnect, select your network and click Connect. Put in your connection settings when prompted. You should get a connection and an IP if your settings are right.

4. gedit /etc/network/interfaces
Remove all interfaces you're not using (at minimum must keep wlan0 and lo, I also kept eth0). My wlan0 section looks like this, the last line I had to add:

auto wlan0
iface wlan0 inet dhcp
up wifi-radar -d

After this, when I restarted I had a flawless internet connection. I have had no stability or speed problems.

My other observations are not related to wireless.

It's a lot of trouble to play DVDs and RealMedia. I figured out how to install libdvdcss2, I installed VLC Player, and I went with the xine version of Totem instead of the gstreamer version, and all my media work the way I want so far. Even though there are some barriers here to new users, I understand *why* this is hard and I don't think much can be done about it.

Samba is another matter. When you share folders with Samba, Gnome should come right out and tell you you need to use smbpasswd to set up a password for the share to work, and preferably it should provide a convenient graphical interface right away so users aren't exposed to the guts of how it works. This is a hole.

DRM is another disturbing matter. DRM is disturbing in and of itself. Microsoft is slowly tightening the screws so that the entire OS conspires to control your use of content you purchased, and if Microsoft DRM becomes enough of a universal standard that major content providers cater to solely, then MS will obtain essentially a monopoly on almost all of the content the majority of people actually want and have access to. This will essentially push all other OSes out of the mainstream desktop for almost all users. I had to give up a few DRM-protected files in order to go to Ubuntu... Not an easy or uncontrovertial issue to address, but I think other OSes including GNU/Linux distros need to incorporate some kind of less evil support for some form of DRM or they're toast and Microsoft wins the OS wars decisively and forever and all "options" live permanently on the margins.

---

### Post by javedan on 2008-03-27
Thank you sdegrace.  Took me forever but the neti200.inf driver works!  The .inf file available from linksys simply does not work.   Thanks again.

---

### Post by sdegrace on 2008-03-28
Glad to help. :)

---

