---
title: "HOW TO: WIRELESS for Toshiba Satellite A135-S7404 in Gusty"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by crazyforpurple on 2007-10-24
I am by no means an Ubuntu expert, but I have been spending an awful lot of time with my terminal and researching my wireless connection the last month or so and so I thought I would post exactly how I got my wireless working on my Toshiba Satellite A135-S7404 IN the new release of GUTSY, in the hopes that it might help someone and save their sanity while trying to set up their wireless!!

The instructions below go through what I did step by step and being a noob myself I have tried to keep them as simple as possible without assuming any prior knowledge of linux. 

The main resource I used when setting up my wireless was the following web page:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and I also had help from lots of wonderful users of this forum and I thank everyone who helped me for that too xxxx

so here goes:

Installing WiFi drivers on Toshiba Satellite A135-S7404

1.Go to System, Administration, Restricted Drivers Manager and then click to disable the HAL driver that is shown. 

2.Restart your Laptop. 

3.Now, although we have disabled the driver we also need to blacklist it:
Go to Applications, Accessories, Terminal and type
gksu gedit /etc/modprobe.d/blacklist 
A file should pop up in another window, scroll to the bottom and add
blacklist ath_pci
then save and close this window.

4.Install the kernel headers:
Go to Applications, Accessories, Terminal and type
sudo apt-get install linux-headers-$(uname -r)
enter your password when prompted
next type
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential

5.Download and Install the current version of ndiswrapper from here:
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
I chose to download the latest version which is currently in testing and the direct link for that one is here:
[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=167243&release_id=547277](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=167243&release_id=547277)
download and save the version on ndiswrapper to your desktop (if you are using Firefox it should automatically default to save it to the desktop if you click on “save to disk”)

6.Next we need to unpack our download. In the terminal type 
cd /home/[username]/Desktop 
in my case this is 
cd /home/mommy/Desktop 
this changes the directory to the desktop where we saved ndiswrapper. (note the capital D for desktop... this does make a difference)
next type
tar xvfz ndiswrapper-[current version].tar.gz
in my case this was 
tar xvfz ndiswrapper-1.49rc4.tar.gz 
then we have to change to the ndiswrapper directory by typing
cd ndiswrapper-[current version]
in my case this was
cd ndiswrapper-1.49rc4 

7.Next we install ndiswrapper:
type
sudo make uninstall
and enter your password when prompted. you will get some code and then this message:
“Run uninstall as many times as necessary until no "removing" messages appear below. ” do this by typing the command sudo make uninstall as many times as you need until you no longer see the “removing” message.
next type:
sudo make
now we need to run in fakeroot by typing:
fakeroot
and then
sudo make install
read carefully the output of these steps, if there are any errors reported, you will need to try installing again. It may be required for you to run in fakeroot during the entire process.
NOTE: I did get one error message when I went through the instructions so I went back and did these last 4 steps all in fakeroot and I still got the error messages but I continued onto step 8 anyway).
8.Installing Packages:
I choose to connect my laptop to the internet with the wired connection for simplicity, but if you can't do this then you can access the files from another computer that is connected to the internet, and transfer them to your desktop via either a USB flash drive or CD-R etc....
Go to system, administration, synaptic package manager, 
type in your password
in synaptic package manager, go to settings, repositories, and in the Ubuntu Software tab look for “downloadable from the internet” and make sure that multiverse and universe are checked. Close this box and click “apply” in synaptic package manager if you need.
In the synaptic package manager, click on search and type ndisgtk. when you get the results of the search click on ndisgtk and mark it for installation. Click apply to install ndisgtk. Once it has installed, close the synaptic package manager. 

9.Now we have to identify the wireless card:
in the terminal type:
lspci
look through the long list of results for something that looks like your wireless card.. mine gave me this result:
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01) 
next type 
lspci -n
again, look through the list of results for one that corresponds to the result above mine was the result:
04:00.0 0200: 168c:001c (rev 01) 
and so the pcid for my card is 168c:001c.

10.Now we need to get the drivers to work with ndiswrapper, I have tried using windows drivers from an installation cd but they dont work as well as ones that are known to work with ndiswrapper. 
go to
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)
and look through the list for drivers that are most similar to yours looking both at the pcid number, chipset and the manufacturer etc...
for my laptop the best driver was this one:
[http://www.atheros.cz/](http://www.atheros.cz/)
as we know from above that the card is the  AR5006EG we can click on the appropriate link to get the windows driver, I used the windows XP driver from:
[http://www.atheros.cz/download.php?atheros=AR5006EG&system=1](http://www.atheros.cz/download.php?atheros=AR5006EG&system=1)
download and save the driver to the desktop as before. 

11.Find this folder (a zip file) and right click on it and choose “extract here”.

12.Click on system, Administration, Wireless windows drivers, and enter your password. In the window that pops up, click “install new driver”, in the drop down menu find the desktop, the folder that was just extracted (not the one you downloaded) and find the .inf file that is in there, then click install. It should then come up saying that the hardware is present. 

13.Check to see if the drivers have been installed, in the terminal type:
ndiswrapper -l
I get:
mommy@mommy-toshiba:~$ ndiswrapper -l 
net5211 : driver installed 
        device (168C:001C) present (alternate driver: ath_pci) 
(This is good! we wanted to see the device and driver present, dont worry about the alternate driver as that was blacklisted at the beginning).

14.Now we need to load the driver into the memory: In the terminal type:
sudo depmod -a
sudo modprobe ndiswrapper
and 
tail /var/log/messages
Check for error messages. I get:
mommy@mommy-toshiba:~$ tail /var/log/messages 
Oct 24 13:49:56 mommy-toshiba kernel: [   27.740000] lo: Disabled Privacy Extensions 
Oct 24 13:58:27 mommy-toshiba kernel: [  538.456000] ndiswrapper version 1.49rc4 loaded (smp=yes, preempt=no) 
Oct 24 13:58:27 mommy-toshiba kernel: [  538.548000] ndiswrapper: driver net5211 (,06/21/2007,5.3.0.56) loaded 
Oct 24 13:58:27 mommy-toshiba kernel: [  538.548000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16 
Oct 24 13:58:27 mommy-toshiba kernel: [  538.548000] ndiswrapper (ZwClose:2230): closing handle 0xf03fc328 not implemented 
Oct 24 13:58:27 mommy-toshiba kernel: [  538.960000] ndiswrapper: using IRQ 16 
Oct 24 13:58:28 mommy-toshiba kernel: [  539.164000] wlan0: ethernet device 00:1b:9e:55:c8:70 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: '', 168C:001C.5.conf 
Oct 24 13:58:28 mommy-toshiba kernel: [  539.168000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
Oct 24 13:58:28 mommy-toshiba kernel: [  539.168000] usbcore: registered new interface driver ndiswrapper 
Oct 24 13:58:28 mommy-toshiba kernel: [  539.360000] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
I think this is all okay, theres just a little more tweaking to be done with the wlan0. Type 
ifconfig
and 
iwconfig
to see the results, we are looking for the wireless card with an interface of wlan0. If it doesnt appear then the driver is not working properly. My results were:
mommy@mommy-toshiba:~$ ifconfig eth0      Link encap:Ethernet  HWaddr 00:1B:38:44:E8:EA  
         inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::21b:38ff:fe44:e8ea/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2584 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2162 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2149106 (2.0 MB)  TX bytes:470117 (459.0 KB) 
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

wlan0     Link encap:Ethernet  HWaddr 00:1B:9E:55:C8:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:16 Memory:d8000000-d8010000 

mommy@mommy-toshiba:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

15.Now when I go the the network applet on my toolbar at the top I have many options to connect to all the wireless networks that are around. I click on our home one and enter the details....and it connects!!! (for now!...) 

16.We now need to load it at start up so that it works every time.... in the terminal type 
sudo ndiswrapper -m
then type:
gksudo gedit /etc/modules
and in the window that opens add the word ndiswrapper to the end of the list. Save and close this window. 

17.Restart and your wireless should be working fine!!!
	

love lucy xxx

---

### Post by maxesanu on 2007-11-23
Hello, thank you for the great how to. It worked perfectly in my case. I got to see my adapter, got to see the networks and to connect. However, I would need to put my wifi card in monitor mode and as far as I know this is not supported if you have the windows drivers emulated with ndiswrapper (pardon me my terminology as I am a complete newbie to Ubuntu). 

I have a Toshoba satellite A215-S4697 laptop and an Atheros wireless card with the AR5006EG chipset and I couldn't get it working with madwifi drivers although they say my chipset is supported. I tried everything, from installing restricted modules in Synaptic for my kernel version, to installing the latest version of madwifi-ng and my iwconfig still shows only: 

lo        no wireless extensions.

eth0      no wireless extensions.

However it used to work perfectly with ndiswrapper, but like I said before, I need it in monitor mode and I can't set it with ndiswrapper. I have placed the ath_hal in disabled modules and I have placed ath_pci in modules, however I think they do not appear when I type the command which shows me the loaded modules (can't remember it right now).

There are a whole bunch of how to's on ubuntu forums about how to get virtually any Atheros based card to work, even the newest threads on madwifi site says that Atheros cards should just work in Ubuntu.

Your how to with ndiswrapper work perfectly for me, I was wondering if you or anyone else could write a detailed how to on now to get the Atheros AR5006EG card working in Ubuntu running on a Toshiba laptop using the native linux drivers. I would like to mention that I have the x86-64 version of Ubuntu 7.10. Thank you in advance. I hope to get help on this one. I promise to try your advices on a fresh installation of Ubuntu, so you don't have to worry that I messed up something trying to fix it.

Cheers.

---

### Post by Tedificator on 2007-12-13
Hi,

Would anybody know what I'm doing wrong at step 7?  When I type "sudo make uninstall", it says:

ted@ted-laptop:~$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.

---

### Post by jsharkey on 2007-12-21
Just a heads up that the S7403 has an Atheros chipset which is now directly supported by madwifi directly.  It was just released a few days ago, so you'll probably need to download, patch, and compile a new version of madwifi.  Here's more information from the madwifi site:

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Also I've been working to get wireless, sound, and graphics working on my S7403 under Gentoo linux.  Here is more information about what I did to get everything working:

[http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_A135](http://gentoo-wiki.com/HARDWARE_Toshiba_Satellite_A135)

---

### Post by asplodzor on 2008-04-16
Thanks crazyforpurple! I've been trying to get wifi working on my Toshiba on and off since I installed about half a year ago, and had all but given up until I read this post. It works marvelously.

---

