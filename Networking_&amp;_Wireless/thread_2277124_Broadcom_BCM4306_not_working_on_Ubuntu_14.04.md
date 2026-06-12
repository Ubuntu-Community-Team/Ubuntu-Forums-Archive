---
title: "Broadcom BCM4306 not working on Ubuntu 14.04"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by truetech08 on 2015-05-06
I'm at a loss here, hoping someone can help. I have an old Dell Inspiron 5100 with a Broadcom BCM4306 wireless chipset, which is not working. Clicking on the wireless icon at the top shows "No network devices available." Out put for lshw -c network shows the device, and for "configuration" it says "driver=b43-pci-bridge latency=32" (sorry for no copy-paste of output, the wired isn't working either, so I can't post from the same machine). 

 Output of lspci -nnk | grep -iA2 net is "Kernel driver in use: b43-pci-bridge. This device has an ID of [14e4:4320]. So as far as I can tell from posts online, that is the correct driver. However, ifconfig -a shows no wlan0 entry, so I'm guessing that has something to do with it. What am I missing here?

Please remember, I don't have internet on the machine in question, so posting output is difficult, and I'll have to copy installation packages over manually. I'm not very familiar with Linux, so step-by-step commands will be needed.

Thanks!

---

### Post by chili555 on 2015-05-06
Please check the message log to see if firmware is missing:```
dmesg | grep b43
```If that is the case, here are instructions to get it without an internet connection: [http://ubuntuforums.org/showthread.php?t=2208644&p=12944001#post12944001](http://ubuntuforums.org/showthread.php?t=2208644&p=12944001#post12944001)

---

### Post by truetech08 on 2015-05-07
Thanks, output says 

Direct firmware load failed with error -2
Falling back to user helper

Says this four times, then:

Firmware file "b43/ucode5.fw" not found
Firmware file "b43-open/ucode5.fw" not found

Then tells me to go to a website to download correct firmware. I'll follow your link to instructions and give it a shot, then post back with results.

---

### Post by pgaboria on 2015-05-07
Loading drivers for wifi
1. Menu->Administration->Synaptic PackageManager->in search window type in BCM
and check the driver installer for b43-fwcutter and check thedriver firmware-b43-installer, then
apply to download these two items.
 
2. May have to use the Driver Manager.
 
3. If the commands show proper driver for mine it was b43 forwireless BCM4318 chip set.
 
phil@phil-Pavilion-dv8000-EZ590UA-ABA ~ $ rfkill list all
0: phy0: Wireless LAN
            Softblocked: no
            Hardblocked: no   
1: hp-wifi: Wireless LAN
            Softblocked: no
            Hardblocked: no   **(Not Hard blocked showsthat the on/off switch is in the on position).**
phil@phil-Pavilion-dv8000-EZ590UA-ABA ~ $ sudo lshw -c network
[sudo] password for phil:
  *-network:0             
       description:Network controller
       product: BCM4318[AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: BroadcomCorporation
       physical id: 2
       bus info:pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities:bus_master
       **configuration:driver=b43-pci-bridge latency=64**
       resources:irq:21 memory:c0204000-c0205fff
  *-network:1
       description:Ethernet interface
       product:RTL-8139/8139C/8139C+
       vendor: RealtekSemiconductor Co., Ltd.
       physical id: 6
       bus info:pci@0000:06:06.0
       logical name:eth0
       version: 10
       serial: 00:16:d4:3c:34:17
       size: 10Mbit/s
       capacity:100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pmbus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fdautonegotiation
       configuration:autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MIIspeed=10Mbit/s
       resources:irq:22 ioport:a000(size=256) memory:c020a400-c020a4ff
  *-network
       description:Wireless interface
       physical id: 3
       logical name:wlan0
       serial:00:14:a5:bd:c9:14
       capabilities:ethernet physical wireless
       configuration:broadcast=yes driver=b43 driverversion=3.11.0-12-generic firmware=666.2ip=192.168.1.10 link=yes multicast=yes wireless=IEEE 802.11bg
phil@phil-Pavilion-dv8000-EZ590UA-ABA ~ $
 
4. If the above is good and the wireless adapter is not onthen issue the following two commands.
 
sudo modprobe -r b43 ssb
sudo modprobe b43
 
5. If the wireless adapter comes on and works, connect to theinternet to check it out.
 
6. To have the wireless adapter start when booting up do thefollowing.
 
   Issue thesecommand         ** cd /etc**      then **pwd** to check that you are inthat directory. Then issue the following command  **sudo gedit modules**  this is an editor add below the last entry ** b43  **thensave exit
the file then Menu select the Power down button to shut thepc down.
When you power up this time the wireless adapter should beon.

---

### Post by truetech08 on 2015-05-07
Ok, following chili555's instructions, I got the firmware installed and the wireless adapter immediately started detecting networks. (so far so good) When I tried to connect to my network, it requested the WPA password, which I entered correctly, then it tries to connect (wireless icon is animated), but after 15 or 20 seconds, a notification "Disconnected - you are now offline". So it never actually connects.

After the wireless started working, I reenabled the Ethernet port in BIOS and rebooted, then checked the driver for that as well. It is the Broadcom BCM4401 rev 01 using the b44 driver, and firmware appears to be installed (checked using dmesg as instructed above, replacing b43 with b44). I get the same behavior when connecting a network cable...tries for 15 or 20 secs, then the disconnected notification. Any ideas on that? Thanks for all the help so far.

---

### Post by chili555 on 2015-05-07
Please run:```
sudo iwlist wlan0 scan
```Show us the scan result for just your own network and disguise the MAC address like this:> Cell 04 - Address:[COLOR="#FF0000"]XXXX[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c7c0af50a1
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A2C1917FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B081600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500000000000040
                    IE: Unknown: DD090010180201000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057200010000

---

### Post by truetech08 on 2015-05-08
Ok, thanks, results are below. The redacted SSID is my wireless network. EDIT: I have tried making the network completely open with no authentication as well.

wlan0     Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"XXX-REDACTED-XXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000050fda8b0c
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 00144269676773576972656C6573734E6574776F726B
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001B00000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000

---

### Post by chili555 on 2015-05-08
> Group Cipher : TKIPI suggest changing to WPA2-AES. Many drivers have difficulty connecting to TKIP and, moreover, it is less secure than AES: [https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol](https://en.wikipedia.org/wiki/Temporal_Key_Integrity_Protocol)>  TKIP is no longer considered secure and was deprecated in the 2012 revision of the 802.11 standard.

---

### Post by truetech08 on 2015-05-08
Amazingly (to me), that actually worked, I had my router set to "WPA or WPA2", with "AES or TKIP" both, and after I set it to WPA2 only mode with AES, the thing immediately connected. Thank you so much!

Any idea why the wired network also does the disconnect? Is there a command I can run for that to show you what you need to give me more magic?? :-) If not, no big deal, I'm happy I have access!

---

### Post by chili555 on 2015-05-08
I suggest you start a new thread concerning the ethernet. 

I'm glad the wireless is working!!

---

### Post by truetech08 on 2015-05-09
Will do, thanks again!

---

