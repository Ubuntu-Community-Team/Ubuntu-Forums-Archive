---
title: "Atheros ar928x working..."
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by a3qp on 2008-08-19
Hi,

After 10 days of hard work and headaches, I got my Atheros ar928x wireless card working. I hope this thread can help others:

Summary:
- I have an Atheros ar928x wireless card (see below for "lspci" output), and I got it working by doing what Volanin says in post #5 in the thread
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097). It worked for me in 32bit and now in amd64.

Long story:
(some people may identify with me or have similar problems).

My new laptop PC is a Sony Vaio SR129E/B, bought 3 weeks ago, in Newegg.
In the specifications of the seller's webpage, and on Sony's webpage, it didn't specify the exact model of the Atheros wireless card.
([official Sony page of the laptop]("http://b2b.sony.com/Solutions/product/VGN-SR129E/B") ). The only way to find it was by looking in the "device manager" of
windows vista, right-clicking the card and selecting properties.

When I typed in the terminal:
```
lspci -nn
```

the output for my wireless card was:

```
05:00.0 Network controller [0280]: Atheros Communications Inc. Unknown device [168c:002a] (rev 01)
```

and this command:
```


lshw -C Network


```

gave:

```

*-network UNCLAIMED
description: Network controller
product: Atheros Communications Inc.
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:05:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0

```

I had installed Ubuntu 8.04, amd64.

I tried using ndiswrapper many times. I used the Windows drivers installed on the Vista partition of my PC; they didn't work. I then tried downloading Windows drivers from:

[http://www.laptopvideo2go.com/forum/index.php?showtopic=14858](http://www.laptopvideo2go.com/forum/index.php?showtopic=14858)
then from: [http://birseyindir.org/driver/Atheros_AR5xxx_Series_Wir___27005.html](http://birseyindir.org/driver/Atheros_AR5xxx_Series_Wir___27005.html)
and finally from: [http://www.atheros.cz/download.php?atheros=AR928X](http://www.atheros.cz/download.php?atheros=AR928X)

None worked, and ndiswrapper spammed dmesg with errors trying to load the Windows driver, athrx.inf.

I downgraded my Ubuntu to 32-bit, hoping that ndiswrapper would work better there, but got the same errors as I had on 64-bit. I also compiled ndiswrapper from source, to no avail.

Finally, with the link that I mentioned in the summary above, I got the card working using the ath9k drivers, which were just released in July 2008 (and should support all Atheros ar9xxx chipests). And as it worked perfectly, I decided to return to my 64-bit version (which I had compromised in the hope of getting the wireless card working), and it also ran smoothly. 

Great!

Special thanks to [**_pytheas22_**]("http://ubuntuforums.org/member.php?u=358340") for his patience, generosity, since he led me in this process, and never lost hope!

---

### Post by AggieJAG on 2008-09-07
I can't get my AR928x wireless card working...

**System**
Sony Vaio FW139E
Atheros AR928x wireless
Intel Core Duo P8400 @ 2.26GHz
3Gb of RAM
ATI Mobility Radeon HD 3400 series graphics

Here's the problem... I don't have access to an hardline ethernet connection, only wireless.  I'm in Rhode Island for training until mid-October and I've searched around and there isn't anywhere to plug in directly in order to d/l dependent packages for madwifi or ndiswrapper, etc.  I've tried to install them, but there's always an error re: a dependent package.

Can anyone suggest a solution where I can figure out which packages i need, download them in Vista and then migrate them over to Ubuntu? 

Thanks in advance!
~AggieJAG

---

### Post by pytheas22 on 2008-09-12
> Can anyone suggest a solution where I can figure out which packages i need, download them in Vista and then migrate them over to Ubuntu?

You can download individual packages from [http://packages.ubuntu.com](http://packages.ubuntu.com).  So find the packages for whichever dependencies it says you need and install them manually that way.

I didn't think that the packages for the ath9k driver should have dependencies, though.  How did you try to install the driver?  Did you download one of the Debian packages from the links in [this thread]("http://ubuntuforums.org/showpost.php?p=5545069&postcount=5")?  Are you sure you're using the kernel that those packages were built for (2.6.24-19-generic)?  You may be trying to do something that's more difficult than it needs to be...

---

### Post by Mgiacchetti on 2008-09-29
you know guys i'm still having trouble with my ar9280...

Signal is horrible, jumps around constantly, cant surf the web without waiting like dialup..


```

  *-network               
       description: Wireless interface
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

``````

03:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002a] (rev 01)

```
```

ping 192.168.1.1 -c 25

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.109 icmp_seq=1 Destination Host Unreachable
From 192.168.1.109 icmp_seq=2 Destination Host Unreachable
From 192.168.1.109 icmp_seq=3 Destination Host Unreachable
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=8.21 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.871 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=0.865 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=0.872 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=0.833 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=0.868 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=0.851 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=0.856 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=2.11 ms

--- 192.168.1.1 ping statistics ---
25 packets transmitted, 9 received, +3 errors, 64% packet loss, time 24029ms
rtt min/avg/max/mdev = 0.833/1.816/8.219/2.297 ms, pipe 3

```
```

wlan0     IEEE 802.11bgn  ESSID:"TopTobo"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: --its there i just edited it here--
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:-----------   Security mode:open
          Power Management:off
          Link Quality=90/100  Signal level:-37 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````

 uname -a
Linux ubuntu 2.6.27-3-generic #1 SMP Wed Sep 10 16:02:00 UTC 2008 i686 GNU/Linux

```

---

### Post by pytheas22 on 2008-09-29
Mgiacchetti,

I'm not sure what's wrong, but here are a few things to check:

1. your bit rate is set to the lowest possible value.  Does it make any difference if you type:
```

sudo iwconfig wlan0 rate 54M
```

2. which mode is your router operating in (b, g, n)?  There may be issues with n mode, and switching back to g might help.

3. does it make a difference if you turn off encryption on your router?

4. if you post the output here of the command:
```

dmesg | grep -e ath -e wlan
```

there may be some useful information that would help to track down the source of the problem.

It seems to think that your signal strength is great (90%), so that's not the issue, but there is a huge amount of packet loss.  This card definitely works in other operating systems, right?  How did you install the ath9k driver?  If you compiled from svn source, it's possible that you just happened to get a buggy build, and that reinstalling would help.  Also, if possible, you may want to try connecting to a different wireless network, as the problem could be your wireless router.

---

### Post by AlexH76 on 2008-10-02
Many thanks for fixing the driver. I'm on an Asus x71a and (as final step) had to follow instructions in [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=930667") to get wlan activated.

---

### Post by natts on 2009-02-13
Hi!
I have sony vaio sr with the same card and i'm runing opensuse linux 11.1. 
The problem is at first, suspend was not working at all. It's kinda normal, using s2ram -f -p -m solved the problem, but after my laptop wakes up, no wireless networks are found. 
rcnetwork restart doesn't do the trick, so wifi trigger doesn't. 

Didn't try to modprobe -r and modprobe again the driver. I will inform u, if i'll get any success. 
The driver is ath9k. So... howto solve? anyone?

---

### Post by pytheas22 on 2009-02-13
> Didn't try to modprobe -r and modprobe again the driver. I will inform u, if i'll get any success.
The driver is ath9k. So... howto solve? anyone?

Removing and reinserting ath9k with modprobe would probably fix the problem.  You could write a script to do that automatically whenever the computer wakes back up, but I don't know how to do that in SUSE.  I'm sure you could figure it out without too much work, however.

---

### Post by rawloz on 2009-03-23
Try changing your encryption to AES it just worked for me...300Mbps sweet

---

### Post by hwfa on 2009-06-28
> **pytheas22 said:**
> You can download individual packages from [http://packages.ubuntu.com](http://packages.ubuntu.com).  So find the packages for whichever dependencies it says you need and install them manually that way.

<snip>


Errm. The link takes me to a completely blank page ????

---

### Post by hwfa on 2009-06-28
> **a3qp said:**
> Hi,

After 10 days of hard work and headaches, I got my Atheros ar928x wireless card working. I hope this thread can help others:

Summary:
- I have an Atheros ar928x wireless card (see below for "lspci" output), and I got it working by doing what Volanin says in post #5 in the thread
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097). It worked for me in 32bit and now in amd64.

<major snip>


Volanin's post now says:
#####################################
OUTDATED!!!
Check the new instructions here!
#####################################

The word "here" is a link to 
[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3)

which says "This is OLD and OBSOLETE. Please don't use it!" underlined and in huge red letters.

Help!

Please.

I have a new Acer Aspire 5738 with the AR928X WiFi adapter. Windows Vista (came on the machine) finds my LAN immediately but I really want to get it working on Ubuntu. The "Ubuntu" machine has *no* internet access unless it can use that wireless connection so I can't do anything like "apt get ...". I'll have to download something via a different (wireless, Windows) machine, copy it to a USB stick and copy from that into Ubuntu. Or use Ubuntu to copy from Vista's file system after downloading via Vista on the Acer.

How, please?

---

### Post by pytheas22 on 2009-06-28
hwfa: please post the output of these commands so I can have a better idea of your situation:
```

lspci -nn
lshw -C Network
uname -rm
sudo iwlist scan
dmesg | grep -e ath -e wlan
```

You can save the output of the commands into a text file (Applications>Accessories>Text Editor) and either transfer that file into Windows using a USB drive or CD, or save it directly to your Windows file system from Ubuntu (you can open the Windows partition under the Places menu).  That should make it easier to upload the output here.

---

### Post by hwfa on 2009-06-29
> **pytheas22 said:**
> hwfa: please post the output of these commands so I can have a better idea of your situation:
```

lspci -nn
lshw -C Network
uname -rm
sudo iwlist scan
dmesg | grep -e ath -e wlan
```

You can save the output of the commands into a text file (Applications>Accessories>Text Editor) and either transfer that file into Windows using a USB drive or CD, or save it directly to your Windows file system from Ubuntu (you can open the Windows partition under the Places menu).  That should make it easier to upload the output here.

Please everybody accept my apologies for wasting your time. I was running from a live CD and had been advised that if this couldn't find my wLan then a real installation wouldn't either. Turns out this is not true. I took the plunge and installed Ubuntu Intrepid Ibex and, of course, it found my WLan immediately. It even retains the connection after hibernation.

So, thanks for the help and patience and, once more, sorry.

---

### Post by pytheas22 on 2009-06-29
> **hwfa said:**
> So, thanks for the help and patience and, once more, sorry.

Not a big deal; glad to here you've sorted it out.  It actually is a bit surprising that your wireless didn't work on the live CD but works fine on a real installation--that doesn't make too much sense--but if it works, so much the better.

---

### Post by geruetzel on 2009-07-25
hi, i am having troubles with my atheros card as well (ar928x).
the signal of my router is really bad when i connect, the net is very slow and the connection dies very often (even when i sit next to the router) on my other laptop it works well.
i have tried different things which all did not work for me:

*installing the win drivers with ndiswrapper
*802.11G only (no n)
*encryption off
*rate 54M

here's all information:

ubuntu 9.04
kernel 2.6.28-11-generic i686

```
4:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

``````
  *-network             
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:5f:87:78:e8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn

``````
wlan0     Scan completed :
          Cell 01 - Address: 00:22:B0:8C:C3:55
                    ESSID:"brunnernet"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=65/100  Signal level:-78 dBm  Noise level=-120 dBm
                    Encryption key:on
                    IE: Unknown: 000A6272756E6E65726E6574
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030107
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010020FF7F
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000004f518f58
                    Extra: Last beacon: 64ms ago
``````
~$ dmesg | grep -e ath -e wlan
[    3.860312] device-mapper: multipath: version 1.0.5 loaded
[    3.860314] device-mapper: multipath round-robin: version 1.0.0 loaded
[   10.419714] ath9k: 0.1
[   10.419753] ath9k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.419764] ath9k 0000:04:00.0: setting latency timer to 64
[   10.855757] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.887520] Registered led device: ath9k-phy0:radio
[   10.887535] Registered led device: ath9k-phy0:assoc
[   10.887551] Registered led device: ath9k-phy0:tx
[   10.887565] Registered led device: ath9k-phy0:rx
[   44.537647] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   60.698012] wlan0: authenticate with AP 00:22:b0:8c:c3:55
[   60.712319] wlan0: authenticated
[   60.712323] wlan0: associate with AP 00:22:b0:8c:c3:55
[   60.719778] wlan0: RX AssocResp from 00:22:b0:8c:c3:55 (capab=0x431 status=0 aid=2)
[   60.719781] wlan0: associated
[   60.742798] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   70.952098] wlan0: no IPv6 routers present
[  110.703465] wlan0: No ProbeResp from current AP 00:22:b0:8c:c3:55 - assume out of range
[  113.605093] wlan0: authenticate with AP 00:22:b0:8c:c3:55
[  113.613259] wlan0: authenticate with AP 00:22:b0:8c:c3:55
[  113.812171] wlan0: authenticate with AP 00:22:b0:8c:c3:55
[  114.012151] wlan0: authenticate with AP 00:22:b0:8c:c3:55
[  114.212183] wlan0: authentication with AP 00:22:b0:8c:c3:55 timed out
[  129.600407] wlan0: authenticate with AP 00:22:b0:8c:c3:55
[  129.601935] wlan0: authenticated
[  129.601940] wlan0: associate with AP 00:22:b0:8c:c3:55
[  129.605004] wlan0: RX AssocResp from 00:22:b0:8c:c3:55 (capab=0x431 status=0 aid=2)
[  129.605009] wlan0: associated

```

---

### Post by kungfoofool on 2009-07-26
I'm having the same issue as geruetzel. I've got an ASUS K40A1-IN with a similar setup and while it's booted into Vista there are no problems connecting to the wireless AP. In Ubuntu 9.04, the connection unexpectedly drops and occasionally will not connect at all. Occasionally it does connect, and I can't determine what causes the oddity.

The AP has no encryption, does not filter by MAC, etc.

---

### Post by pytheas22 on 2009-07-26
geruetzel and kungfoofool: recompling the wireless driver using a more recent version of the source code may help you.  To do that, go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2."  Save it to your desktop.  Then run these commands:

```
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Then reboot and please let me know if it helps.  If not, we can try other things.

---

### Post by geruetzel on 2009-07-27
thank you, but as i had problems with my ati-card/chip too (which really were unsolveable) i decided to install vista again. this decision was not easy but everything works fine now.

---

### Post by kungfoofool on 2009-07-27
pytheas22:

I ran into the following after running sudo make load:
```

Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwlagn...
Loading ath...
FATAL: Module ath not found.
Loading ar9170usb...
FATAL: Module ar9170usb not found.
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Loading mwl8k...
FATAL: Module mwl8k not found.
Loading mac80211_hwsim...
FATAL: Module mac80211_hwsim not found.
Loading at76c50x_usb...
FATAL: Module at76c50x_usb not found.
./scripts/load.sh: line 20: athload: command not found
./scripts/load.sh: line 22: b43load: command not found
make: *** [load] Error 127

```

I went ahead & ran make install to see what would happen, and it's doing pretty much the same thing. Here's the log from /var/log/wpa_supplicant.log:

```

Failed to disable WPA in the driver.
Failed to initiate AP scan.
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
CTRL-EVENT-SCAN-RESULTS 
Trying to associate with 00:09:5b:d5:1f:9c (SSID='tankgroup' freq=2442 MHz)
Association request to the driver failed
Authentication with 00:09:5b:d5:1f:9c timed out.

```

dmesg doesn't give much useful information:
```

[   55.806971] wlan0: deauthenticating by local choice (reason=3)
[  112.712036] wlan0: deauthenticating by local choice (reason=3)

```

lspci:
```

05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

lshw:
```

           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: ***
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

```

I appreciate your help. Any other advice?

---

### Post by kungfoofool on 2009-07-27
I turned WEP 128-bit encryption back on, and now it connects without a problem. In find that puzzling, but at this point I'm just happy not to be tethered.

Another oddity is that I haven't had this problem with other AP's, (e.g., coffee cafes), so maybe it was something weird about the access point? Heck if I know.

---

### Post by pytheas22 on 2009-07-27
geruetzel: I'm sorry to hear you had to go back to Vista, but I understand.  If you ever want to give Ubuntu another try, I'm still happy to help you figure out the wireless.  I'm less experienced dealing wth video issues, but I'd help you with the ATI problems as best I can, too.

kungfoofool: it's strange that things work WEP enabled, but it could have to do with your access point being strange, as you mention.  If other APs work fine, I would suspect something odd about your configuration solving the problem.  Of course, if the connection works fine in Windows, it should also work fine in Ubuntu, but if you're satisfied with the situation now, we should probably leave well enough alone.

(Otherwise, the next thing I'd suggest is to try ndiswrapper, which I know gerueztel already tried, but unless the Atheros modules were blacklisted, ndiswrapper would not have taken effect.)

---

### Post by kungfoofool on 2009-07-28
I guess I'll have to use ndiswrapper, because now I'm back to square one. It seems to randomly be able to connect just fine, and then later it'll drop and I can't reconnect at all (now I've seen the same thing occur with other APs).

It appears that others [are having similar problems]("http://ubuntuforums.org/showthread.php?t=1205318").

Edit:
After compiling the driver, I'm now having issues with dropped packets (avging about 50% packet loss) and it appears that attempting to connect is even worse than it was.

---

### Post by pytheas22 on 2009-07-28
kungfoofool: sorry to hear about the regression.  ndiswrapper will hopefully work with less hassle.  To get ndiswrapper working, you need the Windows wireless driver for your card.  If you could post a link to the driver that you used (or upload the .exe or .zip file if it came on a CD), that would be great.  If not, please post the output of this command so I'll at least know what kind of chipset you use and can try to find a Windows driver online:
```

lspci -nn | grep -i atheros
```

I also need to know whether you use 32- or 64-bit Ubuntu.  If you don't know, post the output of:

```
uname -m
```

---

### Post by calle#52 on 2009-07-29
Hi,

I'm experiencing the same problem on my Dell (Studio XPS 13). The command above gave the following:

lspci -nn | grep -i atheros
06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

lshw -C Network
description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:5f:99:32:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn

uname-rm
2.6.28-14-generic x86_64

sudo iwlist scan
wlan0     Interface doesn't support scanning.

dmesg | grep -e ath -e wlan
[    4.308251] device-mapper: multipath: version 1.0.5 loaded
[    4.308252] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.658860] ath9k: 0.1
[   11.658882] ath9k 0000:06:00.0: PCI INT A -> Link[Z016] -> GSI 21 (level, low) -> IRQ 21
[   11.658889] ath9k 0000:06:00.0: setting latency timer to 64
[   12.092296] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.112279] Registered led device: ath9k-phy0:radio
[   12.112306] Registered led device: ath9k-phy0:assoc
[   12.112331] Registered led device: ath9k-phy0:tx
[   12.112359] Registered led device: ath9k-phy0:rx
[   17.725026] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  388.069680] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  545.697696] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  545.838692] ADDRCONF(NETDEV_UP): wlan0: link is not ready


Hope this gives you an idea about what's wrong :-)

---

### Post by pytheas22 on 2009-07-29
calle#52 and kungfoofool: please disregard what I've written above about ndiswrapper.  I read through this thread again (which was started about a year ago), remembered what I went through with the original poster then, and recalled that ndiswrapper won't work for this type of wireless card (unless things have changed since last summer).

However, what we do successfully do to get the original poster's card working was to run these commands:

```
sudo apt-get update
sudo apt-get upgrade
```

Now reboot your machine.  When it's done, continue by typing:

```
wget http://burnthesorbonne.com/files/compat-wireless-ath9k-20080916.tar.gz
tar -xzvf compat-wireless-ath9k-20080916.tar.gz 
sudo ./compat-wireless-ath9k-20080916.sh
```

At this point a shell script will run that will help you compile a new wireless driver based on the code that worked a year ago.  Follow the instructions on the screen for getting it set up.  When it's finished, run:

```
sudo dpkg --install compat*deb
```

Then reboot, and see if things work better.  Hopefully this will do it.

---

### Post by calle#52 on 2009-07-30
pytheas22: Thanks for the swift reply :-)

Just one question before I try your solution: Why is it that you would recomend the 20080916 build? If I'm not mistaken newer versions have been released on [http://linuxwireless.org](http://linuxwireless.org)

I'm a bit in over my head here, so please bear with me on this one ;-)

---

### Post by freewheel84 on 2009-07-30
Hello
 
I am absolutely new to linux, i have a band new hp dv3-2155mx laptop and installed the latest version of ubuntu on it (9.01 i believe), i cannot get my wireless to work, the make of the card is Atheros 9825 , from what i have followed after reading evrything over the net it comes back as network unclaimed, i dont have a wired acces from ubuntu, i need help.

---

### Post by pytheas22 on 2009-07-30
> Just one question before I try your solution: Why is it that you would recomend the 20080916 build? If I'm not mistaken newer versions have been released on [http://linuxwireless.org](http://linuxwireless.org)

I recommended the old build because other people in this thread already tried the new one (on page 2, where I asked kungfoofool and geruetzel to compile the compat-wireless files that downloaded from linuxwireless.org) and it didn't seem to solve the problem of dropping connections.  The old one did work a year ago on Ubuntu 8.04, so hopefully it will work better now.

freewheel84: please start a new thread (so as not to clutter this one) and I'll reply there.  In your thread, please include the output of:
```

lspci -nn
lshw -C Network
dmesg | grep -e ath -e wlan
uname -rm
```

Since you don't have the exact same model of wireless card as the other posters here, your solution is likely to be different.

---

### Post by calle#52 on 2009-08-01
Tried the suggested solution with partial successful result. Managed to get connected once. After an hour I got disconnected. When trying  to reconnect, it fails. Here is a print of the /var/log/syslog:

Aug  1 16:44:43 calle-laptop NetworkManager: <info>  Config: added 'ssid' value 'smurfen' 
Aug  1 16:44:43 calle-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Aug  1 16:44:43 calle-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Aug  1 16:44:43 calle-laptop NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Aug  1 16:44:43 calle-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  1 16:44:43 calle-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  1 16:44:43 calle-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Aug  1 16:44:43 calle-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Aug  1 16:44:43 calle-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Aug  1 16:45:02 calle-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Aug  1 16:45:02 calle-laptop kernel: [ 2419.769870] wlan0: authenticate with AP ffff88015c971ac0
Aug  1 16:45:02 calle-laptop kernel: [ 2419.779248] wlan0: authenticate with AP ffff88015c971ac0
Aug  1 16:45:02 calle-laptop kernel: [ 2419.781243] wlan0: authenticated
Aug  1 16:45:02 calle-laptop kernel: [ 2419.781246] wlan0: associate with AP ffff88015c971ac0
Aug  1 16:45:02 calle-laptop kernel: [ 2419.784682] wlan0: RX ReassocResp from ffff88015e0d204a (capab=0x431 status=0 aid=1)
Aug  1 16:45:02 calle-laptop kernel: [ 2419.784685] wlan0: associated
Aug  1 16:45:02 calle-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'smurfen'. 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Aug  1 16:45:05 calle-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug  1 16:45:05 calle-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug  1 16:45:05 calle-laptop dhclient: All rights reserved.
Aug  1 16:45:05 calle-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug  1 16:45:05 calle-laptop dhclient: 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  dhclient started with pid 5904 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Aug  1 16:45:05 calle-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Aug  1 16:45:05 calle-laptop dhclient: Listening on LPF/wlan0/00:22:5f:99:32:b9
Aug  1 16:45:05 calle-laptop dhclient: Sending on   LPF/wlan0/00:22:5f:99:32:b9
Aug  1 16:45:05 calle-laptop dhclient: Sending on   Socket/fallback
Aug  1 16:45:06 calle-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug  1 16:45:13 calle-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Aug  1 16:45:24 calle-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Aug  1 16:45:40 calle-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Aug  1 16:45:47 calle-laptop kernel: [ 2464.393269] wlan0: beacon loss from AP ffff88015c971ac0 - sending probe request
Aug  1 16:45:49 calle-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected 
Aug  1 16:45:49 calle-laptop kernel: [ 2466.393092] wlan0: no probe response from AP ffff88015c971ac0 - disassociating
Aug  1 16:45:49 calle-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5904 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (smurfen) 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  Marking connection 'smurfen' invalid. 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  Activation (wlan0) failed. 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Aug  1 16:45:51 calle-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Aug  1 16:46:50 calle-laptop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Aug  1 16:46:50 calle-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 3 

Without being an expert: I could see that the log states that the connection took to long to establish.

Another issue: when I had connection it was SLOW (very slow) compared to the wired connection. 

Any suggestions?

---

### Post by pytheas22 on 2009-08-01
Is the signal strength weak when you're connected?  Did it take a long time to connect the time it was successful?

You may have better luck if you used wicd instead of NetworkManager.  You can install wicd with:
```

sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.  Sometimes wicd does a better job of creating and maintaining a connection than NM.

(Note that installing wicd will require the removal of NetworkManager.  If you want NM back, type 'sudo apt-get install network-manager-gnome'.)

---

### Post by calle#52 on 2009-08-01
Tried using wicd, but that wasn't any better. The signal strength is better with wicd (approx 75%), but not bad with network manager (approx 60%). I have only managed to connect for a few seconds, before it dropps again (goes for both wicd and nm). 

Starting to run out of options...

BTW: With Vista I got signal strength of 100%... this doesn't make much sense to me...  which I uninstalled when installing Ubuntu ;-)

---

### Post by networkproblems on 2009-08-03
Don't go back to Vista yet! Look at my other post.

[http://ubuntuforums.org/showthread.php?p=7728539#post7728539](http://ubuntuforums.org/showthread.php?p=7728539#post7728539)

---

### Post by pytheas22 on 2009-08-03
calle#52: I'm really sorry this is not going as well as one would hope.  The only other thing I can think of at this point is to try disabling security on your wireless network to see if that makes things better.  If it does, the problem likely lies in the WPA setup, and either changing those settings (e.g. from WPA1 to WPA2, or vice-versa) or doing the WPA from the command line with special options might help.  If you still have time and patience, please give that a try and let me know.

---

### Post by chenxiaolong on 2009-08-03
I have another laptop running Ubuntu 9.04 x64 with an Atheros card using MadWifi and a desktop running XP and they both connect fine. I have my router set up to allow connections using WPA1 and WPA2. I did try disabling security before and both NM and Wicd wouldn't connect still. But like I said in my previous post, I returned the computer (because of overheating, not wireless (I was really hoping I could get it working someday, but oh well)), so I can't do anymore tests.

---

### Post by drpaul on 2009-08-15
pytheas:

Need to be a little careful with the removal of NM and installation of wicd. For the less experienced it will cause some confusion as network connection will be broken when NM is removed.

Anyway, I have my own difficulties with which I could use some help.  I have a new hp G70-460us which has the Atheros AR928x wireless adapter. I'm using 9.04 recently installed and run thru Update Manager [32 bit] [wired connection finally]. Have tried NM with 2 different wireless routers and wicd with 1 and the connection stinks [used both no enc and WEP].

What can you suggest for the wireless?

lspci:

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

lshw -C network:

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:dc:b4:5b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.25 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:26:5e:1f:30:16
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11abgn

sudo iwlist scan produces

wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:D3:B4:72
                    ESSID:"Erik"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/100  Signal level:-108 dBm  Noise level=-121 dBm
                    Encryption key:on
                    IE: Unknown: 00044572696B
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: DD0600032F010001
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00002d400e4a68a1
                    Extra: Last beacon: 2504ms ago
          Cell 02 - Address: 00:1E:E5:A1:F1:1F
                    ESSID:"cozycave"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=46/100  Signal level:-91 dBm  Noise level=-121 dBm
                    Encryption key:on
                    IE: Unknown: 0008636F7A7963617665
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0107
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1609070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706545720010B10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3409070700000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=0000141d05a0b18f
                    Extra: Last beacon: 2328ms ago

The Erik response is from a neighbor while cozycave is mine.
I have not been able to get a decent connection with wicd, NM, or manually.

Would appreciate your help.

BTW, I run 8.04 on another laptop with Intel wireless chips on this network without a problem.

Paul

---

### Post by pytheas22 on 2009-08-15
drpaul: when I installed wicd and NetworkManager together, I didn't lose connectivity for more than a second, but it's not a recommended procedure and I will try to warn users in the future.  I also realized recently that having both wicd and NM installed makes the package manager really upset, which is something novices will not know how to fix on their own.

As for your problem, I would recommend trying the following things, in this order:

1. switch to the ath_pci module instead of ath9k (I'm not sure that ath_pci will support your device, but it probably would and might work better)

2. recompile your wireless drivers from the latest source using the code from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/), then see if performance is better under either ath_pci or ath9k (both will be updated by recompiling compat-wireless)

3. try ndiswrapper

4. try the latest ath_pci code from [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/) (this is different than the version of ath_pci that's included in the compat-wireless stack)

I assume you know how to do all of the above on your own because you sound like an experienced user, but if you need more specific instructions let me know.

Also, in the 'lshw -C Network' output you posted, your Atheros card is listed as 'DISABLED', which is strange.  Usually this means the card's radio is turned off, but that doesn't make sense because you say you can connect but not maintain a connection.  Are there any other hardware settings that might be affecting the device?

---

### Post by drpaul on 2009-08-16
pytheas:

Thanks for the suggestions. I tried installing Jaunty back posts first, and I am now working over wireless on my G70.

It still doesn't seem like it's 100% as the wireless light above the keyboard switches between orange and blue, especially when it is communicating. Guess I won't bother with it till I start getting garbage.

Thanks again.

Paul

---

### Post by pytheas22 on 2009-08-17
drpaul: good to know that linux-backports-modules-jaunty helped you out.  Hopefully it will continue to work; if you not, you can try the things I suggested, and always just reinstall linux-backports-modules-jaunty if they don't work out.

---

### Post by mj_bell on 2009-08-27
've been having problems getting my Atheros wireless to work in Ubuntu. I've googled around and tried numerous solutions - none of which have managed to fix my problem – including all the aforementioned ideas. I've done a fresh install of Ubuntu so I can start from scratch.  I've hopefully included all the information usually asked for:
 

 Laptop Model: Toshiba Satellite Pro P300-1CV  
 Wireless Card: Artheros AR928X Wireless adapter (PCI-Express)  
 Ubuntu Version: 9.04 - the Jaunty Jackalope (2.6.28-15-generic i686 )
 

 Output from “lspci”:
```


 02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)  

```

 Output from “lshw -C Network”
 

```
 *-network                
        description: Wireless interface  
        product: AR928X Wireless Network Adapter (PCI-Express)  
        vendor: Atheros Communications Inc.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wmaster0  
        version: 01  
        serial: 00:23:4e:20:a4:7e  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless  
        configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn  
   *-network  
        description: Ethernet interface  
        product: Marvell Technology Group Ltd.  
        vendor: Marvell Technology Group Ltd.  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: eth0  
        version: 16  
        serial: 00:1e:68:87:df:7a  
        size: 100MB/s  
        capacity: 1GB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.5 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s  
   *-network DISABLED  
        description: Ethernet interface  
        physical id: 1  
        logical name: pan0  
        serial: da:94:24:d7:90:3c  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes  
 
```

Output from “dmesg | grep -e ath -e wlan”
 

```
[    4.045363] device-mapper: multipath: version 1.0.5 loaded  
 [    4.045365] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [   11.147595] ath9k: 0.1  
 [   11.147639] ath9k 0000:02:00.0: enabling device (0000 -> 0002)  
 [   11.147648] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [   11.147663] ath9k 0000:02:00.0: setting latency timer to 64  
 [   11.582389] phy0: Selected rate control algorithm 'ath9k_rate_control'  
 [   11.729123] Registered led device: ath9k-phy0:radio  
 [   11.729168] Registered led device: ath9k-phy0:assoc  
 [   11.729212] Registered led device: ath9k-phy0:tx  
 [   11.729252] Registered led device: ath9k-phy0:rx  
 [   21.572466] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

 Output from “sudo iwlist scan”
 

```
lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 wmaster0  Interface doesn't support scanning.  
 

 wlan0     No scan results  
 

 pan0      Interface doesn't support scanning.

```

 The wireless “switch” on the laptop is on and light up, and there are active networks around (works fine on same laptop when I boot into either XP or Windows 7)
 

 Cheers,
 

 Michael

---

### Post by pytheas22 on 2009-08-27
mj_bell: so you've tried installing the package linux-backports-modules-jaunty (and rebooting for changes to take effect) to no effect?

What is the output of:
```

modinfo ath9k
```

---

### Post by mj_bell on 2009-08-28
Thanks for the reply pytheas22 :).

I wasn't sure if I had installed the jaunty package you specified, so I did, and it appears as if my wireless is not recognized anymore (No scan results for iwlist). Here the updated outputs:


Output for modinfo ath9k:

```
filename:       /lib/modules/2.6.28-15-generic/updates/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     B066EA404154EA4DD8862D0
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        lbm_cw-cfg80211,lbm_cw-mac80211,led-class
vermagic:       2.6.28-15-generic SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable Bluetooth coexistence support (bool)

```

output from lspci:

```
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

output from lshw -C network:

```
*-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 16
       serial: 00:1e:68:87:df:7a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.5 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:97:20:5c:41:b3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Output from “dmesg | grep -e ath -e wlan”
```

[    4.073364] device-mapper: multipath: version 1.0.5 loaded
[    4.073366] device-mapper: multipath round-robin: version 1.0.0 loaded
```

Output from “sudo iwlist scan”:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```



Really appreciate you looking into this for me - cheers :)

---

### Post by pytheas22 on 2009-08-29
mj_bell: sorry for the slow response.

It looks like the ath9k module isn't being loaded at all.  Do you have it blacklisted (if so, the file /etc/modprobe.d/blacklist.conf would contain a line reading 'ath9k')?  Or maybe it's just not being modprobed.  What happens if you type:
```

lsmod | grep ath
sudo modprobe ath9k
dmesg | tail -30
lshw -C Network
```

---

### Post by mj_bell on 2009-08-29
no mention of ath9k in blacklist.conf - and no apparent blacklisting of any wireless specific modules (but can show you file if you wish?)

With regard to the output you wished for:

lsmod | grep ath - Gives no output

sudo modprobe ath9k, gives: 

```
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting ath9k (/lib/modules/2.6.28-15-generic/updates/ath9k.ko): Invalid module format
```

dmesg | tail - 30, gives:

```
[   11.800070] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   11.902664] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.902766] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.159172] lp: driver loaded but no devices found
[   12.235596] Adding 3630648k swap on /dev/sda6.  Priority:-1 extents:1 across:3630648k
[   12.774554] EXT3 FS on sda7, internal journal
[   13.774275] type=1505 audit(1251588026.215:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2103
[   13.820250] type=1505 audit(1251588026.263:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2107
[   13.820381] type=1505 audit(1251588026.263:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2107
[   13.820423] type=1505 audit(1251588026.263:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2107
[   13.820461] type=1505 audit(1251588026.263:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2107
[   13.948436] type=1505 audit(1251588026.391:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2112
[   13.948626] type=1505 audit(1251588026.391:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2112
[   13.976559] type=1505 audit(1251588026.419:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2116
[   16.611538] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.611541] Bluetooth: BNEP filters: protocol multicast
[   16.646885] Bridge firewalling registered
[   17.828053] ppdev: user-space parallel port driver
[   18.372164] [drm] Initialized drm 1.1.0 20060810
[   18.415737] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.415743] pci 0000:00:02.0: setting latency timer to 64
[   18.416100] pci 0000:00:02.0: irq 2298 for MSI/MSI-X
[   18.416190] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   18.418634] [drm:i915_setparam] *ERROR* unknown parameter 4
[   21.558425] sky2 eth0: enabling interface
[   21.558632] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.279239] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   23.279430] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.873015] eth0: no IPv6 routers present
[  250.665772] cfg80211: exports duplicate symbol cfg80211_wext_giwrange (owned by lbm_cw_cfg80211)
```

lshw -C Network gives:

```

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 16
       serial: 00:1e:68:87:df:7a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.0.5 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:1f:4f:26:ed:61
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A
```


Cheers,

Michael

---

### Post by pytheas22 on 2009-08-29
Ah, the error message you receive when you try to modprobe ath9k explains a lot.  Do you still get that message if you reboot the computer, then type again:
```

sudo modprobe ath9k
```

Usually this 'invalid module format' stuff clears up after a reboot.

---

### Post by mj_bell on 2009-08-30
Afraid I'm still getting the message after a reboot:

```
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-15-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting ath9k (/lib/modules/2.6.28-15-generic/updates/ath9k.ko): Invalid module format
```

Could it maybe be worth re-installing Ubuntu and then seeing what modprobe ath9k gives?

---

### Post by mj_bell on 2009-08-30
I decided to re-install Ubuntu and below shows all the new outputs. If you wish me to go back to the last state, I can just install the jaunty package.
Output from “lspci”:

```

 02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)  

``` Output from “lshw -C Network”
 

```
 WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4e:20:a4:7e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 16
       serial: 00:1e:68:87:df:7a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.0.5 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:da:76:10:b1:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Output from “dmesg | grep -e ath -e wlan”
 
```
 [    4.061362] device-mapper: multipath: version 1.0.5 loaded
[    4.061365] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.568876] ath9k: 0.1
[   11.568936] ath9k 0000:02:00.0: enabling device (0000 -> 0002)
[   11.568946] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.568962] ath9k 0000:02:00.0: setting latency timer to 64
[   12.004510] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.070788] Registered led device: ath9k-phy0:radio
[   12.070807] Registered led device: ath9k-phy0:assoc
[   12.070822] Registered led device: ath9k-phy0:tx
[   12.070836] Registered led device: ath9k-phy0:rx
[   20.581772] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
``` Output from “sudo iwlist scan”
 

```
lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 wmaster0  Interface doesn't support scanning.  
 

 wlan0     No scan results  
 

 pan0      Interface doesn't support scanning.

```

sudo modprobe ath9k - No output.

---

### Post by mj_bell on 2009-08-30
Sorry, forgot to include the more info you requested earlier:

lsmod | grep ath:

```
ath9k                 280760  0 
mac80211              217592  1 ath9k
led_class              12036  1 ath9k
```

sudo modprobe ath9k: Still no output.

dmesg | tail -30:

```
[   17.327393] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   17.328954] [drm:i915_setparam] *ERROR* unknown parameter 4
[   20.568880] sky2 eth0: enabling interface
[   20.569074] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.581772] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.344815] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   22.345009] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.917378] irq 16: nobody cared (try booting with the "irqpoll" option)
[   24.917385] Pid: 0, comm: swapper Not tainted 2.6.28-15-generic #49-Ubuntu
[   24.917387] Call Trace:
[   24.917395]  [<c04fdfc6>] ? printk+0x18/0x1a
[   24.917399]  [<c017ff67>] __report_bad_irq+0x27/0x90
[   24.917403]  [<c018012e>] note_interrupt+0x15e/0x1a0
[   24.917406]  [<c017ecf9>] ? handle_IRQ_event+0x39/0x70
[   24.917410]  [<c01806f3>] handle_fasteoi_irq+0xa3/0xd0
[   24.917415]  [<c015b9a7>] ? tick_check_idle+0x17/0x30
[   24.917418]  [<c010684e>] do_IRQ+0x7e/0xa0
[   24.917422]  [<c015007b>] ? process_cpu_timer_create+0x1b/0x20
[   24.917425]  [<c01051f3>] common_interrupt+0x23/0x30
[   24.917429]  [<c01100d8>] ? set_mtrr_state+0x228/0x2e0
[   24.917433]  [<c0319bfc>] ? acpi_idle_enter_c1+0x6d/0x83
[   24.917437]  [<c040c41f>] cpuidle_idle_call+0x6f/0xd0
[   24.917439]  [<c010285d>] cpu_idle+0x6d/0xd0
[   24.917443]  [<c04ee60e>] rest_init+0x4e/0x60
[   24.917445] handlers:
[   24.917446] [<c03b7ae0>] (usb_hcd_irq+0x0/0x90)
[   24.917451] [<f7cfe860>] (ohci_irq_handler+0x0/0x7b0 [ohci1394])
[   24.917465] [<f7d49030>] (sdhci_irq+0x0/0x240 [sdhci])
[   24.917471] Disabling IRQ #16
[   33.216031] eth0: no IPv6 routers present

```

lshw -C Network:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4e:20:a4:7e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 16
       serial: 00:1e:68:87:df:7a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.0.5 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:da:76:10:b1:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Also checked - and ath9k still isn't blacklisted.

---

### Post by pytheas22 on 2009-08-30
Yes, please now install the backports package (and make sure your system is up-to-date) by typing:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-backports-modules-jaunty
```

Then reboot.  If it still doesn't work, please post:
```

lsmod | grep ath
sudo modprobe ath9k
dmesg | grep -e ath -e wlan
uname -r
```

---

### Post by mj_bell on 2009-08-30
I've installed the januty package (I think last time I installed the wrong one, didn't use backports?)

Anyway, still no luck - but it hasn't disappeared off the iwlist scan, which is a good sign I guess. As for the outputs:

lsmod | grep ath:

```
ath9k                 282420  0 
lbm_cw_mac80211       227492  1 ath9k
led_class              12036  1 ath9k
lbm_cw_cfg80211        73888  2 ath9k,lbm_cw_mac80211

```

sudo modprobe ath9k: No Output.

dmesg | grep -e ath -e wlan:

```
[    4.057363] device-mapper: multipath: version 1.0.5 loaded
[    4.057366] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.762874] ath9k 0000:02:00.0: enabling device (0000 -> 0002)
[   11.762884] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.762900] ath9k 0000:02:00.0: setting latency timer to 64
[   12.197760] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.259381] Registered led device: ath9k-phy0::radio
[   12.259429] Registered led device: ath9k-phy0::assoc
[   12.259470] Registered led device: ath9k-phy0::tx
[   12.259511] Registered led device: ath9k-phy0::rx
[   21.594141] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

uname - r : 2.6.28-15-generic


Thanks again - Michael.

---

### Post by pytheas22 on 2009-08-30
Thanks for the information.  I guess the linux-backports-modules-jaunty package didn't help you like it did the others in this thread.

I've done some more googling and suspect your issue is the same as the one described in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270748").  If you have bluetooth, try disabling that and see if it helps.  If not, please post the output of:
```

locate wlan | grep sys
```

and hopefully we can find the right command to run to force the wireless to turn on, like the others in that bug report.

It might also help to know the make and model of your computer.

---

### Post by mj_bell on 2009-08-30
hmm, no bluetooth on my laptop - but I disabled anything bluetooth related (I think/hope) and still no luck!

locate wlan | grep sys sadly has no output...However output from just locate wlan is:

```
 /lib/linux-restricted-modules/2.6.28-11-generic/wlan
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_acl
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_ccmp
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_scan_ap
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_scan_sta
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_tkip
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_wep
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_xauth
/lib/linux-restricted-modules/2.6.28-11-generic/wlan/wlan.mod.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan/wlan.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_acl/wlan_acl.mod.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_acl/wlan_acl.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_ccmp/wlan_ccmp.mod.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_ccmp/wlan_ccmp.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_scan_ap/wlan_scan_ap.mod.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_scan_ap/wlan_scan_ap.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_scan_sta/wlan_scan_sta.mod.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_scan_sta/wlan_scan_sta.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_tkip/wlan_tkip.mod.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_tkip/wlan_tkip.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_wep/wlan_wep.mod.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_wep/wlan_wep.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_xauth/wlan_xauth.mod.o
/lib/linux-restricted-modules/2.6.28-11-generic/wlan_xauth/wlan_xauth.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_acl
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_ccmp
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_scan_ap
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_scan_sta
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_tkip
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_wep
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_xauth
/lib/linux-restricted-modules/2.6.28-15-generic/wlan/wlan.mod.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan/wlan.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_acl/wlan_acl.mod.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_acl/wlan_acl.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_ccmp/wlan_ccmp.mod.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_ccmp/wlan_ccmp.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_scan_ap/wlan_scan_ap.mod.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_scan_ap/wlan_scan_ap.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_scan_sta/wlan_scan_sta.mod.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_scan_sta/wlan_scan_sta.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_tkip/wlan_tkip.mod.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_tkip/wlan_tkip.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_wep/wlan_wep.mod.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_wep/wlan_wep.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_xauth/wlan_xauth.mod.o
/lib/linux-restricted-modules/2.6.28-15-generic/wlan_xauth/wlan_xauth.o
/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/staging/wlan-ng
/lib/modules/2.6.28-15-generic/kernel/drivers/staging/wlan-ng/prism2_usb.ko
/lib/modules/2.6.28-15-generic/updates/rndis_wlan.ko
/usr/share/app-install/desktop/kwlan.desktop
/usr/share/app-install/icons/kwlan.png
/usr/share/hal/fdi/information/10freedesktop/10-dell-rfkill-switch-wlan.fdi
/usr/src/linux-headers-2.6.28-11/drivers/staging/wlan-ng
/usr/src/linux-headers-2.6.28-11/drivers/staging/wlan-ng/Kconfig
/usr/src/linux-headers-2.6.28-11/drivers/staging/wlan-ng/Makefile
/usr/src/linux-headers-2.6.28-11-generic/include/config/wlan
/usr/src/linux-headers-2.6.28-11-generic/include/config/usb/net/rndis/wlan.h
/usr/src/linux-headers-2.6.28-11-generic/include/config/wlan/80211.h
/usr/src/linux-headers-2.6.28-11-generic/include/config/wlan/pre80211.h
/usr/src/linux-headers-2.6.28-15/drivers/staging/wlan-ng
/usr/src/linux-headers-2.6.28-15/drivers/staging/wlan-ng/Kconfig
/usr/src/linux-headers-2.6.28-15/drivers/staging/wlan-ng/Makefile
/usr/src/linux-headers-2.6.28-15-generic/include/config/wlan
/usr/src/linux-headers-2.6.28-15-generic/include/config/usb/net/rndis/wlan.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/wlan/80211.h
/usr/src/linux-headers-2.6.28-15-generic/include/config/wlan/pre80211.h

```

As for my laptop, its a Toshiba Satellite Pro P300 - 1CV. From lshw:

description: Notebook
product: Satellite Pro P300
vendor: TOSHIBA
version: PSPC9E-002003EN

---

### Post by mj_bell on 2009-08-30
Just noticed that in "User Settings" that "Connect to Ethernet and Wireless Networks" is unticked, but I cannot tick it (the whole area is grayed out). Could this possibly have anything to do with it (I'm currently connected to ethernet network, so I doubt it?) But thought it may be worth raising?

---

### Post by pytheas22 on 2009-08-31
Thanks for all that information.  Unfortunately, I did a lot of searching and the only other thing I turned up (besides the bug report referenced earlier) is [this thread]("http://www.linux-club.de/viewtopic.php?f=19&t=100695&start=20"), where a German experiences the same problem with a Toshiba Pro 300 and ultimately gives up and buys an external wireless card.

In your case, I'm not sure what else to try, but it wouldn't hurt to recompile the compat-wireless package.  To do that, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2." Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make install
sudo make unload
sudo make load

```

Then reboot and see if "sudo iwlist scan" returns any results.

---

### Post by mj_bell on 2009-08-31
Think I've attempted using the compat package...but giving it another go, and appear to have a problem when trying to load:

```
sudo make load
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwlagn...
Loading ath...
FATAL: Module ath not found.
Loading ar9170usb...
FATAL: Module ar9170usb not found.
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Loading mwl8k...
Loading mac80211_hwsim...
Loading at76c50x_usb...
./scripts/load.sh: line 20: athload: command not found
./scripts/load.sh: line 22: b43load: command not found
make: *** [load] Error 127

```

Strange...am I doing something wrong?

I really appreciate your help pytheas22 :)

---

### Post by pytheas22 on 2009-08-31
Those errors aren't too serious.  If you just reboot, the new modules should be loaded.  After a reboot, does "sudo iwlist scan" return anything?

---

### Post by mj_bell on 2009-09-01
Sadly no luck, still no results shown (although it still finds wlan in the search)...

I was thinking, if on other ar928x cards are solved by the jaunty package - and the ones weren't had a conflict with bluetooth, then could it be fair to assume that something that that comes with my Toshiba laptop is interfering with the wlan? Not sure what - but most likely something networking related, perhaps the built in modem?

Sadly I'm new to Linux, as you can tell, so not sure if this is likely or not..?

---

### Post by pytheas22 on 2009-09-01
I'm sorry that didn't help.  To be honest, I'm really not sure what's up with the ar928x cards.  There are lots of reports of issues similar to yours with networks not showing during scans, but there seems to be little apparent logic behind the source of the problem, and no consistency in the solutions: what works for some people doesn't seem to help others.  It doesn't make much sense that the built-in modem should cause the wireless card not to work, but who knows.

I'm not really sure what to try next.  You could try burning a live CD of [Ubuntu 9.10 alpha]("http://cdimage.ubuntu.com/releases/karmic/alpha-4/") to see if the issue is fixed there.

I'm also vaguely suspicious that this has to do with acpi issues, so booting with acpi disabled might help.  There are instructions for doing that [here]("http://ubuntuforums.org/showthread.php?t=21189") (they're old, but should still apply to Ubuntu 9.04).

---

### Post by mj_bell on 2009-09-03
Tried disabling ACPI and it makes wlan0 disappear from the iwlist scan results again... Also noticed that pan0 has gone, but I'm guessing that went when I removed the bluetooth stuff (as pan0 was loaded to deal with a personal area network, such as bluetooth, I assume)?

However after re-enabling acpi, sudo iwlist scan  now shows wmaster0, which I don't remember being there before? Could this have anything to do with anything?

Haven't tried burning the latest alpha release yet - won't get chance for a few days to download it - when I will give it a go.

Think its getting to the give up/drop kick the laptop out of the window point..

Don't be sorry, really appreciate you helping me with this - learning a bit of linux in the process, which is good :).

---

### Post by pytheas22 on 2009-09-05
> 
However after re-enabling acpi, sudo iwlist scan now shows wmaster0, which I don't remember being there before? Could this have anything to do with anything?

It looks like you had wmaster0 before (see iwlist output in post 46, for example), so unfortunately I don't think this means anything.

The only other thing I can suggest at this point is to give 9.10 alpha a try.  I'd love to see this problem solved as it's really baffling to me (and you're not the only one I've tried to help on here with this issue)...

---

### Post by mj_bell on 2009-09-08
Sorry for the late reply!

I've upgraded to the latest version of Ubuntu (9.10 Alpha) and still no luck.

Is it worth printing my outputs for the above statements and seeing if there is anything new?

---

### Post by pytheas22 on 2009-09-09
Sorry to hear that...

Seeing the output from the commands in the new version of Ubuntu couldn't hurt, but I'm skeptical that they'll reveal much.  But I hope I'm wrong.

---

### Post by mj_bell on 2009-09-14
Again, sorry for the late reply - been hectic my end.

Here are outputs from various things u've requested previously:

modinfo ath9k:

```
 filename:       /lib/modules/2.6.31-10-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     21B680AD1946884D70F623E
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        led-class,mac80211,ath,cfg80211
vermagic:       2.6.31-10-generic SMP mod_unload modversions 586 
parm:           debug:uint
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable Bluetooth coexistence support (bool)
 
```

lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 16)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

lshw -C network:

```
   *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4e:20:a4:7e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:80000000-8000ffff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 16
       serial: 00:1e:68:87:df:7a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:80100000-80103fff ioport:2000(size=256) memory:80200000-8021ffff(prefetchable)
  
```

dmesg | grep -e ath -e wlan:

```
 [    2.317212] device-mapper: multipath: version 1.1.0 loaded
[    2.317214] device-mapper: multipath round-robin: version 1.0.0 loaded
[   14.219448] ath9k 0000:02:00.0: enabling device (0000 -> 0002)
[   14.219460] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.219478] ath9k 0000:02:00.0: setting latency timer to 64
[   14.654652] ath: EEPROM regdomain: 0x65
[   14.654655] ath: EEPROM indicates we should expect a direct regpair map
[   14.654658] ath: Country alpha2 being used: 00
[   14.654660] ath: Regpair used: 0x65
[   15.225830] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.226573] Registered led device: ath9k-phy0::radio
[   15.226591] Registered led device: ath9k-phy0::assoc
[   15.226608] Registered led device: ath9k-phy0::tx
[   15.226624] Registered led device: ath9k-phy0::rx
[  168.544110] ath9k 0000:02:00.0: PCI INT A disabled
[  169.137050] ath9k 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[  169.980157] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3666.049088] ADDRCONF(NETDEV_UP): wlan0: link is not ready
 
```

sudo iwlist scan:

```
 [ 3279.164761] i915 0000:00:02.0: DVI-D-1: no EDID data
[ 3665.434590] atkbd.c: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[ 3665.434598] atkbd.c: Use 'setkeycodes e070 <keycode>' to make it known.
[ 3665.444705] atkbd.c: Unknown key released (translated set 2, code 0xf0 on isa0060/serio0).
[ 3665.444711] atkbd.c: Use 'setkeycodes e070 <keycode>' to make it known.
[ 3666.049088] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3667.625169] irq 16: nobody cared (try booting with the "irqpoll" option)
[ 3667.625176] Pid: 0, comm: swapper Not tainted 2.6.31-10-generic #30-Ubuntu
[ 3667.625178] Call Trace:
[ 3667.625187]  [<c0568b7e>] ? printk+0x18/0x1a
[ 3667.625194]  [<c018c597>] __report_bad_irq+0x27/0x90
[ 3667.625198]  [<c018afac>] ? handle_IRQ_event+0x4c/0x140
[ 3667.625202]  [<c018c750>] note_interrupt+0x150/0x190
[ 3667.625207]  [<c015b43c>] ? ktime_get_ts+0x4c/0x60
[ 3667.625210]  [<c018ccac>] handle_fasteoi_irq+0xac/0xd0
[ 3667.625214]  [<c0105728>] handle_irq+0x18/0x30
[ 3667.625217]  [<c0104df7>] do_IRQ+0x47/0xc0
[ 3667.625221]  [<c0103990>] common_interrupt+0x30/0x40
[ 3667.625226]  [<c0364c19>] ? acpi_idle_enter_c1+0x8a/0xa8
[ 3667.625230]  [<c0463526>] cpuidle_idle_call+0x76/0xd0
[ 3667.625233]  [<c010202c>] cpu_idle+0x8c/0xd0
[ 3667.625238]  [<c0559905>] rest_init+0x55/0x60
[ 3667.625241]  [<c07858cd>] start_kernel+0x2e6/0x2ec
[ 3667.625245]  [<c0785406>] ? unknown_bootoption+0x0/0x1ab
[ 3667.625248]  [<c078507c>] __init_begin+0x7c/0x83
[ 3667.625250] handlers:
[ 3667.625252] [<c040a420>] (usb_hcd_irq+0x0/0x70)
[ 3667.625259] [<f8ada220>] (ohci_irq_handler+0x0/0x780 [ohci1394])
[ 3667.625273] [<f91055f0>] (sdhci_irq+0x0/0x23c [sdhci])
[ 3667.625279] Disabling IRQ #16
 
```

locate wlan | grep sys: No Output.

dmesg | tail -30:

```
 [ 3279.164761] i915 0000:00:02.0: DVI-D-1: no EDID data
[ 3665.434590] atkbd.c: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).
[ 3665.434598] atkbd.c: Use 'setkeycodes e070 <keycode>' to make it known.
[ 3665.444705] atkbd.c: Unknown key released (translated set 2, code 0xf0 on isa0060/serio0).
[ 3665.444711] atkbd.c: Use 'setkeycodes e070 <keycode>' to make it known.
[ 3666.049088] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3667.625169] irq 16: nobody cared (try booting with the "irqpoll" option)
[ 3667.625176] Pid: 0, comm: swapper Not tainted 2.6.31-10-generic #30-Ubuntu
[ 3667.625178] Call Trace:
[ 3667.625187]  [<c0568b7e>] ? printk+0x18/0x1a
[ 3667.625194]  [<c018c597>] __report_bad_irq+0x27/0x90
[ 3667.625198]  [<c018afac>] ? handle_IRQ_event+0x4c/0x140
[ 3667.625202]  [<c018c750>] note_interrupt+0x150/0x190
[ 3667.625207]  [<c015b43c>] ? ktime_get_ts+0x4c/0x60
[ 3667.625210]  [<c018ccac>] handle_fasteoi_irq+0xac/0xd0
[ 3667.625214]  [<c0105728>] handle_irq+0x18/0x30
[ 3667.625217]  [<c0104df7>] do_IRQ+0x47/0xc0
[ 3667.625221]  [<c0103990>] common_interrupt+0x30/0x40
[ 3667.625226]  [<c0364c19>] ? acpi_idle_enter_c1+0x8a/0xa8
[ 3667.625230]  [<c0463526>] cpuidle_idle_call+0x76/0xd0
[ 3667.625233]  [<c010202c>] cpu_idle+0x8c/0xd0
[ 3667.625238]  [<c0559905>] rest_init+0x55/0x60
[ 3667.625241]  [<c07858cd>] start_kernel+0x2e6/0x2ec
[ 3667.625245]  [<c0785406>] ? unknown_bootoption+0x0/0x1ab
[ 3667.625248]  [<c078507c>] __init_begin+0x7c/0x83
[ 3667.625250] handlers:
[ 3667.625252] [<c040a420>] (usb_hcd_irq+0x0/0x70)
[ 3667.625259] [<f8ada220>] (ohci_irq_handler+0x0/0x780 [ohci1394])
[ 3667.625273] [<f91055f0>] (sdhci_irq+0x0/0x23c [sdhci])
[ 3667.625279] Disabling IRQ #16
 
```

lsmod | grep ath:

```
 ath9k                 258712  0 
mac80211              181076  1 ath9k
ath                     8060  1 ath9k
led_class               4096  2 ath9k,sdhci
cfg80211               93084  3 ath9k,mac80211,ath
  
```

uname -r:

```
  2.6.31-10-generic 
```


Thanks again,

Michael

---

### Post by pytheas22 on 2009-09-15
It looks like you accidentally copied 'dmesg' output where you meant to paste 'sudo iwlist scan', but unless the latter is any different than it was under Ubuntu 9.04, it probably doesn't make a difference.

I'm still really baffled as to what's going on with this, and am not sure what else to try.  So I'm afraid I have to give up.  I'm really sorry (and frustrated) about your lack of wireless support in Ubuntu, but short of waiting for developers to fix the issue, I'm not sure what else to do...

---

### Post by mj_bell on 2009-09-15
Just tried both Fedora and Opensuse Live CD's, and no look with either of them finding wireless either...bummer.

I really appreciate your time in trying - I will try a few more things and hope for the best, although I'm doubtful!

Thanks again!

---

### Post by carlbeech on 2009-09-27
Hi,

Looks like a lot of posts here..

I've had an AR928x working for some time (Jaunty and Karmic), however, I'm writing this from Vista...

While these work, if I've got to move files of any size, it takes absolutely ages - it seems to have full connectivity for about 10 seconds and then goes down to 0 for about 30 secs to a minute. Upshot - about an hour+ to move a 1Gb file - whereas Vista I can move 10+Gb in an hour....

Might be me, but it seems to have gotten worse in the last few revisions of Karmic (upgraded to this, as I wasn't able to shut down my ASUS laptop under Jaunty)...:confused:

On a side note, I'm able to hibernate, but loose wireless when restarting - rmmod ath9k / modprobe ath9k normally re-enables this...

Do you have any suggestions - I hate having to go back to vista!:(

Stats:
Laptop: ASUS a59x
Wireless: Atheros ar928x
Kubuntu: Karmic (constantly doing aptitude full-upgrade to keep to latest revisions...)
Security: WEP - no problems
WifiManager: Network manager


Many thanks

Carl

---

### Post by pytheas22 on 2009-09-27
carlbeech: one suggestion would be to try using wicd instead of NetworkManager.  I doubt it would make a difference, but it might.

You might also want to try moving closer to your router to see if that improves the performance.  It's possible this is a signal-strength issue where the Linux driver isn't able to get as strong a signal as the Windows one.  I'm not sure how you could solve that if it proves to be the case, but at least you'd have a better understanding of the problem.

---

### Post by Sir_Brizz on 2009-09-29
carlbeech, can you try the latest version of linux-backport-modules-karmic and see if the wireless quality improves?

---

### Post by Strubbl on 2009-10-30
no action here in this thread since a month. has anyone found a solution?

i have karmic and still problems with my AR928X in my dell xps studio :( and after reading the whole 7 pages I am going to try turning of acpi, testing wicd and finally if it is still not working compiling [compat-wireless-2.6.tar.bz2]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2") or the old version from 2008 as I noticed my wireless was working in intrepid very well.

any other ideas on fixing this issue?

---

### Post by pytheas22 on 2009-10-31
Strubbl: what you propose to do sounds like the best idea to me.  Please give those things a try (wicd, compiling older compat-wireless) and if it still doesn't work, let us know.

Also, what exactly is wrong in your case?  Is there no wireless at all or is it just performing poorly?

---

### Post by Strubbl on 2009-10-31
> **pytheas22 said:**
> Strubbl: what you propose to do sounds like the best idea to me.  Please give those things a try (wicd, compiling older compat-wireless) and if it still doesn't work, let us know.

Also, what exactly is wrong in your case?  Is there no wireless at all or is it just performing poorly?my wireless is performing poorly. i am connected to the access point but every (let's say) 2min there is 20sec a hole in which no traffic gets through. and that's very annoying if u work on servers via ssh.

yesterday i tried to turn acpi off. but my pc won't boot at all with that option. (perhaps something to do with grub2 and/or crypted devices...)

i wrote a pm with [Viola00]("http://ubuntuforums.org/member.php?u=939336") as he (or she) has exactly the same hardware and problem. i was told to reinstall compat-wireless in the newest version. so i did. now i am going to test it.

i hope it helped! :)

#edit
okay, while testdownloading some stuff the download speed graph showed, that there are still lags. ping shows it again:

64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=97 ttl=248 time=67.7 ms
64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=98 ttl=248 time=66.1 ms
64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=99 ttl=248 time=68.8 ms
64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=100 ttl=248 time=70.8 ms
64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=101 ttl=248 time=70.0 ms


64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=119 ttl=248 time=21.4 ms
64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=120 ttl=248 time=19.6 ms
64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=121 ttl=248 time=19.8 ms
64 bytes from redirector.heise.de (193.99.144.80): icmp_seq=122 ttl=248 time=20.8 ms

nearly 18sec no traffic and packet loss :(

---

### Post by pytheas22 on 2009-10-31
Strubbl: have you tried an older version of compat wireless?  Perhaps that would work better.

Are you seeing anything in dmesg or syslog that might be relevant?

---

### Post by Strubbl on 2009-11-01
no. i wanted to test a driver vom 2008/09 but this one was only for 2.6.26 kernels. also the newest compat driver 2.6.32... made no improving effect

so i tested installing wicd. now i am downloading a debian dvd and within the first 300MB there was no problem.

sorry, searching the logs is my last choice.

i hope the problem is away now. it would be very cool if this is my solution do get the wlan working more stable.

---

### Post by chenxiaolong on 2009-11-02
Are you using Ubuntu 9.10 Karmic? It pretty much solved all the wireless problems I had, although I don't have an Atheros card any more. The only other thing I can think of is to disable APIC (not ACPI). My laptop has many things that don't work unless I disable apic. Boot with "noapic" "nolapic", or "noapic nolapic" (that's the letter "l" not the number "1"). I have to boot with both.

---

### Post by Strubbl on 2009-11-06
yes i am using karmic since the 3rd alpha as i hoped it will solve my wlan problem. but it doesn't.

my solution was to install the other networkmanager wicd. now my wlan works without lags. *happy*

but after suspend the wlan won't work any more so that i have to reboot. but that's another problem...:lolflag:

---

### Post by chenxiaolong on 2009-11-06
I'm glad it worked out for you. Could you try running ```
sudo rmmod ath9k
``` and then ```
sudo modprobe ath9k
``` and see if it works?

---

### Post by Strubbl on 2009-11-10
> **chenxiaolong said:**
> I'm glad it worked out for you. Could you try running ```
sudo rmmod ath9k
``` and then ```
sudo modprobe ath9k
``` and see if it works?
yeah, that helps. so i don't have to reboot. is there any possibility to fix this bug or to automate removing and inserting that module?

---

### Post by chenxiaolong on 2009-11-10
Try creating a script in /etc/acpi/resume.d/ (like /etc/acpi/resume.d/getstupidwirelessworking.sh)

and copy and paste this into the file

```

#!/bin/bash
rmmod ath9k
modprobe ath9k

```

then run ```
sudo chmod +x /etc/acpi/resume.d/getstupidwirelessworking.sh
```

and see if it works now.

---

### Post by samuel2202 on 2009-11-13
Hi,

It's working very well on Ubuntu Karmic Wifi freezes with this Wireless card !

:popcorn:

---

### Post by chenxiaolong on 2009-11-13
I'm sorry, I don't understand what you are saying? Does it work well or does it freeze?

---

### Post by PenquinCoder on 2009-11-17
I recently bought a new HP DV7 3060US, because my other compaq HDD took a crap on itself, and I am having nothing but problems with this one. I am using the released 'stable' version of Karmic x86_64. One of the biggest, and absolutely most frustrating issues is this damn wireless chip. I have a slew of other issues with Karmic on this laptop, and it really has made this release of Ubuntu the WORST for 'out of the box' support that I have ever had. And I've been using since Breezy....


Computer:HP DV7 3060US
Wireless:Atheros AR928x
Kernel: Linux laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

I have tried absolutely EVERYTHING to get wireless working in a stable manner, including, compat-wireless,ndiswrapper, wicd,network-manager, and a combination of all of them! Currently have the module compat-wireless-ath9k-20080916 installed from THIS thread, and running with network-manager.

When I restart the computer, I have to manually 'sudo modprobe ath9k' to get the wireless detected. I then have to 'sudo ifconfig wlan0 rate 54M' to set the bitrate, or for some reason the module sets it ridiculously low (anywhere from 1mbs to 12mbs). 

Can someone PLEASE explain to me, why the support and driver for this card/chipset (that has been out at least two years now) has such shitty support??? OR at least tell me a guarenteed, stable way to keep this wireless active, and in use without dropping packets and losing signal??

40% - 70% packet loss on a non-secured network, with signal strength extreamly high, is uncalled for.


Output:
iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:03:52:96:8E:A0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-12 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```



dmesg | grep -e ath -e wlan
```

[    1.206321] device-mapper: multipath: version 1.1.0 loaded
[    1.206324] device-mapper: multipath round-robin: version 1.0.0 loaded
[    8.827560] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.827570] ath9k 0000:08:00.0: setting latency timer to 64
[    9.252946] ath: EEPROM regdomain: 0x69
[    9.252948] ath: EEPROM indicates we should expect a direct regpair map
[    9.252951] ath: Country alpha2 being used: 00
[    9.252952] ath: Regpair used: 0x69
[    9.561351] phy0: Selected rate control algorithm 'ath9k_rate_control'
[    9.561998] Registered led device: ath9k-phy0::radio
[    9.562011] Registered led device: ath9k-phy0::assoc
[    9.562023] Registered led device: ath9k-phy0::tx
[    9.562036] Registered led device: ath9k-phy0::rx
[   35.091553] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.076449] wlan0: direct probe to AP 00:03:52:96:4a:00 (try 1)
[   48.076482] wlan0: deauthenticating from 00:03:52:96:4a:00 by local choice (reason=3)
[   48.086264] wlan0: direct probe to AP 00:03:52:96:8e:a0 (try 1)
[   48.102965] wlan0: direct probe responded
[   48.102970] wlan0: authenticate with AP 00:03:52:96:8e:a0 (try 1)
[   48.110122] wlan0: authenticated
[   48.110146] wlan0: associate with AP 00:03:52:96:8e:a0 (try 1)
[   48.115529] wlan0: RX AssocResp from 00:03:52:96:8e:a0 (capab=0xc21 status=0 aid=4)
[   48.115533] wlan0: associated
[   48.116562] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.040073] wlan0: no IPv6 routers present
[   70.400070] wlan0: deauthenticating from 00:03:52:96:8e:a0 by local choice (reason=3)
[   70.400153] wlan0: deauthenticating from 00:03:52:96:8e:a0 by local choice (reason=3)
[   70.418826] wlan0: direct probe to AP 00:03:52:96:8a:90 (try 1)
[   70.422312] wlan0: direct probe responded
[   70.422331] wlan0: authenticate with AP 00:03:52:96:8a:90 (try 1)
[   70.424288] wlan0: authenticated
[   70.460953] wlan0: associate with AP 00:03:52:96:8a:90 (try 1)
[   70.464289] wlan0: RX ReassocResp from 00:03:52:96:8a:90 (capab=0xc21 status=0 aid=3)
[   70.464293] wlan0: associated
[  100.120326] wlan0: deauthenticating from 00:03:52:96:8a:90 by local choice (reason=3)
[  100.120478] wlan0: deauthenticating from 00:03:52:96:8a:90 by local choice (reason=3)
[  100.133396] wlan0: direct probe to AP 00:03:52:97:5c:10 (try 1)
[  100.143887] wlan0: direct probe responded
[  100.143899] wlan0: authenticate with AP 00:03:52:97:5c:10 (try 1)
[  100.150579] wlan0: authenticated
[  100.162799] wlan0: associate with AP 00:03:52:97:5c:10 (try 1)
[  100.167000] wlan0: RX ReassocResp from 00:03:52:97:5c:10 (capab=0xc21 status=0 aid=1)
[  100.167009] wlan0: associated
[  140.060235] wlan0: deauthenticating from 00:03:52:97:5c:10 by local choice (reason=3)
[  140.060383] wlan0: deauthenticating from 00:03:52:97:5c:10 by local choice (reason=3)
[  140.071923] wlan0: direct probe to AP 00:03:52:96:8a:90 (try 1)
[  140.118254] wlan0: direct probe responded
[  140.118266] wlan0: authenticate with AP 00:03:52:96:8a:90 (try 1)
[  140.120520] wlan0: authenticated
[  140.120569] wlan0: associate with AP 00:03:52:96:8a:90 (try 1)
[  140.124419] wlan0: RX ReassocResp from 00:03:52:96:8a:90 (capab=0xc21 status=0 aid=3)
[  140.124427] wlan0: associated
[  861.260746] wlan0: deauthenticated from 00:03:52:96:8a:90 (Reason: 6)
[  865.102373] wlan0: deauthenticating from 00:03:52:96:8a:90 by local choice (reason=3)
[  865.111433] wlan0: direct probe to AP 00:03:52:96:8e:a0 (try 1)
[  865.156694] wlan0: direct probe responded
[  865.156706] wlan0: authenticate with AP 00:03:52:96:8e:a0 (try 1)
[  865.352676] wlan0: authenticate with AP 00:03:52:96:8e:a0 (try 2)
[  865.362888] wlan0: authenticated
[  865.362940] wlan0: associate with AP 00:03:52:96:8e:a0 (try 1)
[  865.370159] wlan0: RX ReassocResp from 00:03:52:96:8e:a0 (capab=0xc21 status=0 aid=2)
[  865.370167] wlan0: associated
[  980.100207] wlan0: deauthenticating from 00:03:52:96:8e:a0 by local choice (reason=3)
[  980.100321] wlan0: deauthenticating from 00:03:52:96:8e:a0 by local choice (reason=3)
[  980.110075] wlan0: direct probe to AP 00:03:52:96:8a:90 (try 1)
[  980.113684] wlan0: direct probe responded
[  980.113695] wlan0: authenticate with AP 00:03:52:96:8a:90 (try 1)
[  980.116253] wlan0: authenticated
[  980.143063] wlan0: associate with AP 00:03:52:96:8a:90 (try 1)
[  980.146242] wlan0: RX ReassocResp from 00:03:52:96:8a:90 (capab=0xc21 status=0 aid=3)
[  980.146250] wlan0: associated
[ 1100.090124] wlan0: deauthenticating from 00:03:52:96:8a:90 by local choice (reason=3)
[ 1100.090295] wlan0: deauthenticating from 00:03:52:96:8a:90 by local choice (reason=3)
[ 1100.099658] wlan0: direct probe to AP 00:03:52:96:8e:a0 (try 1)
[ 1100.105364] wlan0: direct probe responded
[ 1100.105375] wlan0: authenticate with AP 00:03:52:96:8e:a0 (try 1)
[ 1100.108312] wlan0: authenticated
[ 1100.141218] wlan0: associate with AP 00:03:52:96:8e:a0 (try 1)
[ 1100.144354] wlan0: RX ReassocResp from 00:03:52:96:8e:a0 (capab=0xc21 status=0 aid=4)
[ 1100.144364] wlan0: associated
[ 1221.254434] wlan0: deauthenticated from 00:03:52:96:8e:a0 (Reason: 6)
[ 1225.162363] wlan0: deauthenticating from 00:03:52:96:8e:a0 by local choice (reason=3)
[ 1225.173121] wlan0: direct probe to AP 00:03:52:96:8a:90 (try 1)
[ 1225.176657] wlan0: direct probe responded
[ 1225.176666] wlan0: authenticate with AP 00:03:52:96:8a:90 (try 1)
[ 1225.179375] wlan0: authenticated
[ 1225.179411] wlan0: associate with AP 00:03:52:96:8a:90 (try 1)
[ 1225.182573] wlan0: RX ReassocResp from 00:03:52:96:8a:90 (capab=0xc21 status=0 aid=3)
[ 1225.182587] wlan0: associated
[ 1398.264577] wlan0: deauthenticated from 00:03:52:96:8a:90 (Reason: 6)
[ 1402.099948] wlan0: direct probe to AP 00:03:52:96:8a:90 (try 1)
[ 1402.102898] wlan0: direct probe responded
[ 1402.102909] wlan0: authenticate with AP 00:03:52:96:8a:90 (try 1)
[ 1402.104818] wlan0: authenticated
[ 1402.104874] wlan0: associate with AP 00:03:52:96:8a:90 (try 1)
[ 1402.107580] wlan0: RX ReassocResp from 00:03:52:96:8a:90 (capab=0xc21 status=0 aid=3)
[ 1402.107588] wlan0: associated
[ 1460.030188] wlan0: deauthenticating from 00:03:52:96:8a:90 by local choice (reason=3)
[ 1460.030331] wlan0: deauthenticating from 00:03:52:96:8a:90 by local choice (reason=3)
[ 1460.042924] wlan0: direct probe to AP 00:03:52:96:8e:a0 (try 1)
[ 1460.050769] wlan0: direct probe responded
[ 1460.050781] wlan0: authenticate with AP 00:03:52:96:8e:a0 (try 1)
[ 1460.053724] wlan0: authenticated
[ 1460.072681] wlan0: associate with AP 00:03:52:96:8e:a0 (try 1)
[ 1460.080475] wlan0: RX ReassocResp from 00:03:52:96:8e:a0 (capab=0xc21 status=0 aid=2)
[ 1460.080483] wlan0: associated

```

lspci | grep 'Atheros'
```

08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

---

### Post by chenxiaolong on 2009-11-17
I had this wireless card on an HP G60 laptop and it was a terrible experience. Even in Windows, it had many disconnects. I let the comp. overheat a lot, so HP would take it back as defective (had it for 2 months). Ugh. I hate Atheros.

---

### Post by Strubbl on 2009-12-12
> **chenxiaolong said:**
> Try creating a script in /etc/acpi/resume.d/ (like /etc/acpi/resume.d/getstupidwirelessworking.sh)

and copy and paste this into the file

```

#!/bin/bash
rmmod ath9k
modprobe ath9k

```then run ```
sudo chmod +x /etc/acpi/resume.d/getstupidwirelessworking.sh
```and see if it works now.
hi, it doesn't work. I have no directory  /etc/acpi/resume.d. I created it and put the script in it. But the script isn't executed after resuming although execution-bit. (I tested it with a simple additional echo to a file.)

any ideas where to put the getstupidwirelessworking.sh script to make it run after a resume?

---

### Post by chenxiaolong on 2009-12-12
Apparently, the /etc/acpi/resume.d folder doesn't work anymore. Try this: 

Create 10_getstupidwirelessworking in /etc/pm/sleep.d (with no extension) and copy and paste this in the file: 

```
#!/bin/bash

case "${1}" in
        resume|thaw)
		rmmod ath9k
		modprobe ath9k
		echo "The ath9k script sucessfully ran on $(date)" | sudo tee -a /var/log/ath9k_resume_script.log
                ;;
esac
```

---

### Post by Malakai on 2010-01-18
Anyone having troubles with their Atheros AR928X wireless card, please see scottro's post in this thread:

[http://ubuntuforums.org/showthread.php?p=8687880#post8687880](http://ubuntuforums.org/showthread.php?p=8687880#post8687880)

wireless-compat, follow the directions on the site that scott linked to. It replaces the wireless and bluetooth kernel modules with newer and better ones; now my bluetooth mouse is not constantly disconnecting and refusing to reconnect, and my wireless is not totally sucking, barely transferring data at 10kb/sec, and lagging like crazy. Its almost as fast as it is in win7 how, xferring video files at 2-2.5mb/sec over my lowly wireless G network. Beats the heck out of 20kb/sec with the standard ubuntu 9.10 drivers eh?

Good luck, fixed my 1000HE up right!

Note I used the newest wireless-compat driver from the stable page on its website, and had to install patch and patchutils for some of the scripts in the compat driver package to work. I used the make install, make unload, and make load scripts in the driver package to update all the modules, that took care of all wireless and bluetooth modules, didnt even req a reboot heh and everythign was fixed. Just follow the directions on the compat website to the letter and youll be fine.

Also I did not ever install those backports or modify any configs that other recommended to do, just the compat stuff fixed all my wireless/bluetooth problems beautifully!

---

### Post by Chronon on 2010-03-20
I'm using kernel 2.6.32.9-70 and installed the latest stable compat-wireless package from that site and I have no change.  I guess I will try ndiswrapper.

It seems these problems appeared recently.  When I got this netbook about a year ago I didn't have any problems with wireless.  Perhaps I should install an older kernel. . ..

---

### Post by pytheas22 on 2010-03-20
Chronon: if you still haven't figured it out, I'll try to help if you post the output of these commands:
```

uname -rm
cat /etc/issue
lshw -C Network
modinfo ath_pci
modinfo ath5k
modinfo ath9k
dmesg | grep -e ath -e wlan
```

---

### Post by Chronon on 2010-03-25
```

chronon@netbook:~$ uname -rm
2.6.31-20-generic i686
chronon@netbook:~$ cat /etc/issue
Ubuntu 9.10 \n \l

chronon@netbook:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:81:06:a6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:43:86:fc:0a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:fbef0000-fbefffff
chronon@netbook:~$ modinfo ath_pci
ERROR: modinfo: could not find module ath_pci
chronon@netbook:~$ modinfo ath5k
filename:       /lib/modules/2.6.31-20-generic/updates/cw/ath5k.ko
version:        0.6.0 (EXPERIMENTAL)
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     5F4220BF00D02FC4237E03A
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,led-class,cfg80211,ath
vermagic:       2.6.31-20-generic SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)
chronon@netbook:~$ modinfo ath9k
filename:       /lib/modules/2.6.31-20-generic/updates/cw/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D2FCE033DD78D3AB11E320A
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        mac80211,led-class,ath,cfg80211
vermagic:       2.6.31-20-generic SMP mod_unload modversions 586 
parm:           debug:uint
parm:           nohwcrypt:Disable hardware encryption (int)
chronon@netbook:~$ dmesg | grep -e ath -e wlan
[    1.164243] device-mapper: multipath: version 1.1.0 loaded
[    1.164250] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.694033] ath9k 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.694059] ath9k 0000:01:00.0: setting latency timer to 64
[   12.130882] ath: EEPROM regdomain: 0x60
[   12.130890] ath: EEPROM indicates we should expect a direct regpair map
[   12.130898] ath: Country alpha2 being used: 00
[   12.130902] ath: Regpair used: 0x60
[   12.803475] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.805649] Registered led device: ath9k-phy0::radio
[   12.805710] Registered led device: ath9k-phy0::assoc
[   12.805778] Registered led device: ath9k-phy0::tx
[   12.805838] Registered led device: ath9k-phy0::rx
[   17.941003] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   67.451503] wlan0: deauthenticating from 00:1f:33:cf:96:20 by local choice (reason=3)
[   67.451647] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[   67.649088] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[   67.849069] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[   68.049118] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[   78.682203] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[   78.880224] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[   79.081096] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[   79.280103] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[   89.930136] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[   90.128125] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[   90.328128] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[   90.528113] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[  101.179272] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[  101.376166] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[  101.576136] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[  101.776171] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[  112.418201] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[  112.616107] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[  112.816497] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[  113.016101] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[  123.662354] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[  123.860129] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[  124.060103] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[  124.260112] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[  135.074217] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[  135.272121] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[  135.472109] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[  135.672115] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[  146.324299] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[  146.524110] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[  146.724130] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[  146.924108] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[  157.574018] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[  157.772115] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[  157.972087] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[  158.172179] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[  168.822732] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[  169.020103] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[  169.220118] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[  169.420119] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[  180.075756] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[  180.273096] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[  180.473094] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[  180.676471] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out
[  191.310741] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 1)
[  191.508120] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 2)
[  191.708130] wlan0: direct probe to AP 00:1f:33:cf:96:20 (try 3)
[  191.908139] wlan0: direct probe to AP 00:1f:33:cf:96:20 timed out

```

Thanks for the offer.  Here's the output of those commands.  I just freshly installed Karmic and built the compat-wireless drivers.

---

### Post by pytheas22 on 2010-03-25
Chronon: thanks for the output.  Have you ever been able to connect with this wireless card in Ubuntu or did it fail completely both before and after you installed the latest compat-wireless code?

It might be worth trying wicd instead of NetworkManager to see if it works any better.  You can install wicd with these commands (assuming you have a wired Internet connection available):
```

sudo apt-get upgrade
sudo apt-get install wicd
```

If wicd doesn't help, I'm not really sure what to do, other than trying other releases of compat-wireless (for example, one of the stable releases instead of the daily build) to see if it works there.  You could also try booting to Ubuntu 10.04 alpha to see if it's any better than 9.10 for your wireless.

---

### Post by Chronon on 2010-03-26
It used to work just fine with Jaunty.  It worked for a while with Karmic too, but it seems that some update or another (maybe a month or two ago) caused problems for the wireless card.  I see that the kernel has problems for this card right now.  I tried installing Fedora 12, which has a slightly newer kernel version than Karmic, but no dice.

I didn't notice any tangible improvement after installing the newest compat-wireless drivers.  I can see access points I just can't associate.  It seems to fail during authentication.

As far as I can tell it's a kernel/module problem.  I have doubts that wicd will provide much benefit over NetworkManager.  It could be that Lucid will work.  I have seen some discussions that suggest that 2.6.33 and above has improved performance for this chipset.

---

### Post by pytheas22 on 2010-03-26
If it worked on Jaunty, maybe installing an older version of compat-wireless would solve the problem.  There are snapshots at [http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/) going back to the 2.6.30 kernel.  Jaunty's was 2.6.28 so these may not be old enough, but they could be worth a try.

Or you might be able to find older compat-wireless code around somewhere else; I didn't look very hard.

---

### Post by Chronon on 2010-03-26
I have Windows XP as a dual boot on this netbook and I am now unable to authenticate there as well.  It appears that this may be due to a hardware fault rather than a driver issue.

Thanks for your help!

---

### Post by pytheas22 on 2010-03-26
Ah, sorry to hear you may be having hardware difficulties, but at least that helps clear up what was wrong.  Maybe you should try playing around with your router's settings--it could be that something got changed there, rather than a problem with the wireless card.  In any case, good luck!

---

### Post by CaronMargarete on 2010-04-11
Hey there, hoping someone can help me understand how to fix my wireless connection.

I'm not tech-savvy and definitely a Ubuntu newbie so much of the information I've read makes no sense to me. The problem lies in my connection dropping out for no reason or being really low and slow. I cannot connect to a cable where I live either.

When researching I looked at Ndiswrapper but there is soooo much information that I think that there's too much and now I can't understand exactly what I need to do to get it working. I thought that I needed the .inf file from my windows driver but I've no idea what that is or where to find it on my computer and there doesn't seem to be information clear enough for me to follow instructions. I have both XP and Ubuntu loaded on my laptop.

Any help anyone can give me to learn more would be extremely appreciated!!! Please remember if you ask me to do something that simple layman language and instructions are really appreciated.

Many thanks in advance,
Caron Margarete.


From what I've read so far I know the following (sorry they don't have the scroll bars, I don't know how to do that:
[B]
Model:[/B] ACER Aspire 4535
**Graphics:** 64Bit AMD Athlonx2
**Wireless Card: **Atheros AR928x (PCI Express) (rev01)
**Ubuntu Version: **9.10 Karmic Koala

From this thread I know the following may be requested:

**lspci**
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)

**lshw -C Network**
  *-network              
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:17:c4:a3:a0:eb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0500000-f050ffff
  *-network
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:1c:42:af
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 multicast=yes
       resources: irq:27 memory:f0400000-f043ffff ioport:c000(size=128)

**dmesg | grep -e ath -e wlan**
[    4.357796] device-mapper: multipath: version 1.1.0 loaded
[    4.357800] device-mapper: multipath round-robin: version 1.0.0 loaded
[   26.424202] ath9k 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.424215] ath9k 0000:05:00.0: setting latency timer to 64
[   26.856392] ath: EEPROM regdomain: 0x65
[   26.856394] ath: EEPROM indicates we should expect a direct regpair map
[   26.856399] ath: Country alpha2 being used: 00
[   26.856401] ath: Regpair used: 0x65
[   26.885712] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   26.886445] Registered led device: ath9k-phy0::radio
[   26.886464] Registered led device: ath9k-phy0::assoc
[   26.886481] Registered led device: ath9k-phy0::tx
[   26.886504] Registered led device: ath9k-phy0::rx
[   27.618575] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.978096] wlan0: authenticate with AP 00:25:9c:4f:7d:4e
[   34.980390] wlan0: authenticated
[   34.980396] wlan0: associate with AP 00:25:9c:4f:7d:4e
[   34.983131] wlan0: RX AssocResp from 00:25:9c:4f:7d:4e (capab=0x431 status=0 aid=1)
[   34.983139] wlan0: associated
[   34.983970] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   45.752560] wlan0: no IPv6 routers present
[  175.992618] wlan0: no probe response from AP 00:25:9c:4f:7d:4e - disassociating
[  177.227353] wlan0: authenticate with AP 00:25:9c:4f:7d:4e
[  177.229690] wlan0: authenticated
[  177.229697] wlan0: associate with AP 00:25:9c:4f:7d:4e
[  177.232413] wlan0: RX ReassocResp from 00:25:9c:4f:7d:4e (capab=0x431 status=0 aid=1)
[  177.232417] wlan0: associated
[  262.410097] wlan0: no probe response from AP 00:25:9c:4f:7d:4e - disassociating
[  263.624375] wlan0: authenticate with AP 00:25:9c:4f:7d:4e
[  263.626568] wlan0: authenticated
[  263.626579] wlan0: associate with AP 00:25:9c:4f:7d:4e
[  263.629888] wlan0: RX ReassocResp from 00:25:9c:4f:7d:4e (capab=0x431 status=0 aid=1)
[  263.629898] wlan0: associated
[  322.610095] wlan0: no probe response from AP 00:25:9c:4f:7d:4e - disassociating
[  323.837048] wlan0: authenticate with AP 00:25:9c:4f:7d:4e
[  323.839334] wlan0: authenticated
[  323.839345] wlan0: associate with AP 00:25:9c:4f:7d:4e
[  323.842182] wlan0: RX ReassocResp from 00:25:9c:4f:7d:4e (capab=0x431 status=0 aid=1)
[  323.842190] wlan0: associated
[  417.552566] wlan0: no probe response from AP 00:25:9c:4f:7d:4e - disassociating
[  418.761809] wlan0: authenticate with AP 00:25:9c:4f:7d:4e
[  418.763873] wlan0: authenticated
[  418.763880] wlan0: associate with AP 00:25:9c:4f:7d:4e
[  418.766596] wlan0: RX ReassocResp from 00:25:9c:4f:7d:4e (capab=0x431 status=0 aid=1)
[  418.766602] wlan0: associated
[ 2127.919037] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat nls_utf8 isofs usb_storage binfmt_misc ppdev joydev arc4 ecb snd_hda_codec_atihdmi snd_hda_codec_realtek snd_seq_dummy snd_seq_oss uvcvideo videodev v4l1_compat v4l2_compat_ioctl32 snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iptable_filter ip_tables x_tables ath9k mac80211 ath snd_seq_device led_class snd_hda_intel snd_hda_codec snd_hwdep psmouse serio_raw atl1c snd_pcm_oss snd_mixer_oss snd_pcm snd_timer amd64_edac_mod edac_core i2c_piix4 cfg80211 snd soundcore snd_page_alloc shpchp lp parport usbhid video output radeon ttm drm i2c_algo_bit
[ 2127.919329]  [<ffffffffa0299ca0>] ath_tx_complete+0x150/0x170 [ath9k]
[ 2127.919347]  [<ffffffffa0299d5a>] ath_tx_complete_buf+0x9a/0x110 [ath9k]
[ 2127.919365]  [<ffffffffa029b3c8>] ath_draintxq+0xf8/0x2c0 [ath9k]
[ 2127.919381]  [<ffffffffa0283e00>] ? ath9k_hw_reset+0x490/0x800 [ath9k]
[ 2127.919399]  [<ffffffffa029c8fc>] ath_drain_all_txq+0x10c/0x180 [ath9k]
[ 2127.919417]  [<ffffffffa0297ead>] ath_set_channel+0x9d/0x220 [ath9k]
[ 2127.919435]  [<ffffffffa029823e>] ath9k_config+0x20e/0x270 [ath9k]


**sudo iwlist scan**
[sudo] password for caz:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy


*********************************************

---

### Post by chenxiaolong on 2010-04-11
Wow, I feel embarrassed typing this short post in response to your long post :D.

Unfortunately, the Atheros AR928x wireless card is not supported very well under Linux. I've had a computer that had this wireless card earlier and ended up returning it because of the disconnects. I started another thread on this issue at the time ([http://ubuntuforums.org/showthread.php?t=1205318](http://ubuntuforums.org/showthread.php?t=1205318)), but nothing has been solved yet :(.

---

### Post by pytheas22 on 2010-04-11
**CaronMargarete**: as chenxiaolong writes above, the ar928x chips (the model of wireless card that you have) still don't have great support on Linux.

As for ndiswrapper, that also unfortunately will not work for this particular type of wireless card, so there's no need to try to find the .inf file and all that--even if you install everything correctly, ndiswrapper still won't work properly in this case.

However, what may help is to install some "backports" packages.  These provide updated versions of certain software, based on more up-to-date code than that which was available when Ubuntu 9.10 (the version of Ubuntu you have) shipped last fall.  (Normally most software on your system is brought up-to-date when you run the standard update utility, but certain low-level pieces of the system, including wireless drivers, are generally not dealt with by Ubuntu updates.  That's why you need to download these "backports" packages to get more recent versions of wireless drivers.).  You can install them by typing these commands (you will need to have an Internet connection in order to download the packages):
```

sudo apt-get update
sudo apt-get install linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic
```

According to [this thread]("http://ohioloco.ubuntuforums.org/showthread.php?t=1309605"), the backports modules helped several other people who were having issues with the ar928x driver dropping connections on Ubuntu 9.10.  It's worth a try for you.

After installing the modules, you will need to reboot for the updated version of the driver to take effect.  Hopefully that will do the trick for you.  If not, let us know and we can look at other solutions (namely, compiling drivers from source code).

---

### Post by CaronMargarete on 2010-04-12
Thanks chenxiaolong, when I had a looksee at your link it didn't make any more sense to me than reading French. I'm afraid I really am a total newbie but I do appreciate you coming by and giving what help you could...

That said, pytheas22, a thank you to you for something I could work with. I have done as you have suggested and so far it hasn't dropped out. I'll keep working over the next 24hours and we'll see how it goes. Will let you know. 

Thanks again to both of you for your help!

---

### Post by chenxiaolong on 2010-04-13
That's okay. Ubuntu makes more sense after you start using it for a while :D.

---

### Post by CaronMargarete on 2010-04-14
I'm pleased to announce that while the signal is low (improves intermittently at different times of the day) there has been no more drop outs! 

Yah!!!

So if you have an idea if there is something I can do to increase the signal that would be great but I have a good feeling it has more to do with where I am rather than my laptop. 

Thanks again for your help guys. I truly appreciate the support!
Caron Margarete

---

### Post by pytheas22 on 2010-04-14
Glad to hear it seems to be working better.  You might possibly get better signal strength if you recompiled the drivers using the very latest source code, but that's almost certainly more trouble and risk than it's worth.  If things are working well enough now, I'd stick with the current configuration.

I'm not sure what the status of the ath9k driver is in Ubuntu 10.04, the newest version to be released in a couple of weeks, but with any luck your wireless will "just work" in that version (if you choose to upgrade) without any special configuration.

Enjoy Ubuntu!

---

### Post by akikumar on 2010-04-14
Nothing is working for me, first try to connect wireless at home then shove the cable in from modem but nothing at all happen

My driver is ar9285

Below is few details Only copying the error part..My system is HP DV 4 PAVALLION

I have another lap top through which i can download all the packages...its a wireless connection..so i downloaded compact wireless and others as told by people but nothing is working fr me


Tried compact wireless
/home/akshay/compat-wireless-2010-04-13/net/mac80211/driver-ops.h: In function ‘drv_prepare_multicast’: 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/driver-ops.h:92: warning: passing argument 2 of ‘local->ops->prepare_multicast’ from incompatible pointer type 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/driver-ops.h:94: error: dereferencing pointer to incomplete type 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c: In function ‘__check_ieee80211_disable_40mhz_24ghz’: 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c:37: warning: return from incompatible pointer type 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c: In function ‘ieee80211_alloc_hw’: 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c:394: error: implicit declaration of function ‘__hw_addr_init’ 
make[3]: *** [/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.o] Error 1 
make[2]: *** [/home/akshay/compat-wireless-2010-04-13/net/mac80211] Error 2 
make[1]: *** [_module_/home/akshay/compat-wireless-2010-04-13] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
make: *** [modules] Error 2 


After that tried madfi

make

/home/akshay/Desktop/aKI/madwifi-0.9.3.2/ath/if_ath_pci.c:203: error: 'struct net_device' has no member named 'owner' 
make[3]: *** [/home/akshay/Desktop/aKI/madwifi-0.9.3.2/ath/if_ath_pci.o] Error 1 
make[2]: *** [/home/akshay/Desktop/aKI/madwifi-0.9.3.2/ath] Error 2 
make[1]: *** [_module_/home/akshay/Desktop/aKI/madwifi-0.9.3.2] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
make: *** [modules] Error 2 


lspci -v
     02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01) 
	Subsystem: Hewlett-Packard Company Device 303f 
	Flags: bus master, fast devsel, latency 0, IRQ 10 
	Memory at d6400000 (64-bit, non-prefetchable) [size=64K] 
	Capabilities: <access denied> 

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:bf:9d:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:192582150 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:245 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:7280 (7.2 KB)  TX bytes:7280 (7.2 KB) 

eth0      Link encap:Ethernet  HWaddr 00:26:22:bf:9d:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:192582150 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:245 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:7280 (7.2 KB)  TX bytes:7280 (7.2 KB) 

eth0      Link encap:Ethernet  HWaddr 00:26:22:bf:9d:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:192582150 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:245 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:7280 (7.2 KB)  TX bytes:7280 (7.2 KB) 

akshay@akshay:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

akshay@akshay:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge 
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
uvcvideo               63240  0 
snd_timer              29704  2 snd_pcm,snd_seq 
psmouse                61972  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
compat_ioctl32          9344  1 uvcvideo 
serio_raw              13316  0 
videodev               41600  1 uvcvideo 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
pcspkr                 10496  0 
v4l1_compat            21764  2 uvcvideo,videodev 
soundcore              15200  1 snd 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm 
leds_hp_disk           10756  0 
led_class              12036  1 leds_hp_disk 
joydev                 18368  0 
video                  25360  0 
lis3lv02d              17848  0 
output                 11008  1 video 
usb_storage            82880  1 
r8169                  40836  0 
mii                    13312  1 r8169 
fbcon                  46112  0 
tileblit               10752  1 fbcon 
font                   16384  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit 


finally shoving the cable in to use some apt get remedies here but
AFTER CONNECTING IT TO Motorola cable modem 

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:26:22:bf:9d:51  
          inet6 addr: fe80::226:22ff:febf:9d51/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:184549365 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:245 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 


in the connection manager it is showing
autoeth0 but nothing after some time it pops up no wired connection

---

### Post by akikumar on 2010-04-14
I think i need to mention 

My kernal is

2.6.28-11-generic 

and Have Jaunty

---

### Post by pytheas22 on 2010-04-14
**akikumar**: it would be good to know the device ID of your wireless card, and a little extra information.  Please post the output of these commands:

```
lspci -nn
modinfo ath5k
modinfo ath9k
modinfo ath_pci
```

---

### Post by akikumar on 2010-04-15
I dual booted it with window 7 ........so when i need net i restart it n go to windows .....connect through wirelesss ..i dont have access to wired net 





```

```akshay@Gladiator:~$ lspci -nn
  
  00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0044] (rev 02)
  
  00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0046] (rev 02)
  
  00:16.0 Communication controller [0780]: Intel Corporation Ibex Peak HECI Controller [8086:3b64] (rev 06)
  
  00:1a.0 USB Controller [0c03]: Intel Corporation Ibex Peak USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
  
  00:1b.0 Audio device [0403]: Intel Corporation Ibex Peak High Definition Audio [8086:3b56] (rev 05)
  
  00:1c.0 PCI bridge [0604]: Intel Corporation Ibex Peak PCI Express Root Port 1 [8086:3b42] (rev 05)
  
  00:1c.1 PCI bridge [0604]: Intel Corporation Ibex Peak PCI Express Root Port 2 [8086:3b44] (rev 05)
  
  00:1c.2 PCI bridge [0604]: Intel Corporation Ibex Peak PCI Express Root Port 3 [8086:3b46] (rev 05)
  
  00:1c.3 PCI bridge [0604]: Intel Corporation Ibex Peak PCI Express Root Port 4 [8086:3b48] (rev 05)
  
  00:1d.0 USB Controller [0c03]: Intel Corporation Ibex Peak USB2 Enhanced Host Controller [8086:3b34] (rev 05)
  
  00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
  
  00:1f.0 ISA bridge [0601]: Intel Corporation Ibex Peak LPC Interface Controller [8086:3b09] (rev 05)
  
  00:1f.2 SATA controller [0106]: Intel Corporation Ibex Peak 4 port SATA AHCI Controller [8086:3b29] (rev 05)
  
  00:1f.3 SMBus [0c05]: Intel Corporation Ibex Peak SMBus Controller [8086:3b30] (rev 05)
  
  00:1f.6 Signal processing controller [1180]: Intel Corporation Ibex Peak Thermal Subsystem [8086:3b32] (rev 05)
  
  02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
  
  03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 04)
  
  03:00.1 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5288] (rev 01)
  
  03:00.2 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5288] (rev 01)
  
  7f:00.0 Host bridge [0600]: Intel Corporation Device [8086:2c62] (rev 02)
  
  7f:00.1 Host bridge [0600]: Intel Corporation Device [8086:2d01] (rev 02)
  
  7f:02.0 Host bridge [0600]: Intel Corporation Device [8086:2d10] (rev 02)
  
  7f:02.1 Host bridge [0600]: Intel Corporation Device [8086:2d11] (rev 02)
  
  7f:02.2 Host bridge [0600]: Intel Corporation Device [8086:2d12] (rev 02)
  
  7f:02.3 Host bridge [0600]: Intel Corporation Device [8086:2d13] (rev 02)```

```








    ```

```akshay@Gladiator:~$ modinfo ath5k
  
  filename:       /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ath5k/ath5k.ko
  
  version:        0.6.0 (EXPERIMENTAL)
  
  license:        Dual BSD/GPL
  
  description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
  
  author:         Nick Kossifidis
  
  author:         Jiri Slaby
  
  srcversion:     A29DFCA2F56F1FD810F5FA0
  
  alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
  
  alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
  
  alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
  
  depends:        led-class,cfg80211,mac80211
  
  vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 ```

```




    ```

```akshay@Gladiator:~$ modinfo ath9k
  
  filename:       /lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko
  
  license:        Dual BSD/GPL
  
  description:    Support for Atheros 802.11n wireless LAN cards.
  
  author:         Atheros Communications
  
  srcversion:     5530FD7F98BD55CB1169801
  
  alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
  
  depends:        led-class,mac80211
  
  vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 ```

```




    ```

```akshay@Gladiator:~$ modinfo ath_pci
  
  filename:       /lib/modules/2.6.28-11-generic/volatile/ath_pci.ko
  
  srcversion:     D3FD3BD11169A96DBCFF8DE
  
  alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
  
  alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
  
  alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
  
  alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
  
  depends:        ath_hal,wlan
  
  vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 
  
  license:        Dual BSD/GPL
  
  version:        0.9.4
  
  description:    Support for Atheros 802.11 wireless LAN cards.
  
  author:         Errno Consulting, Sam Leffler
  
  parm:           countrycode:Override default country code (int)
  
  parm:           maxvaps:Maximum VAPs (int)
  
  parm:           outdoor:Enable/disable outdoor use (int)
  
  parm:           xchanmode:Enable/disable extended channel mode (int)
  
  parm:           rfkill:Enable/disable RFKILL capability (int)
  
  parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
  
  parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
  
  parm:           ath_debug:Load-time debug output enable (int)```

```

---

### Post by akikumar on 2010-04-15
Sorry I forget to put then in code format will take care of this from next time

---

### Post by akikumar on 2010-04-15
[http://ubuntuforums.org/showthread.php?t=1447901](http://ubuntuforums.org/showthread.php?t=1447901)


thinking of trying this......did any one give steps wont i have to install mad fi fr this

---

### Post by pytheas22 on 2010-04-15
**akikumar**: so, this is what's wrong for you: the driver for Atheros 9xxx-based wireless cards that ships by default with Ubuntu 9.04, which is named ath9k, does not support your particular model of wireless card (with device ID 168c:002b) because your card is too new.  In order to get wireless working, therefore, you need a more recent version of the ath9k driver.

To get that, you have three options:

1. compile the compat-wireless stack from source using the latest code.  You tried this and the compilation failed; I'm not sure why and this may be difficult to solve without having any Internet connection available on Ubuntu.

2. install the linux-backports-modules-jaunty package, which should provide a version of the ath9k driver that will support your device (I can't confirm this because I don't have a jaunty system available).  To get that package, you will need an Internet connection, however.

3. upgrade to Ubuntu 10.04, which should support your wireless card out-of-the-box.  Ubuntu 10.04 won't be officially released for a couple more weeks, but the beta version should be relatively stable now.  You can download the Ubuntu 10.04 beta CD at [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/).

If I were you, I'd probably go with option 3, because that will give you a more up-to-date version of Ubuntu itself.  But depending on how much you have invested in your current system, this may or may not make sense.

If you want to try going with options 1 or 2 and need help, let me know and I'll do my best to guide you.
> 
[http://ubuntuforums.org/showthread.php?t=1447901](http://ubuntuforums.org/showthread.php?t=1447901)


thinking of trying this......did any one give steps wont i have to install mad fi fr this 

That's for a different issue.  I don't see any reason why that would help in your case, unfortunately.

Also, I'm not positive that madwifi will support your wireless card, because I'm not sure if the madwifi developers are implementing support for newer Atheros 9xxx chips, or if they're just maintaining the old ones.  The only driver that I'm sure provides support for your card is ath9k, which is part of the compat-wireless stack.

---

### Post by Chronon on 2010-04-15
> **pytheas22 said:**
> Ah, sorry to hear you may be having hardware difficulties, but at least that helps clear up what was wrong.  Maybe you should try playing around with your router's settings--it could be that something got changed there, rather than a problem with the wireless card.  In any case, good luck!

You are correct.  After playing with it a bit, it seems my wireless router has problems.  The router bit works but the WiFi part doesn't seem to work well.  After resetting settings it seems to work for a few days.  Then it returns to not allowing connections via WiFi.  My desktop system is plugged into the RJ45 connector on the back of the router and has no connectivity issues.

I have tried WPA, WEP and No security and I still cannot reliably connect.  Anyway, I can happily report that the compat-wireless drivers are working just fine for me.  I will look elsewhere for possible actions to take for my Netgear router.

Thank you for your patient assistance.  I appreciate it.

---

### Post by CaronMargarete on 2010-04-16
> **pytheas22 said:**
> ...that's almost certainly more trouble and risk than it's worth.  If things are working well enough now, I'd stick with the current configuration 

Completely agree that stuffing with something that works now just to get it a little better would be an insane notion. 

I'm going to do the upgrade but I'm just wondering if I'll have to install the same things as I just did for Koala again??? Guess I'll find out and write again if it doesn't work...

Thanks again, it's people like you that make trying something new worth it. I appreciate you.

---

### Post by akikumar on 2010-04-16
> **pytheas22 said:**
> **akikumar**: so, this is what's wrong for you: the driver for Atheros 9xxx-based wireless cards that ships by default with Ubuntu 9.04, which is named ath9k, does not support your particular model of wireless card (with device ID 168c:002b) because your card is too new.  In order to get wireless working, therefore, you need a more recent version of the ath9k driver.

3. upgrade to Ubuntu 10.04, which should support your wireless card out-of-the-box.  Ubuntu 10.04 won't be officially released for a couple more weeks, but the beta version should be relatively stable now.  You can download the Ubuntu 10.04 beta CD at [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/).
.

Well Thanks ! I am going for option 3 now..will let you know soon

Thanks

Aki

---

### Post by fogNL on 2010-04-16
> **akikumar said:**
> 
Tried compact wireless
/home/akshay/compat-wireless-2010-04-13/net/mac80211/driver-ops.h: In function ‘drv_prepare_multicast’: 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/driver-ops.h:92: warning: passing argument 2 of ‘local->ops->prepare_multicast’ from incompatible pointer type 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/driver-ops.h:94: error: dereferencing pointer to incomplete type 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c: In function ‘__check_ieee80211_disable_40mhz_24ghz’: 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c:37: warning: return from incompatible pointer type 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c: In function ‘ieee80211_alloc_hw’: 
/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.c:394: error: implicit declaration of function ‘__hw_addr_init’ 
make[3]: *** [/home/akshay/compat-wireless-2010-04-13/net/mac80211/main.o] Error 1 
make[2]: *** [/home/akshay/compat-wireless-2010-04-13/net/mac80211] Error 2 
make[1]: *** [_module_/home/akshay/compat-wireless-2010-04-13] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic' 
make: *** [modules] Error 2 


I had that same compile error, and after some research, it looks like it was introduced around April 1st commit.  I downloaded the archive from march 28th, and it compiled correctly for me...
[http://www.orbit-lab.org/kernel/compat-wireless-2.6/2010/03/compat-wireless-2010-03-28.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2010/03/compat-wireless-2010-03-28.tar.bz2").  Give that a shot and see if you have any better luck.

---

### Post by pytheas22 on 2010-04-16
> I'm going to do the upgrade but I'm just wondering if I'll have to install the same things as I just did for Koala again??? Guess I'll find out and write again if it doesn't work...

If you upgrade over the Internet, you shouldn't have to reinstall everything, because all of your current applications and settings will be preserved; they'll just be replaced with more recent versions where relevant.

If you have issues upgrading, you could instead install Ubuntu 10.04 from scratch, and then obviously you'd need to reinstall/reconfigure everything again to your liking.  But I assume that's not what you're planning on doing.

As a word of advice: if you're going to upgrade over the Internet, wait a few days after the new release comes out to do it; otherwise you can run into issues because Ubuntu's servers get bogged down by everyone else trying to upgrade, and it can take days to get the files you need.

**akikumar**: sounds good.  Also note cquilliam's comment above (post #110) which makes a very useful point about how to compile compat-wireless from source without running into errors, in case you decide to go that route instead.

---

### Post by CapnGimp on 2010-04-16
HP G60-519WM laptop with the atheros 9285 wifi, I have Ubuntu STudio 10.4 B installed. lspci -nn identifies it but I still have no wireless. Ran all the updates and still nada. searching the forums/web now...

---

### Post by pytheas22 on 2010-04-16
> HP G60-519WM laptop with the atheros 9285 wifi, I have Ubuntu STudio 10.4 B installed. lspci -nn identifies it but I still have no wireless. Ran all the updates and still nada. searching the forums/web now...

What is the PCI ID given by "lspci -nn"?

---

### Post by CapnGimp on 2010-04-17
Solved it... First off and the CAUSE of my heartache is that Studio doesn't install Gnome Network Manager.... so no way of utilizing wifi until I installed it. Once that was in, I pulled the cat5 rebooted(force of habit lol) and went to SYSTEM>PREFERENCES>NETWORK CONNECTIONS >which did not exist before, obviously< and input my SSID n info and it works. The system recognized it but there was no way to configure it(no gui/app) and I'm not a command line guru.   
 Anywho thanks for having a look...



 lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
john@LINUX7ubuntu:~$

---

### Post by akikumar on 2010-04-17
Well ! I checked from live cd WI FI is working out of the box, But i am facing a problem.......My computer has following partition

1. System recovery 10  gb
2. Downloads and Documents 10 GB
3. INstallatons 26 GB
4, WIndows  225 GB
5.system  1 MB


6. Free unallocated drive 100 GB

When i try to install ubuntu , i get only three drives

1 MB
200 some thingGB
200 some thing GB

I dont know what to do last time! I erased my system recovery drive whole windows got crashed....How can i specify Free unallocated drive to Ubuntu ..

Thanks

AKi

---

### Post by akikumar on 2010-04-18
I tried it again! My windows is showing from left to right  all r NTFS excpet unallocated

System 199 Mb 
Window 225.29 Gb
Installation 97.66 Gb
Document 25.44 Gb
Unallocated space 97.66 Gb
Recovery 19.43 Gb
Hp tools 104 Mb

I am trying to install UBUNTU on unallocated space, but after putting cd when i choose manual partition i am getting this
                     size                used
/dev/sda1       1Mb             
/dev/sda2        208 Mb               33360 Mb    
/dev/sda3        241900 Mb          3221
 
/dev/sda4        257996               3221



So what should i do ! 

Aki

---

### Post by chenxiaolong on 2010-04-18
Well, I don't know how you have 5 partitions as an MBR partition table (what most people use) can only handle 4, which is why Ubuntu isn't detecting all of them. You can open Gparted on the LiveCD (System - Administration - Gparted) to see what exactly Ubuntu detects.

---

### Post by CapnGimp on 2010-04-18
You can only have 4 PRIMARY partitions on a single physical drive... How many physical drives do you have? If you have more than ONE physical drive, then look up in the top right section of gparted or whatever partition manager u r using and there is a drop down menu where you choose WHICH physical disk the program is displaying the partitions of. Then choose whic h one u want.

Still not sure of the setup u have, but I am assuming you already have 4 primary partitions so you are presented with erasing one to do the install.
 
 Now here is how I do mine...A primary partion for windows, then the rest of the drive in EXTENDED partion, with logical drives sized to fit other partitions for windows docs, pics and mp3. The remaining logical partitions are unformated, so that
there are 3 possible primaries remaining.  my linux distros can then pick or me manually partition for Linux....this is what has worked for me as I always leave windows alone except for about twice a year reload it. I change linux distros as I want. 

 A total fresh install u can install windows first...I give xp 20gb, win7 40gb and the rest of the drives are logical on an extended partition...75gb each til I fill the drive...software drives for each windows, a doc drive shared between them, a mp3/picture drive and that gets win covered. If u do manual from here, it is EASY to shrink/resize the extended partition and install ubuntu or whatever linuxes u want. Holler if u need any help.

---

### Post by akikumar on 2010-04-18
ok this is third time i crashed my windows ! fr ubuntu lol ! So trying it again installing windows again from scratch ....so 
Windows will have C drive and a recovery drive and another drive of HP tools also some system of 199 mb 

Can you give me step wise instructions this time ......Plz i am screwed crashing windows so many times although i have taken all my data as a back up but it waste lot of time help help help

Also if i keep one drive unallocated wont it will be recog while installing ubuntu i want to install ubuntu in that drive

---

### Post by pytheas22 on 2010-04-18
There are good instructions on partitioning [here]("https://help.ubuntu.com/community/HowtoPartition") that should help you.

Also, if you don't want to partition, you could use [wubi]("http://wubi-installer.org") instead.

---

### Post by akikumar on 2010-04-18
Well ! I read all that But still i need help !

I have Four Primary partitions ! I reformatted my lap top 

C 446 GB
SYSTEM 199MB
RECOVERY 19.43 GB
HP TOOLS 103 MB 


Now I dont want to crash my lap top again ! For installing Linux i need to make one more primary partition But i done some googling and found that I cant may the last three partitions extended drive ..........I have HP DV 4 PAVALLION

---

### Post by akikumar on 2010-04-18
So ! What i learned from the documentation is i can choose C and make a extended partition out of it aand can install linux in that partition ! I will attempt it hope it will work
Thanks

---

### Post by akikumar on 2010-04-18
After much much much googling i came to know no body has given solution feed back.........So i am left with 4 primary partition and I dont know how i can install linux.......i deleted recovery partition last time my whole lap top crashed .....Hp tools which is 4th partition I dont have courage to delete it unless some one tell me to do it ......

Problem : 4 primary Partitions ! system , C, Recovery, HP tools ..Where to install linux

From live cd here what i c


/dev/sda1 ntfs system 199 MB  
/dev/sda2 ntfs 446 GB used 30 free 420Gb
/dev/sda3 ntfs Recovery 20 GB free 3 gb
/dev/sda4 fat32 HP tools





Now what should i do ! from here /dev/sda2 is my C drive with window OS in it......


Thanks

---

### Post by akikumar on 2010-04-18
I finally decided to put a live cd again ! and shrink C and make some free space that is unalloctable in it ! now i am getting following in the table

/dev/sda1 ntfs
/dev/sda2 ntfs
unusable
/dev/sda3 ntfs
/dev/sda4 Fat32 

When i try selecting the unusable part for linux then i get following error

No root system is defined plz ccorrect this from the partiioning menu 

tHERE IS NO option of install in free space too

---

### Post by akikumar on 2010-04-19
Success Success....Finally ubuntu is on my lap top !

People with HP DV 4 here is what u need to do ! Put a live cd in !Go go System > admin > gparted delete your HP tools partition now we have three partition ! Go to C drive free some space from it create unallocated drive and boot it again and u will get a option of installing it in free space ......and done


But i have a question ! when i selected free space manually i get message no root is define why i am getting this

Thanks Every one !

And people on ubuntu try try n try u will get what u wan finally

---

### Post by isterios on 2010-04-19
Does anyone have news for the ar928x?

I still have the same problems a lot of people met (disconnections after transfer of big files, weak signal, deauthenticating after boot etc)

I tried almost everything I read on forums, except drivers recompilation.

It's quite irritating nothing's going better months after months for this driver...

---

### Post by akikumar on 2010-04-19
Use Ubuntu 10.04 Beta 2 ! Its perfect ! No disconnections ......WI fi works out of the box !
I am having ar9285....


Thanks

AKshay

---

### Post by pytheas22 on 2010-04-19
> Use Ubuntu 10.04 Beta 2 ! Its perfect ! No disconnections ......WI fi works out of the box !


Glad to hear you've got it sorted out :)

> Does anyone have news for the ar928x?

I still have the same problems a lot of people met (disconnections after transfer of big files, weak signal, deauthenticating after boot etc)

I tried almost everything I read on forums, except drivers recompilation.

It's quite irritating nothing's going better months after months for this driver...

Have you installed the linux-backports-modules-jaunty package?  You could also see if things work better in Ubuntu 10.04 (using the beta, or waiting for the stable release in a couple weeks).

---

### Post by akikumar on 2010-04-19
I was a Mac user a year back! then moved to windows finally to Ubuntu ! And just want to tell Its supereb ! Its more or less like Mac ! I love it ! Ubuntu 10.04 is working like a Knife in hot butter  ....:):guitar:.....Again ! Try following steps if ur not sucessful move to 10.04

1. Try installing compact wireless
[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)
2. if its not working try linux backport jaunty package
[http://packages.ubuntu.com/search?keywords=linux-backports-modules-jaunty](http://packages.ubuntu.com/search?keywords=linux-backports-modules-jaunty)
3. fail again try madfi
[http://wireless.kernel.org/en/users/Drivers/madwifi](http://wireless.kernel.org/en/users/Drivers/madwifi)

Now ! if u fail in all three process install 10.04 beta :) it will work perfectly....I am sure

Thanks Every one

AKshay

---

### Post by isterios on 2010-04-20
> **pytheas22 said:**
> 

Have you installed the linux-backports-modules-jaunty package?  You could also see if things work better in Ubuntu 10.04 (using the beta, or waiting for the stable release in a couple weeks).

I am using Karmic, but yes I installed linux-backports-modules-wireless-karmic-generic:
Package: linux-backports-modules-wireless-karmic-generic
New: yes
State: installed
Automatically installed: no
Version: 2.6.31.20.33

and:
linux-backports-modules-karmic
linux-backports-modules-karmic-generic





It didn't change anything for me :(

---

### Post by akikumar on 2010-04-29
update it to stable release now

---

### Post by isterios on 2010-05-14
Finally I found the solution for my case:

in summary, I tried everything I read without sucess (backports, blacklisting of ath9k, compat drivers, bluetooth desactivation etc.)

My symptoms were regular disconnections, blank connections (said connected but not) and sometimes difficulties to reconnect.

My solution is just to force the speed on my router in 802.11N (I was before in G/N). No more problems since.

It seems that the driver for this card manages very badly the G speed.

---

### Post by ubudyr on 2011-07-18
When I started working as a programmer I spent my a day with an Ampex terminal on a UNIX System III computer. A lot has happened since then so I must admit I am a bit lost with Ubuntu. So it's really great with this forum and all the information you can get.

As a lot other people contributing in this thread I also spent a lot of time getting the Atheros AR92X Wi-Fi to work. I have an Acer Aspire 7730Z and installing Ubuntu really went smoothly. Unfortunately the Wi-Fi was unstable. The connection toggled on and off and kept prompting for the password.

I tried several solutions I found but none of them worked. Then I saw the suggestion in this thread to simply remove and insert the module. And it works! You just have to do:

Alt-F2 and enter "gksudo xterm" to get a terminal.

```
modprobe -r ath9k
modprobe ath9k
```So I put the attached script in /etc/init.d and created a symbolic link:

```
ln -s /etc/init.d/atheros.sh /etc/rc2.d/S99atheros
```and now the wifi is rock steady.

---

### Post by Captain Easypants on 2011-08-23
> **isterios said:**
> 

My solution is just to force the speed on my router in 802.11N (I was before in G/N). No more problems since.

It seems that the driver for this card manages very badly the G speed.

I know it's been a while but did you do this on the router itself or did you find a way to do this on the card? Because I have devices on my network which are only 802.11G so I can't force the router into n only mode.
I've had a quick look and I can't find any way to force the chip itself into n only mode

---

### Post by pytheas22 on 2011-08-24
> I know it's been a while but did you do this on the router itself or did you find a way to do this on the card? Because I have devices on my network which are only 802.11G so I can't force the router into n only mode.
I've had a quick look and I can't find any way to force the chip itself into n only mode

In principle you should be able to force 11n with the iwconfig command:
```

sudo iwconfig wlan0 modu 11n
```

But this doesn't always work in practice.  For more information check on the "modu[lation]" section of the [iwconfig manpage]("http://manpages.ubuntu.com/manpages/hardy/man8/iwconfig.8.html").

---

### Post by punx2400 on 2011-09-27
Mine's not working either on my Asus G72GX.  However, I'm not using Ubuntu.  I'm using windows 7....  any idea how to fix the problem with windows?

---

### Post by chenxiaolong on 2011-09-28
Hmmm...if it doesn't work under Windows, it's probably either a driver problem or faulty hardware. Try downloading the wireless driver from ASUS's website here: 

```
http://support.asus.com/download.aspx?m=G72GX
```

If that doesn't work, I'd call ASUS and see if they can fix it (if your warranty hasn't expired).

Of course you can also download the Ubuntu Live CD too to test the wireless, since the Atheros cards work perfectly fine under Linux now... :)

---

### Post by cckspe on 2011-09-30
Oh Boy another noob, sorry!
I'm having similar problems with my PBell easynote, windows reports the network card as an AR5B93. I cannot log onto my BTHomeHub2 even with the security settings removed completely BUT I can log on to my BTFon/Openzone and get full access to the net, this is running from my hub. Tried loading ndiswrapper but to no avail and have loaded Mint (Ubuntu) but same result. Any ideas.

---

### Post by pytheas22 on 2011-09-30
**cckspe**: first of all, are you sure your BTHomeHub2 is not configured to filter MAC addresses?  If that's not the problem, I would try changing the wireless channel and/or mode on the router--e.g., if the router is currently in 11b/11g mixed mode, try only 11g, or vice-versa.  Sometimes changes like this can help in situations where you can connect to one router but not another.

You should also look at your dmesg output after trying to connect (just type "dmesg" in a terminal).  It may provide information on what's not working.  If you don't know how to interpret the output you can post it here.

---

### Post by cckspe on 2011-09-30
[RIGHT]ok m8 thanks for the pointers I'll go have a nosy just now and see whats what.
[/RIGHT]

---

### Post by omelette on 2011-10-02
Am I correct in thinking that Ndiswrapper does NOT work for this chipset?
  
I've just installed Ndiswrapper, downloaded the M$ driver but can't get it to work - although it installs ok, rebooting or modprobing ndiswrapper doesn't even find the wireless hardware.  I've had some success with Ndiswrapper with another Atheros card sos I'm  pretty sure I'm doing things right...

---

### Post by omelette on 2011-10-03
A little progress.  Most people seem to be sourcing their M$ driver from this site - [http://www.atheros.cz/]("http://www.atheros.cz/").  The thing is that although you are presented with an extensive selection (multiple OS's etc) in reality there is just one download for this driver -** and it's a Vista/System7 driver, which is not NDiswrapper-compatible, it will only work with XP-drivers!**

Luckily I had a system disk from a mini-pc which contained the driver and I've uploaded it in case someone wants to try it;

[http://ubuntuone.com/2drDSaucgcVc78ZYfAITTH]("http://ubuntuone.com/2drDSaucgcVc78ZYfAITTH")

Now the Ndiswrapper-installed driver is instantly picked up by the kernel.  But that's as good as it gets.  Trying to set up a ad-hoc network, it resolutely refuses to create any sort of network connection, just scanning & scanning - it even does the same when set to "share to other computers" which requires no connection to be completed, which is maddening.  Trying to assign it a client-role & connect to another pc also fails.  Also, disabling encryption has no effect...

I'm sure if there is a hell, it's networked by Linux/ad-hoc wireless boxes! :twisted: Linux's wireless sucks generally, but the ad-hoc support is really shambolic and doesn't even appear to be tested in many cases. For instance, running the latest Hiren 14.1 rescue-cd and in Linux-LiveCD-mode, the latest & greatest WiCD cannot be used to join a ad-hoc network, complaining about a bad-password. And the reason seems clear - it flashes up text saying "WPA" when it tries to connect! Something that the developers would have immediately caught had they ever tried it!  What sucks is that ad-hoc networking works perfectly if you choose to boot in XP_LiveCD-mode... Also, on Mageia, the latest KDE's Network-Manager is practically useless with ad-hoc, being relegated to no more than a glorified applet as you can only connect to 'system-created' networks & which it cannot edit in any way. Create a connection through it and it refuses to connect with it...

---

### Post by pytheas22 on 2011-10-04
**omelette**: ndiswrapper can be fickle.  You might have better luck if you use a different version of the Windows driver--e.g., try the Windows 2000 driver, or version 1.0 of the driver instead of 2.0.

By the way, I don't know what your situation is, but perhaps you could avoid ad-hoc networking altogether by setting up another Linux computer as an AP station.  One of the nice things about Linux wireless is that most of the native drivers now support AP mode, allowing you essentially to use your computer as a real router, without doing ad-hoc.  Ad-hoc support may not be as solid as you would like (although it sounds like the issues you're having have more to do with the particular clients you're using than the wireless drivers), but Linux does make a quite impressive showing when it comes to advanced wireless features.  I've only very rarely heard of any Windows wireless drivers supporting AP mode, for instance.

---

### Post by omelette on 2011-10-05
@pythes22 - Thanks, your info about AP's had me scurrying off looking it up - I thought there was only 2 options available!  Unfortunately the current Ubuntu 10.04LTS wireless driver does not appear to support 'Master' mode which from my reading of the Ubuntu WIFI docs seems to be a prerequisite. :(

I'm doubtful that a Win2k ar928x driver exists, at least it's not listed as being available at the above Atheros-drivers site, and even finding 'newer' XP Atheros-drivers is a chore (above site excepted) which surprised me.

What sticks in my craw regarding Linux & ad-hoc is that it is obvious (to me anyway!) that developers no longer even support this mode now, never mind fix the multiple bugs that exist!  The one recent exception to this rule seems to have been a kernel-bug (2.6.38-8 if memory serves) that effects the client-side of an ad-hoc connection - at least with Fedora, this bug had been identified & removed with 2.6.40. Incidentally the then brand-new Ubuntu 11.04 also suffered from this, and probably still does given Ubuntu's lethargic kernel updates!  This and a buggy Gnome3 was the reason I switched back to my reliable old Ubuntu 10.04LTS.

I've been threatening to get a router for ages, maybe the time has arrived...

---

### Post by pytheas22 on 2011-10-05
**omelette**: I've never done master mode on Ubuntu myself, but I think it should work as long as your driver supports it.  But that depends on which particular driver you're using, which in turn depends on your wireless chipset.  With some drivers the support is not yet there.

By the way, have you tried using the ath9k driver (which [does support master mode]("http://www.linuxquestions.org/questions/linux-networking-3/master-mode-on-ar928x-using-ath9k-driver-756247/"), by the way) to drive your device?  If it's an ar928x chip it should work--although if it's really new perhaps you'll have to compile the driver from source using the latest code rather than Ubuntu's version.

Or, yes, just buy a router--they're quite cheap these days :)

---

### Post by omelette on 2011-10-07
@Pytheas22 - Some more searching revealed that Master-mode is indeed possible with my chipset, it just that my simplistic 'iwconfig' check wasn't enough - iwconfig can't initialise Master-mode.  So I've made some more progress, when I finally managed to get the AP up and running, all the problems I was experiencing with over the ad-hoc link - long-winded version available here-> [http://ubuntuforums.org/showthread.php?p=11305314#post11305314]("http://ubuntuforums.org/showthread.php?p=11305314#post11305314") - seems to have vanished!

The bad news, getting an AP running proved a bit of a nightmare.  In principle it's fairly simple - just install 'hostapd',  configure hostapd.conf, allow it to auto-start at boot by enabling it in /etc/default/hostapd (the default is 'disabled' which is just plain silly).  Once done, iwconfig list wlan0 as being in Master-mode and the client picks it up as such.  But that's it, it absolutely refuses to complete the connection!  After many hours I finally managed to 'fudge' it by enabling a ad-hoc connection, disabling & re-enabling ath9k then finally restarting hostapd...

Turns out I'm not to first to come across this either and a solution appears elusive.  Someone said the fix was to build the compat-wireless drivers from the latest source, which I did but was no help.  Then I found someone else saying that it's hostapd that's the problem, so I tried & failed at re-building that - my 10.04LTS has too many old core-libraries and I kept getting 'too old a version' failures.  But for the latest Ubuntu's it should be pretty simple to build.

So at least I have the satisfaction of having a more secure wpa2 connection at the moment, even if it's not really viable long-term.

---

### Post by pytheas22 on 2011-10-07
**omelette**: sorry to hear AP mode didn't turn out to be as effective in practice as in theory, but kudos to you for going to so much work trying to get it up and running.  It may be that the driver support just isn't really there yet for your chip, unfortunately.  But where would be the fun in Linux if it always worked perfectly? :)

---

### Post by omelette on 2011-10-08
@pytheas22 - if 'fun' is synonymous with Linux not working perfectly then its one hell of a party we've got going here! :lolflag:

For what it's worth, I had another go at compiling 'hostapd' and succeeded largely as a result of finding a Wiki-entry on hostapd which listed the error I was getting & the solution - I just needed to install 'libssl-dev'. Didn't help though.  I built both 0.6.10 and 0.7.3 versions successfully but none of them even run properly, each producing different error(s).  In fact the only ones that runs properly (not connecting excepted!) is 0.6.9 - the one in the repository.  So I've had enough of it and will leave it at that.

---

### Post by omelette on 2011-11-10
Just thought I'd post a little update regarding my experience with AP-networking connections - its been a whole month now! - just in case some long-suffering ad-hoc users happen to google across my problem.

It turns out that the Linux ad-hoc implementation is even more crappy than I had assumed.  Since I've been using AP's, another networking bug that I had thought was unrelated to ad-hoc has completely vanished, namely the ad-hoc network share just disconnecting, mainly when data-throughput was high.  To give you an idea of how bad this was, while downloading a 800meg torrent, it disconnected 6 times!  Until I figured out how to restart the ad-hoc connection manually, I had actually been reduced to restarting the computer each time this happened, which made the whole thing barely usable.  This nightmare has completely vanished with AP-connections!

It's actually pretty simple to implement too, the only niggle being that the server-side of things needs to be started manually when the computer (re)starts,  but once everything is setup, this just involves a single **"sudo service hostapd restart"** command.  Very important though, even though you are now using AP/WPA2 connections, you must setup and run a 'dummy' ad-hoc connection as well - otherwise, the client-side fails to connect!  And if you are nervous about the obvious security considerations of an open-but-unused ad-hoc connection, you can safely disable/delete it once the AP connection is running, but as I mentioned, if you reset the computer, it will be needed again.  Personally, I just set up a 128bit-key ad-hoc connection and leave it running, as another one of ad-hoc's numerous bugs seems to be that it will only connect with the 40bit key - so even if someone still had the password, they still couldn't connect with it!

In conclusion, imo AP rocks and anyone still using ad-hoc should switch immediately!

---

### Post by pytheas22 on 2011-11-12
omelette: so you finally got hostap working?  Did you use the version in the repositories?

---

### Post by omelette on 2011-11-15
Hi pytheas22.  Yes, I am using the version in the repositories.  As I mentioned, I managed to compile 2 more-recent versions of hostapd, which included the latest,  but for some reason, neither work properly or not at all - at least with Ubuntu 10.04LTS.

And like I said, it may not be ideal as it stands but it's an order of magnitude better than ad-hoc. :)

---

### Post by omelette on 2012-03-11
This is just for the random Googlers who are searching for XP drivers for this chipset still.  I spent an insane amount of time on this chipset & WEP networks, before finding some sanity with AP networks, and finally doing the really sane thing and buying a router!  Anyway, like an itch that just won't go away, I started playing with NDiswrapper again today, after finding a new (to me!) driver website that looked promising - and ho & behold, all the problems vanished!  It was all a case of finding the right driver!!!  Although with a router & WPA, NDiswrapper isn't needed as the Linux driver seems to work perfectly. Much better in fact - NDiswrapper only seems to cater for 54Mb/s b/g networks, whereas the Linux driver works great with the much faster 11n as well. :)

It also gave me courage to have another go with a different NIC that has nearly driven me to distraction over the years - a Dlink DWL-G520 - this is one that the Linux developers just didn't put much effort into imo, so NDiswrapper is essential.  And rather than just hope the driver matched the chipset, I made sure this time by removing the cards shielding (just a couple of screws) and eye-balling the chip - turned out to be a 5212 - something I should have done years ago! This driver worked first time as well which amazed & delighted me. :)

**The driver-site in question is - **[www.nodevice.com]("www.nodevice.co/driver")

and in case it ever vanishes, below are links to the 2 'worked-for-me' drivers.
**Atheros AR5212** - [http://ubuntuone.com/2oW8EC3yzyo3b38xY15DDH]("http://ubuntuone.com/2oW8EC3yzyo3b38xY15DDH")
**Atheros AR928X** - [http://ubuntuone.com/3BZVN476Qv0FMK5RcZLds6]("http://ubuntuone.com/3BZVN476Qv0FMK5RcZLds6")

---

### Post by TBABill on 2012-03-12
For anyone previously struggling with their AR928* adapter, my 9287 absolutely flies with NO configuration necessary in 12.04. I had to tweak it in prior versions but it seems fixed now.

---

