---
title: "I have absolutely no idea how to get my wireless working"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by filthmontane on 2010-10-24
im sorry to be another person posting something about wireless help but i dont want to ruin my brand new laptop without knowing what im doing. 

This seems important somehow

sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

---

### Post by spiky001 on 2010-10-24
Have you updated the system if not then connect an eth0 wire run update and check for drivers administration/system/hardware drivers

---

### Post by swoody on 2010-10-24
Can you also post the output of:

```
lspci | grep -i network
```

This will help us determine exactly which wireless card you have so we can tailor our answers to fit your particular hardware.

Thank you!

- Woody

---

### Post by filthmontane on 2010-10-24
i already updated everything

here's that thing

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by Guilden_NL on 2010-10-24
Two more requests, in a terminal copy and paste this into the terminal and then hit enter, then post the results here.

nm-tool

Second command in a terminal:

sudo lshw -C network


Out of curiosity, what manufacturer and model is the laptop?

---

### Post by filthmontane on 2010-10-24
here you go
NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        4C:0F:6E:0D:0D:90

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Buy a Macintosh: Infra, 00:19:E3:FA:46:35, Freq 2412 MHz, Rate 54 Mb/s, Strength 31 WPA2
    Belkin.31BA:     Infra, 94:44:52:1F:F1:BA, Freq 2412 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2
    CGD8280:         Infra, 30:46:9A:87:56:CF, Freq 2462 MHz, Rate 54 Mb/s, Strength 31 WPA2
    print server 5FEEEC: Ad-Hoc, 02:90:C0:17:0E:71, Freq 2462 MHz, Rate 11 Mb/s, Strength 37
    chad:            Infra, 00:1C:10:BE:6C:43, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    Grandma's Place: Infra, 00:22:3F:9A:03:BF, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Highland:        Infra, 68:7F:74:11:A6:06, Freq 2437 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        60:EB:69:5F:6A:FD

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.112
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             65.32.5.111


and this 

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 4c:0f:6e:0d:0d:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0100000-d010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:5f:6a:fd
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.112 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:2000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:d0020000-d002ffff

i just got it, the box says it's an HP G62-340US.

---

### Post by Guilden_NL on 2010-10-24
When you run the lshw command (that first character is a lower case L), there are several interesting bits of info, but the one that is most interesting would be a line similar to this one:

 configuration: broadcast=yes '''driver=ath_pci driverversion=0.9.6.0

:D  I see that your reply and mine passed in the Ethersphere.

OK, thanks.  I'll take a look and see what I can determine.

Oh boy! A virus!! >>>>>>>>>"Buy a Macintosh"      

Just joking, I work for HP...... :D

I'll read through this and hopefully find something for you.

---

### Post by Guilden_NL on 2010-10-24
Check it out, wireless is working - it sees the wireless access points!

Now you need to set up the WAP encryption so that you can connect.

Do you know how to do that, or need help?
As a suggestion, I like to use the app WiCD for wireless config, it's a nice GUI tool that makes it easy to configure Wireless Access Points encryption.  You can get it from 
the Ubuntu Software Center.  Connect up with wired Ethernet, then go to Applications>Ubuntu Software Center>Get Software then search for WiCD over in the search box at the upper right.  Then click on Install.  It should show up in your tray and then you click on it for configuration of Wireless Access Points.
 
How do I know that your wireless card is working with Ubuntu?  Because of this:
[I]
- Device: wlan0 ----------------------------------------------------------------
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points
Buy a Macintosh: Infra, 00:19:E3:FA:46:35, Freq 2412 MHz, Rate 54 Mb/s, Strength 31 WPA2
Belkin.31BA: Infra, 94:44:52:1F:F1:BA, Freq 2412 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2
CGD8280: Infra, 30:46:9A:87:56:CF, Freq 2462 MHz, Rate 54 Mb/s, Strength 31 WPA2
print server 5FEEEC: Ad-Hoc, 02:90:C0:17:0E:71, Freq 2462 MHz, Rate 11 Mb/s, Strength 37
chad: Infra, 00:1C:10:BE:6C:43, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
Grandma's Place: Infra, 00:22:3F:9A:03:BF, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
Highland: Infra, 68:7F:74:11:A6:06, Freq 2437 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
[/I]

---

### Post by filthmontane on 2010-10-25
I already got that program but it keeps telling me i was giving it a bad password so i assumed that there was probably something wrong. sorry for making you go through all that.

---

### Post by d3v1150m471c on 2010-10-25
is your network manager picking up a wireless signal?

---

### Post by filthmontane on 2010-10-25
it does, i try to connect, got into properties put in my password and then it tells me bad password. I installed ubuntu using the install inside windows option and it said it reduces disk performance. not quite sure what that quite means, but maybe this problem something to do with that. it connects just fine using windows.

---

### Post by Guilden_NL on 2010-10-25
d3v1150m471c,
Yes it is, see the output above, there are several wireless access points being seen.

filthmontane,
No problem, that's why we're here - to help!

There could be other reasons, but one to get out of the way is the password.
I have several tricks to get it right, but the simplest one is to type the password into a text editor and then copy it and then paste it into the password field.  That makes sure that you're getting the password entered right.

If you are still getting "bad password" errors, then there are several other troubleshooting paths to take.

---

### Post by filthmontane on 2010-10-25
No dice my good sir. im going to try something out. since im not running ubuntu and windows as a proper dual boot, maybe they're interfering with each other. im going to disconnect from the wireless on windows and restart.

---

### Post by 3rdalbum on 2010-10-25
My next step would be to try connecting again, and then when the "bad password" message comes up type this into the terminal:

dmesg

The last couple of lines should relate to the wireless. A "bad password" message only means that there was a failure to connect, because your router doesn't actually tell the computer when the password is wrong.

---

### Post by filthmontane on 2010-10-25
here's what it tells me

aid=1)
[  481.018090] wlan0: associated
[  481.032699] wlan0: deauthenticating from 68:7f:74:11:a6:06 by local choice (reason=3)
[  481.040154] cfg80211: All devices are disconnected, going to restore regulatory settings
[  481.040163] cfg80211: Restoring regulatory settings
[  481.040170] cfg80211: Calling CRDA to update world regulatory domain
[  481.048627] cfg80211: World regulatory domain updated:
[  481.048634]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  481.048643]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  481.048651]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  481.048658]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  481.048664]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  481.048670]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  482.297286] wlan0: authenticate with 68:7f:74:11:a6:06 (try 1)
[  482.299409] wlan0: authenticated
[  482.299454] wlan0: associate with 68:7f:74:11:a6:06 (try 1)
[  482.302067] wlan0: RX AssocResp from 68:7f:74:11:a6:06 (capab=0x411 status=0 aid=1)
[  482.302076] wlan0: associated
[  482.320152] wlan0: deauthenticating from 68:7f:74:11:a6:06 by local choice (reason=3)
[  482.320459] cfg80211: All devices are disconnected, going to restore regulatory settings
[  482.320467] cfg80211: Restoring regulatory settings
[  482.320475] cfg80211: Calling CRDA to update world regulatory domain
[  482.330197] cfg80211: World regulatory domain updated:
[  482.330205]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  482.330214]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  482.330222]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  482.330229]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  482.330235]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  482.330242]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  482.878135] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  483.004224] r8169 0000:03:00.0: eth0: link up
[  493.128147] eth0: no IPv6 routers present

---

### Post by 3rdalbum on 2010-10-25
What if you use Network Manager instead if WICD?

---

### Post by filthmontane on 2010-10-25
well, i tried to get it working with network manager first but either it doesnt work or i dont know how to use it

---

### Post by d3v1150m471c on 2010-10-26
the following is from thread: [http://ubuntuforums.org/showthread.php?t=1244686](http://ubuntuforums.org/showthread.php?t=1244686)

> **kfries6 said:**
> NP, I actually have the AR9285 working in Ubuntu, but it does not work out of the box unfortunately.

There are two solutions to this.  First of all, let me state that the  solution is already on the way, and this will very shortly work out of  the box... its just not there today.

Also, unfortunately, both solutions require a network connection of some  sort.  What I did was use a cheap, Linksys Wired Ethernet to USB  adapter.  It got me over my initial problem, and provides a fast and  cheap failover.

[http://www.partstore.com/Part/Cisco+Systems+Inc/Linksys/USB100M/New.aspx](http://www.partstore.com/Part/Cisco+Systems+Inc/Linksys/USB100M/New.aspx)

Once you have network, connectivity you can either install the drivers in JJ by issuing the following command:

# apt-get install linux-backports-modules-$(uname -r)

or do an early upgrade to Karmic Koala by issuing this command:

# do-release-upgrade -d

(or in a graphic environment, press CTRL-ALT-F2, and type "gksudo update-manager -c -d" in the run box)

Both of these solutions will add the appropriate drivers.  Restart  network or reboot.  The device will be added to your system... look in  /etc/udev/rules.d/70-persistent-net.rules to see what interface name the  system created for your device.  It will be the one using the ath9k  driver.

HTH
Kevin Fries

i hope that helps. seems a lot of people have problems with this card.

---

### Post by filthmontane on 2010-10-26
both of those didn't do anything when i put it in the console

---

### Post by filthmontane on 2010-10-27
well, i guess i might just uninstall ubuntu because i cant get wireless for my laptop which defeats the purpose of having one

---

### Post by ugm6hr on 2010-10-27
> **filthmontane said:**
> i already updated everything

here's that thing

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

Apparently, there are a few different versions of this wifi card, hence the problems with documentation.
Here's another help tutorial:
[http://ubuntuforums.org/showpost.php?p=10017274&postcount=3](http://ubuntuforums.org/showpost.php?p=10017274&postcount=3)

However, if you are keen to get this working, re-post this:
```
lspci -nn | grep -i network
```
This specifies exact hardware device ID's - which hopefully might be able to differentiate between them.

Remember, you will need a wired connection during any new driver install.

---

### Post by tajiknomi on 2010-10-27
[SIZE=2]watch out...hope it help you..

[/SIZE][https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html)

---

### Post by tajiknomi on 2010-10-27
[SIZE=2]quite similar...
[/SIZE][http://www.linuxforums.org/forum/wireless-internet/164139-wireless-connection-problems-ubuntu-10-04-a.html](http://www.linuxforums.org/forum/wireless-internet/164139-wireless-connection-problems-ubuntu-10-04-a.html)

---

