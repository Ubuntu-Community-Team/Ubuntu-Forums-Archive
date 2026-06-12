---
title: "Wireless Help on DV2000 (Broadcom 4311)"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by Wheelman on 2006-10-21
I need some help getting wireless to work on my DV2000.  I am not sure where to start really.  I have a fresh install of Ubuntu 6.06 and installed network manager but it won't show any wireless networks.  I commented everything out of the config file already and still nothing.  My IWCONFIG results look like this:
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"2wire281"  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```
and IFCONFIG
```
eth1      Link encap:Ethernet  HWaddr 00:16:D3:10:2B:53
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe10:2b53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4667924 (4.4 MiB)  TX bytes:736529 (719.2 KiB)
          Interrupt:225 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

```
I am sort of a linux newbie so can someone guide me in the right direction as far as what to look for next as far is figuring this out?

---

### Post by TrueJk7 on 2006-10-22
[http://ubuntuforums.org/showthread.php?t=281713](http://ubuntuforums.org/showthread.php?t=281713)

I've got the same exact problem. I checked though the forum to find, but no one else had the same problem. Ill let you know when I got mine fixed.

---

### Post by greybit on 2007-01-10
I've got an HP dv2171cl. I couldn't connect to a wireless network until I installed Wifi-radar. You might give it a try.
 
Edit: Well, I forgot the trouble I went through initially to get the wireless working.  I was reminded when I destroyed my installation and chose to reinstall a couple of days ago.  It is true that Wifi-radar allowed me to connect in the end but before that I did the following:
 
First I installed ndiswrapper which allows linux to use a Windows wifi driver:
 
```
sudo -i
apt-get update
apt-get install ndiswrapper-utils*
```
(or you could use the latest version from the ndiswrapper website)

Then I downloaded from the HP website the Windows XP driver for the wireless card in my laptop.  Since it is of .exe format, I installed cabextract and decompressed the file as follows:

```
apt-get install cabextract
cabextract filename.exe
```

Now there should be a .inf file.  Use ndiswrapper to install it:

```
ndiswrapper -i something.inf
```

Finally, so the old driver isn't loaded upon startup but ndiswrapper and the new driver are loaded, do the following:

```
nano /etc/modprobe.d/blacklist
```
add the line "blacklist bcm43xx" without the quotes, save & exit.

```
nano /etc/modules
```
add the line "ndiswrapper" without the quotes, save & exit.

Hope this helps.

---

### Post by Tiro00 on 2007-04-10
Hello linuxers

I have a HP 5040EA with a wireless 1390 Broadcom dell card.
I just recently installed ubuntu 6.10 and am running on the 2.6.17-11-generic kernel.
I've spent many days now on various forums trying to get the wireless card up, but have been, to say the least, totally uncessefull.
I tried ndiswrapper in the terminal, than using ndisngtk.

What's weird is that the system recognizes my card (I immediatly after installation is complete, have acces to the wireles configuration option ) but doesn't allow me to connect .
Here's my iwconfig : 
[PHP]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[/PHP]

And my lspci
[PHP]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[/PHP]




I'm thinking maybe I didn't correctly configure my wireless settings in networking.
Then again, I thought that by using wireless radar or wireless asssistant, I could do that.

There another problem : HP doesn't offer a windows xp driver on it's website, only vista.
My computer came with a pre-installed version of vista.
I was alble to get the wireless working under xp by using a driver from a dell computer.
If I use this driver under linux, ndiswrapper exepts it ( hardware present ) 
but my wireless configuration interface under networking dissapears !

I'm clueless.

I turn to the community in an outcry for help ^^.
Tiro00.

---

### Post by dbott67 on 2007-04-10
Hi Tiro00,

I've got the 4311 in my Dell laptop & this is what I did for Edgy (summarized from my post [here]("http://ubuntuforums.org/showthread.php?t=274915")).  Just be sure to follow the instructions in step #3 very carefully.

**_Broadcom 4311 Wireless:_**

I was able to get the wireless card working, however, I needed to blacklist the existing bcm43xx module and use ndiswrapper:

1. Install **build-essential** from Synaptic (for compiling ndiswrapper)

2. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

3. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

4.  Blacklist the bcm43xx module:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```5. In order to get 'iwlist scanning' to display results, I needed to edit my /etc/network/interfaces file to contain the appropriate settings for my AP:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
[COLOR=Red]wireless-essid MYSSID
wireless-key s:mysecretwepkey
[/COLOR]
auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```I'm not sure why my wireless card is now using eth1 (it used to be wlan0 in Dapper), but hey, it's working! :)

```
dbott@edgy:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:40:05:B2:AF:45
                    ESSID:"bott"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```[COLOR=Red]Note: any kernel updates will require that ndiswrapper be recompiled[/COLOR]

**_February 24, 2007 - Wireless Update_**

Regarding the eth1 issue, I believe it was related to an entry in my iftab file that contained the following line:
```
eth1 mac 00:16:ce:31:88:XX arp 1 
```I changed the file to read:
```
dbott@edgy:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:c5:0c:ad:XX arp 1
[COLOR=Red]wlan0[/COLOR] mac 00:16:ce:31:88:XX arp 1

```And then I installed **network-manager-gnome** and it seems to have cured all my problems.  The card is now recognized as **wlan0** and the network manager handles all the settings (WEP, scanning, etc.).

As for your laptop, you can get the drivers from this site:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

It looks as though you want to try B 40:
> 40. Card:Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card rev 01 [LIST]
[*]PCIID: 03:00.0 0280 14e:4311 rev 01
[*]PC: HP pavilion dv6000 series 'DV6105US'
[*]OS: Slackware 11.0
[*]Driver Used:  Win32 Driver from HP
[*][HP Driver]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=sg&dlc=en&product=3245619&os=228&lang=en")[/LIST]-Dave

---

### Post by Tiro00 on 2007-04-10
well good thing is it seems to have recognized my card but I wonder if I blacklisted correctly : 
ndiswrapper -l gives me 

[PHP]tiro@tiro:~/Desktop/driver$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
[/PHP]


+ an error occured blacklisting :

[PHP]tiro@tiro:~/Desktop/driver$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
tiro@tiro:~/Desktop/driver$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
[/PHP]

---

### Post by gregmcnichol on 2007-04-10
I'm having the same problem with my DV2000t, I don't understand why i would need to use ndiswrapper if others seem to be able to use it OOTB

---

### Post by dbott67 on 2007-04-10
I don't know either... it could be a combination of things related to the various hardware and software differences that allows it to work flawlessly on some machines and fail miserably on others (like mine).  All I know is this: on my machine, I have never had success with the bcmxx driver and have been using ndiswrapper successfully since I bought my laptop about a year ago (March '06).

I tried fiddling with fwcutter & what-not but it was more hassle than just going to ndiswrapper.

-Dave

---

### Post by dbott67 on 2007-04-11
I found this HOWTO from DarknOOb that may help:

[http://ubuntuforums.org/showthread.php?p=2431305#post2431305](http://ubuntuforums.org/showthread.php?p=2431305#post2431305)

-Dave

---

### Post by gregmcnichol on 2007-04-11
> **dbott67 said:**
> I found this HOWTO from DarknOOb that may help:

[http://ubuntuforums.org/showthread.php?p=2431305#post2431305](http://ubuntuforums.org/showthread.php?p=2431305#post2431305)

-Dave

This worked like a charm thank you!! Only problem is that my connection is not very fast at all It says i have a 100% connection and even right in front of the router it is pretty slow any ideas? Either way your a life saver!

---

### Post by dbott67 on 2007-04-11
It could be related to IPv6.  You could always try disabling it:

Type the following commands to verify & blacklist:

```
dbott@thedrake:~$ lsmod | grep ipv6
ipv6                  265856  10

``````
sudo rmmod ipv6
```Try your connection speed again.  If performance improves:
```
sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6
```Restart

You can also disable it Firefox - [http://ubuntuforums.org/showpost.php?p=1364798&postcount=66](http://ubuntuforums.org/showpost.php?p=1364798&postcount=66)

1. Type **about:config** in the address bar
2. Enter **network.dns.disableIPv6 **
3. Change the value to **true**.  Double click the line to enable/disable.  Enabled=true / Disabled=false.  This will disable IPv6 dns lookups from within Firefox only--not your entire Ubuntu system.

-Dave

---

### Post by gregmcnichol on 2007-04-11
root@greg-laptop:~# rmmod ipv6
ERROR: Module ipv6 is in use

When i disable it in firefox there is no speed increase. hmmm

---

### Post by gregmcnichol on 2007-04-11
Useing: members.cavtel.net/speed

under windows: 885.63 kb/s
under ubuntu: 16.8 kb/s

ouch

---

### Post by dbott67 on 2007-04-11
Do you have a wired connection you can verify it against?  That is, can you plug in the computer to a wired connection and run the same tests?

Post them here, as we need to find out if it's a "wireless" issue or an "ubuntu" issue.

Go to [www.speedtest.net]("http://www.speedtest.net") and post your results here (wired/ubuntu, wired/windows, wireless/ubuntu, wireless/windows)

This is my wired Ubuntu connection (on P4-1.8 Desktop):

[[IMG]http://www.speedtest.net/result/111981452.png[/IMG]]("http://www.speedtest.net")

Here's my wireless Windows XP Pro connection (Core Duo 1.83 laptop):

[[IMG]http://www.speedtest.net/result/111982824.png[/IMG]]("http://www.speedtest.net")

Same wireless laptop running Ubuntu 6.10:

[[IMG]http://www.speedtest.net/result/112018585.png[/IMG]](http://www.speedtest.net)


-Dave

---

### Post by gregmcnichol on 2007-04-11
Strange i plugged into the router and its just as slow as the wireless! It wasnt like that before doing the firmware installation you pointed out. I'm trying to get you the speedtest.net results but i need to download flash and its taking forever on this slow connection. Before rebooting to ubuntu i ran the test on vista using the wireless and i got this

[[IMG]http://www.speedtest.net/result/112033489.png[/IMG]](http://www.speedtest.net)

---

### Post by gregmcnichol on 2007-04-11
Here is ubuntu wireless:

[[IMG]http://www.speedtest.net/result/112041590.png[/IMG]](http://www.speedtest.net)

Here is the wired ubuntu:

[[IMG]http://www.speedtest.net/result/112042141.png[/IMG]](http://www.speedtest.net)

I really appreciate the help so far!

---

### Post by DarkN00b on 2007-04-12
According to post #55 at the original fwcutter thread [here]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear"), these drivers are limited to 11Mbps. You should be getting better speed than that though... 

[img]http://img463.imageshack.us/img463/6357/huh4lc.gif[/img]

What to you get when you type ```
iwconfig |grep Bit
```

into the terminal?

---

### Post by Tiro00 on 2007-04-13
Hi again,

well here's where I'm at.
I installed Draknoob's firmware after a fresh installation of ubuntu.
When I go to networking and enable my wifi card, its light now turns on.That a very good sign.
Could you please help me configure my card; do I enter the same ip coordinates as for ethernet? Is there a way for my card to find essid or do I have to type this in my self.

I tried using my essid + wep key  + automatic DHCP, than manually entered ip adress -- no luck.
Does wifi radar or wlassistant carry this function?

Help much apreciated up to now :D 
Tiro00


btw; iwconfig : 

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Ron"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

---

### Post by dbott67 on 2007-04-13
You could manually edit your **/etc/network/interfaces** file to look something like this:
```
dbott@dapper:~$ cat/etc/network/interfaces
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
[COLOR=Blue]wireless-essid bott
wireless-key s:[COLOR=Red]mysecretwepkey[/COLOR][/COLOR]
```The [COLOR=Red]s:[/COLOR] prefix is if your key is ASCII; otherwise use the HEX key without the s: prefix.  Having said that, [NetworkManager]("http://www.gnome.org/projects/NetworkManager/") is an application that I have had great success with:
```
sudo apt-get install network-manager-gnome
```My first post in [this thread]("http://ubuntuforums.org/showthread.php?t=274915") outlines what I needed to do (read the part under _**Broadcom 4311**_, step #5 and subsequent follow-up on Feb. 24, 2007).

-Dave

---

### Post by raja.aydina on 2007-10-19
I followed the directions for installing BroadCom drivers, however on: iwconfig, i get

lo no wireless extensions

eth0 no wireless extensions

my notebook is a hp dv 2415, w/ Broadcom Dell 1390

---

### Post by Enriquecaribe on 2008-05-20
hmph, this thread seems to be old but I kinda still need wireless on HP dv2000. I love linux to death but i need wireless

---

