---
title: "Installing RT73 (RT71) drivers for a belkin wireless usb stick"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by TRApReGeTr on 2008-06-03
I just installed Ubuntu 8.0.4 Server on my laptop and I'm trying to follow the instructions outlined in the thread below to get my 802.11g belkin usb to work:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)

The problem is when I try to run make in step 7 I get:

```

root@Fl9359-UbntuSrvr:/usr/src/rt73-cvs-2008060202/Module# make
The program 'make' is currently not installed. You can install it by typing:
apt-get install make
bash:make: command not found
root@Fl9359-UbntuSrvr:/usr/src/rt73-cvs-2008060202/Module#apt-get install make
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package make
root@Fl9359-UbntuSrvr:/usr/src/rt73-cvs-2008060202/Module#

```

My question is, does anybody have the steps involved on how to install this package? Based on what I'm finding on the net, build-essential seems to be what I need. I tried using apt-get but got the same stating it couldn't find the package. If someone could point me in the right direction, I'd appreciate it. Thanks in advance.

---

### Post by TRApReGeTr on 2008-06-04
Ok, I went to the sticky under this forum and followed the link to a different script to install my drivers except even that hasn't worked. This is making me wonder if I'm installing the correct drivers or not. 

The instructions I'm following now is at:

[http://ubuntuforums.org/showthread.php?p=4732883](http://ubuntuforums.org/showthread.php?p=4732883)

The script seems to go through fine, except no lights appear on my wireless usb stick. I brung the interface down and back up and even restarted the server with no luck. So my question now is, how do I verify the integrity of the compiled rt73 module. 

Running this script did correct several issues I was having for instance it seemed to have compiled build-essential for me since running [COLOR="DimGray"]apt-get intstall make[/COLOR] confirms that I already have the latest version installed. Before it didn't. *Not sure why this wasn't included in the server install to begin with.*

Anyhow, from what's left on the screen for me to read after running it again it shows the following..

```
wlan0: ERROR while getting interface flags: No such device
*   COnfiguring new device..
Error for wireless request "Set ESSID" (8B1A) :
  SET failed on device wlan0 ; No such device. 
Error for wireless request "Set Encode" (8B2A) :
  SET failed on device wlan0 ; No such device. 
*   Running dhclient..
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
*   Script complete, You should now be able to connect, if not -Read the FAQ.
```


lol.. I just read the very last line. I'll go ahead and do that right now but if someone has any suggestions I'd appreciate it. If not, hopefully the FAQ will have what I'm looking for.

---

### Post by james_vanb on 2008-06-04
I have Belkin F5D7050 installed on an old Dell Latitiude CP M233St with xubuntu hardy herron and a Desktop running ubuntu hardy herron. Responding on Desktop using Belkin F5D7050, v. 3000 with rt73 driver. Install has been the same using ndiswrapper and the install cd as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```


I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

---

### Post by linkunderscore on 2008-06-13
I screwed up after the blacklist section. I forgot to reboot (i had to write down teh instructions then boot back into ubuntu and try it..I left that part out. 

If i follow these same steps again will it work again (it didn't work for me the first time).

---

### Post by linkunderscore on 2008-06-13
HWELLL YEAAAA 

it worked!! woo  


Thanks man :popcorn::guitar:

---

### Post by TRApReGeTr on 2008-06-22
Nice to know it worked for somebody. Will re-install OS clean to make sure none of the garbage from my previous tries gets in the way. Will post with updates.

---

### Post by jtbalt on 2008-07-20
I've followed these directions and all seems well until the last step.  When I enter sudo ndiswrapper -m I get a message that the command is deprecated.  I'm not sure what to do from here, or whether or not this command is critical to getting it working.

My network manager shows that I'm connected to my wireless network, yet I cannot browse or download updates.  On very rare occasions it will work after booting, only to stop working minutes later, though network manager still shows a good connections.

My usual methodology is to resintall Hardy, use an ethernet connection to download the updates that are available, then follow these directions.  I have tried using both the windows drivers off of the Belkin CD, as well as the drivers I dowloaded from Belkin's website.

Any ideas?  I can't even ping my router.  I'm using WPA for security.  I have also noticed that when I issue the command 

ndiswrapper -l

that is says the rt73: driver installed
        device (050D:705A) present (alternate driver: rt73usb)

I know that I have blacklisted the rt73usb driver as directed - so something doesn't appear correct.

Any ideas?  Anyone?

Thanks in advance.

---

### Post by james_vanb on 2008-07-20
That you can connect on rare occasions suggests that the driver is installed and working.  I use this Wireless USB on an old Dell Latitiude and an old IBM Thinkpad.  On the Dell, Network Manager set to roaming works sporadically and when I can connect, may lose the connection and be unable to restore.  On the IBM, Network Manager works without a hitch.  Don't know why.

On the Dell, only way I can get connected is to manually configure.  If you haven't tried it:

Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WEP and enter password as appropriate. Set Configuration to Automatic configuration (DHCP). See if that gets you on.  (Please note that I am not using security at this time as that poses a whole different set of issues.  If the above doesn't work, try again without security - this will at least narrow your issue).

Good luck - Let us know how you do.

EDIT:  Just reread your post - You mention your using WPA for security.  This may be your issue.  Try disabling security and see if you connect.  If you do, the issue is configuring your security and not the driver.  See this link for WPA security config:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

