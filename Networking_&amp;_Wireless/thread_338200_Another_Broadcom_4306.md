---
title: "Another Broadcom 4306"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by bogertron on 2007-01-14
I have attempted the ndiswrapper and the firmware cutter. I am beginning to get to my wits end...

I have a Dell D600 Latitude with a Braodcom 4306 Wireless Card. 

Now, I know that many, and i repeat MANY people have suffered my problem, but I am hoping that I have just done something incredibly dumb. I think that I have installed everything, but my Network Manager is not picking up any signal. 

If anyone can find out what is going on, I would be much appreciated, and you would be awarded many internets....

---

### Post by teaker1s on 2007-01-15
see if I can help you

terminal 
[COLOR="Red"]modprobe ndiswrapper[/COLOR]

note it is a small L not i

[COLOR="Red"]ndiswrapper -l[/COLOR]

[COLOR="Red"]iwconfig[/COLOR]

post output for me to see

---

### Post by wscheer on 2007-01-15
Teaker,
I have a hp pavilion ze5570us laptop (4306 broadcom wireless card) with a similar problem.
When I try to install the ndiswrapper, it makes gnome hang upon my next bootup.
Basically, I get the login screen followed by the desktop but there is an error box in the upper left hand corner. It stay white for a few min then it fills in the info with something about a gnome desktop settings error. The standard brown theme that gnome comes with is switched to blue although my desktop bg is still the same.

I have uninstalled and reinstalled ndiswrapper a couple of times using some different methods i saw on the forum.

I'll look and see if I left it installed or not, its been a few days.
I'll paste my output info here if i have any.

p.s. i might be trying a different wireless card today too. i work for an IT company and they happen to have a few laying around. I'll keep you guys updated.

---

### Post by wscheer on 2007-01-15
Well...
When type:
modprobe ndiswrapper, i get
FATAL: Could not open '/lib/modules.... : no such file or directory

ndiswrapper -l
bash: ndiswrapper: command not found

iwconifg
lo     no wireless extensions
eth0  no wireless extensions

eth1 IEEE 802.11b/g ESSID:"linksys" Nickname:"Broadcom 4306"
       Mode: Managed Frequency=2.437 GHz Access Point: 00:13:10:11:0C:03
       Bit Rate=11 Mb/s      Tx-Power= dBm
       RTS thr:off    Fragment thr:off
       Link Quality=48/100   Signal level=-74 dBm     Noise level=-70 dBm
       Rx invalid nwid:0    Rx invalid crypt:2627      Rx invalid frag:0
      Tx excessive retries:0     Invalid misc:0      Missed beacon:0

sit0   no wireless extensions.

- i did install the GUI ndiswrapper app that lets you select a .inf file. (bcmwl5.inf) but after install it, it still does not show up as an installed driver.

it almost looks like its picking up the unencryped linksys router from the people downstairs  :)

---

### Post by teaker1s on 2007-01-15
my mistake, also looks like you have removed it

[COLOR="Red"]sudo modprobe ndiswrapper[/COLOR]

also have you blacklisted the kernel driver? as i see 11mbit\s which from what you have show me it looks like your gnome error is because ndiswrapper and kernel driver were both trying to run

okay well you would be best looking at this page I have been involved in, please read through it before trying anything as it's quite possible you will spot your Problem
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")


also ndisgtk gui app you talk about doesn't work from my experience it will tell you there is a driver installed but ndiswrapper can't see it. you want to install it by using the command

[COLOR="Red"]sudo ndiswrapper -i nameofdriver[/COLOR]

---

### Post by wscheer on 2007-01-15
teaker1s,
i got the wireless workings !!!!!!!!!!!!!!!!!!
i can't thank you enough for all of your help

bogertron,
I was having the same issues as you, so i'll post all of the outputs I got because it took a little teaking here and there.

---

### Post by teaker1s on 2007-01-15
result  , glad your sorted wscheer !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by wscheer on 2007-01-15
oh i forgot to add this is the guide i followed
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-ea76065f30b99d3b8472289cd049e2b141856b55](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-ea76065f30b99d3b8472289cd049e2b141856b55)

```
user@ubuntu:~$ lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

# Step 1 - Remove any existing copies of ndiswrapper that you may have
-!- followed as is -!-

# Step 2 - Disable any Competing Drivers
```
user@ubuntu:~$ cat /etc/iftab
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0d:9d:89:09:16 arp 1
#eth1 mac 00:90:4b:44:49:f5 arp 1

-!- I had to comment out eth1 -!-

# Step 3 - Prepare the Linux build environment
-!- followed as is -!-

# Step 4 - Download the latest version of the ndiswrapper driver
-!- i downloaded the latest, i think it was 1.34 -!-

# Step 5 - Extract and install the ndiswrapper using make
-!- followed as is, but substituted 1.34 where 1.28 was -!-
-!- also i downloaded my driver right off the HP website  -!-

```
user@ubuntu:~/bcm4311$ sudo gedit /etc/ndiswrapper/bcmwl5/.conf
```
-!- i could not edit this file unless i had my network cable unplugged -!-

# Step 6 - Install the device and configure the network settings
```
user@ubuntu:~/bcm4311$ cat /etc/modprobe.d/ndiswrapper

```
alias wlan0 ndiswrapper
-!- think i had to edit that one -!-

# Step 7 - Testing the device
```
user@ubuntu:~bcm4311$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:13:10:44:11:8C   
          Bit Rate:48 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-!- mine still says "eth1" but it works -!-

# Step 8 - Controlling the device 
don't think i did any of this 

did this though
```
sudo /etc/init.d/dbus restart
```

---

### Post by bogertron on 2007-01-24
Sorry to take so long to get back. I have reinstalled and been driven up a wall over this and other things

Anywho-

ndiswrapper -l:

Installed drivers:
bcmwl5          driver installed, hardware present 

iwconfig:

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So it looks like i cannot pick up the wireless signal.

Any ideas?

---

### Post by teaker1s on 2007-01-25
device is running-but not configured-easiest way to sort it is 

[COLOR="Red"]sudo apt-get install network-manager-gnome [/COLOR]

 now on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

---

### Post by bogertron on 2007-01-27
Ok, so now it may work, but i am unable to connect to my network, i have an encryption on and even though i enter the correct information, i am still unable to connect....any ideas?

---

### Post by teaker1s on 2007-01-28
I only ever used [COLOR="Red"]network-manager-gnome[/COLOR] only issue I have is with a friends orange livebox router that has wep key and network manager thinks it's wpa.
you could uninstall network-manager-gnome and try either comandline setup or wifi radar

**another thought -do you use WPA as that could be the problem**
look at link below it has info

---

### Post by MystaMax on 2007-01-29
> **teaker1s said:**
> I only ever used [COLOR=Red]network-manager-gnome[/COLOR] only issue I have is with a friends orange livebox router that has wep key and network manager thinks it's wpa.
you could uninstall network-manager-gnome and try either comandline setup or wifi radar

**another thought -do you use WPA as that could be the problem**
look at link below it has info


I was wondering what the better solution was between wifi-radar and network-manager? I found a [blog post]("http://www.flexion.org/site/index.php?gadget=StaticPage&action=Page&id=11") which states to use wifi-radar with the D600. I also found this [forum post]("http://www.ubuntuforums.org/showthread.php?t=344420&highlight=BCM4306+802.11b%2Fg+Wireless+LAN") which states to use network-manager.

I had the intentions of using network-manager and following the forum post, but wanted to get some feedback from others. thanks

---

### Post by teaker1s on 2007-01-29
I never really got on with wifi radar, network-manager-gnome is much more straight forward

---

### Post by bigken on 2007-01-29
oops wrong thread lol

---

### Post by MystaMax on 2007-01-30
> **teaker1s said:**
> I never really got on with wifi radar, network-manager-gnome is much more straight forward

thanks for the reply. I decided on network manager, it seems by far the popular choice around the forums.

My only issue now is that icon only reports a wired connection. The icon are two computers, but from other screenshots, it seems it should be the ascending bars (denoting signal strength). I can scan for networks from the CLI, and it finds my network as well as surrounding neighbors networks. but i can't get network-manager to manage the wifi connect? any ideas?

---

### Post by teaker1s on 2007-01-30
possibly you need to
on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key :guitar:

---

### Post by fevieira on 2007-02-08
I had the same problem as you but with a Belkin Card...this is how I got around it...  (sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh ) and then manually put it in the kernell...it should work for you since its a broadcom chipset...
here are the actual steps taken.
#
#
terminal > sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh > cd /lib/firmware/ { the .fw's should be all listed here chose one or just move them all }
now just do sudo mv /lib/firmware/ bcm43xx_*.* /lib/firmware/ {put your kernel version here} 
and that should be it.
just restart and you should see the lights come on.

hope it works.

---

