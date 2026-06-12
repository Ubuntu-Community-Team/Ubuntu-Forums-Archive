---
title: "WUSB300N adapter"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by tnh5g3zpi7bzcev on 2007-08-20
Any more news on this adapter? I've tried what is suggested (ndiswrapper) and it doesn't work. It installs driver and adapter light comes on, lets me configure WEP, etc, but just no connection after all that. Any experts here got this thing working? Or, maybe, more technical tricks/suggestions? Thanks!!

---

### Post by mcdsco on 2007-08-24
**Here is how I got it working, don't plug in the WUSB300N yet:**

**Download the drivers:**
[http://www.atvnation.com/WUSB300N.tar](http://www.atvnation.com/WUSB300N.tar)

**Extract them to /opt/ndis/:**
# mkdir /opt/ndis
# tar xvf WUSB300N.tar -C /opt/ndis/
# cd /opt/ndis/Drivers

**Install the Driver using NDISWrapper**
# sudo ndiswrapper -i netmw245.inf
[INDENT]installing netmw245 ...[/INDENT]

# sudo ndiswrapper -l
[INDENT]netmw245 : driver installed[/INDENT]

# sudo modprobe ndiswrapper
... go ahead and plug in the adapter ... 

# sudo dmesg | grep ndis
[INDENT]"[ 9273.652000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[ 9273.712000] usbcore: registered new interface driver ndiswrapper
[ 9340.364000] ndiswrapper: driver netmw245 (Linksys, A Division of Cisco Systems, Inc.,12/07/2006,1.0.5.1) loaded"
[/INDENT]

You should now be able to go to your Network Applet Icon and see wireless network in the list.

... or the command iwconfig should return an entry for wlan0, mine looks like this:
[INDENT]wlan0     IEEE 802.11FH  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/INDENT]

If you have an unprotected wireless hub, then issue this command to connect:
# sudo dhcpclient wlan0

Hope that helps <><Scott><>

---

### Post by mcdsco on 2007-08-25
I changed my instructions listed above, so if you ran into trouble, here is how you need to undo the changes.

I assumed incorrectly that ndiswrapper loads the inf file and you don't need it on the system any more ... this is incorrect.  When you reboot the system, all of the contents of /tmp goes away and it breaks the WUSB300N.  To undo this do the following:

1.  The driver is still installed, but it is in a funky state because the inf file is missing.  If you need to, download the tar file again as mentioned above and copy it to /opt/ndis/ as mention in the beginning of the instructions above.

2.  You now have to delete the old driver, so copy the four files in the tar to the /tmp/Drivers/ directory like it originally was before you rebooted, then issue this command:
[INDENT]# sudo ndiswrapper -r netmw254[/INDENT]

-- Now follow the instructions listed above ... sorry for the confusion.

---

### Post by tnh5g3zpi7bzcev on 2007-08-26
Awesome dude! No worries, I followed the instructions after you changed them. I've got wireless! Thanks for the easy to follow instructions (*_*)

---

### Post by tnh5g3zpi7bzcev on 2007-08-26
On that note, any support for WPA or am I left with WEP only? I haven't tried it as I didn't want to mess things up. Thanks.

---

### Post by notz on 2007-08-28
i have a identical card. you should use ndiswrapper version 1.43. that version works (1.38 ist too old). newer version have some problems after a amount of time.

---

### Post by tnh5g3zpi7bzcev on 2007-08-29
Also, don't forget to 

# sudo ndiswrapper -m 

adding the above loads the drivers on each boot to maintain wireless network activity.


Ha. I kept rebooting and losing my internet and couldn't figure out why.

---

### Post by patrickfromspain on 2007-09-05
why are you moving all stuff into /opt? once you finish installing the drivers with ndiswrapper you don't need them anymore.

---

### Post by johngonewbie on 2007-12-27
I'm confused. ndiswrapper 1.5.1 isn't installing. I got kubuntu to install ndiswrapper comon from the CD. However no luck in installing the driver. I copied the drivers to my user directory (my sisters computer actually) and the ndiswrapper 1.51. 

I type in 

# sudo ndiswrapper -i netmw245.inf 

and i get an error  no ndiswrapper utils found

:confused:

I cannot create /opt/ndis/ because there are no permissions to do so.

I am new to unix but am determined to get this working.

---

### Post by johngonewbie on 2007-12-28
Wireless is now working. I needed to actually do some reading. I'm smart!!!

:)

Thanks for your help mcdsco

The tar command as written did not work for me. Got it resolved eventually.

---

### Post by terryfunk4life on 2008-01-16
Wow thank you very much man :guitar:

---

### Post by smokebox46and2 on 2008-01-25
hi... i'm a complete noob... sorry ...but

when i run the

sudo ndiswrapper -l

it returns "invalid driver"

i have the files in the correct place, i'm sure

when i run the sudo dmesg | grep ndis

it says ndiswrapper 1.51 is loaded

why does it say invalid driver?

thanx

---

### Post by just4priya on 2008-02-07
Hi, 

I am able to scan the wireless network with WUSB300N
However i m unable to connect. 
How do i connect to a wireless network manually.
I do not have the GUI installed... 

I have the WEP key for a particular essid.
Desperately looking out for some help/solutions. 

Pleaase help :(


~just4priya

---

### Post by s0sheamex5 on 2008-02-29
I am a true nubie to all things linux.  I am trying to get my Wireless adaptor running, but when I follow the procedure provided I get this:

# sudo ndiswrapper -i netmw245.inf
       **netmw245 is already installed**
# sudo ndiswrapper -l
       **netmw245 : invalid driver**

Can anyone help me understand what I am doing wrong?

This is the same problem which has smokebox46and2.

---

### Post by Jungliztik on 2008-05-01
Hi,

I followed the instructions provided and was able to get the adapter working and connected to my network but when I reboot the system, the adapter is not recognised. :(

I can get it running again by re-issuing the command:
sudo modprobe ndiswrapper , and then everything is fine again.

I've tried to run the command sudo modprobe ndiswrapper and I see the following returned:
*module configuration already contains alias directive*

I've added the command *gksudo modprobe ndiswrapper* to my session configuration, so I can get it to work but it's not ideal.

I'm running a newly installed 8.04 image.

Any help greatly appreciated.

Dave.

---

### Post by Jungliztik on 2008-05-01
Okay, so I've worked it out... add ndiswrapper to /etc/modules, remove the  entry in the 'startup programs' tab in 'System >> Preferences >> Sessions', reboot and the network connects. :)

Thanks for the guide, much appreciated.

---

### Post by itsfullofstars on 2008-05-15
The following was taken directly from a post on the Linksys forum.  Minor edits.

**PROBLEM**

Disconnects or system hangs/crashes.

After dozens of hours working on this, researching on the net, etc., I have the answer to the problems.
 
The WUSB300N uses a chipset called TOPDOG made by Marvell. This same chipset is in every 802.11n draft adapter implementation out there from what I can tell -- Linksys, Belkin, D-Link, etc. There might be a competing chipset, but I stopped investigating when I nailed down the source of the problems.
 
All these implementations use a driver made by Marvell, the manufacturer of the TOPDOG chipset. There are different versions out there, but apparently none that are OEM-specific.
 
**CAUSE**
 
Two manufacturers NICs experienced the same issues -- Linksys, and D-Link. I didn't try any others. Both cause disconnects (manufacturer's wifi manager managing the connection) or system hangs/crashes (XP managing the connection through WZC). **The failure seems to only occur when a large number of TCP connections are being managed by the system, as well as a high rate of connection attempts to different hosts.**
 
This sort of environment is exactly what happens in P2P applications. Most common are bittorrent clients, and on-line gaming.
 
I could blow out the WUSB300N within a minute or two by firing up Azureus (bitorrent), with a lot of seeding torrents (60).
 
Problem #1 is the Linksys WUSB300N implementation. It's flaky hardware. I had two, and both behaved exactly the same on my WinXP machine with the latest driver available from Linksys (v1.0.1.7, IIRC).
 
The DWA-142 Wireless N USB adapter from D-Link performed much better regardless of the driver. The Marvell driver installed from the CD was version 1.0.1.2; Both NICs worked with this driver, and average throughput was about 25% faster than with v1.0.1.7 shipped with the WUSB300N. As noted, WUSB300N died within a minute or two of cranking up the connections and connrate. D-Link ran for as long as 2 hours without a problem, then same failure mode.
 
This was true with all three Marvell driver versions I had: 1.0.1.7 from Linksys, 1.0.1.2 from D-Link, and one other, 1.0.5.5 that came from a Microsoft optional update. Again, both mfg adapters worked with all these drivers, all failed in the same way, D-Link was massively more stable (and a little faster) than Linksys.
 
**THE SOLUTION**
 
Marvell apparently has fixed these problems in their latest driver. It is version 1.0.6.4. The only place I could find it was on the D-Link website, in the support section, available as a beta download for the DWA-142. Unfortunately, this is a package (v1.2) that includes all the D-Link custom monitor apps and other crapola, and the driver files (inf, sys, cat) are buried in a cab file, so it's not easy to install just the driver. You have to install the package. However, once installed, I was configured and running in no time, and started testing.
 
Solid as a rock.
Fast.
 
No disconnects or crashes (yet).

---

### Post by wklang on 2008-05-18
First, let me say I'm a newbie as far as 'administrative' tasks around Linux, and - according to my wife, I frequently can't see something that's right in front of my face.

I appreciate the instructions in this thread about getting my Linksys wireless adapter to work and I did add the line "sudo ndiswrapper -m" hoping to solve the problem of the adapter not starting up on each boot.

Somewhere, I've missed something and I have to run a short script on each boot to get the wireless networking going.

The script I'm using (in the /opt/ndis/Drivers directory is:

sudo ndiswrapper -i netmw245.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper
sudo dmesg | grep ndis
sudo ndiswrapper -m

Can someone please help me see what instruction(s) I have left out to keep it from starting up on each reboot?

Thanks,

Wes

---

### Post by DataKnutten on 2008-06-02
> **itsfullofstars said:**
> The following was taken directly from a post on the Linksys forum.  Minor edits.

**PROBLEM**

Disconnects or system hangs/crashes.

After dozens of hours working on this, researching on the net, etc., I have the answer to the problems.
 
The WUSB300N uses a chipset called TOPDOG made by Marvell. This same chipset is in every 802.11n draft adapter implementation out there from what I can tell -- Linksys, Belkin, D-Link, etc. There might be a competing chipset, but I stopped investigating when I nailed down the source of the problems.
 
All these implementations use a driver made by Marvell, the manufacturer of the TOPDOG chipset. There are different versions out there, but apparently none that are OEM-specific.
 
**CAUSE**
 
Two manufacturers NICs experienced the same issues -- Linksys, and D-Link. I didn't try any others. Both cause disconnects (manufacturer's wifi manager managing the connection) or system hangs/crashes (XP managing the connection through WZC). **The failure seems to only occur when a large number of TCP connections are being managed by the system, as well as a high rate of connection attempts to different hosts.**
 
This sort of environment is exactly what happens in P2P applications. Most common are bittorrent clients, and on-line gaming.
 
I could blow out the WUSB300N within a minute or two by firing up Azureus (bitorrent), with a lot of seeding torrents (60).
 
Problem #1 is the Linksys WUSB300N implementation. It's flaky hardware. I had two, and both behaved exactly the same on my WinXP machine with the latest driver available from Linksys (v1.0.1.7, IIRC).
 
The DWA-142 Wireless N USB adapter from D-Link performed much better regardless of the driver. The Marvell driver installed from the CD was version 1.0.1.2; Both NICs worked with this driver, and average throughput was about 25% faster than with v1.0.1.7 shipped with the WUSB300N. As noted, WUSB300N died within a minute or two of cranking up the connections and connrate. D-Link ran for as long as 2 hours without a problem, then same failure mode.
 
This was true with all three Marvell driver versions I had: 1.0.1.7 from Linksys, 1.0.1.2 from D-Link, and one other, 1.0.5.5 that came from a Microsoft optional update. Again, both mfg adapters worked with all these drivers, all failed in the same way, D-Link was massively more stable (and a little faster) than Linksys.
 
**THE SOLUTION**
 
Marvell apparently has fixed these problems in their latest driver. It is version 1.0.6.4. The only place I could find it was on the D-Link website, in the support section, available as a beta download for the DWA-142. Unfortunately, this is a package (v1.2) that includes all the D-Link custom monitor apps and other crapola, and the driver files (inf, sys, cat) are buried in a cab file, so it's not easy to install just the driver. You have to install the package. However, once installed, I was configured and running in no time, and started testing.
 
Solid as a rock.
Fast.
 
No disconnects or crashes (yet).

Thanks itsfullofstars!
Good explaination any congratulations!. You should also add this success story to the ndiswrapper page "List of cards supported" and the Ubuntu wiki:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I'm myself searching for a 802.11n-based USB adapter that works with Linux. I've until today only found this one that was reported to work.
However, I do know one competing chipset from Atheros, the AR9100/AR9170 (Netgear WNDA3100), that I have been looking at (see also [http://ubuntuforums.org/showthread.php?t=690699](http://ubuntuforums.org/showthread.php?t=690699)) but I don't see any success stories for that.
I might work with ndiswrapper too!? 
Can anyone try this please?

---

### Post by haroman145 on 2008-06-10
okie dokie....i have ubuntu 8.04....i have installed the wusb300n driver but as soon as I type modprobe ndiswrapper it says

josh@Josh-Ubuntu:/opt/ndis/Drivers$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.24-17-generic/misc/ndiswrapper.ko': No such file or directory
 i couldt find anyboys else having this same problem pleassee gimme a hand sum1...

---

### Post by nyrb4life on 2008-07-01
what if you have amd 64?? Please I need help.

---

