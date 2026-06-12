---
title: "change MAC address permanently"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by ovidescu on 2006-12-10
Hello everyone

I am new to the linux world and after careful considerations and reading many reviews, I have recently set up my computer with a dual-boot Windows XP / Ubuntu 6.10. Everything works well, except for my network card. 
In Windows I have set up the mac address manually, because I have a mac that I use since 2-3 network cards ago :) while in Ubuntu I have to manually change the mac address, either with macchanger of using the ifconfig commands. So far no good. 
My network card acquires IP using DHCP service from my ISP, which in turn uses my mac to share connection, so I want to make it a permanent change, so that whenever I boot up in Ubuntu I have internet connection working.
Can you please guide me to the correct and properly ordered steps for permanently changing my network card mac address ?
I have searched this forum, and others like linuxforums.org, and found bits and pieces of how to change your mac using macchanger, how to change your mac with ifconfig ](*,)  and so on, but nothing concrete on how to do it permanently. 

Thank you so much in advance for any help.

---

### Post by DaveBorealis on 2006-12-10
> **ovidescu said:**
> I want to make it a permanent change, so that whenever I boot up in Ubuntu I have internet connection working.

Hello,

You could try changing it with the network interface.  In '/etc/network/interfaces' add the following line under (I'm assuming) 'auto eth0':
```
hwaddress ether 01:01:01:01:01:01
```
(Use your own mac number, of course.)

I've never spoofed a mac before, so I can't guarantee this'll work.

But hope that helps,
Dave

---

### Post by ovidescu on 2006-12-10
> **DaveBorealis said:**
> 
In '/etc/network/interfaces' add the following line under (I'm assuming) 'auto eth0':
```
hwaddress ether 01:01:01:01:01:01
```
(Use your own mac number, of course.)


I have done that, but it doesn't help at all. Now the Network utilities reads no connection active... :confused:

---

### Post by DaveBorealis on 2006-12-10
> **ovidescu said:**
> Now the Network utilities reads no connection active... :confused:

Did you restart your laptop after making the changes, or at least restart the ethernet?  Assuming eth0:
```
sudo ifdown eth0
sudo ifup eth0
```

If it works after a reboot, then it'll work every time you switch from Windows to Ubuntu, which requires a reboot.

Dave

---

### Post by FrodoB on 2006-12-10
1) The commands to manually change the MAC:

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 01:02:03:04:06:06


2) Test the change:

sudo ifup eth0

sudo ifconfig eth0 


3) Make it permanent:

Edit /etc/network/interfaces and add the "pre-up ifconfig eth0 hw ether" to your device configuration:

sudo gedit /etc/network/interfaces


Find the record for eth0 and change it:

auto eth0
iface eth0 inet dhcp
hwaddress ether 00:01:02:03:04:05


Also see this wikipedia article:

[http://en.wikipedia.org/wiki/MAC_address](http://en.wikipedia.org/wiki/MAC_address)

---

### Post by ovidescu on 2006-12-11
> **DaveBorealis said:**
> Did you restart your laptop after making the changes, or at least restart the ethernet?  Assuming eth0:
```
sudo ifdown eth0
sudo ifup eth0
```
Dave

Of course I rebooted after making the changes. I still haven't found a way to just reset the NIC, like Disable/Enable in Windows, I know there is a way, I just have to google deeper.

---

### Post by ovidescu on 2006-12-11
@ FrodoB

Thank you for the info. I will try it later today, when I get back home. Will let you know how things work out.
All the best

Ovidiu

---

### Post by wieman01 on 2006-12-11
Best way to resolve this is to give your ISP a call & have them reset the MAC address. Or you use a router that clones your MAC address. But having the ISP help you out will be the simplest option I reckon.

---

### Post by ovidescu on 2006-12-11
> **wieman01 said:**
> Best way to resolve this is to give your ISP a call & have them reset the MAC address. Or you use a router that clones your MAC address. But having the ISP help you out will be the simplest option I reckon.

Yeah, well, that was the first thing I thought of when I realized the situation ;) and that would have been the easy way. BUT, I thought that since I want to start learning to use Linux/Ubuntu why not find a way round this situation, like I can do in Windows ? So, here I am, begging for your help and attention :mrgreen: 
Now I can't wait to get home so I can try FrodoB's instructions.

---

### Post by ovidescu on 2006-12-11
](*,) I have followed FrodoB's instructions and nothing good came out.
This is my /etc/network/interfaces file

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
hwaddress ether 00:01:02:03:04:05
```

And SYSTEM/ADMINISTRATION/NETWORK TOOLS, under the DEVICES tab, reads: *Network device: loopback interface* and nothing more, no eth0, eth1, or anything...:-? 

I noticed that If I boot up first in Ubuntu, I don't have internet connection. If I boot up first in Windows and then reboot and choose Ubuntu from GRUB, all is okay, I have internet connection. This makes sense, since Windows writes my custom mac to the EPROM of the NIC.

So, am I doing something wrong here ? Can anyone pleeease help ?

---

### Post by spd106 on 2006-12-11
The line should look like this
```

auto eth0
iface eth0 inet dhcp
[COLOR="Red"]pre-up[/COLOR] hwaddress ether 00:01:02:03:04:05 
```

You have to tell it to run the command before "pre-up" or after "post-up". The command can be anything you like, so if you want to use macchanger instead then you can.
Check out the wikipedia page mentioned earlier.

FYI Ubuntu does include the iproute2 tools as well.

---

### Post by FrodoB on 2006-12-11
Strange, it works here just as I wrote it. I started out with the pre-up but when I read the Wikipedia article I changed it and it still works.

---

### Post by ovidiu on 2006-12-11
Ok, now my interfaces file is like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
pre-up hwaddress ether 00:01:02:03:04:05
```

But when I boot in Ubuntu I still have no network connection and I only have loopback interface listed in Network Tools under the Devices tab, no eth0 :confused: :( .
Is it somewhere else I need to insert some code lines ? 
Thank you for all the help

---

### Post by ovidescu on 2006-12-11
Without making any changes to the interfaces file, I tried
```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```
at which point I got an error: 
```
/bin/sh: hwaddress: not found
failed to bring up eth0
```
Does this help ?

---

### Post by FrodoB on 2006-12-11
Did you try it without the pre-up in front of hwaddress? That should do it.

If not change that line to something like:

pre-up ifconfig eth0 hw ether 02:01:02:03:04:05

---

### Post by FrodoB on 2006-12-11
Just checked mine it says:

auto eth0
iface eth0 inet dhcp
#pre-up ifconfig eth0 hw ether 00:01:02:03:04:05
hwaddress ether 00:01:02:03:04:05

And works through a reboot. Pre-up option also works, but is presently commented out.

---

### Post by spd106 on 2006-12-11
[QUOTE=FrodoB]Strange, it works here just as I wrote it. I started out with the pre-up but when I read the Wikipedia article I changed it and it still works.[/QUOTE]

You are quite right, the hwaddress line is an option for the interfaces file, just like address and netmask etc. So you don't need the pre-up bit.

I suggest you find a command that works from the terminal directly, then add it to the interfaces file. The ifconfig line given in the last post looks good, so try that first. My Atheros wifi card didn't like ifconfig or hwaddress when I tried to change the mac address, but I found that it did work with macchanger. So try a few variations until you find one that works.

---

### Post by FrodoB on 2006-12-11
It is working with an Aironet 340 wireless card as well as built-in SiS ethernet.

---

### Post by ovidescu on 2006-12-13
> **FrodoB said:**
> Just checked mine it says:
auto eth0
iface eth0 inet dhcp
#pre-up ifconfig eth0 hw ether 00:01:02:03:04:05
hwaddress ether 00:01:02:03:04:05


My interfaces file is identical to yours. 
Eth0 seems to get new mac and the only problem I have now is that it can't get IP from DHCP server. The Devices tab in Network tools does show loopback and eth0 (with spoofed mac) but interface information displays "not available" on all 5 descriptors and it only has IPv6 protocol, no IPv5.
Am I doing something wrong ? :confused:

---

### Post by FrodoB on 2006-12-13
Maybe your chosen MAC is seen as illegal to your DHCP server?

---

### Post by 454redhawk on 2006-12-13
I made a nifty little Zenity script to change your MAC for lazy people (like me) if anyone would like to give it a try. I had to frequenty change my mac and this helped.




```

#!/bin/sh
# This script requires "ZENITY" be installed and will change your MAC to a random or user supplied value.
# The MAC will always start with 00:
# It will only back up and restore the single previous MAC. Only 1 MAC is ever stored at any time for back up.
# That back up file will be kept in ~/ (home dir of the SU user that has executed script) and it will be named macbkup.
# After a MAC is restored the macbkup file will be deleted.
# To make changes to the MAC you must be root so follow the below instructions.
# You can run this from the desktop or the KDE menu. The command to start should be "kdesu filename" without quotes or gksu or sudo for you Ubuntu guys

# 454redhawk created this script using MEPIS 6 on 19 Sep 2006 in Afghanistan.
# I am only a newbie & copied the random number generator from the web and modified it a bit for this use.

#==============================================================================

# CHECK TO MAKE SURE YOU ARE RUNNING PROGRAM FROM ROOT!!

function id_check ()
{

if [ `id -u` -ne 0 ]; then
	zenity --error --text="You MUST be root to run MAC changer. If running from a menu then
use kdesu for KDE or gksu for GNOME. Or su and sudo from the command line."
	exit
else
	select_nic
	
fi

}

function type_action ()
{
type_of_action=`zenity --height=300 --width=275 \
			--title="Select Action" \
			--text="Pick your Fuction" \
			--list \
			--radiolist \
			--column="Pick This" \
			--column="Nic" \
			True "Change MAC" \
			False "Restore To Previous MAC" \
			False "View MAC info" \
			False "Cycle $SELECTED_NIC" \
			False "Bring down $SELECTED_NIC" \
			False "Bring up $SELECTED_NIC"`
		if [ $? = 1 ]; then
		exit
		fi

		if [ "$type_of_action" = "Restore To Previous MAC" ]; then
		
		OLDMAC="`cat ~/macbkup`"
		ifdown $SELECTED_NIC 2>/dev/null
		ifconfig $SELECTED_NIC hw ether $OLDMAC
(
			echo "0"; sleep 1
			echo "# Taking the Network Down"
			echo "10"; sleep 1
			echo "20"; sleep 1
			echo "# Bringing the network back up"
			echo "40"; sleep 1
			echo "50"; sleep 1
			echo "# Trying to aquire an IP. Could take 45 sec or more, Please wait"
			echo "60"; sleep 1
			echo "70"; sleep 1
			echo "80"; sleep 1
			ifup $SELECTED_NIC 2>/dev/null
			echo "# Network is back up"
			echo "90"; sleep .7
			echo "99"; sleep .7	
		) |	zenity 	--width=300 \
					--progress \
					--pulsate \
					--auto-close \
					--title="Restoring Previous MAC" \
					--text="Please Wait" \
					--percentage=0

		zenity 	--info --text="$SELECTED_NIC has been successfully changed to $OLDMAC"
		
		rm ~/macbkup
		
		elif [ "$type_of_action" = "Change MAC" ]; then
		make_mac
		elif [ "$type_of_action" = "View MAC info" ]; then
		 ifconfig $SELECTED_NIC | zenity --width=525 --height=450 --list --title 			"$SELECTED_NIC Info" --text "" --column "Details about $SELECTED_NIC"
		elif [ "$type_of_action" = "Cycle $SELECTED_NIC" ]; then
		ifdown "$SELECTED_NIC"
		ifup "$SELECTED_NIC"
		zenity 	--info --text="$SELECTED_NIC has been cycled"
		elif [ "$type_of_action" = "Bring down $SELECTED_NIC" ]; then
		ifdown "$SELECTED_NIC"
		zenity 	--info --text="$SELECTED_NIC is down"
		
		elif [ "$type_of_action" = "Bring up $SELECTED_NIC" ]; then
		ifup "$SELECTED_NIC"
		zenity 	--info --text="$SELECTED_NIC is up"
		fi
		    if [ $? = 1 ]; then
		exit
		else
		select_nic
			fi
}

# SELECT WHICH NIC CARD YOU WANT TO MODIFY!!

function select_nic ()
{
	SELECTED_NIC=`zenity	--height=300 \
			--width=225 \
			--title="Pick your interface" \
			--text="Pick your NIC" \
			--list \
			--radiolist \
			--column="Pick This" \
			--column="Nic" \
			True "eth0" \
			False "eth1" \
			False "eth2" \
			False "ath0" \
			False "ath1" \
			False "wlan0" \
			False "wlan1"`
			

	if [ $? = 1 ]; then
		exit
	else
		type_action
	fi
}

# CREATE NEW MAC ADDRESS!!

function make_mac ()
{
	METHOD=`zenity 	--title="Change MAC address" \
				--text="Make your selection" \
				--list \
				--radiolist \
				--column="" \
				--column="Select MAC type" \
				True "RANDOM" \
				False "CUSTOM"`

	if [ $? = 1 ]; then
		exit
	fi

	if [ $METHOD = "RANDOM" ]; then
		
		ifconfig  $SELECTED_NIC | grep -o ..:..:..:..:..:..  >~/macbkup
		ifdown $SELECTED_NIC 2>/dev/null
		match1=00
		match2=`head -1 /dev/urandom | md5sum | cut -b 4,5`
		match3=`head -1 /dev/urandom | md5sum | cut -b 6,7`
		match4=`head -1 /dev/urandom | md5sum | cut -b 8,9`
		match5=`head -1 /dev/urandom | md5sum | cut -b 10,11`
		match6=`head -1 /dev/urandom | md5sum | cut -b 12,13`
		NEW_MAC="$match1":"$match6":"$match2":"$match5":"$match3":"$match4"
	
		update_mac
		
	elif [ $METHOD = "CUSTOM" ]; then
		
		ifconfig  $SELECTED_NIC | grep -o ..:..:..:..:..:..  >~/macbkup
		NEW_MAC=`zenity	--entry \
			--title="Change MAC" \
			--text="Enter MAC, First 2 digits should be 00 then [0-9 a-f]   for the rest, Example 00:54:9c:0c:7e:6b" \
			--entry-text "00:40:CA:35:6A:EE"`
		if [ $? = 1 ]; then
			exit
		fi
		
		update_mac
		exit_stat=$?
		return 
		fi

}

# UPDATE MAC ADDRESS TO "$NEW_MAC"!!

function update_mac ()
{
	if [[ $NEW_MAC == 00:??:??:??:??:?? ]]; then
		ifdown $SELECTED_NIC 2>/dev/null
		ifconfig $SELECTED_NIC hw ether $NEW_MAC 2>/dev/null
		(
			echo "0"; sleep 1
			echo "# Taking the Network Down"
			echo "10"; sleep 1
			echo "20"; sleep 1
			echo "# Bringing the network back up"
			echo "40"; sleep 1
			echo "50"; sleep 1
			echo "# Trying to aquire an IP. Could take 45 sec or more, Please wait"
			echo "60"; sleep 1
			echo "70"; sleep 1
			echo "80"; sleep 1
			ifup $SELECTED_NIC 2>/dev/null
			echo "# Network is back up"
			echo "90"; sleep .7
			echo "99"; sleep .7	
		) |	zenity 	--width=300 \
					--progress \
					--pulsate \
					--auto-close \
					--title="Changing MAC" \
					--text="Please Wait" \
					--percentage=0

		zenity 	--info --text="$SELECTED_NIC has been successfully changed to $NEW_MAC"

	elif [ $NEW_MAC != 00:??:??:??:??:?? ]; then
		zenity 	--error \
				--text="Invalid MAC address, Make sure the first two are 00 and the rest are [0-9 a-f] "
		make_mac
		exit
	fi 
}

id_check

```

---

### Post by ovidescu on 2006-12-14
> **FrodoB said:**
> Maybe your chosen MAC is seen as illegal to your DHCP server?
The same MAC works ok in Windows :confused: 
I think I will call my ISP and ask them to change my MAC on the dhcp server, which is what I should have done when I changed the first NIC. Will let you know how things work out. Thank you for all the help.

Ovidiu

---

### Post by ovidescu on 2006-12-14
@ 454redhawk

I am REALLY new to the linux world and scipts and such are things I only hear about  and never try it for myself. Thank you for posting your code for me, but I think I will call my ISP and ask them to change my MAC in the dhcp server. 

Ovidiu

---

### Post by FrodoB on 2006-12-14
Good luck.

---

### Post by ovidescu on 2006-12-15
I am writing these from my Ubuntu installation. I have called my ISP and ask them to change my MAC in the DHCP server and all is well now. I have internet connection in Ubuntu as well as in Windows. 
Thank you guys for your replies. I will check these forums on a regular basis for sure, as they seem to be an endless source of inspiration. 

Ovidiu

---

### Post by galileon on 2007-02-03
> **DaveBorealis said:**
> Hello,

You could try changing it with the network interface.  In '/etc/network/interfaces' add the following line under (I'm assuming) 'auto eth0':
```
hwaddress ether 01:01:01:01:01:01
```
(Use your own mac number, of course.)

I've never spoofed a mac before, so I can't guarantee this'll work.

But hope that helps,
Dave

worked like a charm here, and internet is working after a reboot. ifconfig shows the spoofed mac address.

however, network-manager is now oblivious of the existence of a wired network!

any ideas?

---

