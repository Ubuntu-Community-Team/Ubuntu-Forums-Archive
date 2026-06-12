---
title: "bcm4318 ndiswrapper wpa_supplicant NetworkManager no worky"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by garrye on 2006-08-01
Laptop Acer Aspire 3003WLCI sporting Broadcom 4318 wireless silicon

From: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

Did: 
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

followed by:
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

BTW I'm using bcmwl5a.inf and bcmwl5.sys stolen from the XP that is co-installed on this lappy wherewith the wireless works of course.

Wireless connection with NO security to an SMC router works.  I can get the web-based admin page, do web surfing, streaming audio, etc etc.

Now on to wpa and here is where I run into to rough water.

Using wpa_gui I cannot get things to work
It says "Could not get status from wpa_supplicant" on the status line and the Adapter and Network drop-down lists are blank
Output from the terminal is:
dad@dad-buntu:~$ wpa_gui
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Failed to open control connection to wpa_supplicant.
PING failed - trying to reconnect
PING failed - trying to reconnect
PING failed - trying to reconnect

It continues endlessly to ping, trying to reconnect until I end the process using system monitor or simply closing the window.

So I remove all of wpa_supplicant and wpa_gui and install network-manager-gnome 0.6.2-0ubuntu7  which of course brings wpa_supplicant along with it again.

On reboot I see nearly 100% cpu load.  The tray applet tooltip says "No Network Connection".  Have to stop/end/kill the NetworkManager process to bring the cpu load down so as to not cook my Sempron.

Another thing I find odd is that device manager shows only "BCM4318 [AirForce One 54g] 802.11g" for the wireless device and no "WLAN Interface" under it UNTIL I code "sudo modprobe ndiswrapper".  After that the "WLAN Interface" entry appears.  In the right hand pane for the BCM4318 entry a line also appears that reads "info.linux.driver     strlist ndiswrapper" which only appears AFTER I code "sudo modprobe ndiswrapper".

So then!

How to make sure ndiswrapper loads at boot time?

What's the meaning/cause of the wpa_supplicant error?

What's causing the high cpu load thing with NetworkManager?

Comments anybody?

---

### Post by amp_man on 2006-08-02
edit: sorry for the previous post, I failed to read the first line of your post. Try switching over to the native driver, I had issues in the past with my broadcom card, ndiswrapper, and encryption of any kind. Instructions are in the same wiki page as you pulled the blacklist command from. Also, make sure you read the note toward the bottom of that page about modifying your interfaces file for Network Manager, that's probably where your high CPU usage is coming from

another edit: to load ndiswrapper at boot, add it to /etc/modules

last edit: [wpa_supplicant howto](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa_supplicant%29). I'm so bored that I'm trying this myself also, just to see if it works, I've relied on WEP until now.

last edit...really this time: I now have wpa_supplicant working perfectly using that wiki article I linked to, and the native bcm43xx drivers. your turn!

---

### Post by Banewood on 2006-08-02
I have a fairly similar configuration and had a real time getting it all to work.  I gave up on the blacklisting and ndiswrapper for a trial version of Linuxant:
[http://www.linuxant.com/driverloader/?PHPSESSID=e9d14b98e85cb4cd7aeac071a2773f67](http://www.linuxant.com/driverloader/?PHPSESSID=e9d14b98e85cb4cd7aeac071a2773f67)

Oh, and I also used the plain old bcm4318 (without the "a")

---

### Post by garrye on 2006-08-07
> **amp_man said:**
>  [shnip] I now have wpa_supplicant working perfectly using that wiki article I linked to, and the native bcm43xx drivers. your turn!

HOLY SCHMOKES!! I leave for a coupla days and my post is on page seven!!
Ouch busy place - (Mental note to myself to review policy on off topic stuff and post hijacks so as to NOT waste resources)

Kay amp_man really appreciate you jumping in on this, and sorry for not replying sooner.  Been busy around here for the past few days.  Anyhoo read on for a blow-by-blow of what went down.

sudo nano /etc/modprobe.d/blacklist and comment out the bcm43xx entry

sudo ndiswrapper -e bcmwl5a
ndiswrapper -l to ensure no drivers are installed

synaptic package manager - remove ndiswrapper-utils bye bye!

Do a search for filenames containing "ndiswrap" to see what remains as I manually created some files
There are some leftovers what do you make of these?
/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
***Could/should a guy remove these?***
/usr/share/app-install/desktop/ndisgtk.desktop
/usr/share/app-install/icons/_usr_share_ndisgtk_ndisgtk.png
***and these two above look like leftovers from when I had the graphical front end installed. Could yank them too not?  No biggie really though if they're left alone what?***

yanked ndiswrapper and ndiswrapper.modprobe which are files that I created manually out of desperation to see if they would fix things

sudo nano /etc/modules to remove entry ndiswrapper -m

sudo rmmod ndiswrapper
sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
sudo modprobe bcm43xx
~$ (Just discovered that the little squigly (~) means home directory!!

sudo gedit /proc/modules - GIVES A BLANK FILE!!!!
sudo nano /proc/modules - phew!!! - see selected portion below

bcm43xx 124044 0 - Live 0xceb26000
ieee80211softmac 29696 1 bcm43xx, Live 0xceaf7000
ieee80211 37064 2 bcm43xx,ieee80211softmac, Live 0xceaec000
ieee80211_crypt 6272 1 ieee80211, Live 0xceac3000

Looks good to me...
(I didn't know you could highlight and copy to clipboard from nano! Me like Nano - it starts fast)

BTW uname -a yields Linux dad-buntu 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux  (Just did the latest kernel update today via synaptic update)

Hmmmm (note to myself 11Mb rate and some pre-configs might be needed to make this work)


Another BTW - I do satellite internet, build wireles/wired home (and some business) networks, clean pests out of PC's and generally fix em for a living.  Have been horsing around with Ubuntu and other distros for several months.  I want to get Ubuntu working shlick as a whistle on this lappy so that I can start promoting this to people around town and offering my support when they get in trouble.  I have EVERYTHING working on this lap top EXCEPT the wireless.  I even got the touchpad working on the synaptics driver with tap-to-click turned off just the way I like it.  Even standby works although it's a little buggy.  The only thing that has me stumped is the wireless and even that I feel like I'm REALLY close.  I get the feeling I'm just missing a setting or two someplace along the line.  Read on...

sudo nano /etc/default/wpasupplicant yields a single line 'ENABLED=0'

sudo nano /etc/network/interfaces gives the following

auto lo
iface lo inet loopback



iface eth0 inet dhcp


iface wlan0 inet dhcp
wireless-essid default
     pre-up iwconfig wlan0 rate 11M
auto wlan0

auto eth0

that takes care of 1.3 in [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
reboot time!

nnnnnnnope!  Still no worky!

Now I'm mad @ NetworkManager - Synaptic completely remove network-manager-gnome and network-manager

flounder about for a while with wpa_supplicant and wpa_gui doing some reading on the config files and how that all works.  Still no progress.

Time to step back and take a look at this.

Back into Winbloze XP. Yup I have a Dlink DI-624 set up for this, broadcasted SSID=default WEP disabled.  It's open and easy to connect to.

I have used fwcutter to hack useful parts out of the winbloze files to feed to bcm43xx.
Have a whole bunch of bcm43xx-?????????.fw files copied to /lib/firmware/2.6.15-26-386
These are the very same files windows uses - when I did the fwcutter thing there were some messages about parts that could not be extracted.  Maybe I need to grab a different version of the files from elsewhere as detailed in other posts what?

Now reboot (bad winbloze habit)

Kay sudo ifdown wlan0 gives
Listening on LPF/wlan0/00:14:a4:35:46:bd
Sending on   LPF/wlan0/00:14:a4:35:46:bd
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.2.1 port 67

K good....
sudo ifup wlan0 gives
Listening on LPF/wlan0/00:14:a4:35:46:bd
Sending on   LPF/wlan0/00:14:a4:35:46:bd
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Rrrrrrrrrrrrrrrrrrrrrrr...

iwconfig gives
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b/g  ESSID:"default"  Nickname:"default"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:46:C6:5E:BE
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

odd that "Link Quality", "Signal Level", and "Noise Level" are all at zero

There's a light on the front of the laptop that (in windows) comes on when wireless is enabled.
I get nothing from this light when I use ifup or ifdown.
However if I use wifi-radar then the light comes on and there's a bunch of blinking and whatnot but still no connection to this easy-as-pie DI-624 with no security on it.
What am I missing?

What diagnostics can I code that would be revealing in this case???

OH and I notice that wifi-radar claims to be able to work with wpa_supplicant.  Had wifi radar working with ndiswrapper and rather liked the way it worked.  But then again it seems that Ubuntu is moving in the direction of having network manager become the defacto standard default app for managing wireless networks. Methinks could go with wifi-radar for now as it seems a little more mature, get the bugs worked outta this thing and then slide network manager back into the picture once I have everything working.

For that matter (off-topic? ouch ouch!) I would like to stay as much as possible with what Ubuntu plans to support/develop in the way of network management tools whatever those are.  Any comments on this?

---

### Post by garrye on 2006-08-14
Was originally gonna post a detailed accounting of my struggles.  At 11K I think it wise to NOT do that.

Tried bcm43xx with firmware stolen from the co-installed win xp and could NOT get it to work. Went back to ndiswrapper.  Did some more reading and figured it out.  Got wpa_supplicant working and with even more reading figured out that my problems was that I was attempting to initiate a WPA2/CCMP-AES session with my WRT54G when I should have been using WPA/CCMP-AES!!!

Now that's behind me.

Back to network manager.  STILL cannot get it to work.  STILL results in nearly 100$ CPU usage.  My Sempron is starting to hate me!

What is the position of the Ubuntu developers on Network Manager.  Is it here for the long term or is there a switch in the wind to another package.

Methinks time to pitch Network manager and just use wpa_supplicant.  Now that I have it figured out it's really not that complicated.

---

### Post by garrye on 2006-09-26
> **garrye said:**
> 

[SCHNIPP]

Back to network manager.  STILL cannot get it to work.  STILL results in nearly 100$ CPU usage.  My Sempron is starting to hate me!




HERE I AM TALKING TO MYSELF AGAIN.

A couple of kernel updates and many hours of happy Ubuntuing later I grow tired of poking around with...

"sudo leafpad /etc/wpa_supplicant.conf"

I put NetworkManager back in and restart and I STILL get nearly 100% CPU load from NetworkManager.

I have ditched the broadcom silicon and put a card sporting AR5212 silicone in its place.  This I have been wifi-ing merrily about the town with since my last post and I've found it to generally work like a charm.

Examining syslog I find the following:

A whole bunch of ath0 stuff including...
ath0: Atheros 5212: mem-0x32000000, irq=217

followed by...
NetworkManager: <information>^Istarting...
NetworkManager: <WARNING>^I main (): nm_data_new: Ssetting up dbus filter

what pray tell, does this mean.  Can this explain why NetworkManager is not working?

I get the icon in the notification area with a tooltip that says "No Network Connection".  Right clicking I get "Enable Networking" is checked and "Connection Information" is greyed out.  There is also "About" and "Remove"

---

### Post by puppy on 2006-09-26
Good luck with it GarryE - I have been completely unable to get my broadcom card to use WPA with either WifiRadar or the network manager applet (and I can't tell you how many hours I've wasted on this :rolleyes: )

I'm making do with the built-in networking and WEP for the moment until a more mature solution comes along... not very secure but it's all I have :neutral:  wired is not an option for me unfortunately...

---

### Post by joshlfisher on 2006-09-27
> **amp_man said:**
> edit: sorry for the previous post, I failed to read the first line of your post. Try switching over to the native driver, I had issues in the past with my broadcom card, ndiswrapper, and encryption of any kind. Instructions are in the same wiki page as you pulled the blacklist command from. Also, make sure you read the note toward the bottom of that page about modifying your interfaces file for Network Manager, that's probably where your high CPU usage is coming from

another edit: to load ndiswrapper at boot, add it to /etc/modules

last edit: [wpa_supplicant howto](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa_supplicant%29). I'm so bored that I'm trying this myself also, just to see if it works, I've relied on WEP until now.

last edit...really this time: I now have wpa_supplicant working perfectly using that wiki article I linked to, and the native bcm43xx drivers. your turn!


I am running Kubuntu dapper, and I don't have a /etc/modules.
Also, I have an /etc/ndiswrapper, but it is empty.

I REALLY want to get WPA working.
-Josh

---

### Post by garrye on 2006-09-29
> **joshlfisher said:**
> I am running Kubuntu dapper, and I don't have a /etc/modules.
Also, I have an /etc/ndiswrapper, but it is empty.

I REALLY want to get WPA working.
-Josh

Odd...I don't have /etc/modules either :confused: 

yes wpa is pretty well essential if you're using network shares and the like.  It's been so long since I've used ndiswrapper that I don't remember the specifics of getting it going.  I do remember that it is a bit on the subborn side.  It did take a kick start.  Seems to me I DID have to enter "ndiswrapper" in some file someplace and also that using the GUI for ndiswrapper did NOT work.  I had to use the command line. Also make sure you have blacklisted any other driver that the kernel is trying to load in response to having detected your wifi hardware.  This is particularly true of the broadcom silicon so common these days.  You will have to blacklist bcm43xx by placing an entry in /etc/modprobe.d/blacklist.

Lots and lots of reading and figuring out how to find stuff in the forums and the wiki's  those were my best resources.  I have since the broadcom days also discovered the Unbuntu Document Storage Facility which is a kind of collection of the best of the best Howto's.  Excellent resource.

And if you think wifi on Ubuntu is tough, try getting XGL to go some time!!

Good luck and enjoy reading and tinkering!!

---

### Post by compwiz18 on 2006-10-13
If you still need help:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

I know that this works with WPA and network manager because I used WPA with it myself.

Good luck.

---

