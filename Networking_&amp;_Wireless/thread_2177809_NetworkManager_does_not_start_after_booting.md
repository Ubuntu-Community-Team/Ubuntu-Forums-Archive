---
title: "NetworkManager does not start after booting"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by NewbieOld on 2013-09-30
Hi together,

after booting my system the network manager does not startup autoatically.
When I start him by 
```
sudo NetworgManager
```
he works fine.

**/etc/Network-Manager/NetworkManager.conf**
```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=*

[ifupdown]
managed=true

[keyfile]
unmanaged-devices=mac:00:23:14:d5:dc:ec;mac:5c:ff:35:09:70:78

[logging]
level=INFO
domain=HW, ETHER, WIFI, DHCP4, WIFI_SCAN, IP4, DNS, SUPPLICANT

```

[B]/var/lib/NetworkManager/NetworkManager.state:
[/B]```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```


Any ideas what's wrong?

thy in advance !!!

---

### Post by theDaveTheRave on 2013-09-30
NewbieOld,

Is this is a recent problem that has arrisen, or are you on a new install?

I've seen another thread with a problem with wifi, is your problem specifcally with network manager or is it with the wifi card?

to test the wifi card try the following.
```

ifconfig

```
followed by
```

iwlist scan

```

otherwise you can check to see if the networkmanager app is in the apps to run at boot, or put in a startup script search the forums for running a script at startup ~ you will be led to /etc/rc.d , drop a reply here if you need a hand.

David

---

### Post by theDaveTheRave on 2013-09-30
NewbieOld,

Is this is a recent problem that has arrisen, or are you on a new install?

I've seen another thread with a problem with wifi, is your problem specifcally with network manager or is it with the wifi card?

to test the wifi card try the following.
```

ifconfig

```
followed by
```

iwlist scan

```

otherwise you can check to see if the networkmanager app is in the apps to run at boot, or put in a startup script search the forums for running a script at startup ~ you will be led to /etc/rc.d , drop a reply here if you need a hand.

David

---

### Post by NewbieOld on 2013-09-30
Hi David,

it is a new install.
I think it is not an issue of the wifi card as ifconfig and iwlist scan shows normal results:
ifconfig
```
bond0     Link encap:Ethernet  HWaddr 28:02:06:07:ae:ad  
          inet addr:192.172.10.100  Bcast:192.172.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:2998 errors:0 dropped:22 overruns:0 frame:0
          TX packets:2557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2780118 (2.7 MB)  TX bytes:609335 (609.3 KB)

eth0      Link encap:Ethernet  HWaddr 28:02:06:07:ae:ad  
          UP BROADCAST SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2500000-f2520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34067 (34.0 KB)  TX bytes:34067 (34.0 KB)

wlan0     Link encap:Ethernet  HWaddr 28:02:06:07:ae:ad  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:2998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2780118 (2.7 MB)  TX bytes:609335 (609.3 KB)

```

iwscan list
```

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:FE:AE:E9:66
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"HomeOffice"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012c4baf0180
                    Extra: Last beacon: 160ms ago
                    IE: Unknown: 000A486F6D654F6666696365
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACE131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0A00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: DD0C00040E010102010000000000
                    IE: Unknown: DD6A0050F204104A0001101044000102103B000100104700104BB6B7CA8CC1B17BA3779AB1E50A2EF71021000341564D10230009465249545A21426F78102400043030303010420004303030301054000800060050F20400011011000446426F78100800020188103C000103
          Cell 02 - Address: 00:1F:3F:D6:4C:43
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"HfV79d"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e7d4a745f
                    Extra: Last beacon: 5736ms ago
                    IE: Unknown: 0006486656373964
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32088C129824B048606C
                    IE: Unknown: DD0A0800280101000200FF0F
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: F0:7D:68:8F:D8:4E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"WLAN Jochen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017bdee1917a
                    Extra: Last beacon: 5361ms ago
                    IE: Unknown: 000B574C414E204A6F6368656E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700103DA420E7D661197158D4F07D688FD84E10210006442D4C696E6B102300074449522D363030102400074449522D3630301042000830303030303030301054000800060050F2040001101100074449522D363030100800020086
          Cell 04 - Address: C0:25:06:18:4E:2F
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box WLAN 3370"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000361ea510180
                    Extra: Last beacon: 4896ms ago
                    IE: Unknown: 0013465249545A21426F7820574C414E2033333730
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF111BFFFFFF00000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF111BFFFFFF00000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: 34160B001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD6F0050F204104A0001101044000102103B0001031047001000000000000010000000C02506184E2F1021000341564D10230009465249545A21426F78102400043030303010420004303030301054000800060050F204000110110009465249545A21426F78100800020188103C000103
          Cell 05 - Address: 00:19:CB:89:32:7E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"o2DSL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001247fb269
                    Extra: Last beacon: 5932ms ago
                    IE: Unknown: 00056F3244534C
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050C020300000000000000000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 06 - Address: 00:1A:2B:1E:51:E9
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"WLAN-1E5103"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008035decba88
                    Extra: Last beacon: 5357ms ago
                    IE: Unknown: 000B574C414E2D314535313033
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0E181AFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F1100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330E181AFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B0F1100000000000000000000000000000000000000
          Cell 07 - Address: 00:0B:3B:D5:D5:5E
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"devolo-000B3BD5D55E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002cce859f
                    Extra: Last beacon: 5085ms ago
                    IE: Unknown: 00136465766F6C6F2D303030423342443544353545
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160D070000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000007127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000B3B07000000
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340D070000000000000000000000000000000000000000
                    IE: Unknown: DD7D0050F204104A0001101044000102103B000103104700102880288028801880A880000B3BD5D55E102100066465766F6C6F10230015576972656C6573732041636365737320506F696E7410240005574C414E4E1042000831323334353637381054000800060050F204000110110003415053100800020086103C000101

eth0      Interface doesn't support scanning.

bond0     Interface doesn't support scanning.

```


But there is not nm runing.
How to can I check to see if the networkmanager app is in the apps?

thx in advance

---

### Post by theDaveTheRave on 2013-10-03
NewbieOld,

So those results say that the card is visible, and you have a number of wifi networks available.

on a side note I guess you are connected via the network card called ```
bond0
```, as it has an IP address. You have this running through a 'bonded' type (see the debian docs [here]("https://wiki.debian.org/Bonding") for more info.

from this page, can you post the output of
```

more /etc/network/interfaces 
[code]

It is possible that the bonding is attempting to link both the wifi and ethernet cards, which, from what I read, probably won't work (ie i haven't seen any docs that have this type of setup).

in terms of network manager, run the following from the command line
[code]
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome

```
and you will either get the network manager installed, and the notifier placed into your main panel notification area, or you'll get an error message saying that both the item are allready installed and on thier latest version, in which case you will likely find them in the menu, under system:administration (or similar), it all depends on which desktop you are using...

talking of which what desktop are you using? the above if for gnome, but if you use KDE you may want the KDE version so run
```

sudo apt-get install network-manager
sudo apt-get install network-manager-applet

```

Of course the above will depend on the presence of a notification area on your panel....

David

---

### Post by NewbieOld on 2013-10-03
Hi David,

please see at [http://ubuntuforums.org/showthread.php?t=2177633](http://ubuntuforums.org/showthread.php?t=2177633) for all network configs I have.

I found a lot of articels, blogs, etc. in the internet about bonding wlan0 and eth0.

the two packages about nm are already installed.

what can I do ???

thx in advance.

---

### Post by theDaveTheRave on 2013-10-03
NewbieOld,

OK I looked at your other thread.

I'm still not convinced that you can bond together a wired and wifi link.

but first you can ensure that network manager is in your stuff to start up at boot with the following

> 
I'm absolute beginner. I reinstall the network manager and found that nm-applet didn't show up in the notification area.

So, this is what I did and it worked for me.

1. Go to /usr/share/app-install/desktop and find Network Manager
2. Right click.. Properties.. copy the command line
3. Go to System.. Preferences.. Startup Applications and look for Network Manager
4. Click Edit and paste the command then save
5. Log out, log in

Command should be something like this
Code:

nm-applet --sm-disable


Hope it works for you. 

taken from this [thread]("http://ubuntuforums.org/showthread.php?t=1074132")

now after a reboot you should be OK for your wifi

Once you've done that you should be able to get to the network manager applet from the notification area, if however you don't have a notification area, have a quick search on how to add it, it may be different depending on your desktop.

If the above doesn't work... you can try the following, if you come up against a wall during any of the following, stop and drop a message here, and I'll see if I can help out.

I'm not sure how you  tell the bonded interface about the SSID of the wifi link, and the password, you can't place this in the network manager conf file directly.

However that said, a bit of a rummage has led me here....

Navigate to the ```
/etc/NetworkManager
``` directory from the command line, then once there do... 
```

ls -al

```
will give a list of the files / directories, it should look similar to this....
```

drwxr-xr-x 166 root root 12288 Oct  3 08:21 ..
drwxr-xr-x   2 root root  4096 May  1 20:44 dispatcher.d
drwxr-xr-x   2 root root  4096 Sep 14  2012 dnsmasq.d
-rw-r--r--   1 root root   107 May  1 18:05 NetworkManager.conf
drwxr-xr-x   2 root root  4096 Aug  6 20:51 system-connections
drwxr-xr-x   2 root root  4096 May  1 20:51 VPN

```

you now want to navigate to the system-connections directory, and again do a directory listing.
Here you should find that each connection that you have created will have a file that relates to that connection.
So I have a file for my home, and another for my wifi link at work, yet another for the wifi link at the Eurostar station in France... etc etc.
You should be able to identify your wifi link, if not creat a file with contents similar to the one below similar to the one below....

```

id=[COLOR="#00FF00"]wifiLinkID[/COLOR]
uuid=[COLOR="#00FF00"]002e894d-c22a-4dc3-92d4-b2cd30fd98c3[/COLOR]
type=802-11-wireless
timestamp=1361386880

[802-11-wireless]
ssid=[COLOR="#00FF00"]wifiLinkID[/COLOR]
mode=infrastructure
mac-address=[COLOR="#00FF00"]48:5D:60:B0:C8:BE[/COLOR]
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
psk=[COLOR="#00FF00"]yourpassword[/COLOR]

[ipv4]
method=auto
dns=8.8.8.8;
ignore-auto-dns=true

[ipv6]
method=auto

```

remember you will need to do this as the root / admin user... so ...
create the file
```

sudo touch /etc/NetworkManager/system-connections/wifiLinkID

```
this will create a blank file, which you can then open with a text editor (eg gedit)
```

gksudo gedit /etc/NetworkManager/system-connections/wifiLinkID

```

The items that are colloured green are required to be modified for your install. You will also need to create a new UUID using   [uuidgen]("http://linux.die.net/man/1/uuidgen") with this line of code in the terminal
```

uuidgen

```
Just duff this into the place for the UUID in the file above.

you should now be good to go, but remember to have the network manager run at startup as I said at the top

David

---

