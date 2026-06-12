---
title: "NDISwrapper,Netgear wg111 v1 and v2 Guide (should work with any adaptors)"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by Azoix on 2007-07-12
[B][FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]I hope this guide may be of some help to other's , it was written from the viewpoint of a Windows crossdresser , who couldn't even work out simple Linux syntax to make even basic commands work, it took me 3 weeks to understand how to install and update apt-get alone.......i know PATHETIC , but i try hard !!!
So i hope those who do know HOW TO , don't flame us folk who don't.

Hope it helps someone like me :
[/COLOR][/SIZE][/FONT][/B]

[FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]NDISWRAPPER INSTALLATION
Tested and Working 100% on :[/COLOR][/SIZE][/FONT]

**[COLOR="Red"]Debian 4 , Ubuntu** , Mandriva , Knoppix 2007 , Slackware SlaxLiveCD , Kanotix 2005 LiveCD and HDD Install ,  Kanotix 2007 LiveCD(unable to install to hdd) , OpenSuSE 10.2 , Fedora Core 7 , Fedora Live CD , Yellowdog , Gentoo LiveCD , aLinux , Red Hat  , LinuxXP and more.  **The wg111v1 dongle mentioned DOES NOT WORK ON UBUNTU on this IBM or on an HP eVectra i tried also.[/COLOR]**

Wireless Key Used : Netgear WG111v2 
Serial Number : 165264BE05D67
&#8211; works on Ubuntu with Version Windows 2000 1.3.0 driver.UBUNTU terminal also shows an optional Realtek driver you can use for this device, but i DID NOT TRY THIS MYSELF AS THE WINDOWS DRIVER WORKED FINE WITH NDIS.
Shows as WG111v2 model on the side of the device.
[FONT="Comic Sans MS"][SIZE="3"][COLOR="Red"]If you wish a copy of this driver, please PM me.[/COLOR][/SIZE][/FONT]
Command   ::   ndiswrapper -l   
ndis output  :
net111v2 : driver installed 
        device (0846:6A00) present (alternate driver: rtl8187) as installed on IBM R31 Ubuntu 7.04

Wireless Key Used : Netgear WG111 ( WG111v1)
Serial Number : WG7214CZD248340
This Wireless dongle [SIZE="3"][COLOR="Red"]DOES NOT WORK FOR ME ON UBUNTU 7.04[/COLOR][/SIZE] on this laptop, and did not work on an UBUNTU 7.04 HP eVectra i had laying about either.
This dongle [COLOR="Lime"]DOES WORK[/COLOR] well on , Kanotix Live CD 2005 and 2006, both 2005 Live CD and HD installation will find and use the driver for Windows for this dongle,the Kanotix 2006 Live CD will work, but refused to transfer to the HD for testing ( install constantly hangs at 53% , and the 2nd disc i downloaded , burned and tried , isn't a bootable ISO and wont start up, so i can't say if it will work when installed to the HD , it works on the CD so should also work on HD install's, if you can get it onto the drive in the first place....)

ndiswrapper reports this WG111 USB dongle as Globespan Virata Netgear wg111
The Install Procedure
Open a ROOT terminal to do these commands.To access a root terminal in Debian or KDE, open any terminal window and type 'su' , then insert your root password , this will then switch to the root terminal.You can also preface each command with sudo if you wish, instead of logging into root, but it is easier to log-in and get it going then log-out, rather than typing sudo each time, particularly on installing ESSID and WEP keys, as the command can need up to 5 hits of the same command for the config to be accepted.

Just copy and paste the commands below ( in ORANGE ) into the window, one after the other, pressing ENTER for each seperate command of course !!
Each command returns a list of data in the terminal window, as it downloads , unpacks and ready's each part of the module.Some will ask if you wish to do some other things to other files during install, asking for simple YES / NO answers, just type yes and enter.

[COLOR="DarkOrange"]apt-get update
apt-get install module-assistant
apt-get prepare module-assistant[/COLOR] &#8211;this command may not be necessary
[COLOR="DarkOrange"]apt-get build module-assistant[/COLOR] &#8211;this command may not be necessary
[COLOR="DarkOrange"]apt-get install ndiswrapper-common
apt-get install ndiswrapper-source
apt-get install ndisgtk
module-assistant build ndiswrapper
module-assistant prepare ndiswrapper
modprobe ndiswrapper[/COLOR]
[COLOR="DarkOrange"]ndiswrapper -l[/COLOR] &#8211; should give no driver found result, at this point in time.
Please Note : 
This way of installing ndiswrapper DID NOT work for me on Ubuntu, but if you install ndiswrapper, and the 3 other related packages through Synaptic Package Manager, it works fine.Open Synaptic , click on search and type in ndiswrapper, this finds all the needed, and related packages, tick for install, ALL four, and then click apply, then ndiswrapper will work perfectly in the terminal.

My result through trying the installing in the terminal was the application installed OK, it even installed the driver, seen with `ndiswrapper -l ` command, but `modprobe ndiswrapper ` command returned an error saying ndiswrapper application not found ??? 
So i re-installed with Synaptic, and it worked first time.
I assume this was the result of my lacking the understanding of the system , i guess this fault was rectifiable another way , but i am FAR from that competant as yet.

[FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]Installing Window's Driver Component[/COLOR][/SIZE][/FONT]

To work this on a LiveCD , create the folder for the Window's Drivers on the desktop and run from there.

You need to log in as ROOT first, and make the folder /usr/bin/wg111v? write enabled.
If this is where you install the Window's driver files


[COLOR="DarkOrange"]ndiswrapper -i[/COLOR] /usr/bin/folder/.inf file* (i found placing the .inf and .sys file for the Windows driver into a folder named wg111v? in the /usr/bin/ directory allows easy location of the file, and it works perfectly well from here.)*Use your own folder location and name for the file name with .inf extension.( I use this location purely as a personal choice , i like a clean desktop.)BOTH THE FOLDER WITH THE .inf and .sys FILE MUST BE OWNED BY THE USER, and programs in the wg111v2 folder MUST BE set executable allowed 


[COLOR="DarkOrange"]modprobe ndiswrapper[/COLOR] &#8211; should now show installed driver if compatable, and display the hardware if present.
You can now use the inbuilt Network Tools to configure and enable the wlan0 interface you have just set-up.
You can choose to set a static or DHCP provided I.P. address , either way should work on all systems.

[FONT="Comic Sans MS"][SIZE="3"][COLOR="Blue"]Configuration of iwconfig in terminal[/COLOR][/SIZE][/FONT]

[COLOR="DarkOrange"]iwconfig wlan0 essid &#8220; &#8220;[/COLOR]  -- enter your network ID here !! WITHOUT QUOTES !!
[COLOR="DarkOrange"]iwconfig wlan0 key open**[/COLOR]  --YOUR WEP KEY HERE  **(either set open or restricted here WITHOUT the asterisks)
[COLOR="DarkOrange"]iwconfig[/COLOR] &#8211; check if all fields are set as requested 
[COLOR="DarkOrange"]iwconfig wlan0 commit[/COLOR] &#8211; finalises settings to the network interface.**Needs to be supported by your hardware.

---

