---
title: "wireless card cannot connect"
date: 2016-09-12
forum: Networking &amp; Wireless
---

### Post by danielsender on 2016-09-12
Hi,

I just installed 16.04 on a Dell T3400. I had a vintage Ralink wireless card that lspci gives the following output:

**05:04.0 Network controller: Ralink corp. RT2600 802.11 MIMO**


Opening the wireless networks I can see all the SSIDs that are WPA2 encrypted, however my system does not connect to those that I have acces to. I searched for that issue and it appears that all solutions are quite old (e.g. circa 2008). Is there any more current way of solving the problem or I should go for a new card?

Thanks.

---

### Post by Bucky Ball on 2016-09-12
What is the output of this command (between code tags, please; link in my signature if you don't know how)?

```
sudo lshw -C network
```

When you say it doesn't connect to the networks you have access to, how doesn't it connect? Wheel keeps spinning on network manager? Connects then cuts off? Do you know the IP address of your router?

Give us a description of what happens when you try to connect to your network. You sound like you have a few available. Let's concentrate on one only for clarity.

---

### Post by danielsender on 2016-09-12
Hi,

Yes, it keeps spinning on the Network Manager. I installed myself the router so I know all the details, e.g. my IP is 192.168.2.1 (WPA2) - Below is the output of **lshw** command:
```
  *-network       description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 02
       serial: 00:1d:09:30:0e:9a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5754-v3.24 ip=192.168.2.71 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:31 memory:fe7f0000-fe7fffff
  *-network
       description: Wireless interface
       product: RT2600 802.11 MIMO
       vendor: Ralink corp.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: wlp5s4
       version: 00
       serial: 00:14:a5:da:02:8a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=4.4.0-36-generic firmware=0.8 latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:fe6f8000-fe6fffff
```

Thank you very much.

PS I edited, I made a mistake a wrote the output from another machine.

Daniel

---

### Post by wildmanne39 on 2016-09-12
Please do:
```
echo "options rt61pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt61pci.conf
sudo modprobe -rfv rt61pci
sudo modprobe -v rt61pci
```
then if you still can not connect run the wireless script in my signature and post the file here, there war directions at that link for running it without an internet connection if you need them.

---

### Post by danielsender on 2016-09-12
Man, you're a champ, after rebooting it started working.

Thank you very much.

---

### Post by danielsender on 2016-09-12
Sorry, it did connect right after rebooting but it was very slow and after got disconnected. I couldn't connect again unless I rebooted the machine that in turn repeated the behaviour. I'm attaching the wireless-info.tar.gz file.

Thanks again.
[ATTACH]271133[/ATTACH]

---

### Post by wildmanne39 on 2016-09-12
There may not be a lot we can do for speed with that device and ubuntu drivers but we will try first we are going to remove the extra driver you have loading that you do not need please do:
```
echo "blacklist rtl8187" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Now let's turn power management off:
```
sudo -H gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlp5s4 power off
```

above exit0, then save gedit, close.

Go into your router settings and make sure your router is set to 802.11bg then save the settings.

Please do:
```
sudo su 
echo rt61pci >> /etc/modules 
exit
```

Make sure your wired connection is unhooked before you reboot and if it connects please run the wireless script again so I can see the settiings while it is connected if it does not connect tell me the name of the network you want to connect too.
Reboot Thanks

---

### Post by danielsender on 2016-09-12
This time it didn't connect right after boot (no ethernet cord connected) - In this case I want to connect to "vivaldi", however I will later move the machine to another site.

Thanks for your time.

Daniel

[ATTACH]271137[/ATTACH]

---

### Post by danielsender on 2016-09-12
after a few minutes it did connect but is taking 20,000msec between ping packets to the router that is only 6 metres away!

---

### Post by Bucky Ball on 2016-09-12
Have you got the wireless card's power management off? Run 'iwconfig' and check. If on, switch off by using Wild Man's instructions from where it says:

[QUOTE=Wild Man]Now let's turn power management off[/QUOTE]

... if you haven't already.

---

### Post by wildmanne39 on 2016-09-12
The power management did not turn off we will look into it further in a little while.

Go into your router and change the channel to 1, take it off auto, to many people on the same channel as you and they have better signal so you are trying to connect to there network.

I made a mistake I have the wrong wifi name that is why power management is still on, I am going to correct the name in the previous post so give me about five minutes then open that file again and change the name then save,close and reboot.

---

### Post by danielsender on 2016-09-12
yeah, iwconfig says that power management is on, I think what happened is that I copied and paste your instructions but my interface is not "**wlan0**" as you wrote but "**wlp5s4**", right?

---

### Post by wildmanne39 on 2016-09-12
Exactly I fixed it, it is hard to get it to stay off sometimes.

---

### Post by danielsender on 2016-09-12
after correcting the file, iwconfig says that the power management is still on

---

### Post by Bucky Ball on 2016-09-12
> **Wild Man said:**
> Exactly I fixed it, it is hard to get it to stay off sometimes.

+1.

---

### Post by wildmanne39 on 2016-09-12
Is it working after changing the channel?

---

### Post by danielsender on 2016-09-12
I have the router on channel 5 and all the other entries are bridge repeaters.

[ATTACH=CONFIG]271138[/ATTACH]

---

### Post by wildmanne39 on 2016-09-12
So this other network that has a stringer signal then yours is not an issue like it appears to be? I imagine your wifi is roaming back a forth continually.
```
Cell 03 - Address: <MAC 'vivaldi' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"vivaldi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000569d4b9860
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'grieg' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"grieg"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000001fd92183
                    Extra: Last beacon: 880ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```

---

### Post by danielsender on 2016-09-13
In the survey I posted all the routers in the house are on the same channel as the router on AP mode and working as bridge repeaters. I have other computers that have no problems connecting to all these ssid's, so I don't think is an issue related to the channel.

---

### Post by wildmanne39 on 2016-09-13
Okay, I could not read the small print of the survey you posted that is why I asked.

I will take another look tomorrow it is late here, but I can tell you that router settings impact the way linux drivers connect and work remember we do not have venders making drivers for us we have to backwards engineer them in most cases.

---

### Post by danielsender on 2016-09-13
I appreciate the effort and great attitude that the people on the forum have.

Good night.

---

### Post by danielsender on 2016-09-13
I did a bit of characterization of the behaviour of the card, here it goes.

After a long time connects to the desired SSID. I fired **ping** to the router and if I let it go for enough time so the system's power savings kicks in, that is the monitor becomes dark, the pinging seems OK, that is about 2ms to the router. However as soon as I move the mouse, so the monitor goes up again the pinging goes up to 20000ms for a few packets and after it stops and I start getting a ping response "**ping: sendmsg: No buffer space available**".

I don't know if this is useful in the context of the driver.

---

### Post by wildmanne39 on 2016-09-13
Please do:
```
sudo echo 83886080 > /proc/sys/net/core/wmem_max
```
Reboot
let us know how it is working, there may be another driver parameter we can try.

---

### Post by Bucky Ball on 2016-09-13
This is a bit out of left-field and I know it might sound a bit bizarre, but are you using a wireless keyboard/mouse combo and 16.04 LTS? If so, could you possibly try a *wired* keyboard, USB or PS2, doesn't matter, and see what happens with wifi then, please?

---

### Post by danielsender on 2016-09-13
It didn't work, is not connecting.

---

### Post by danielsender on 2016-09-13
sorry, I didn't see your question about the wireless keyboard/mouse - yes indeed, I'm using these. however I don't have at the present time a wired keyboard (yes a mouse) - but when I plug an USB wireless adapter (netgear) it works flawlessly.

---

### Post by wildmanne39 on 2016-09-13
I still believe it is roaming between your repeaters, please pick the one you are closest too or has the strongest signal and use network manager to set an explicit mac address, the following command will show you the addresses.
```
sudo iwlist scan
```
If you need help with that just let us know.

Edit:
Are you using a vpn connection I see [COLOR="#FF0000"]tun[/COLOR] please make sure your wired connection is unplugged it will always override the wireless connection.

---

### Post by danielsender on 2016-09-14
Whenever I tried one of the suggestions I had the ethernet cable disconnected. I'm using a VPN service (logmein). I tried with the main router (SSID = vivaldi) and also another one that is closest to the machine (SSID = discepolo).
```
lo        Interface doesn't support scanning.

wlp5s4    Scan completed :
          Cell 01 - Address: 00:1C:10:27:B7:79
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"vivaldi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002914ca14c
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 0007766976616C6469
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020AF1000000
          Cell 02 - Address: 02:26:5A:C5:00:E8
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"bach"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000291375aae
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000462616368
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: DD180050F2020101000003A4400027A4000042435E0062322F00
          Cell 03 - Address: 10:C3:7B:D3:12:18
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"gardel"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002912d927e
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 000667617264656C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 46053208010000
                    IE: Unknown: 7F0104
                    IE: Unknown: DD090010180200000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:1C:10:AD:9D:05
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"discepolo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000290fce98a
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 00096469736365706F6C6F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:21:29:D3:23:D7
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"grieg"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000291053a45
                    Extra: Last beacon: 24ms ago
                    IE: Unknown: 00056772696567
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180204F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: E8:8D:28:5F:A0:17
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ELIJAH's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002d8720de8e3
                    Extra: Last beacon: 18584ms ago
                    IE: Unknown: 0016454C494A414827732057692D4669204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027E9D
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301740320
                    IE: Unknown: DD0E0017F20700010106E88D285FA017
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 07 - Address: 44:E1:37:48:4E:10
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"ATT824"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002525398621f
                    Extra: Last beacon: 1060ms ago
                    IE: Unknown: 0006ham0      Interface doesn't support scanning.


enp4s0    Interface doesn't support scanning.


415454383234
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: FA:8F:CA:31:9B:01
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002912d8140
                    Extra: Last beacon: 2052ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 05050102000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C0103FF000000000000000000000000000000000008E0E10900
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1605000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00



```

---

### Post by wildmanne39 on 2016-09-14
Try connecting with the vpn off, I have vpn on my laptop and it had some issues with 16.04 and even now sometimes the vpn has to be turned off for me to connect.

---

### Post by danielsender on 2016-09-14
I tried with VPN off (no **ham0** on ifconfig) but unfortunately it didn't work. I guess I should be going to get another card, don't you think?

---

### Post by wildmanne39 on 2016-09-14
I would hate to see you buy a new wireless card and still have the same trouble, did you successfully set your mac address?

Please run the wireless script again so we can get a look at the settings after the changes have been made, and please do not change anything back until we are done.
Thanks

---

### Post by wildmanne39 on 2016-09-14
Your driver is throwing out errors and it needs replaced, I am having trouble finding the backported driver in ubuntu at the moment so it may take a little time to locate it.

---

### Post by jeremy31 on 2016-09-14
See if [http://askubuntu.com/a/818415/300665](http://askubuntu.com/a/818415/300665) helps to get power management disabled, replace wlan0 with wlp5s4 and it may help to increase the sleep time

---

### Post by wildmanne39 on 2016-09-14
I finally found the driver after several hours of looking for it today and I compiled it on my computer without any errors but I do not have the device to test it to see if the bug is corrected in this version of the driver but in most cases I have seen the backported driver usually works.

Please copy all commands one line at a time for accuracy while watching fr errors:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
Then download the driver and drag it to your desktop then right click and extract here:
```
cd ~/Desktop/backports-20160324
make defconfig-wifi
make
sudo make install
```
Reboot
If you have a kernel update you will have to recompile the driver again.
```
cd ~/Desktop/backports-20160324
make clean
make defconfig-wifi
make
sudo make install
```
These directions will actually compile all wireless drivers in the backport drivers file it takes longer but will not hurt anything.
Please let us know if this new driver fixes your issues.

---

### Post by danielsender on 2016-09-15
Just to summarize the current status, this is the behaviour: the network manager seems to show every existing network, when I click on one it stays "rolling" for a long time, maybe hours and finally it connects. However the connection is extremely slow - and also disconnects and goes back to the initial situation.

---

### Post by Bucky Ball on 2016-09-15
> **danielsender said:**
> Just to summarize the current status ...

Please summarize whether you followed posts 33 and 34 and describe what happened. Is power management off yet??? Did the driver Wild Man dug up for you do anything? Could you get it installed ok? 

We can't give you much help if you don't respond to instructions and let us know what happened ... Thanks. ;)

---

