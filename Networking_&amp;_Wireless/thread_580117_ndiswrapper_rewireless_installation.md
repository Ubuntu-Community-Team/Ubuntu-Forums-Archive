---
title: "ndiswrapper re:wireless installation"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by halsport on 2007-10-18
Tried to understand the "ndiswrapper" instructions.

I am not a computer geek!  I wish I were and then I would be able to be on the internet with Ubuntu.

HELP.  There has to be a way for us "stupid regular folks" to get help in getting our wireless to work.

It seems that everything else is working great.  If someone has instructions that are clearer than the "ndis wrapper" instructions, please let me know.

---

### Post by spd106 on 2007-10-18
Which instructions are you following? Can you provide a link?

The directions in the Ubuntu system help are quite good, look under Connecting to the Internet -> Wireless Cards.

Also see the help [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), though it is a little too detailed.

---

### Post by unisol on 2007-10-18
you can try this:
ndiswrapper is a project that provides a kernel module to load Windows NDIS wireless card drivers under Linux. NDIS stands for Network Driver Interface Specification and is the Windows/DOS driver interface. The ndiswrapper module wraps around this driver, acting as a translator between it and the Linux kernel. 

You can use ndiswrapper to get a great deal of cards working that don't have a native Linux driver. There is a lot of information on the ndiswrapper wiki (discussion site) about various card and driver combinations that work well, but it often works with other cards too. There is no guarantee it will work perfectly with your card, however. Although ndiswrapper has become many orders of magnitude more stable over time, it still can very rarely crash or lock up your Linux system. You can visit the ndiswrapper wiki here. 

Installing ndiswrapper is not for point-and-click users. It requires using the command line and being able to locate drivers and specialised instructions for your card. If this sounds like something you'd have difficulty doing, ask a geek to help. Your local Linux Users Group is a great place to find a friendly Linux guru who can help you with this. 

Installing ndiswrapper
Many Linux distributions have binary packages for ndiswrapper. Use the package updating tool for your distribution to make sure you have the latest version available installed. Some distributions separate out the driver and the command-line tools into two packages, so check to make sure that you have ndiswrapper-utils or any similarly named package installed if typing ndiswrapper at the command line as root results in command not found. 

Figure 1. Installing ndiswrapper 

Identifying Your Card
To install and set up ndiswrapper, you need to know the chipset of your wireless card and find a suitable Windows driver to use. Then, you need to install ndiswrapper either from a package or by compiling the sources. 

The chipset of your card differs from the brand or model. It refers to the actual chips inside the card that control its function. So a planet-, belkin- or genius-branded card could all have the same chipset and be able to use the same driver. Some manufacturers even have been known to use different chipsets in cards with the same model number. 

Figure 2. The KDE Info Center 

As shown in Figure 2, I'm using the KDE Info Center (kinfocenter) to get information about my devices. Your wireless card should show up under the PCI section, regardless of whether the card is built-in to your computer or is a PCMCIA card. The last item in the list in Figure 2 is my wireless card. According to this, it has a Realtek chipset, model 8180l, revision 20. This is a little cryptic, but all we need to do with this information is match it up to a driver that works with ndiswrapper. 

If you don't have a graphical tool like the KDE Info Center at your disposal, you can get the same information from the command line using the command lspci. If your shell tells you the command is not found, try specifying the full path--often /sbin/lspci. 

Armed with the knowledge of what chipset your card is, the next port of call is the ndiswrapper wiki's card list. 

Find the Driver
In some cases, you may have the original Windows driver disk. You can use this disk instead of downloading a driver, although you're likely to get a more recent driver if you download one. The ndiswrapper wiki page says that most people have had success using the Windows XP driver from the chipset manufacturer's Web site. Once you've located a driver for your card, copy it from your driver CD/floppy or download it to disk and extract it. 

If your driver is in the form of a Windows self-extracting zip file with a .EXE extension, it's possible that Linux unzip can still extract it. Try using unzip file.exe from the command line. Locate the driver installation instructions file. It will have the extension INF. If there is more than one of these files, the ndiswrapper wiki will often point you to which one you should use. 

This step requires some command-line use. Open up a terminal and change to the directory containing your drivers. If you use Konqueror as your file manager, you can bring up a terminal in the directory you're already in by using Window&#8594;Open Terminal Emulator. This lets you see a graphical representation of the current directory in the top pane, and use the command line in the bottom pane. You need root privileges for this step. Either use the su - command to change to the root user, or if you have your system set up for it, use sudo. 

# ndiswrapper -i filename.INF
This causes ndiswrapper to create a configuration directory in /etc to hold the driver file and configuration pertaining to the driver and install the driver to it. Now if you issue the command: 

# ndiswrapper -l
you should see something like the following: 

dessa@holly:~> /usr/sbin/ndiswrapper -l
net8180         driver present, hardware present
To load the module, type modprobe ndiswrapper as the root user. To set up the ndiswrapper module to be loaded on boot, type: 

# ndiswrapper -m
This writes out a line in a system configuration file--usually /etc/modprobe.conf--to tell the system that your wireless card uses the ndiswrapper driver. 

Set Up Networking
Now that you have ndiswrapper installed and a driver for your card, you should be able to set it up using the networking tools that come with your distribution. Here, I'm using SUSE 9.3, but these settings would apply no matter what distribution I'm using. 

The ndiswrapper device is called wlan0, which means the first wireless networking device on the system. If the ndiswrapper -m step completed correctly, your system knows that the wlan0 device and the ndiswrapper driver are supposed to go together. 

Generally, if you have a wireless access point set up, you'd enable getting an IP address assigned via DHCP. If you were going to use a static IP (one you specify, rather than one assigned to you by your wireless router), you'd specify it here. I'm also adding in the ESSID, which is the name of the access point to which I want to connect. If your access point is using encryption, and you have to specify a WEP key, this is the place to do so. It might require trying a few different options until you find the settings that work best with your particular card. If you have any difficulties here, referring back to the ndiswrapper wiki can give you hints about specific options required for your card. 

Figure 3. One Step in Setting Up Networking 

Figure 4. Another Step in Setting Up Networking 

Potential Problems
It's very difficult to describe a method that will work on every possible Linux distribution. What if these instructions don't work for you? A few minutes spent in troubleshooting and gathering information makes it much more likely that you'll find some help. Your first port of call should always be Google. Try to search for "ndiswrapper SUSE", replacing SUSE with the name of your distribution. 

1) Check that the module is loaded: open up a terminal and type in lsmod. This shows you a list of the currently loaded driver modules. Does ndiswrapper appear in this list? If it doesn't, try typing modprobe ndiswrapper and make a note of any errors. No output at all means the module loaded fine. 

2) Check that the card is associating with an access point: open up a terminal and type iwconfig as root. You should see some output something like this: 

wlan0     IEEE 802.11b  ESSID:"internet@home"  Nickname:"holly"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:3A:51:E5
          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr=2432 B   Fragment thr=2432 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-72 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
If the part after ESSID reads off/any and the part after Access Point is full of 0s, try manually associating. Type iwconfig wlan0 essid Name of your access point here, and see if the lights on your card light up. 

3) Check that the card has a valid IP address: open up a terminal and type ifconfig as the root user. Look for the section that says inet addr under the wlan0 section. Do you have a valid IP address there, on the right subnet for your network? If so, try to ping some things on your home network. Try to ping your wireless access point or any other computers to figure out if you have any connectivity at all. 

4) Check your default route: open up a terminal and type route -n as the root user. Do you have a line that starts with 0.0.0.0? Under the Gateway column, does it show you the address of your router? 

5) Check your DNS: if you can ping local machines by their IP addresses, but you cannot see sites on the Web, it's possible you don't have correct settings for DNS.

---

### Post by kevdog on 2007-10-18
Check out the ndiswrapper link in my signature.  Its fairly straight forward although you will need to use the command line.

---

