---
title: "Lnksys WMP11 V4 Edgy Installtion Help"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by novice1 on 2007-03-01
OK here goes my first request for help. I am new to Linux and to UBUNTU as well.  I am retired network engineer but all my experience is with Novell and Windows Servers.  I have a good grasp of hardware and networking and computer configuration but I am confounded by the abject convolutions entailed in installing and using a wireless card in Edgy. I have searched and read through more advice and HowTo's on Wireless UBUNTU   configurations than I can list here.   The computer I am using has both a wired and a wireless ethernet card. I have no problems with the wired card configuration but nothing I have found in the way of help as worked yet for the wireless card. My computer is a small tower NOT a notebook or laptop and the wireless card is a PCI card Linksys WMP11 V4 card and I have with much difficulty installed the Ndiswrappers for this card.  The problem is that Edgy OS does not recognize the wireless card. If I do  lspci at the command prompt the Linksys Card is properly listed. iwconfig shows no wireless connection to anything. Its obvious that no drivers are loaded. The "Networking" gui does not show a wireless card. I have used the Ndiswrapper-utils-1.8 as advised in one HowTo. I have insured that I have the correct version of the Ndiswrapper downloaded from Linksys  Oddly enough this same Linksys Card was working fine under Linspire Linux.  After previewing Ubuntu I am much more impressed by it than by Linspire. So I am determined to make this work.  

I am asking for advice as to where to go now. I believe the problem lies with Edgy not recognizing the PCI card even though it is properly listed. What can be done to coax Edgy into recognizing this card?  Or is the problem not related to recognition but to a missing or improperly installed driver or utility? Is there anyone out there who can/will advise me how to proceed? Any and all advice is welcome.

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Floppyjoe on 2007-03-01
Can you post the results of these commands from the terminal?
```
lspci
```
and
```
ndiswrapper -l
```

The first command lists the various PCI devices on your computer and the second will list the ndiswrapper drivers installed.

Also show the output of the file /etc/modules to see if ndiswrapper loads at boot time.
```
sudo gedit /etc/modules
```
This file should have the word ndiswrapper in it.

---

### Post by novice1 on 2007-03-01
Thanks for the quick response -the following is the results of running the commands you indicated"


lspci:


00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:00.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
01:02.0 Ethernet controller: Linksys, A Division of Cisco Systems WMP11v4 802.11b PCI card

ndiswrapper -l

Installed drivers:
lsbcmnds        invalid driver!
lspinds invalid driver!
wmp11nds        invalid driver!

sudo getedit /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp




Please note that I added "ndiswrapper" to the modules file and I am going to reboot the see the results.  And will post the results here as well. 

Kind regards, \\Chuck

---

### Post by novice1 on 2007-03-01
[SIZE="4"][/SIZE]

I rebooted and checked the networking gui under systems admin -- still no wireless card!  Gonna check the setup using terminal and line commands next. Running the same line commands as you have suggested yielded the identical results as before except the "modules" file now contains the "ndiswrapper" line.  Still hoping to find the magic incantation that will invoke wireless communications.

\\Chuck

---

### Post by Floppyjoe on 2007-03-01
> ndiswrapper -l

Installed drivers:
lsbcmnds invalid driver!
lspinds invalid driver!
wmp11nds invalid driver!
All your ndiswrapper drivers show as invalid here.
You need to delete these three drivers by issuing the following commands:
```
sudo ndiswrapper -e lsbcmnds
```
and
```
sudo ndiswrapper -e lspinds
```
and
```
sudo ndiswrapper -e wmp11nds
```

Then you have to reinstall(using sudo ndiswrapper -i driver.inf) the needed driver(s) making sure that any .sys and .bin files are also in the directory that you installed the .inf file from. I'm not sure that you need those first two listed drivers with your card.

---

### Post by novice1 on 2007-03-01
floppyjoe:

OK - according to other community posts and HowTo's the ndiswrapper does not work in Edgy. One  source stated that ndiswrapper-1.8 has to be used. Another source stated that all three files needed to be installed.  But in any case no matter what version of ndiswrapper I use to install the .inf files the all fail with the following error: (each .inf file has its appropriate name displayed)

"Installing name_of_driver couldn't copy /home/chuck/wireless/name_of_driver.inf at /usr/sbin/ndiswrapper-1.8 line 144."

But if you do an ndiswrapper -l the files will be listed as installed but with the "invalid driver!" tag
I have reviewed every source I can find and the drives I am trying to install are the ones that are recommended.  I have checked and double checked, even triple check to be sure that I am attempting to install the correct drivers.  

But I followed your suggested instructions and removed and reinstalled the drivers -- which did not work.   :confused: 

My instinct is telling me that the Edgy OS is not detecting the Linksys Wireless PCI card.  Could it be that the PCI driver(s) or utilities are the problem? In my thought the "invalid driver!" tag is only being displayed because the OS thinks it does not have a piece of hardware for these drivers. I am very green and very new to Linux so I am uncertain of my conclusions about this.  In reading all I can find on line about installing and configuring wireless cards some where I remember reading a comment that the ndiswrapper simply does not work in Edgy and that it is a bug that needs fixing -- but I can not find that comment again.  

So alas I am still looking for the magic bullet that will get ndiswrapper and related drivers working.  As I mentioned before this Linksys Wireless card worked properly using Linspire Linux on this very same computer.  So its a puzzle to me. Still seeking all the advice I can get on this.

\\Chuck

---

### Post by Floppyjoe on 2007-03-01
The OS recognizes your card because otherwise it would not be listed in lspci like yours is.
The problem is that your ndiswrapper drivers are the wrong ones for the device or you are somehow installing them incorrectly or that version of ndiswrapper does not work with that device properly.

If it was correctly installed and the device was not recognised it would say the driver was installed without the invalid remark but would not say device present like it is supposed to.

Are you using the word sudo in front of the ndiswrapper install command?

---

### Post by novice1 on 2007-03-01
Yes I am using the sudo infront of the ndiswrapper command.  I dowlaoded the ndis drivers for the card from the Linksys site from a link found in the ndiswrapper.sourceforge.net page listing the following advice:

Card: Linksys #[WMP11 v4] 802.11b -- [link here|List#WMP11 v4]

    * Chipset: InProComm? ?
    * pciid: 17fe:2120
    * Driver: Linksys [ftp://ftp.linksys.com/pub/network/wmp11_v4_dr.zip](ftp://ftp.linksys.com/pub/network/wmp11_v4_dr.zip)
    * Other: Debian Unstable/Sid with NdisWrapper 0.11. You must install all three inf files from the driver zip file (I had to force NDIS to load all three drivers for the one card with the -d option on each inf). Card works great, but WEP is untested. Works great on Slackware 10.1 with a 2.6.10 kernel, and Ubuntu Breezy using the latest version of NdisWrapper.
    * Fedora Core 5, Kernel 2.6.15-1.2054_FC5, works fine with ndiswrapper 1.13, I only needed the LSIPNDS.INF file. I added the line "alias wlan0 ndiswrapper" to the /etc/modprobe.conf file so that the network configuration gui would pick it up. Once I applied DNS, IP, Gate, Mask, ESSID, I was running wide open. These are good inexpensive cards at any WalMart in USA. 

This is purported to be the latest information from users installing this card.

I will check the Linksys web site directly and see what I can find out about ndis downloads,   Again thank you for your help.

\\Chuck

---

### Post by novice1 on 2007-03-01
\\:D/ 

Floppyjoe:

I am a happy camper now as I type this response I am up and running on my Linksys Wireless network card!  I did two thing differently -- first I downloaded the "latest" ndiswrapper version 1.38 and installed it.  Secondly all the driver install errors when trying to install the 3 .inf files were caused by typo's -- some of the file names contain CAPITAL letters and they do make a difference!  I found by typing the .inf files EXACTLY as they are displayed in the File Browser did the trick.  I also found the "driver" files were created by ndiswrapper under the mistyped names which explains why I was getting the "Invalid Driver!" response to ndiswrapper -l.

I also believe you are right about not needing all three .inf files.  When I do an ndiswrapper -l
the only driver that show that hardware is connected is LSIPNDS.  The other two files: WMP11NDS and lsbcmds do not show hardware connected.  

Bottom line is that the .inf file names must be typed exactly as displayed and perhaps the upgraded ndiswrapper was needed. All I had to do after running modprobe ndiswrapper was to open the network GUI and configure the now present Wireless card with fixed IP addresses - I don't use DHCP.   I ran wifi-radar and confirmed the wireless data and we were off and running. 

Any way thanks to your able assistance and observations its up and running now.  Your help was greatly appreciated.

Warm Regards,  \\Chuck

---

### Post by Floppyjoe on 2007-03-02
You may still need all the files there though. Don't fix it if it aint broke.
I was just going to suggest that the Names are case sensitive ;-)

---

### Post by novice1 on 2007-03-02
Been around computers a networks long enough to know not to fix what ain't broke!  I learned a lot by spending the better part of sveral days setting this up.  I never knew that in Linux file names are case sensitive - so now I will never forget it.   \\Chuck

---

### Post by TXBDan on 2007-06-28
hey all,

i can't get my wmp11v4 to work either.

i have ndiswrapper-util 1.8  and the linksys drivers installed properly. hardware and drviers present. lspci shows the device.

i did the ndiswrapper -m but i cant find the wlan0 alias anywhere... if i do a iwconfig, it shows two devices (l0 and eth0) but not anyting wireless. it says no wireless extensions.

also in the GUI network tools, now wireless devices show up. only the two above.

Any ideas on how i can get this going? thanks a lot!

---

