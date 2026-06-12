---
title: "Ralink RT2561 wifi card stopped working in 14.04"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by hoodbrothers2 on 2014-07-30
Hi everyone I am new to the forums so sorry if I do something wrong!  A couple months ago I built a computer and installed ubuntu 12.04 64 bit.  I was on a budget so I scavenged parts from an old pc including the wifi card which is the one in the title.  It worked fine for me until I upgraded to ubuntu 14.04 64 bit, at which I began to have slow speed.  It seems to have become worse, and when I click on connection information it says I only get 1 mbs.  I have tried multiple commands but nothing has worked.  Currently there is no wifi on the computer.  Is there a way to fix this or should I invest in a new card?  It's pretty old but I don't really want to spend money.  Also, what new card would work with ubuntu 14.04 if I have to get one?  Thanks in advance.

---

### Post by mörgæs on 2014-07-30
Hi, welcome to the fora.

The card is fine. Do you get connection in a live boot of 14.04.1?

---

### Post by hoodbrothers2 on 2014-07-30
I like to stick with the LTS and I'm kind of a noob at this sort of thing, so I'd prefer to not do a live boot or anything.  I upgraded 12.04 to 14.04 directly through commands at the terminal.

---

### Post by mörgæs on 2014-07-30
Interesting. Why don't you want to do a live boot?

---

### Post by hoodbrothers2 on 2014-07-30
Well to do a live boot would I just download 14.04.1 on a USB and start my computer?  If that's all I have to do I'll give it a try.

---

### Post by hoodbrothers2 on 2014-07-30
Hey I actually didn't know 14.04.1 was out, but now that I do I am using my slow and little wifi to upgrade because it's LTS.  Hopefully this solves my problems but I'll report back later to tell what happened.  Might take a while though...

---

### Post by hoodbrothers2 on 2014-07-31
I was reading more online, and now I think upgrading could help me.  So I entered this command:

sudo update-manager -d

It said ubuntu 14.10 is available.  I like to stick with LTS, so is 14.10 a LTS?  Did they mess up and it's supposed to say 14.04.1?  How do I know if I have 14.04.1?  If I don't have it, how can I download it easily without messing up my files?  Thanks.

---

### Post by hoodbrothers2 on 2014-07-31
I guess all in all I want to know this:  my software is up to date, (besides the 14.10 thing) so do I have 14.04.1 all ready?  And, is that the lastest LTS that is not beta or alpha?

---

### Post by mörgæs on 2014-07-31
14.10 refers to the year 2014, 10. month. In other words it's the development version due to release in October. 

The X-number in 14.04.X (as in 14.04.1) indicates a point release, that is an ISO file with all bug fixes which have been released until now. 

It only matters for ISO files. If you have any 14.04.X installation and apply all updates you will get to the latest version. 

I never do upgrades and I don't recommend them. If you are in doubt best you can do is a fresh install of 14.04.1.

---

### Post by hoodbrothers2 on 2014-07-31
I have downloaded 14.04.1 using my slow wifi, but unfortunately nothing has changed.  Another thing I should add though, when I click on connection information right above the speed it shows the driver.  Except there is nothing there.  This had previously led me to believe it was a driver problem but I never figured out how to download the driver.  I like in ubuntu how you can use the additional drivers feature, but nothing related to my wifi card comes up.  It's strange though how in ubuntu 12.04 I don't remember downloading any drivers and yet it worked... If anyone has any ideas like how to download the drivers or any commands to help me please speak up.  And thanks for the help so far mörgæs.

---

### Post by mörgæs on 2014-08-04
Let's forget the wirefree for a moment. 
Did you do a fresh install of 14.04.1 using wired internet access and applied all updates? If not please do and post the results.

---

### Post by hoodbrothers2 on 2014-08-04
My wifi is very bad right now but sometimes I get periods of less bad.  During one of those I managed to download 14.04.1 and all updates.  If I had a choice I would use wires, but this computer is up stairs with the modem/router downstairs.  I don't have any Ethernet jacks in the room.  I thought 14.04.1 could have worked, but there is no difference and I still have very slow wifi.

---

### Post by varunendra on 2014-08-04
First off, AR8151 is not a wifi card at all, it is an Ethernet card. So the title of your thread is misleading and confusing.

To see which wifi card you have, run the following command in a terminal -
```
lspci -nnk | grep -iA2 net
```

Or even better, run the wireless_script mentioned here : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) - and post back the report it generates.

---

### Post by hoodbrothers2 on 2014-08-05
Sorry, I actually don't know the difference between a wifi card and a ethernet card.  The first line of code:
```

scubaturtle@Pc:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151v2.0 Gigabit Ethernet [1969:1083] (rev c0)
            Subsystem:Gigabyte Technology Co., Ltd Device [1458:e000]
            Kerneldriver in use: atl1c
03:06.0 Network controller [0280]: Ralink corp. RT2561/RT61802.11g PCI [1814:0301]
            Subsystem:Gigabyte Technology Co., Ltd GN-WP01GS [1458:e934]
            Kerneldriver in use: rt61pci
scubaturtle@Pc:~$

```
I also clicked the link, but since I was viewing from an ipad I manually typed the code in.  I got an error saying I was not authorized.  I ran it as sudo a second time but it still didn't work.

---

### Post by hoodbrothers2 on 2014-08-05
I got the linked code to work.  Here is the result:
```


                ========Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~
xxxxxPc 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty
CPU    : AMDFX(tm)-4130 Quad-Core Processor
Memory : 7983 MB
Uptime : 23:16:52 up 55 min, 2 users,  load average: 0.13,0.06, 0.10


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151v2.0 Gigabit Ethernet [1969:1083] (rev c0)
                Subsystem:Gigabyte Technology Co., Ltd Device [1458:e000]
                Kerneldriver in use: atl1c
03:06.0 Network controller [0280]: Ralink corp. RT2561/RT61802.11g PCI [1814:0301]
                Subsystem:Gigabyte Technology Co., Ltd GN-WP01GS [1458:e934]
                Kerneldriver in use: rt61pci


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 002 Device 004: ID 0781:5575 SanDisk Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roothub
Bus 006 Device 002: ID 046d:c51b Logitech, Inc. V220 CordlessOptical Mouse for Notebooks
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roothub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub
Bus 003 Device 003: ID 045e:0719 Microsoft Corp. Xbox 360Wireless Adapter
Bus 003 Device 002: ID 10f5:0285 Turtle Beach
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 roothub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE802.11bg  ESSID:"xxxxxx"  
         Mode:Managed  Frequency:2.422GHz  Access Point: <MAC C-01 xxxxxx>   
          Bit Rate=12Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7  RTS thr:off   Fragment thr:off
          PowerManagement:off
          LinkQuality=47/70  Signal level=-63 dBm  
          Rx invalidnwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessiveretries:207  Invalid misc:59   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN     no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt61pci               32115  0
rt2x00pci             13287  1 rt61pci
rt2x00mmio            13603  1 rt61pci
rt2x00lib             55307  3rt61pci,rt2x00pci,rt2x00mmio
mac80211             630653  2 rt2x00lib,rt2x00pci
cfg80211             484040  2 mac80211,rt2x00lib
eeprom_93cx6          13344  1 rt61pci
crc_itu_t             12707  1 rt61pci
wmi                   19177  0


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2):ieee80211_regdom=00
mac80211      (5):probe_wait_ms=500
rt61pci       (1):
wmi           (2):


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===================o=============o=========o=============o=========o===========o==============o===========
 Interface &ID    | Type        | Driver  | State      | Default | Speed     |Support      | HW Addr   
===================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [xxxxxx] | 802.11 WiFi | rt61pci |connected   | yes     | 18 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    *xxxxx:       Infra, <MAC C-01 xxxxxx>, Freq2422 MHz, Rate 54 Mb/s, Strength 57 WEP

    Address:         192.xxx.1.xx
    Prefix:          24 (xxx.xxx.xxx.0)
    Gateway:         192.xxx.1.xxx
    DNS:             192.xxx.1.xxx
-------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0              | Wired       | atl1c  | unavailable | no      |           |              | <MAC eth0>
-------------------+-------------+---------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

xxxxx             :ssid=xxxxx | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto
xxxxxx       : ssid=xxxxx| mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto
xxxxxx          : ssid=xxxxx| mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver xxx.x.x.x
search xxxxxx.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination    Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         xxx.xxx.x.xxx   0.0.0.0         UG   0      0        0 wlan0
xxx.xxx.x.0    0.0.0.0         xxx.xxx.xxx.0   U    9      0        0 wlan0

--- xxx.xxx.x.xxx ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time1001ms
rtt min/avg/max/mdev = 2.549/4.979/7.410/2.431 ms

--- xxx.x.x.x ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.027/0.031/0.036/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country US:
                (2402 -2472 @ 40), (3, 27)
                (5170 -5250 @ 40), (3, 17)
                (5250 -5330 @ 40), (3, 20), DFS
                (5490 -5600 @ 40), (3, 20), DFS
                (5650 -5710 @ 40), (3, 20), DFS
                (5735 -5835 @ 40), (3, 30)
                (57240 -63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channelsin total; available frequencies :
          Channel 01(2.412 GHz) - 11 (2.462 GHz)

          CurrentFrequency:2.xxx GHz (Channel x)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scancompleted :
          Cell 01 -Address: <MAC C-01 xxxxxx>
                   Channel:x
                   Frequency:2.xxx GHz (Channel x)
                   Quality=49/70  Signal level=-61dBm  
                   Encryption key:on
                   ESSID:"xxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6Mb/s; 9 Mb/s
                             11 Mb/s; 12 Mb/s; 18 Mb/s
                    BitRates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                   Mode:Master
                   Extra:tsf=000001de2ccfee29
                   Extra: Last beacon: 20ms ago


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-local.conf]
blacklist nvidia_331

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rt61pci]
filename:      /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
firmware:      rt2661.bin
firmware:      rt2561s.bin
firmware:      rt2561.bin
version:        2.3.0
srcversion:    CF4E6C5B3BC64AAF193A5A5
depends:       rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
parm:          nohwcrypt:Disable hardware encryption. (bool)

[rt2x00pci]
filename:      /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
version:        2.3.0
srcversion:    9B9D0D0D0F8571AF43705FD
depends:       rt2x00lib,mac80211

[rt2x00mmio]
filename:      /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
version:        2.3.0
srcversion:    07530604F5CE4EF69872C75
depends:       rt2x00lib

[rt2x00lib]
filename:      /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:    CC69EE39E7D673974A21C0A
depends:       mac80211,cfg80211

[mac80211]
filename:      /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:       cfg80211
parm:          max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting(reason 4). (int)
parm:          max_probe_tries:Maximum probe tries before disconnecting (reason 4).(int)
parm:           beacon_loss_count:Numberof beacon intervals before we decide beacon was lost. (int)
parm:          probe_wait_ms:Maximum time(ms) to wait for probe response beforedisconnecting (reason 4). (int)
parm:          ieee80211_default_rc_algo:Default rate control algorithm for mac80211 touse (charp)

[cfg80211]
filename:      /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:    E786D076B61F97809B04B64
depends:        
parm:          ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:          cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band(bool)

[eeprom_93cx6]
filename:      /lib/modules/3.13.0-32-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:    215D8C1284A3C33B4A5A1C5
depends:        

[crc_itu_t]
filename:      /lib/modules/3.13.0-32-generic/kernel/lib/crc-itu-t.ko
srcversion:    57DB184B6F722970048006C
depends:        

[wmi]
filename:      /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:    CED5410F008DC70DF5F064B
depends:        
parm:          debug_event:Log WMI Events [0/1] (bool)
parm:          debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device0x1969:/sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add",DRIVERS=="?*", ATTR{address}=="<MAC eth0>",ATTR{dev_id}=="0x0", ATTR{type}=="1",KERNEL=="eth*", NAME="eth0"

# PCI device0x1814:/sys/devices/pci0000:00/0000:00:14.4/0000:03:06.0 (rt61pci)
SUBSYSTEM=="net", ACTION=="add",DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0",ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        :Not Default
/etc/rc.local       :Default
/etc/modprobe.d     :Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
nouveau

[/etc/modprobe.d]
ath5k.conf        :options ath5k nohwcrypt=1
ath9k.conf        :options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                   (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs/sbin/rmmod) \
                   && /sbin/modprobe -r mac80211
mlx4.conf         :softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=xxxxxxxxxxxxxxxxxxxxxro quiet splash


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.095810]microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>,Peter Oruba
[    1.096211] audit:initializing netlink socket (disabled)
[   21.644520] wmi:Mapper loaded
[   21.754196]ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2561, rf: 0003,rev: 000c
[   26.335960]Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.077041]ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file'rt2561s.bin'
[   30.464858]ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version:0.8
[   30.503648] IPv6:ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.505166] IPv6:ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.779569] wlan0:authenticate with <MAC C-01 xxxxx>
[   31.791325] wlan0:send auth to <MAC C-01 xxxxxx> (try 1/3)
[   31.832959] wlan0:authenticated
[   31.833090] rt61pci0000:03:06.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   31.833095] rt61pci0000:03:06.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   31.833097] rt61pci0000:03:06.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   31.835228] wlan0:associate with <MAC C-01 xxxxxx> (try 1/3)
[   31.838452] wlan0:RX AssocResp from <MAC C-01 xxxxxx> (capab=0x431 status=0 aid=3)
[   31.838625] wlan0:associated
[   31.838649] IPv6:ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

                ========Done ========


```

---

### Post by varunendra on 2014-08-05
You have masked even the channel no. in use? :p

As per the report, you are connected and have 'Everything' (most of which has to be 'Assumed' due to aggressive masking) fine.

With a fresh mind, I maybe able to cipher out a few useful hints, but right now, tired brain + abnormal Fonts + Ultra masking are making it difficult for me to identify a problem (if it is hinted in the report) and suggest a solution.

I hope someone else may be able to help you out with the report, since I'm not sure of my availability to the forums for a few days.

Good luck!

---

### Post by mörgæs on 2014-08-05
Changed the thread title.

---

### Post by hoodbrothers2 on 2014-08-06
I did this command:
```

sudo ifdown wlan0 && sudo ifup wlan0

```
to restart it.  I got this:
```

ifdown: interface wlan0 not configured

```
Is this a/the problem?

---

### Post by hoodbrothers2 on 2014-08-06
Another thought, although I think I mentioned this, would I have to install new drivers?

---

### Post by hoodbrothers2 on 2014-08-07
I think I successfully installed new drivers but it didn't do anything.  Also, when I was looking at the information in system/network it sometimes say the wireless network is out of range, but it used to work just fine.

I'll be away from my computer for 10 days, but I'll still have wifi acces for iPads, laptops, etc. so keep sending ideas.  I am not enjoying my pc without Internet and this problem has been bugging for a long time now, so I really want to fix it.

---

### Post by hoodbrothers2 on 2014-08-17
I am back and have access to my pc again.  The wireless is still not working (Not that I thought it would be).  If anyone has any ideas please speak up.  I'm starting to think getting a new wireless card/ethernet card or whatever will be the only way.  I hope not though.  I wonder if you have more time to look at the code report I sent varunendra?  Thanks.

---

### Post by varunendra on 2014-08-19
Actually I am even more stressed, but forums is kinda break from stressful work for me, so did take a look again.

First issue - why are you so paranoid about security while posting a report on the forums? On the other hand, you are using WEP security which any 10 year kid can break in less than 10 minutes these days (not using any 'expertise', but free tools available on the net). :p

Even after masking, I can tell by a two-second calculation that you were using channel-3 while the last report was generated. I don't think declaring that (and other parts included in the script report) is any harmful, as the potentially sensitive data is already filtered out by the script. By excessive masking you are only preventing potential helpers from helping you.

That being said (as a really friendly advice), I have the following suggestions for you -

**1)** Try changing the channel in the router to 1 or 11. Currently it is set to either 'auto' or channel '3'.

**2)** In the router, try changing the encryption type to WPA2-PSK with AES (or just for a test, try completely turning it off). WPA2 with AES is the best security protocol/algorithm and you card seems to support it. It also improves performance if the card supports it well. Remember - pure WPA2 with AES (may be listed as "CCMP"); no WPA/WPA2 mixed mode, no TKIP. Reboot the router after saving the changes.

**3)** Try a driver parameter in Ubuntu -
```
sudo modprobe -rv rt61pci
sudo modprobe -v rt61pci nohwcrypt=Y
```
This will be a temporary change that will be reset at next boot. If it helps, we can make it permanent.

**PS:**
You don't seem to be using any Atheros cards, internal or USB. As such, the two 'ath...conf' files in your /etc/modprobe.d directory are useless. You can delete them with -
```
sudo rm /etc/modprobe.d/ath{5,9}k.conf
```
(they are not related to the current problem though, and are harmless; just useless as well)

---

### Post by hoodbrothers2 on 2014-08-19
Thanks for the response.  I'm willing to try this stuff but the wifi here is shared by multiple people and I do not want to mess it up for them.  (I'm noob on this topic). So will doing this stuff change the wifi speed or anything?  Also, after I do this they won't have to like log back on or anything right?  Another thing to note also is that there is a computer in my basement that is hooked up to the router and modem.  It is running windows.  I want to try this stuff but I also want to make sure it won't mess stuff up and cause more problems for me or the others who didn't have problems in the first place.  Also again, would I do this using my pc or the one hooked up to the router?  Thanks!

---

### Post by varunendra on 2014-08-19
WPA2-AES (CCMP) is recommended encryption these days. But if someone in the network is still using more than 10 year old wireless devices, then yes, those devices may not support WPA2 or AES and thus may have problems.

Depending upon the kind of security key you have used for the WEP encryption, you *may* need to change the security key as well (WPA2/AES may not accept some keys that are acceptable by WEP). In which case, the users will need to save a new profile for the connection using the new key (their system should ask them automatically for the security key). They 'may' have to delete current profiles if the system doesn't automatically create a new one with new key.

You need to be connected to the router while doing this, so it is best to do it via a system that is connected via Ethernet cable. Please refer to your router's user manual to see how to change encryption.

Changing from WEP to WPA2 will enhance the security (from "a piece of cake" to "extremely hard even for experts"), and *may* enhance speed/performance as well. The speed/performance improvement is not guaranteed, but it *should* not be bad compared to current state. At least that's what my theoretical knowledge and limited experience says.

---

### Post by hoodbrothers2 on 2014-08-20
All right thanks, I'm new to this stuff but I'm learning! :). I just thought I would add something.  I managed to install kubuntu and in kubuntu I got the notification that the wifi network could not be found.  I then found a list of notifications.  It looks somewhat like this:

Active connection state changed
Missing VPN plugin
VPN connection state changed

Device failed to connect

I wonder if this means anything to you?  As for your suggestions I think I will try them this weekend with some help from someone.  Thanks

---

### Post by hoodbrothers2 on 2014-08-20
The pc running windows downstairs is using a realtek rtl8139/810x family fast ethernet NIC.  Would this work with ubuntu?  Do you think it's worth it to try and switch the two cards?

---

### Post by hoodbrothers2 on 2014-08-21
Forget the card downstairs- there isn't one.  I'm really just done with this whole thing.  Do you think getting a new card would be a good idea?  The current card is kinda old and only goes up to 54 Mb/s.  What card does someone know FOR SURE that works with ubuntu 14.04?  I'd prefer pci.  Also don't think I'm not still willing to try and fix the problem, so if anyone has any ideas please, tell me.  I'm just saying that if buying a new card fixes the problem then I'm certainly thinking about it.

---

### Post by hoodbrothers2 on 2014-08-21
Found this. [http://www.amazon.com/TP-LINK-TL-WN881ND-Wireless-Express-Low-profile/dp/B0079XWMEI/ref=sr_1_2?s=electronics&ie=UTF8&qid=1408598633&sr=1-2&keywords=Wireless+cards](http://www.amazon.com/TP-LINK-TL-WN881ND-Wireless-Express-Low-profile/dp/B0079XWMEI/ref=sr_1_2?s=electronics&ie=UTF8&qid=1408598633&sr=1-2&keywords=Wireless+cards)
Could this work?  I have one pci x16 left I believe, so would this work in it?

---

### Post by varunendra on 2014-08-21
> **hoodbrothers2 said:**
> Found this. [http://www.amazon.com/TP-LINK-TL-WN881ND-Wireless-Express-Low-profile/dp/B0079XWMEI/ref=sr_1_2?s=electronics&ie=UTF8&qid=1408598633&sr=1-2&keywords=Wireless+cards](http://www.amazon.com/TP-LINK-TL-WN881ND-Wireless-Express-Low-profile/dp/B0079XWMEI/ref=sr_1_2?s=electronics&ie=UTF8&qid=1408598633&sr=1-2&keywords=Wireless+cards)
Could this work?  I have one pci x16 left I believe, so would this work in it?

Seems to come with AR9287 chip using ath9k driver (as stated [here]("https://wikidevi.com/wiki/TP-LINK_TL-WN881ND")). Should be okay, although the ath9k driver in the current kernel versions may need a little tweaking to work optimally.

You may also wish to take a look at thinkpenguin.com who claim to supply 100% Linux-compatible hardware : [https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)

I don't have any personal experience with them, but based on the posts I've seen here, it seems they are good at customer care (warranty, replacements if required etc.).

---

### Post by hoodbrothers2 on 2014-08-21
Thanks for the answer, this card looks good but the "tweaking" part worries me.  I want something that I know can work, and is fairly easy to setup.  Would tweaking the driver be easy and problem free or would it just lead to more problems?

---

### Post by hoodbrothers2 on 2014-08-21
I saw an amazon review that said it worked plug in play out of the box on ubuntu 14.04.  I think I might go for it... Sure hope it works!!  This problem has been going on for a looong time.

---

### Post by varunendra on 2014-08-22
My laptop has an AR9285 card, and is working perfectly with ath9k driver, but I am still using a much older kernel (3.2.0-36).

I know that some regressions started in this driver since kernel version 3.5, got worst in kernel 3.8 series, but then improved again in kernel 3.11 and later. However, recently we are once again seeing complains like low speeds and frequent disconnection. But given how these problems have suddenly started with almost all the wifi drivers in Ubuntu 14.04, I personally suspect that the problem is some broken script or some other program/package in Ubuntu or the Kernel that may or may not be networking related.

Anyway, things that you are interested in - the 'tweaks' that are required (if at all) are minor, easily reversible, and then wifi starts working as it should without adversely affecting anything else. But then again, things are changing fast and it is hard to predict whether this 'unusual' behaviour of wifi drivers is going to improve in future updates or not.

Your best bet - look for [SOLVED] threads in the Networking and Wireless section, and note down the models that take minimum amount of effort to make everything nice and cheesy. The unfortunate aspect of these support forums is that only those come and post here who have problems with their OS, not those for whom things worked out-of-box.

As far as this particular card goes, I *believe* we have solved a few problem threads related to this chip (AR9287). But that doesn't mean that it is bound to have problems (many problems mostly depend on external factors). It WILL work out-of-box, but I can't say how well.

---

### Post by hoodbrothers2 on 2014-08-22
I got this card because this one is for pci.  Basically the same card.

[http://www.amazon.com/TP-LINK-TL-WN851ND-Wireless-Adapter-Low-profile/dp/B005NHIQ06/ref=sr_1_12?ie=UTF8&qid=1408762272&sr=8-12&keywords=Wireless+cards](http://www.amazon.com/TP-LINK-TL-WN851ND-Wireless-Adapter-Low-profile/dp/B005NHIQ06/ref=sr_1_12?ie=UTF8&qid=1408762272&sr=8-12&keywords=Wireless+cards)

It will be here in about 2 days.  I've read some positive reviews about it for Linux, so I hope it works!  Might need some help with the drivers though, I did the "remove ath9k drivers" thing you suggested early, but if I'm correct that wasn't permanent.

---

### Post by hoodbrothers2 on 2014-08-26
I got the new card.  Compared to the old one, it's a lot better.  Currently while watching a YouTube video I'm getting 48 Mb/s,  which is a lot better than the 1 Mb/s with the old card.  I tried downloading something that was like 70 mbs, and it took around two minutes.  (I didn't time I'm just guessing).  However, I've noticed two strange things.  One, there is a light on the card, but it is not on, even though I have Internet.  Second, sometimes the speed just drops.  It just went from 48 (Mb/s) to 36, then to 1, then up to 24, then 36, then back up at 48.  It said it's supposed to reach maximum 300 Mb/s.  I didn't expect to reach this high, but I thought I would get more than 54 Mb/s.  What are your thoughts?

---

### Post by varunendra on 2014-08-27
Not knowing exact chip on the card, or the driver in use, I don't dare to express many thoughts :p

To let us see these (chip and the card), you should post the outputs of -
```
lsusb
nm-tool
```
Or better, an entire new wireless_script report to show us overall new settings. It will also help us as a feedback/proof of 'acceptable' performance for that chip/driver. Without enough clues, my best guess is that the variable speed is due to either interfering neighbourhood signals, or power management policies on the driver/networking.

But if you really want to try optimizing it, if possible, you should start a new thread since it is definitely a different chip/driver.

---

### Post by hoodbrothers2 on 2014-08-30
I'm going to close this thread.  My wifi is better, but not really what it used to be.  I guess I might try some other stuff to try and fix it, so hopefully it gets better.  Thank you all so much for helping though.  Varunendra, I think I will use your advice to optimize this card, so thanks.  Again, thanks everyone.

---

### Post by hoodbrothers2 on 2014-09-03
Unfortunately I'm back.  I tried starting a new thread about updating the kernel but people started getting PO'd at me.  (You can view the thread if you want).  Basically I just wanted some advice about updating the kernel so I started a new thread.  But then people got mad because they thought I should've just stayed on this thread.  So here I am.  Anyways, I was thinking updating the kernel could help, so I want to know how to do it via USB, and which version of the kernel would be best to upgrade to.  After that if it doesn't work, I'll send some info about the new card like you said.  Thanks everyone.

Ps. Guys sorry for dragging this on a lot, it's just really annoying to not have Internet, after I've spent so much money to make my computer.

---

### Post by mörgæs on 2014-09-03
If you want to get help with kernel versions a good beginning is posting which one you are using now.

Anyway, a good option is trying the development version 14.10.

---

### Post by varunendra on 2014-09-03
Sorry about your disappointment in the other thread, probably a misunderstanding due to mixing of issues. You didn't clearly mention that you are now using a completely different card, and only talked about kernel upgrade.

Installing a newer kernel is as easy as downloading and double-clicking its .deb package. They can be downloaded manually from here : [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/)

For a normal installation, it is the "linux-image-*[COLOR="#0000CD"]<desired version>[/COLOR]*-generic-*[COLOR="#0000CD"]<version no. and architecture>[/COLOR]*.deb" file. For example,
linux-image-3.16.0-12-generic_3.16.0-12.18_amd64.deb

Not necessary, but is highly recommended to also install the headers of the same version as the kernel image. For example, for the headers packages corresponding to above image are -
linux-headers-3.16.0-12-generic_3.16.0-12.18_amd64.deb
and
linux-headers-3.16.0-12_3.16.0-12.18_all.deb

However, a much safer way to test the latest kernels that are not installed by default on your existing system is to test the development version in Live mode, as mörgæs suggested -
> **mörgæs said:**
> ....a good option is trying the development version 14.10.
You can download the Live DVD image of the development version from here : [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
Or using the smarter (but not as simple as above) way : [https://help.ubuntu.com/community/JigdoDownloadHowto](https://help.ubuntu.com/community/JigdoDownloadHowto)

---

### Post by hoodbrothers2 on 2014-09-04
I downloaded the image and made it bootable on a USB.  However, it gave me this message "gfxboot.c32: not a COM32R image" I then pressed tab and typed live.  At first it appeared to be working, but then it failed to load nouveau and I'm at a basic terminal version of 14.10.  I don't know if this has anything to do with me having NVIDIA drivers, but the bottom line is that it didn't work.

---

### Post by varunendra on 2014-09-05
Since the target is to try the wireless stuff, maybe you can ignore graphics and try to load basic graphics mode with 'nomodeset' option? Did you try it?

If the Live USB fails to work with your graphics, then it is quite possible installing that kernel will cause graphics troubles too.. unless you know how to deal with it (I don't).

---

### Post by hoodbrothers2 on 2014-09-05
How do I boot it up live with nomodeset?

---

### Post by varunendra on 2014-09-06
Press any key during the splash screen to bring up advanced boot menu > select the language > press 'F6' to pop up boot options menu > highlight 'nomodeset' option using arrow keys > press 'Spacebar' to put a cross (means selection) before it > press 'Esc' (the selection would be saved) > press 'Enter' to boot with it.

Explained in detail here, with screenshots : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by hoodbrothers2 on 2014-09-06
That's what I thought, but the problem is I don't get a splash screen.  When I start my pc with the USB in and set to first boot priority, it says Verifying DMI Pool Data .......... Like normal.  Then however it says gfxboot.c32: not a COM32R image.  After that it says boot: and then just repeats itself.  But, if I press tab when it says boot: it gives me a list of options to type: live live-install check memtest hd mainmenu help.  I tried typing live, and then pressed enter and it started booting up ubuntu 14.10.  But then it starts me in a basic terminal mode after listing some nouveau errors.

---

### Post by hoodbrothers2 on 2014-09-06
I tried doing a live boot of ubuntu 12.04, which I used to use when my internet worked.  Currently I am typing from my computer, which means my wifi is working.  But, right now I am only getting 11 Mb/s which is less than I used to.  Another weird thing though is that it detects my monitor as a laptop when I go into displays.  Also, when I click on connection information it actually tells me that I'm using the ath9k drivers, which I've never seen before.  Another thing I just noticed is that it says I'm using wlan0, when in ubuntu 14.04 I'm pretty sure it tells me I'm using wlan1.  I'm not sure what all this means, but maybe you can make sense of it.  Also I switched the router to channel 11.

---

### Post by varunendra on 2014-09-06
> **hoodbrothers2 said:**
> That's what I thought, but the problem is I don't get a splash screen.  When I start my pc with the USB in and set to first boot priority, it says Verifying DMI Pool Data .......... Like normal.  Then however it says gfxboot.c32: not a COM32R image.  After that it says boot: and then just repeats itself.  But, if I press tab when it says boot: it gives me a list of options to type: live live-install check memtest hd mainmenu help....
Sounds like a non-standard USB boot method. How have you created the live usb? The lack of splash screen and the 'gfxboot.c32' error could be due to the method used to boot it. The nomodeset option can still be used, but in which step and how depends on the method used to boot the USB, which can be guessed by the program you used to create it.

I personally prefer the "Startup USB Creator" that exists within Ubuntu live, which keeps the booting exactly as the Live DVD (besides offering the persistence on a USB).

> **hoodbrothers2 said:**
> Also, when I click on connection information it actually tells me that I'm using the **[COLOR="#FF0000"]ath9k drivers[/COLOR]**, which I've never seen before....
In post #34, you mentioned you "got the new card", so not really a surprise you are using a different driver now. And that's precisely why I suggested to start a new thread if you need help with that.

If you do so now, make sure to clearly mention that you are _NOT_ using the same card/driver that _this thread_ was started with, hence the new thread.

---

### Post by hoodbrothers2 on 2014-09-07
Here are the steps I took to make the bootable USB: first I formatted a USB on a windows machine.  Then I downloaded the image and put it on the USB also on windows.  I then took out the USB and put it in my ubuntu machine.  I searched startup disk creator in the unity dash, and I think I used the one with the USB icon on it.  I chose my image, made the USB bootable by following the steps in the program, and then restarted my computer with the USB as first boot priority.  As to the ath9k drivers thing, what I meant was that it actually said I was using drivers in 12.04.  In other versions it just left that spot blank.

---

### Post by varunendra on 2014-09-07
The steps to create the USB seem to be okay, not sure why the problem then. But you should be able to add the 'nomodeset' option permanently to it. Here's how -

[INDENT]1) Plug in the USB in a working system (don't boot from it). This system should preferably be running Ubuntu or any other Linux OS. Windows may corrupt the file we are going to edit.
2) Locate 'syslinux' directory on the USB
3) Locate 'txt.cfg' file in 'syslinux' directory, and open it on text editor. (preferably, save a copy of it somewhere as backup first)
4) Locate the 'default' section in the file. It should be at the top.
5) In the 'default' section, locate the line that ends with "quiet splash --". This entire section (from 'default' to the "quiet splash --") should be something like -
```
**[COLOR="#FF0000"]default[/COLOR]** live
label live
menu label ^Try **Xubuntu** without installing
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz **[COLOR="#FF0000"]quiet splash --[/COLOR]**
```

6) Edit the line to insert "nomodeset" before "quiet splash". Make sure there are blank spaces before and after "nomodeset". This line should now look something like -
```
append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.lz **[COLOR="#0000FF"]nomodeset[/COLOR] [COLOR="#FF0000"]quiet splash --[/COLOR]**
```

7) Save and close the file.[/INDENT]

Now, whenever you boot from this USB it should boot with the "nomodeset" option by default. Steps for appending other parameters (as and if required) would be same as above.

About the driver confusion, it seems from your description that 'other versions' did not load a driver at all, I can't say why. But loading of ath9k driver in 'any version' indicates it is an atheros card. To confirm that, you can check the output of -
```
lspci -nnk | grep -iA2 net
```
..on 12.04 where it seems to partially work.

---

### Post by hoodbrothers2 on 2014-09-07
I did as you suggested by adding the parameter 'nomodeset'.  Luckily this time I didn't get any nouveau errors.  However, it still gave me the gfxboot.c32: not a COM32R image, and it still booted in the basic terminal mode after I typed 'live'.  I found this website [http://www.syslinux.org/wiki/index.php/Common_Problems](http://www.syslinux.org/wiki/index.php/Common_Problems) I'm going to look around some more and see if I can find anything.

---

### Post by hoodbrothers2 on 2014-09-07
I replaced the new gfxboot with the one I currently have.  That seemed to work, as it brought me to the screen where it asks if you want to download or try without installing.  When I click try without installing it loads for a long time, and then gives me an error and crashes.  From then on I'm left with a black screen.

---

### Post by hoodbrothers2 on 2014-09-08
I found this thread with a link in it to another thread with some code on it.  [http://ubuntuforums.org/showthread.php?t=2220169](http://ubuntuforums.org/showthread.php?t=2220169) Do you think it could be edited to match my card and fix my problem?

---

### Post by hoodbrothers2 on 2014-09-08
I am very near the end of my line here, this problem is extremely frustrating.  I just uninstalled my nvidia graphic drivers, because I've read of some conflicting problems with those and wifi.  Unfortunately, nothing.  Let me tell you more about how this whole thing started just so you have for information.  Back in July I got a new fancy nvidia graphics card for my computer.  I put it in, turned the pc on, but I kept getting errors and the computer wouldn't boot.  (This is back when I had 12.04)  I eventually found out there was an update for ubuntu (14.04).  I installed it, the wifi was working, everything was good.  Also, when I booted my computer with the new graphics card, it worked!  I was excited, but quickly learned that I didn't have any drivers for the card, and nothing showed up in the additional drivers program.  I vaguely remember searching the internet for how to install drivers, so the wifi must have been working.  But, I accidentally broke the Xserver trying to install drivers, and had to go through a whole process to fix it.  I eventually did and I think everything was fine.  Anyways, I came across a video that showed how to install nvidia drivers.  The video was very strange, the guy making it pretended he was 'Barney Bear'.  But, alas, I decided to give it a try.  It worked!  My graphics card was working and everything seemed to be good.  Then, sometime after that my wifi stopped working.  I don't think I ever used the new graphics card on the internet really.  That's why I tried uninstalling the nvidia drivers.  So since midway July about it's been like this.  Low speeds and frequent disconnects.  I'm almost thinking that maybe I should completely wipe my hard drive, just start over?  I don't know.  I just really want to fix this problem.  Part of me is actually wanting to get Windows, as much as I love ubuntu.  I guess what I'm saying is, I sick of this problem and want it to be fixed, even if that means starting over.  If there is a better way I'd like that, but we've been doing this for a while, and I'm just tired of it.  Thanks for all of the help I've been getting though, I really appreciate it.  It must be kind of frustrating to try and help me solve this problem.  It's definitely a tricky one.

Link to weird video: [COLOR=#006621][FONT=arial]www.youtube.com/watch?v=1oKn8DHvOrk[/FONT][/COLOR]

---

### Post by wildmanne39 on 2014-09-08
When you have more then one issue you need to start a new thread for each issue, only one issue per thread is allowed, the reason for that is if you were searching for a solution using google for a wifi issue and you find this thread that is about two different wifi cards and booting issues and it is marked solved but you have wasted your time because the thread is very confusing now.
Please get back on topic.
Thanks

---

### Post by hoodbrothers2 on 2014-09-09
I understand Wild Man, and I actually did start a new thread but people closed it because they thought it was related to this too much.  I'll just ask one more question, and then I think I'll close this thread because it's already way too long .  (Or if you could close it because I'm not entirely sure how to).  How do I wipe the hard drive so that it is like new, so that I can reinstall ubuntu or a different OS?

---

### Post by varunendra on 2014-09-10
> **hoodbrothers2 said:**
> How do I wipe the hard drive so that it is like new, so that I can reinstall ubuntu or a different OS?

During installation, Ubuntu or Windows (or any other major OS I guess) prompts for partitioning scheme. You can choose there what you want to do with existing partitions or entire disk.

Alternatively, you can use Ubuntu Live DVD/USB (one that works) or Parted Magic live cd, or any live system tools cd that has 'Gparted' on it, then use Gparted to delete the partitions and create new ones as you need.

By the way, it is not necessary to delete all partitions just to try/use a different OS or a new installation of Ubuntu again. You can simply choose to format only that partition which you are going to install the OS upon.

---

### Post by hoodbrothers2 on 2014-09-12
I didn't delete my hard drive yet, I'm not eager to.  But, I did find something very good I think... When I type
sudo iwconfig wlan1 rate 18M
I get better speeds.  First I tried 54M but it went down to 18 so I chose 18 the second time I typed it.  Right now I'm getting a solid 18 Mb/s.  However I read that this is only temporary.  Does this mean anything to you?

---

### Post by varunendra on 2014-09-12
It means the card and router are probably having problem negotiating an 'optimal' speed for communication between them.

We don't usually force custom speeds because drivers are usually smart enough to figure out the optimal speed and change it dynamically as required to avoid bad packets (forcing a speed higher than affordable for the connection quality results in lost or corrupt packets).

But yes, sometimes a forced speed does give better results. Although I personally have seen it happen only in some VERY old cards, or temporarily in a few buggy releases of some drivers.

If you think the connection speed is stable and good enough with that, you can make it permanent by adding the command to your /etc/rc.local file. Make sure you add it ABOVE the last line that says "exit 0". The following command can do it properly for you -
```
sudo sed -i '/^exit 0/i iwconfig wlan1 rate 18M' /etc/rc.local
```

The other supported speeds above 18M that you may experiment with are : 24M, 36M, and 48M.

Please try it for a sufficiently long period to be sure, and let us know if this really proves to be a stable solution for you. :)

---

### Post by hoodbrothers2 on 2014-09-13
I experimented more with the command I said, but unfortunately it wasn't good.  Right now it says I'm supposed to be getting 48 Mb/s, but when I try to load youtube it takes a long time and it even said unable to connect to the internet.  However, I was talking to some friends about my problem.  One said that maybe the pci slot was messed up, or the BIOS was.  So I reflashed the BIOS.  It didn't work.  But I am still wondering if the pci slot might be the problem... My neighbor has a usb wifi thing, and he let me borrow it.  Ubuntu didn't detect it at all, and I think it is not compatible.  It is the Netgear WNDA3100 USB.  If it is compatible with linux though, we could test to see if it is a pci problem or not.  I find it strange though that I AM getting wifi, just very low speeds.  Right now I am on a windows 7 laptop that is right next to my computer and the wifi is fine.  I also find it strange that the speed seems to jump around a lot and disconnects.  Like right now it just disconnected.  When I go to the networking settings it says that my wifi is out of range and or when I am connected it says that the signal strength is weak.  On this laptop it says the signal strength is excellent.

---

### Post by hoodbrothers2 on 2014-09-13
I know I should have done it a lot earlier but I just decided to change the wifi encryption type to wpa2 aes.  It actually has improved my wifi a little!  I think.  It does feel a little better, but it still says I'm only getting around 18 Mb/s.  I don't want to end the thread though because my wifi is still not what it used to be.

Edit: I spoke too soon.  It just disconnected.

---

### Post by hoodbrothers2 on 2014-09-13
If you remember when I said I uninstalled my nvidia drivers, I think I never uninstalled a ppa that I had to install to get the drivers working.  It is called the xorg edgers ppa or something like that.  Do you think that ppa could be causing wifi issues?

---

### Post by varunendra on 2014-09-13
I don't think graphics driver should or could interfere with wifi speeds. But since you are having difficulty booting in Live mode, I can't think of a 100% safe way to verify that.

---

### Post by hoodbrothers2 on 2014-09-14
Ok, so I've been using my wifi with the wpa2 encryption, and I have noticed a difference.  I hope I don't jinx myself, but right now it is running pretty smoothly at 36 Mb/s.  I am even downloading a game on steam!  It isn't what it used to be, and it still says the network strength is 'ok.'  It also drops and disconnects sometimes.  It just did but now it is back up at 36 Mb/s.  I am not going to close this thread yet, as I want to see how things continue.

---

### Post by hoodbrothers2 on 2014-09-19
Allright, I have used the wifi further and I've come back to report.  It has definitely been better.  I have been able to view websites, work on Google Drive, listen to Pandora, and more.  My average speed is around 36 Mb/s on a good day, and 18 Mb/s on a bad day.  However, the speed jumps around a lot, and sometimes disconnects.  When it does disconnect, I find that it doesn't really want to reconnect.  This forces me to restart my computer if I want wifi again.  Overall, my wifi works to an extent, so I am going to mark this tread as solved.  Thank you so much varunendra and morgaes for everything you have done and for sticking with me the whole way.  I still love ubuntu!

---

