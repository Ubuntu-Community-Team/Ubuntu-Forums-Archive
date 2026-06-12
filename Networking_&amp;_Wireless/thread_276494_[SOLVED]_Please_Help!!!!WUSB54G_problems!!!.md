---
title: "[SOLVED] Please Help!!!!WUSB54G problems!!!"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by JawsThemeSwimming428 on 2006-10-13
I have been trying to install my WUSB54G wireless network adapter on my Ubuntu 6.06 system for about 2 weeks. I am having no luck with any of the links I have been given with instructions. I am very new to linux and ubuntu and need detailed instructions. If anyone is willing to help I would be very greatful! 

   I already blacklisted rt2570 and installed build-essentials and linux-source. I have absolutely no idea how to install Ndiswrapper. I am using 2 different PC's. The one I am typing this on right now runs WinXP SP2 and I have a separate box that just runs ubuntu. I download ndiswrapper to this machine and put it on a thumb drive and copy it to the Ubuntu machine. When I copy it to the Ubuntu machine the file comes up as 'Found.000' and I have no idea what to do with it. 
   When I look in Admin->Networking I see etho0 which is active and ppp0 (modem) that says "not configured". Thanks for taking the time to try and help me out, I appreciate it all. My AIM screnname is Trust428, please feel free to contact me that way as well. Thanks!!!!!!!!!!!!!!

---

### Post by wieman01 on 2006-10-13
Hang on a minute... I have seen this post before. Was the other instruction unclear?

The first thing you should do it install these packages using Synaptic (the packages are on the **[COLOR="Red"]Ubuntu Live CD[/COLOR]**):

1. ndiswrapper-utils
2. ndisgtk

I reckon that's not too difficult, is it? Please do this first and find the corresponding WINDOWS driver for your card. We will need the Windows driver together with the 2 mentioned packages to get your card working.

Is that a problem?

---

### Post by wieman01 on 2006-10-13
If you have problem with the CD & Synaptic, try this (throw in the Live CD first):
> sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils ndisgtk

---

### Post by JawsThemeSwimming428 on 2006-10-13
No, I'm ok doing that. However, when I went into synaptic I installed ndiswrapper-utils, but ndisgtk is non-existent. There is nothing by that name. Am I doing something wrong or does Ubuntu 6.06 not have an ndisgtk package? Yea I have been posting on the Ubuntu forum for about a week now trying to have someone help me get this thing installed. I appreciate your help!

---

### Post by wieman01 on 2006-10-13
Ok, don't worry about "ndisgtk" for now. It's just a graphical frontend for "ndiswrapper". Have you got the Windows drivers on hand?

If you have the driver, then see if the driver file is an *.EXE. If so, you need to UNZIP the *.EXE since it's a mere archive that contains the driver files.

Put all the driver files (next to *.INF) in one folder on your Ubuntu PC.  The run this command to deploy the *.INF / driver:
> sudo ndiswrapper -i /path/to/folder/drivername.inf
Replace "/path/to/folder/" with the corresponding path and "drivername.inf" with the right name of the *.INF file. That done do this to see if this has been successful:
> ndiswrapper -l
Please post the output of all commands you're running.

---

### Post by wieman01 on 2006-10-13
IMPORTANT NOTE: If you deploy *.INF while all other driver files are not in the same folder, it will fail. "ndiswrapper" needs all files and will copy them to another directory.

---

### Post by JawsThemeSwimming428 on 2006-10-13
Ok, I did everything you said and I didn't encounter any problems. Here is the output:

willy@willy-desktop:~/Desktop/WUSB54Gv4$ sudo ndiswrapper -i /home/willy/Desktop/WUSB54Gv4/rt2500usb.inf
Password:
Installing rt2500usb
willy@willy-desktop:~/Desktop/WUSB54Gv4$ ndiswrapper -l
Installed ndis drivers:
lswlusb         driver present
rt2500usb               driver present
willy@willy-desktop:~/Desktop/WUSB54Gv4$


What do I do next?

---

### Post by wieman01 on 2006-10-13
Congrats, buddy. That's a another step in the right direction. :-)

Next commands. Please also post the output for each command so that we now what's going on.

>> "Blacklisting" old rtxxx driver which may conflict with "ndiswrapper":
> echo 'blacklist rt2570' | sudo tee -a /etc/modprobe.d/blacklist
>> Load the driver module ("ndiswrapper") on start-up:
> sudo gedit /etc/modules
>> Add this line at the end of the file ("/etc/modules"):
> ndiswrapper
>> Save the file & restart the computer.

That's it. Now we continue from there. You'll have to let me know more about your network & its settings: DHCP or Static IP, ESSID (= wireless network name), encryption, router address, etc.

To begin with I would disable all kinds of encryption. Done that post the contents of this file:
> sudo gedit /etc/network/interfaces

---

### Post by JawsThemeSwimming428 on 2006-10-14
Ok...I did all of that stuff as well, no problems yet. The network is DHCP, we'll use linksys as the network name, I don't know the router address, and the rest is done. Here is the output from the /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


I really appreciate your help and patience, I realize I'm not the most knowledgable person in this area. What next??????????

---

### Post by wieman01 on 2006-10-14
> **JawsThemeSwimming428 said:**
> I really appreciate your help and patience, I realize I'm not the most knowledgable person in this area. What next??????????
Don't worry. My pleasure.

Try this command first & post the output:
> iwlist wlan0 scan
The edit "interfaces" so that it looks like this (this is all you need):
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
[COLOR="Red"]wireless-essid linksys[/COLOR]
Then restart the network & see how it goes (output please):
> sudo /etc/init.d/networking restart

---

### Post by JawsThemeSwimming428 on 2006-10-14
ok....from the 'iwlist wlan0 scan' command I got the following output:

   wlan0 Interface doesn't support scanning.

Then I edited 'interfaces' with what you had....but am I supposed to delete everything else and just have what you have...or just add what you have to the whole file? I kept everything that was in there and just added what you did.

Lastly, when I ran '/etc/init.d/networking restart' I got the following output:

    willy@willy-desktop:~$ sudo gedit /etc/network/interfaces
willy@willy-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:76:46:92:a2
Sending on   LPF/eth0/00:16:76:46:92:a2
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:76:46:92:a2
Sending on   LPF/eth0/00:16:76:46:92:a2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


What does that mean? What should I do now?

---

### Post by JawsThemeSwimming428 on 2006-10-14
Also, should I have my wireless network adapter plugged in to the PC while I'm doing this stuff? Right now it's not. I think it was plugged in when I ran the network restart command but then that didn't work so I took it out again. Thanks again!!

---

### Post by wieman01 on 2006-10-14
> **JawsThemeSwimming428 said:**
> Then I edited 'interfaces' with what you had....but am I supposed to delete everything else and just have what you have...or just add what you have to the whole file? I kept everything that was in there and just added what you did.
Please replace the content of your "interfaces" file with what I have posted previously. That's all you need actually because the other lines are all "dummies".
> **JawsThemeSwimming428 said:**
> Also, should I have my wireless network adapter plugged in to the PC while I'm doing this stuff? Right now it's not. I think it was plugged in when I ran the network restart command but then that didn't work so I took it out again. Thanks again!!
Well... yes. We cannot proceed or scan or connect to the wireless network if we don't have the adapter plugged in I guess.

Have you turned on the router? That done do these commands again (_all_ 3 of them please):
> ifconfig
> iwconfig
> iwlist scan
See you later!

---

### Post by JawsThemeSwimming428 on 2006-10-15
OK, sorry for the delay I've been pretty busy. I did not have a chance to do that stuff yet but tonight when I get home from work around midnight I will. Thanks for your help!!!!!!!!

---

### Post by wieman01 on 2006-10-15
Don't worry. I'll check on you later on again. We're getting there. :-)

---

### Post by JawsThemeSwimming428 on 2006-10-16
Alright, I did everything you said and my network adapter is plugged in (yes, the router was plugged in before). Here is the output from the 3 commands you told me to run:

willy@willy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:46:92:A2
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5412 (5.2 KiB)  TX bytes:5412 (5.2 KiB)

willy@willy-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

willy@willy-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

willy@willy-desktop:~$


    I know nothing about what I am about to say but it doesn't seem that anything is recognizing 'wlan0'. Is there any reason it doesn't come up in the scan?

Here is what my 'interfaces' file looks like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys


What's next?

---

### Post by wieman01 on 2006-10-16
Oh man... I have just discovered a mistake on my part. Please make sure that...
> ndiswrapper
...is listed at the end of this file...
> sudo gedit /etc/modules
...and - **by no means** - here:
> /etc/modprobe.d/blacklist
I have corrected my previous post. Sorry for the mishap if you have fallen into the trap. Could you check & then do the scanning again (after a reboot)?

Let me know how that goes.

---

### Post by JawsThemeSwimming428 on 2006-10-16
It's ok, I had ndiswrapper in the right spot but I did check. At the end of /etc/modules I have "ndiswrapper". However, I still got the same output:

willy@willy-desktop:~$ iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

sit0 Interface doesn't support scanning.

What is sit0? and is wlan0 supposed to be there? It seems like something is wrong, it doesn't know the adapter is there?

---

### Post by wieman01 on 2006-10-16
Ok. Have you got **[COLOR="Red"]NetworkManager[/COLOR]** installed? **[COLOR="Red"]"sit0"[/COLOR]** seems to indicate that... If so, please uninstall it, otherwise we won't succeed. :-) That done restart the computer and do a few more scans.

Let's see if the hardware & the driver have been installed:
> sudo lshw | grep 'Links'
Output please...

---

### Post by JawsThemeSwimming428 on 2006-10-16
I went to check and see if Network Manager was installed in Applications-> Add/Remove and I found four instances with network manager, none of which were installed. There was a KnetworkManager and a GnomeNetworkManager, I clicked the check box on the gnome one just to see if it was installed and this is the error message that came up:“ network-manager-gnome is not available in any software channel. The application might not support your system architecture.” So there are none installed unless I missed something.

 I then did the command sudo lshw | grep 'Links' and I got the following output:

willy@willy-desktop:~$ sudo lshw | grep 'Links'
Password:
                   vendor: Cisco-Linksys
willy@willy-desktop:~$

That's good right? What next?

---

### Post by wieman01 on 2006-10-16
Please scan again:
> iwlist scan
If "sit0" is still there then NetworkManager might still be there. The try this:
> sudo apt-get remove network-manager-gnome
> sudo apt-get remove knetworkmanager
Please restart the computer and scan once more. Also run this command and post the output (again):
> sudo /etc/init.d/networking restart

---

### Post by wieman01 on 2006-10-16
> **JawsThemeSwimming428 said:**
> I then did the command sudo lshw | grep 'Links' and I got the following output:

willy@willy-desktop:~$ sudo lshw | grep 'Links'
Password:
                   vendor: Cisco-Linksys
willy@willy-desktop:~$

That's good right? What next?
Is that all it says? No mentioning of the wireles card or model? What about this one:
> lsusb
Can you find it there?

---

### Post by JawsThemeSwimming428 on 2006-10-16
Here is the output when I scanned again:

willy@willy-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


Then I did both of the remove commands for the network managers and here is the output for that:

willy@willy-desktop:~$ sudo apt-get remove network-manager-gnome
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package network-manager-gnome
willy@willy-desktop:~$ sudo apt-get remove knetworkmanager
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package knetworkmanager
willy@willy-desktop:~$

 After that I restarted and then scanned again, here is the output:

willy@willy-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


Then I ran the networking restart command and this is the output:


willy@willy-desktop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:76:46:92:a2
Sending on   LPF/eth0/00:16:76:46:92:a2
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:76:46:92:a2
Sending on   LPF/eth0/00:16:76:46:92:a2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]

Lastly, I did the lsusb command and got this:

willy@willy-desktop:~$ lsusb
Bus 003 Device 002: ID 13b1:000a Linksys
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
willy@willy-desktop:~$

Any idea? Do we have to bring up the 'wlan0' interfaces? I worked a little with Fedora last year in a networking class I had and I remember we had to “bring up” the interfaces to use them. Just an idea! Now what?

Also, I don't know whether this has any thing to do with the situation but the wireless adapter I am using (WUSB54G) is a wireless-G network adapter and I am trying to connect to a wireless-B network. G is backward compatible, just at the slower speed, right? We have already purchased a Wireless G router we just are looking for time to install it. So the network, within the next few weeks will be G. Is this the problem?

---

### Post by wieman01 on 2006-10-16
Ok, I need to search for something else when I am back home tonight. I am not sure what's going on at the moment. I will also upload a copy of my WUSB54G driver, perhaps this will help.

As for "bringing up" the interfaces, the mentioned command ("sudo /etc/init.d/networking restart") should to. But could you do me a favor and **check** if the little green light on the adapter is turned on?

The wireless B router will do as well. You'll might have timeout/performance issues later on but it should let you connect by all means. You're right in that it is backward compatible.

What does...
> ndiswrapper -l
...say again? Driver is installed, right? The problem is that "wlan0" has not been configured, basically meaning that there is no "ndiswrapper" and not Windows driver installed. Let's ignore "sit0" for the time being.

You have a WUSB54G **[COLOR="Red"]V4[/COLOR]**, right?

---

### Post by JawsThemeSwimming428 on 2006-10-16
Yes, the Power light on the adapter is lit when the computer is on. So it is receiving power. I know I saw somewhere it said V4 but I can't remember where...Where can I find that out?

Ndiswrapper -l outputs:

willy@willy-desktop:~$ ndiswrapper -l
Installed ndis drivers:
lswlusb      driver present
rt2500usb            driver present, hardware present

---

### Post by JawsThemeSwimming428 on 2006-10-16
Also, when I run 'ifconfig' all I see now is 'eth0' and 'lo'. Shouldn't 'wlan0' be there as well?

---

### Post by wieman01 on 2006-10-17
> **JawsThemeSwimming428 said:**
> Also, when I run 'ifconfig' all I see now is 'eth0' and 'lo'. Shouldn't 'wlan0' be there as well?
Yes, "wlan0" should be there as well. Everything is telling us that the installation has been successful.

There is a graphical configuration tool for wireless adapter in Gnome. Can you open it & activate "wlan0"? Can you see "wlan0" in the drop-down list?

---

### Post by wieman01 on 2006-10-17
I'll find a few more tools back home that we can use in order to test your network. Try my previous proposal first, however. This is odd.

---

### Post by JawsThemeSwimming428 on 2006-10-17
I'm not sure if this is what you meant but I went to System->Administration->Networking and looked in the connections tab and the only two interfaces there are the Modem (ppp0) and eth0. Is there another utility and if so where is it located?

---

### Post by wieman01 on 2006-10-17
> **JawsThemeSwimming428 said:**
> I'm not sure if this is what you meant but I went to System->Administration->Networking and looked in the connections tab and the only two interfaces there are the Modem (ppp0) and eth0. Is there another utility and if so where is it located?
That's the right utility... Man, this is indeed odd. I have to think for a while & get back to you later on. We're missing something here...

---

### Post by JawsThemeSwimming428 on 2006-10-17
Ok sounds good, sorry for the trouble. I appreciate your help! This is completely up to you but it might be quicker if we could "directly speak", through AIM. Tomorrow night around 8pm EST I will be available, and if you are I would greatly appreciate it if we could try this. If not, it's completely fine, I just don't want to waste more of your time than I already am!! Just let me know, I will be online tomorrow around 8 and my AIM screen name is TrUsT428. If you have any ideas let me know and I'll get right on them. Talk to you later.

---

### Post by wieman01 on 2006-10-17
> **JawsThemeSwimming428 said:**
> Ok sounds good, sorry for the trouble. I appreciate your help! This is completely up to you but it might be quicker if we could "directly speak", through AIM. Tomorrow night around 8pm EST I will be available, and if you are I would greatly appreciate it if we could try this. If not, it's completely fine, I just don't want to waste more of your time than I already am!! Just let me know, I will be online tomorrow around 8 and my AIM screen name is TrUsT428. If you have any ideas let me know and I'll get right on them. Talk to you later.
That's fine. Problem is that I am in a different timezone (China) so the only option we have is Friday night (your time). That will be Saturday morning my time... 

Just to get this right: What time is it where you are right now? It's 12.45 PM here (Tuesday).

---

### Post by wieman01 on 2006-10-17
To round this up, please also post this one:
> sudo gedit **/etc/modprobe.d/ndiswrapper**
I'll create an AIM account tonight & see if I can get hold of you on line.

---

### Post by JawsThemeSwimming428 on 2006-10-17
It's 1am (Tuesday) here. So I see the dilemma! Friday night should be good too. Just let ne know what time. I think you are 12 hours ahead of me in time. When you create your AIM account put the screen name on here so that I can check for you too. Thanks again for your help! Talk to you soon.

---

### Post by wieman01 on 2006-10-17
> **JawsThemeSwimming428 said:**
> It's 1am (Tuesday) here. So I see the dilemma! Friday night should be good too. Just let ne know what time. I think you are 12 hours ahead of me in time. When you create your AIM account put the screen name on here so that I can check for you too. Thanks again for your help! Talk to you soon.
In the meantime, you can perhaps show us this file:
> sudo gedit /etc/modprobe.d/ndiswrapper
That's where your WLAN alias for "ndiswrapper" is hiding...

---

### Post by JawsThemeSwimming428 on 2006-10-17
I did the command 'sudo gedit /etc/modprob.d/ndiswrapper' and the file it opened was blank. Did something maybe go wrong with the installation of ndiswrapper? That seems strange.

---

### Post by wieman01 on 2006-10-17
That IS strange. So there is no alias for "ndiswrapper" at all. No surprise the system cannot find it. Please add this line & restart the PC:
> alias wlan0 ndiswrapper
What does the scan say after a reboot?
> islist scan

---

### Post by JawsThemeSwimming428 on 2006-10-17
'iwlist scan' still says:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys


Would it be possible that ndiswrapper was not set up right? Could we have to run 'ndiswrapper -d devid driver'?

---

### Post by wieman01 on 2006-10-17
> **JawsThemeSwimming428 said:**
> 'iwlist scan' still says:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys
That's not a scan, but your "interfaces" file. That scan delivers no results at all?
> iwlist wlan0 scan
> **JawsThemeSwimming428 said:**
> Would it be possible that ndiswrapper was not set up right? Could we have to run 'ndiswrapper -d devid driver'?
According to my understanding that is not necessary. "ndiswrapper" even says that the driver has been installed correctly, however, you can try.

---

### Post by wieman01 on 2006-10-17
The problem is that your driver has been installed, it's just that the "ALIAS" is somehow missing. The solution above should fix that at least.

---

### Post by JawsThemeSwimming428 on 2006-10-17
sorry I ran the wrong scan. 'iwlist wlan0 scan' returns 

'wlan0          Interfaces doesn't support scanning'  



what do you think I should do?

---

### Post by JawsThemeSwimming428 on 2006-10-17
'/etc/modprobe.confg' is empty if you wanted that.

---

### Post by wieman01 on 2006-10-17
Ah... We have to wait until Friday. Running out of ideas at the moment. This IS a though one. :-) But don't worry, we'll find a way.

---

### Post by wieman01 on 2006-10-17
> **JawsThemeSwimming428 said:**
> '/etc/modprobe.confg' is empty if you wanted that.
That's fine. I'll do some more thinking and talk to you on Friday at the latest. :-)

---

### Post by JawsThemeSwimming428 on 2006-10-17
Ok, sounds good! Sorry it's taking a while. Thanks for everything. If you think of anything I can do till then just let me know.

---

### Post by wieman01 on 2006-10-17
Alright, one last thing for today. What files are in this folder?
> /etc/ndiswrapper/rt2500usb
Please post all files with [COLOR="Red"]*.conf[/COLOR] suffix.

---

### Post by JawsThemeSwimming428 on 2006-10-17
It says it can't open the file, I think it is blacklisted. Should I take it off the blacklist?

 Side note: I just ran the command 'sudo ndiswrapper -d 13b1:000a lswlusb' then i rebooted and it wouldnt get past loading manual drivers. I unplugged the adapter and it booted fine. How do I undo what I just did?

---

### Post by JawsThemeSwimming428 on 2006-10-17
rt2570 is blacklisted

---

### Post by wieman01 on 2006-10-17
> **JawsThemeSwimming428 said:**
> It says it can't open the file, I think it is blacklisted. Should I take it off the blacklist?

 Side note: I just ran the command 'sudo ndiswrapper -d 13b1:000a lswlusb' then i rebooted and it wouldnt get past loading manual drivers. I unplugged the adapter and it booted fine. How do I undo what I just did?
Oh oh... 
> sudo ndiswrapper [COLOR="Red"]-e[/COLOR] 13b1:000a lswlusb
Play around with the -e option.

---

### Post by JawsThemeSwimming428 on 2006-10-17
now when i look in the ndiswrapper folder there is only rt2500usb and there is no lswlusb anymore...what do i have to reinstall?if anything

---

### Post by wieman01 on 2006-10-17
I would try to reinstall...

---

### Post by JawsThemeSwimming428 on 2006-10-17
Reinstall what....and how?

---

### Post by JawsThemeSwimming428 on 2006-10-17
Do I reinstall the driver? and how do I do that...what commands? Sorry. Just tell me what commands I need to run in order to reinstall lswlusb. Thanks...talk to you soon.

---

### Post by wieman01 on 2006-10-18
> **JawsThemeSwimming428 said:**
> Do I reinstall the driver? and how do I do that...what commands? Sorry. Just tell me what commands I need to run in order to reinstall lswlusb. Thanks...talk to you soon.
What I would do it fire up Synaptic, the graphical installer. Then search for "ndiswrapper-utils", right-click & press "complete removal" or similar. That will eliminate all configuration files, etc. 

After that reboot the computer and start all over again from the beginning of this thread. That's the safest way to undo all the changes.

The rest we will tackle on Friday.

---

### Post by wieman01 on 2006-10-18
One more thing: Try to get the latest driver for your card from the vendor's web-site. Also check the **back** of the adapter & confirm that it says "WUSB54G **[COLOR="Red"]V4[/COLOR]**".

---

### Post by JawsThemeSwimming428 on 2006-10-18
I think I found our problem...its WUSB54G v2 not v4. I guess I should just go back to the beginning of this post and do everything again with the v2 drivers. I'll probably do this either tonight(wed night) or tomorrow night(thurs night). I'll post on here and let you know how it goes. Sorry.

---

### Post by wieman01 on 2006-10-18
> **JawsThemeSwimming428 said:**
> I think I found our problem...its WUSB54G v2 not v4. I guess I should just go back to the beginning of this post and do everything again with the v2 drivers. I'll probably do this either tonight(wed night) or tomorrow night(thurs night). I'll post on here and let you know how it goes. Sorry.
Don't worry... Actually I was hoping that this is the problem. Simply because I cannot tell at the moment whatelse could be wrong.  :-)

Please also get the latest driver from Linksys' website. Just to avoid any other surprises. Let me know how it goes. You got me curious. 

See you soon!

---

### Post by JawsThemeSwimming428 on 2006-10-18
OK, so that's what it was. I removed everything, reinstalled ndiswrapper, and installed the new driver. 5 minutes later I had internet. Thanks for your help!

---

### Post by wieman01 on 2006-10-18
> **JawsThemeSwimming428 said:**
> OK, so that's what it was. I removed everything, reinstalled ndiswrapper, and installed the new driver. 5 minutes later I had internet. Thanks for your help!
Holy... Oh well. Sometimes the solution are so obvious you don't see the wood for the trees. Glad it helped. Let me know if you need help with setting up WEP or WPA (encryption, authentication).

Cheers / He

---

### Post by mtutty on 2006-11-25
Well, I'm a little sorry to hear about Jaws... solution because it's definitely not mine. I've been following this entire thread, checking all of the same things you've suggested along the way.

Here are some diags from my terminal session:

```

family@mediabox:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:15:05:12:06:DB
                    ESSID:"tutty"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:0/100  Signal level:-33 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

family@mediabox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

family@mediabox:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5749
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:b6:96:63:70
Sending on   LPF/wlan0/00:16:b6:96:63:70
Sending on   Socket/fallback

family@mediabox:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:16:b6:96:63:70
Sending on   LPF/wlan0/00:16:b6:96:63:70
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9

family@mediabox:~$ modprobe -l | grep ndis
/lib/modules/2.6.17-10-generic/kernel/drivers/usb/net/rndis_host.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

family@mediabox:~$ modprobe -l | grep rt2
/lib/modules/2.6.17-10-generic/kernel/drivers/usb/net/rt2570/rt2570.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/rt2x00-legacy/rt2500/rt2500.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/rt2x00-legacy/rt2400/rt2400.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/rt2x00/rfkill.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/rt2x00/rate_control.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/rt2x00/crc-itu-t.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/rt2x00/80211.ko

family@mediabox:~$ sudo ndiswrapper -l
Installed drivers:
rt2500usb               driver installed, hardware present 

```

My integrated nic (eth0) works fine. When I bounce it with ifup/ifdown, I see a "normal" (successful) DHCPDISCOVER/DHCPOFFER/DHCPREQUEST/DHCPACK sequence.

This box/wlan unit/wireless router have previously worked together under Windows XP and been fine. I also had KnoppMyth running on it for a few days and the wlan worked there, too, right out of the box.

Any ideas?? I'm stuck on my project until I get this licked.

Thanks!

---

### Post by wieman01 on 2006-11-26
When you try to connect to the wirelesse network, you need to make sure that the Ethernet cable is unplugged. What card have you got?

---

