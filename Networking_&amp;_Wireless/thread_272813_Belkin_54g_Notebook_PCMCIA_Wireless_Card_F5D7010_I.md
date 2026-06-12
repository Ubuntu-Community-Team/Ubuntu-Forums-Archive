---
title: "Belkin 54g Notebook PCMCIA Wireless Card F5D7010 Installation for Novices"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by Fitzcarraldo on 2006-10-07
After three solid days of effort and frustration, my brother finally managed to install successfully his Belkin 54g Notebook Wireless Card (model no. F5D7010) on a laptop/notebook PC. I asked him to document the whole process in detail and he kindly obliged. Below, in his words, is how he did it. He wrote this in Word and the formatting, fonts, italics, bold text, underlining and so on have been lost when pasting it here. Nevertheless, I hope it is still understandable.

Thanks for documenting it, Bro. =D> 


----------------------------- BEGIN QUOTE ------------------------

Ubuntu
Belkin 54g Notebook Wireless Card Installation for Novices

Note:	If you are a Unix novice like me you will need a wired Ethernet card connected to your laptop to download updates to it from the Internet. If you are having difficulties trying to install your wireless card and there is no other means of getting a connection to the Internet, you may as well either give up now or become very good friends with a Unix “guru”.

The most crucial part of this procedure is to get hold of the ‘ndiswrapper’ programme and utilities. Ubuntu uses ‘ndiswrapper’ to wrap the Windows drivers of your wireless card with code that provides full compatibility between the Ubuntu network sub-system and the wireless card and chipset.

Foreword
Before starting this procedure, please make a strong cup of coffee and make sure that you have something nearby, like worry beads, to alleviate your pent up frustration.

I have my gripes about Windows from time to time, like most of those who use it I suppose. There are occasions when things go wrong when installing new devices and software but on the whole I’m pretty confident that most things will go as planned and I don’t approach new installations with trepidation.

Not so, I’m afraid, with Unix. It is clear to see why Unix based laptops will not be a mass market phenomenon until it is designed by engineers for users, not designed by engineers for engineers. I tend to see my computers as tools to do a job or as things that can entertain and give me pleasure. OK, I am a self-confessed Unix novice but in the short space of time that I have been using (trying to use) Unix on my laptop I have spent more time attempting to get it working than I have being able to use it.

Maybe I’ve just been plain unlucky on this occasion or perhaps I lack the intellectual staying power of the “gurus” who regard as entertainment fiddling with kernel builds, tinkering with endless utilities, entering cryptic commands and updating interminable configuration files.

“Ah!” I hear them say, but you learn more when things go wrong and you fix problems. “Yeah?” say I. “But I don’t want to get my entertainment from constantly battling with challenges. “If you buy a new car, don’t you want to be driving around in it? Or would you rather be on the roadside on a regular basis trying to keep it running and constantly searching the web trying to find reasons why the catalytic converter doesn’t work, or the cam belt keeps breaking?”. Particularly if the web sites that you find leave you more confused than when you started.

Anyway, enough of that! I’ve tried to put together a step-by-step set of easy to read instructions to help other novices like me to get their wireless cards working. The instructions are based on my own experience of getting my wireless card to work in my home laptop. I recognise that it may not be perfect but it’s a genuine attempt to help others who may also be confused by the myriad of conflicting and contradictory instructions I’ve found so far on the web.

Environment
Laptop:	Dell Inspiron 5000e (Compal N30 Series), 600Mhz.
Note:	Yes, it’s an old one but it worked pretty well with Windows 98.

Ubuntu:	Version 6.06 LTS – Dapper Drake – Released June 2006
Kernel Version 2.6.15-26-386

Belkin:	54g Wireless Notebook Card, Part No. F5D7010

Drivers:	Rt2500.sys – Version 2.02.07.0000, Date 29th July 2004, Ralink Technology Inc.
	rt2500.cat – Date 3rd August 2004
	rt2500.inf – Date 29th July 2004

Installation Procedure
1. Install Ubuntu from the ISO CD.

2. Connect an Ethernet cable to the laptop to get access to the Internet. [COLOR="Red"]DO NOT[/COLOR] insert your Belkin 54g card into the PCMCIA socket yet.

3. Select System -> Administration -> Update Manager from the menu panel at the top of the screen. The purpose of this step is to get hold of the ‘ndiswrapper’ code and utilities.

- Click on the Check button to find updates on the Internet.

- Select the upgrades you want to install and click on Install.

Note: I chose to install all of the updates because I wasn’t sure which of them contained the ‘ndiswrapper’ components. Incidentally, this upgrade brings the Ubuntu Kernel up to version 2.6.15-[COLOR="Red"]27[/COLOR]-386.

4. Once the upgrade is complete, click Close to exit from Update Manager.

5. Select System -> Administration -> Synaptic Package Manager from the menu panel at the top of the screen.

- Scroll down the right-hand panel until you find ‘ndiswrapper-utils’ and select it.

- Click Apply to initiate the installation and a summary screen showing ‘To be installed’ is displayed. Click Apply again.

- Click Close when the installation has completed and exit Synaptic Package Manager.

6. Create a directory into which to copy the Belkin 54g wireless card drivers. Select Applications -> Accessories -> Terminal from the menu bar at the top of the screen. This will open a command line terminal on the desktop. Type in the following (without the apostrophes):

‘sudo mkdir /windows-drivers’

to create a sub-directory underneath the root directory.

- Copy the Belkin 54g wireless card driver files (mentioned in the section above - Environment) into this directory. The files can be copied across with a floppy disk, CD, FTP or memory stick.

7. Type in the command ‘sudo ndiswrapper –l’ (minus letter ‘EL’) to see if any NDIS “wrapped” wireless drivers are already running. There shouldn’t be and ‘No drivers installed’ should be displayed.

Note:	If a driver is displayed, rt2500 for example, type in ‘sudo ndiswrapper –e rt2500’ to make sure that the driver is uninstalled. In addition, type in ‘sudo rmmod rt2500’ to remove any rt2500 driver modules from the Ubuntu Kernel. This is why you should not plug your wireless card in yet (the command immediately below also removes modules from the Ubuntu Kernel).

8. Type in ‘sudo modprobe –r rt2500’ to make sure that there is absolutely no chance that an older rt2500 driver module is linked into the Ubuntu Kernel.

9. Now install the new driver by typing in ‘sudo ndiswrapper –i /windows-drivers/Rt2500.inf’. Note that the file names are case sensitive so be sure to type in the file name exactly as it was copied to the ‘/windows-drivers’ directory. ‘Installing rt2500’ will be displayed.

10. Type in ‘sudo ndiswrapper –l’ (minus ‘EL’) and you should see ‘rt2500 driver present’ displayed.

11. Type in ‘sudo ndiswrapper –m’. The message ‘Adding “alias wlan0 ndiswrapper” to /etc/modprobe.d/ndiswrapper’ should be displayed. This creates a file in directory ‘/etc/modprobe.d’ called ‘ndiswrapper’ and inside the file is the statement ‘alias wlan0 ndiswrapper’. This statement associates the NDIS wrapped driver with the wireless interface alias ‘wlan0’, which is what the interface will be known as henceforth.

12. Type in ‘sudo modprobe ndiswrapper’ to add the NDIS wrapped rt2500 driver module to the Ubuntu Kernel.

13. Type in ‘dmesg’ immediately after the command above and you should see an entry at the end of the log file that says ‘ndiswrapper version <n.n> loaded (preempt=yes,smp=no)’.

14. [COLOR="Red"]NOW PLUG IN YOUR Belkin 54g WIRELESS CARD.[/COLOR]

15. Type in ‘sudo ndiswrapper –l’ (minus letter ‘EL’) and you should see the following displayed ‘rt2500 driver present, hardware present’.

16. Type in ‘ifconfig’ and hit RETURN. You should see interfaces ‘l0’ (Loopback 0) and ‘wlan0’.

17. Now configure the wireless card. Select System -> Administration -> Networking from the menu panel at the top of the screen. In the ‘Connections’ tab you should see ‘Wireless connection’ underneath which is displayed ‘The interface wlan0 is active’.

18. Highlight ‘Wireless Connection’ and click on the ‘Properties’ button on the right hand side. Make sure that the ‘Enable this connection’ box is ticked (tick it if it isn’t) and enter the appropriate wireless settings e.g. SSID, WEP Key and DHCP or Static IP Address information.

19. Click ‘OK’ and after one or two seconds the LEDs on the wireless card should light up and the card is ready to use; provided that you have a wireless router or access point that is configured as a DHCP server if you selected the DHCP option above. I used the DHCP option.

20. Type in ‘cat /etc/network/interfaces’ and you should see something like this in the file:

auto wlan0
iface wlan0 inet dhcp (if you selected the DHCP option)
wireless-essid <your SSID>
wireless-key <loads of Hex digits>

21. Exit from the Networking configuration utility and return to the command line terminal window. Type in ‘ifconfig’ and confirm that interface ‘wlan0’ has the correct IP address. Test connectivity using ‘ping’ to the default gateway on your LAN or, if you are feeling adventurous, ‘ping’ somewhere on the Internet – ‘ping [www.google.com’](www.google.com’), for example.

At this point, all would appear to be going very well. But before you put away your worry beads, please grab another cup of coffee……….. and then reboot your laptop.

At the start of the boot sequence, the wireless LED on the card will light up. However, don’t be lulled into a false sense of security because once the Ubuntu boot screen appears and you see displayed ‘Loading hardware drivers…’, you will hear a barely audible click and the wireless LED on the card will extinguish; never to return again.

The reason for this, I gather from other users who’ve posted questions on the web and received answers from the “gurus”, is that the drivers load before the PCMCIA code does. Or something like this anyway (please don’t shoot the messenger).

Those in the know also tell us to do the following:

22. Open another command line terminal window and type in ‘sudo gedit /etc/modules’. At the bottom of the file type in ‘ndiswrapper’ and be sure to enter a carriage return at the end of the line. Close the editor and try rebooting again.

23. If Step 22 doesn’t work (it didn’t on my laptop) there is an alternative approach that I have tried and tested on my laptop. Type in ‘sudo gedit /etc/init.d/bootmisc.sh’ and insert the following commands shown in red towards the end of the file:

#!/bin/sh
### BEGIN INIT INFO
# Provides:          bootmisc
# Required-Start:    $local_fs hostname
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:
# Short-Description: Miscellaneous things to be done during bootup.
# Description:
### END INIT INFO
#
# Version:	@(#)bootmisc.sh  2.85-17  04-Jun-2004  [email]miquels@cistron.nl[/email]
#

[ -z "$DELAYLOGIN" ] && DELAYLOGIN=yes
[ -z "$EDITMOTD" ] && EDITMOTD=yes
[ -f /etc/default/rcS ] && . /etc/default/rcS

do_start () {
	#
	#	Put a nologin file in /etc to prevent people from logging in
	#	before system startup is complete.
	#
	if [ "$DELAYLOGIN" = yes ]
	then
		echo "System bootup in progress - please wait" > /etc/nologin
	fi

	#
	#	Create /var/run/utmp so we can login.
	#
	: > /var/run/utmp
	if grep -q ^utmp: /etc/group
	then
		chmod 664 /var/run/utmp
		chgrp utmp /var/run/utmp
	fi

	#
	#	Set pseudo-terminal access permissions.
	#
	if [ ! -e /dev/.devfsd ] && [ -c /dev/ttyp0 ]
	then
		chmod -f 666 /dev/tty[p-za-e][0-9a-f]
		chown -f root:tty /dev/tty[p-za-e][0-9a-f]
	fi

	#
	#	Update /etc/motd. If it's a symbolic link, do the actual work
	#	in the directory the link points to.
	#
	if [ "$EDITMOTD" != no ]
	then
		MOTD="`readlink -f /etc/motd || :`"
		if [ "$MOTD" != "" ]
		then
			uname -a > $MOTD.tmp
			sed 1d $MOTD >> $MOTD.tmp
			mv $MOTD.tmp $MOTD
		fi
	fi

	#
	#	Save kernel messages in /var/log/dmesg
	#
	if [ -x /bin/dmesg ] || [ -x /sbin/dmesg ]
	then
		dmesg -s 524288 > /var/log/dmesg
	elif [ -c /dev/klog ]
	then
		dd if=/dev/klog of=/var/log/dmesg &
		dmesg_pid=$!
		sleep 1
		kill $dmesg_pid
	fi

	#
	#	Save udev log in /var/log/udev
	#
	if [ -e /dev/.udev.log ]
	then
		mv -f /dev/.udev.log /var/log/udev
	fi


	#
	#	Remove ".clean" files.
	#
	rm -f /tmp/.clean

[COLOR="Red"]>>>> INSERT HERE
	#
	#	Uninstall and Re-install WLAN Driver
	#
	ndiswrapper -e rt2500
	rmmod rt2500
	rmmod ndiswrapper
	ndiswrapper -i /windows-drivers/Rt2500.inf
	modprobe ndiswrapper

>>>> INSERT HERE[/COLOR]

}

case "$1" in
    start)
        do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

: exit 0

The above procedure, complicated as it is, now works for me. But I have spent three days solid (it is now 04:15 in the morning) trying to get this to work. I have much better things to do.

I am sorry to say that if anyone tries to tell me that Unix, in whatever flavour it comes, is suitable for your average laptop and/or PC user like me, then I may just get a mention in the Guinness Book of Records as the person who uttered the loudest and foulest string of concatenated obscenities that anyone in the history of mankind has ever uttered to date.

----------------------------- END QUOTE ------------------------

---

### Post by cydec on 2006-10-07
I have the install CD for my F5D7010 but I'm not able to find the rt2500.inf file.
i have the .sys and .cat but the .inf is nowhere to be found ... do you know where i can find it?
I searched the internet and googled like a freak, but not able to find it anywhere.

---

### Post by Fitzcarraldo on 2006-10-08
Hi there *cydec*,

My brother had the same problem. You can do one of two things:

1. Install the drivers from the CD onto a Windows machine and locate them underneath the Program Files -> Belkin -> WinXP [2K or 98] directory and copy the .cat, .inf and .sys files into another location (which is what my brother did). He used the Win98 drivers, by the way, because his old Dell laptop was running Win98 and probably wouldn’t support the XP drivers but I guess you’ll have to choose based on the machine you have installed Ubuntu on. You can then uninstall the Belkin drivers on the Windows PC to get rid of them.

OR

2. If you send me a PM (Private Message) giving me your e-mail address, I can e-mail to you the files my brother obtained (rt2500.cat, Rt2500.inf and Rt2500.sys).

---

### Post by dbrum on 2006-10-16
Any chance you can put these drivers up for us someplace?  I need to follow these steps and I can't seen to find the files on the windows download, just a few .exe's which I guess self-extract but I don't have a windoze box to try it on...

thanks!

---

### Post by sunspots on 2006-10-16
Hi,

I thought I would cross reference to my help request.

[http://www.ubuntuforums.org/showthread.php?p=1625074#post1625074](http://www.ubuntuforums.org/showthread.php?p=1625074#post1625074)

I used the notes to install for Belkin F5D6020 wireless card (I know the message quotes F5D7010 but I must have written it in my sleep (just as well otherwise I would not have had this great help document).

Thanks again to your brother.

---

### Post by sunspots on 2006-10-16
dbrum,
Try [http://www.drivermagic.com/](http://www.drivermagic.com/) to get your drivers. I got my drivers from there. Or maybe search for web sites using the term drivers. That will return many sites offering drivers.

Best of luck.

---

### Post by Fitzcarraldo on 2006-10-17
> **dbrum said:**
> Any chance you can put these drivers up for us someplace?  I need to follow these steps and I can't seen to find the files on the windows download, just a few .exe's which I guess self-extract but I don't have a windoze box to try it on...

thanks!

I received your PM, *dbrum*, and have e-mailed a ZIP file to you with the three Belkin Win98 driver files.

EDIT: :-? My e-mail bounced. I cut-and-pasted your e-mail address from your PM, so did not mistype it.

---

### Post by squirmster on 2006-10-17
I recently installed Ubuntu 6.06 on a Dell Latitude C600 laptop. I have a Belkin F5D7010 Wireless G Notebook Network Card which I have been trying to install for the last couple of weeks. ](*,) 

This thread was really helpful but when I get to point 19 of my lights don’t come on. Everything up until then works fine - my drivers are found, the hardware has been found (even if it doesn't light up). Any ideas? 

My card says it is on ra0 whereas the howto says wlan0. Does this make a difference?

I am need wireless with this laptop as it doesn't have an ethernet port and I don't have a modem adapter for it.

---

### Post by TGIF Tony on 2006-10-18
Hi Squirmster,
Did you carry out step 11 by typing in ‘sudo ndiswrapper –m’?
This creates the alias for wlan0.

ndiswrapper should cause your card to be referenced as wlan0. If this is not happening then it will not work. Are you able to start from scratch i.e. leave the drivers on the hard disk but carry out all the other steps again?

Are the drivers definitely the right ones for your card?

Please let me know how you get on.

---

### Post by squirmster on 2006-10-19
Hi TGIF Tony,

Thanks your the advice. Still stuck I am afraid.

I tried to do sudo ndiswrapper -m and got the message "modprobe config already contains alias directive"

I didn't think this was supposed to happen so I repeated steps 7 to 10 and everything seemed to go smoothly and work the way it should. Did step 11 and got the same message. Not sure what else to do and I can't find any guidance that I understand.

BTW. I downloaded the drivers from the link on the ndiswrapper site as the instructions said to not trust the ones I already have. The card works fine in my other laptop and worked fine in this one before ubuntu was installed so hardware is not an issue.

---

### Post by Kirium on 2006-10-19
Hi folks,

This guide is great for a total newbie to Linux like myself.. I've been trying to setup my Belkin car with this, but am experiencing some differences in my setup to what is in the guide...

First of all, I've got 6.06 installed on a Toshiba Satellite notebook, dual boot with XP on a 30gb partition and 6.06 on a 25gb partition. I used the Belkin XP drivers, bcmwl5.inf etc. instead of the rt2500.inf as listed in the guide because I couldn't find the rt2500 driver anywhere. 

One difference in my efforts is that it's calling the wireless card 'eth1' so far, not 'wlan0'. I've managed to get up to step 15 with it telling me 'bcmwl5 driver present, hardware present'

but when i 'ifconfig' after that, there is no 'eth1' mentioned anywhere. I only get 'eth0' (my ethernet port I'm guessing) and 'lo' listed.
'iwconfig' has 'eth1' listed and some details about the card (IEEE 802.11b/g Broadcom 4306 etc...)

When I go to the network settings and the connections tab, the Wireless connection needs to be activated. when I try to activate it takes the better part of 30-45 seconds, and no lights come up on the card. the interface eth1 then eventually says it is active. Then when I click OK, it takes another 60-odd seconds to close the network settings window. still no lights on the card. When i re-open the network settings, the wireless connection 'eth1' is inactive again...

It seems like it's having real troubles with the card (which works find under XP)

Can anyone shed some light on the problem?? Would it be easier to just try and do this with the rt2500 drivers? If so, could someone please direct me to them?

Cheers

---

### Post by squirmster on 2006-10-19
Hi Kirium,

This is the list from the Ndiswrapper wiki. Here is a link to the page I used to get my drivers: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Just search for your device and download the compatible drivers

---

### Post by Fitzcarraldo on 2006-10-19
One of the problems with the Belkin F5D7010 wireless card is that there are different versions of it, using different chipsets and drivers. According to the ubuntu documentation page (see link below), there are four different versions of the F5D7010 card: one using the Ralink RT2500 chipset/driver, one using the Broadcom 4318 chipset/driver, one using the Broadcom 4306 chipset/driver and one using the Atheros AR5211 chipset/driver:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

You have to use the correct driver for your version of the F5D7010. A Ralink driver, for example, will not work with a F5D7010 that contains a Broadcom chipset, and vice versa.

According to the Web page that *squirmster* gave the link for above, there are six F5D7010 card variants:

1. Card: Belkin F5D7010 
Chipset: Broadcom 94306 

2. Card: Belkin F5D7010 54g (802.11g and 802.11b capable) 32-bit CardBus wireless card (Rev 5000) 
Chipset: AR5211 (Atheros Communications, Inc. AR5211) 

3. Card: Belkin F5D7010 Wireless-G Notebook Adapter 
Chipset: RaLink RT2500 

4. Card: Belkin F5D7010 54g (802.11g and 802.11b capable) 32-bit CardBus wireless card 
Chipset: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 

5. Card: Belkin F5D7010 54g (802.11g and 802.11b capable) 32-bit CardBus wireless card (Rev 02) 
Chipset: BCM4306 (Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)) 

6. Card: Belkin F5D7010au 54G Wireless Notebook Network Card 32-bit CardBus (VER.1224au sticker on bottom of box) 
Chipset: BCM4306/BCM2050 reported by Windows 2000 

My brother's card is type no. 3 in the above list, which is why he used Ralink Technology Corp.'s RT2500 Win98 driver, which he extracted from the Belkin CD that came with the card.

---

### Post by sunspots on 2006-10-19
Hi Kirium,

Have a look at my link below, it related to my belkin F5D6020 but it still may help to give you clues on things to try.

[http://www.ubuntuforums.org/showthre...74#post1625074](http://www.ubuntuforums.org/showthre...74#post1625074)

I had a similar problem that the card kept becoming deactivated when I came out of the configuration. I then rebooted my laptop. Then was able to configure. Also, I dont have WLAN but eth1. It is now up and running for the past two days with fresh reboots each day.

Hope this helps.

---

### Post by TGIF Tony on 2006-10-19
Hi squirmster, All,
I guess I'm stumped if you're struggling to get the wlan0 alias to be recognised by the system. I only managed to get my card to work when it was referred to correctly as wlan0, previously the system kept on referring to it as ra0 (for some reason). Sounds like a similar problem to what some of you are having?

I then stopped trying to download drivers from the web that I thought were the right ones and installed the original drivers for the card onto my Windows work laptop, even though the laptop didn't have a Belkin card in it, just so I could get at the INF and SYS files to copy to the Ubuntu machine. I then uninstalled the drivers from my work laptop afterwards.

As soon as I used the original drivers, the card worked. But I still had to edit the '/etc/init.d/bootmisc.sh' file (as per my procedure) to get it to work consistently on a reboot.

If you still have the original drivers disk I can only suggest trying the same thing i.e. install the drivers on Windows machine to get hold of them first.

Can't think of anything else to recommend.

Regards.

---

### Post by S-n-o on 2006-10-21
hi, i got up to stage 14, and when i do the next step it dosnt say that the hardware is there, but the lights faintly glow on the card..

could any1 possible help me out? been trying for days to get this working for my brother.

---

### Post by TGIF Tony on 2006-10-21
Hi S-n-o, if when you get to step 15 and type in "sudo ndiswrapper -l" and you don't get the reply "<driver> present, hardware present" it means that the driver hasnt loaded.

What does the 'dmesg' command display at the end? Does 'ndiswrapper....loaded' appear?

I feel for everyone who is trying to get this to work as I spent days doing the same, hence my cynical comments in the foreword. In my case I could only get the card to work when I got hold of the original INF and SYS files. Do you definitely have the right INF and SYS files for your Cardbus or PCMCIA chipset?

---

### Post by dbrum on 2006-10-22
I tried the above, with the Win98 drivers and didn't work.  No errors, everything reports as added to the bootup, all the right output, etc.  yet no lights on the card.  I know the card works fine, I can dual-boot into windows and it just works.

Here is my exact card, I managed to find it on the Belkin site.  

[http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179466](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179466)

I am going to try and find the right drivers for it, as I think this is the root problem for me.

thanks.

---

### Post by dbrum on 2006-10-22
One more thing I forgot to mention.  If you load up Synaptic and search on 'ndis' you can install the ndisgtk package which is a gui front-end for installing windows NDIS drivers, does all the steps outlined in the original post.  Pretty nice.

---

### Post by S-n-o on 2006-10-22
> **TGIF Tony said:**
> Hi S-n-o, if when you get to step 15 and type in "sudo ndiswrapper -l" and you don't get the reply "<driver> present, hardware present" it means that the driver hasnt loaded.

What does the 'dmesg' command display at the end? Does 'ndiswrapper....loaded' appear?

I feel for everyone who is trying to get this to work as I spent days doing the same, hence my cynical comments in the foreword. In my case I could only get the card to work when I got hold of the original INF and SYS files. Do you definitely have the right INF and SYS files for your Cardbus or PCMCIA chipset?
the drivers are present, its just not detecting the card,
ndiswrapper does appear when i do 'dmesg'.

it just wont detect the card, card works fine on windows.

---

### Post by TrueJk7 on 2006-10-23
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

*Highly* recommend checking this out. I had all types of errors (detected, not detected, turning on and off randomly...) and I follwed Ubunut's wiki docs and got it to work. So I recommend hitting this up for a resolution. Worked for me!

---

### Post by S-n-o on 2006-10-24
> **TrueJk7 said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

*Highly* recommend checking this out. I had all types of errors (detected, not detected, turning on and off randomly...) and I follwed Ubunut's wiki docs and got it to work. So I recommend hitting this up for a resolution. Worked for me!
mine dosnt use the 'bcm4xx' driver, i grabed the driver files from the official disk i had with it.

---

### Post by AndyCooll on 2006-10-31
As has already been mentioned, there are different versions of this card. 

Some actually work "out of the box" with Ubuntu 6.06 and 6.10. For instance I have three of these cards and two of them (version 3000uk) required no configuration at all. As far as I was aware the Ralink rt2500 driver is part of the kernel. So ...these cards showed up as "ra0" and I simply entered my network details and they worked.

However, the third card (which I've just purchased) is version 6000uk. And although the card is recognised and shows up as "wlan0" I haven't got it working yet. Since I only installed 6.10 yesterday I've also not had time to play around and get it working. When I do I might well try this HOWTO and see if this works!

:cool:

---

### Post by Village on 2006-11-01
I'm having all sorts of problems with this card. Sometimes it works and then my laptop just stalls.

I've tried going though the process described in the first post, but during the command the driver doesn't seem to install correctly. 

And all I want to do is sit at my kitchen table and enjoy a cup of coffee and surf the net.

Village

---

### Post by igknighted on 2006-12-06
I am trying to install this card, and I have gotten everything to work fine right up until the point where I actually plug the card in.  At this point the computer wont recognize that the card is there.  Would *really* like to get this working, any ideas on where I can go from here?  Is there something I can post that would be helpful?

---

### Post by igknighted on 2006-12-07
Sorry to double post, but make sure you use the drivers from your CD!  There are many different versions of this card, some use the rt2500 chipset, others us madWIFI and still others use broadcom... check the version of your card and get the proper drivers!

---

### Post by csparks1982 on 2006-12-30
The drivers on my cd are rt61, has anybody used these?

Also, when I go todo step step twelve: "sudo modprobe ndiswrapper" I get this error: 

> craig@laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument


the last lines of dmesg is: 
> **dmesg]
[17181884.608000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17181884.632000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512) said:**
>  ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17181921.904000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17181921.908000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17181921.908000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17181964.720000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17181964.724000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17181964.724000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed


---

### Post by penorwood on 2007-01-01
> **TrueJk7 said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

*Highly* recommend checking this out. I had all types of errors (detected, not detected, turning on and off randomly...) and I follwed Ubunut's wiki docs and got it to work. So I recommend hitting this up for a resolution. Worked for me!

This worked PERFECTLY for me ... and now don't need ndiswrapper at all. Thanks for the info after hours of aggravation!

---

### Post by joyflop on 2007-02-03
Hello-

I am stuck on #9 - I get an error message, and I'm not entirely sure what I am missing.

*Terminal says:*
pam@ubuntu-laptop:~$ sudo ndiswrapper -i /windows-drivers/Rt2500.inf
Installing rt2500
couldn't copy /windows-drivers/Rt2500.inf at /usr/sbin/ndiswrapper-1.8 line 144.

My intuition tells me that it's because I don't know how to do #6: "Copy the Belkin 54g wireless card driver files (mentioned in the section above - Environment) into this directory."

How does one go about copying the files to the directory? I am a total n00b, so I need the most basic of instructions :)

Thanks to any/all who help.

Pam

---

### Post by GaiusJuliusCaesar on 2007-09-12
Hi.  Many thanks for writing this guide.

I'm running 7.04 and the serialmonkey driver supplied in the dist didn't work properly, it could see all the available wlans but wouldn't successfully connect to any.

Following these instructions was easy but anyone running feisty should add blacklist rt2500 to /etc/modprobe.d/blacklist to stop the serialmonkey kicking back in on reboot.

I had problems getting the belkin drivers but searched for rt2500.inf on google and downloaded one to go with the .cat and .sys files extracted from the belkin installer.

Now I'm not sure if this is because I'm using a randomly downloaded inf file but I can only choose WPA Personal and can't seem to connect to my Netgear router without turning off security on the router (well I have setup access lists).  Does anyone else have this problem, and if not could they send me some up to date Belkin drivers (version 3000uk).

Thanks, Julius

---

### Post by Roasted on 2007-11-25
I got to number 17.


  892.564000] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  892.564000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  892.572000] sd 4:0:0:0: [sdb] 1001472 512-byte hardware sectors (513 MB)
[  892.572000] sd 4:0:0:0: [sdb] Write Protect is off
[  892.572000] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  892.572000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  892.572000]  sdb: sdb1
[  892.576000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  892.576000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 1097.584000] ndiswrapper version 1.45 loaded (smp=yes)
[ 1097.628000] usbcore: registered new interface driver ndiswrapper
jason@jason:~$ sudo ndiswrapper -l
net8185 : driver installed
jason@jason:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:88:CB:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

jason@jason:~$ 



However when I did ifconfig, I did not get the exact results you said. I just shrugged it off and went to system - admin - network, where you said that I should see a wireless connection there.

I saw no wireless connection.

If I don't get a response by morning I'm just going to return the card, because staples has a wireless card that supposedly works "out of the box" with Ubuntu (according to the documentation). :)

---

### Post by TGIF Tony on 2007-11-26
Hi Roasted,
I think that you will be better placed to acquire and try another card that "works out of the box". The only reason for saying this is that I had quite a job getting this particular card to work (all those months ago) and the instructions I wrote at the time were based upon the specific output I saw from my old laptop during the installation and troubleshooting process.

It is entirely possible that things have moved on since then or that the different chip-sets in my and your machines result in different symptoms being reported for different inherent problems.

I think this is part of the problem with all of these solutions that are posted (mine included). It's virtually impossible to tell whether everyone else is having exactly the same issues.

Please let me know if all goes well with another card. If not, I can revisit what I did and see if there is any way I can help you. I will need to refresh my memory on what I did though, old age and consumption of Guinness are starting to take their toll :-)

All the best,

Tony

---

