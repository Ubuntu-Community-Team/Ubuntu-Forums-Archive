---
title: "Network Manager not connecting to Linksys Wireless-G when SSID is Hidden"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by TheHardestWayPossible on 2010-12-19
Hi!
 
I'm brand new to Linux (had some very limited experience with Unix in the 80s, but primarily a windows user otherwise).
 
I am having trouble getting Network Manager to establish a connection to my Linksys Wireless-G when the broadcast of the SSID is disabled.
 
Some background:
 
My wife just replaced her small business laptop with a new laptop, and I am the beneficiary of the old Dell Inspiron 500m w/1.3 GHz Pentium M Centrino. It had been running XP (home edition?) and we had upgraded to 1 GB of RAM from its original 256 MB. It has a 20 GB hard drive.
 
I decided to go fully into the deep end and overwrote XP with a full install of Ubuntu 10.10 desktop. After an initial installation glitch (bad CD?), I tried the USB drive, and the new Linux OS came right up!
 
I had trouble establishing/maintaining a wireless connection to my Linksys Wireless-G. I am using WPA-PSK and I disable the broadcast of the SSID. Checking through the posts, I see there is a history of trouble with Network Manager and wireless connections.
 
I found these pages enlightening, though they did not provide me with a solution:
 
[[COLOR=#444444]https://help.ubuntu.com/community/Wi...ShootingGuide/[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/")
 
I had noticed that my config/driver was using Channel 1, though my router was on Channel 9. iwconfig would not allow me to change the driver setting ("Error for wireless request 'Set Frequency' (8B04) : SET failed on device eth1 ; Operation not supported."). So, just for grins, I decided to make my SSID visible just to see if my router showed up among the other neighborhood routers that are broadcasting their SSIDs. The router immediately connected! And, the config/driver was switched to Channel 9 to match my router. So, it seems like hiding the SSID may be contributing to the problem. 
 
I re-booted a couple times, and the connection promptly re-established. But, after disabling the broadcast of the SSID, again, and rebooting, the computer could not find the router, again, and this time, the config was set to Channel 0(?)! 
 
I've left my SSID broadcasting for a day, now, and have had no problem maintaining or re-establishing a connection upon re-boot. So, I am concluding that the hidden SSID is the culprit.
 
But, I don't like broadcasting my SSID - is there a fix for this glitch?
 
Thanks!

---

### Post by napoleon3665 on 2010-12-19
ive heard that some network managers dont like "hidden SSID's". you could try to download a different network manager, and see if that works. but honestly, if you have WPA2 encryption on ur router, its pretty tough to crack and i wouldnt worry about turning off ssid broadcasting.

---

### Post by TheHardestWayPossible on 2010-12-19
Thank you for the reply, Napoleon3665.  While I appreciate that the connection is likely secure, I'm definitely interested in learning about and tweaking my Linux installation.  So, if replacing "Network Manager" is the next logical step, I am game!
 
I did read somewhere in the community documentation that there are alternatives to "Network Manager" (is Wicd an example?). Since I am a complete noob w/Linux, I am not really sure I have figured out how to try one of the alternates. I believe I need to remove "Network Manager" and select and install one of the alternates - is this correct? Is there a preferred/recommended alternate?
 
Thanks!

---

### Post by pgibson on 2010-12-19
I"ve not heard of any fix for the hidden SSID issue.  I tried setting up a hidden WPA at home and had all sorts of problems with my Kubuntu and Ubuntu machines.  My Xubuntu machine worked, however ... I'm guessing it's a chipset issue.  I don't know why.  

For what it may be worth to you, I have successfully installed wicd using a package manager on a Kubuntu 10.10 install and, though it didn't solve my problem as a workaround (a problem that began with setting up the hidden WPA network on my router ;)), it was no great trouble to install or remove wicd using the Kubuntu package manager.

Wicd indicates that just by using Synaptic (System > Administration > Synaptic Package Manager) to install wicd, NM would be removed at the same time.  But this was with a slightly older version of Ubuntu, so it may no longer be true --- (it wasn't on a Kubuntu 10.10 usb drive installation.)  [[COLOR="Blue"]Here's wicd's install proceedure[/COLOR]]("http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu")

It might be worth simply trying wicd and seeing if it works for you.:D  I got rid of the hidden network here at my place, but I live in the middle of nowhere, so I don't worry about it too much.  I understand your wanting to do everything you can to guarentee your privacy.

I don't think there is any sort of "preferred" alternative network management app, but wicd certainly seems to be the popular one.

Sorry I couldn't be more help.

pgibson

---

### Post by wep940 on 2010-12-19
I've always had hidden SSID's and network manager, and never had a problem using Belkin, Netgear or Linksys and WPA2. I realize this is a very basic question, and you seem beyond that, so forgive me for asking:
 
- you are using the "Connect To Hidden Network" function of network manager, right?  Do you have it set for connect automatically? (I've had to go through "Edit Connections" in the past also to actually get it set up when I had a problem).
 
- the PC, with the same wireless adapter, had connected to the router in the past, and the router has not been reset, so if there is MAC filtering on the router the MAC address of the adapter is in the router allowed table, right?
 
I'm sorry if these questions are too basic for what you already know and are doing.

---

### Post by walt.smith1960 on 2010-12-20
Like WEP940 I've been connecting successfully to hidden networks for years.  One thing you could try if you haven't done so is to delete your network (system->preferences->network connections) then recreate it.  I've never had to select the router channel.  That has always been automatic.  I've heard that hiding an ESSID doesn't contribute  much to security-there are utilities that can sniff hidden ESSID's-I figure every little bit helps.

---

### Post by TheHardestWayPossible on 2010-12-21
Thanks, all, for replying!
 
Here is an update:
 
First, to respond to wep940's questions (and I really am a novice, so I appreciate all the questions/suggestions!):
 
  -- I did attempt to "Connect to a Hidden Network" and I have "Connect Automatically" set.
  -- Prior to installaing Ubunut 10.10, we had this computer operating on our hidden network with not problems using Windows XP.
 
I also tried deleting and re-establishing the network connection, but no luck.
 
Last night I updated my router's firmware (noting that it was very out-of-date).  Because all the settings were reset in this process (I did not attempt to save any settings), I decided to try connecting to the network with the SSID hidden,  but not secured.  To my surprise, "Network Manager" was immediately able to find and connect!  So, the problem is not with "Network Manager" connecting to a hidden network, or to a secured network, but connecting to a hidden & secured network!
 
In playing around, I see that there are many router and "Network Manager" settings with which I have no familiarity (even though, at first glance, I'm not sure changing them will impact my issue).  So, prior to moving to wicd, I think I'll try to learn more about these settings.  If nothing looks promising, I'll give wicd a try.  I'll need to learn more about installing applications, first, however!
 
Thanks!

---

### Post by wep940 on 2010-12-22
Hummmmm.  I use hidden and WPA2 encryption without a problem, and I use network manager, but I probably have a different adapter from you, and that can make a difference.
 
So, let's ask another question:
 
- what wireless adapter are you using?
 
if usb:
 
lsusb
 
if internal:
 
lspci
lsusb
 
 
It's possible the Linux driver for your wireless adapter either doesn't support the encryption you are using, or needs specific configuration.  Since this driver is not the same as the Windows driver (unless you are using a Windows driver via ndiswrapper), the same device can work in Windows but not in Linux.
 
Since you have already reset your router and updated the firmware, it's just another simple step to test this:
 
- since you can connect to the hidden SSID, set encryption to the lowest above an open network, normally WEP.  Can you connect now?
 
- bump encryption up 1 level at a time until you can no longer connect.  Note what level this is.

---

