---
title: "RT61: Followed kevdog's summary, but not quite working yet"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by schwim on 2007-10-19
Hi there everyone,

Fresh install/all updates

Linksys WPM54G

Kevdog was kind enough to summarize and alter the little tutorial for the 73 card, making it pertain more to the 61 card(thread [here]("http://ubuntuforums.org/showthread.php?t=499617&highlight=rt61+blacklist&page=2")).

I followed the instructions as closely as I could.  I didn't have a cd, so I ran the aptitude commands without it.  Also, the download had the files in a Modules subdir of the extracted tar.gz, so I didn't do the make & make install commands from the parent directory, but inside the subdir Modules.  Lastly, I saw earlier in the thread that you were supposed to blacklist rt61pci, so I added that to the blacklist that kevdog posted, since it didn't say anything about that particular driver there.

all of the commands executed without error.  I ran modinfo before restart:

> 
schwim@schwim-basement:~/serial_monkey/rt61-cvs-2007101921/Module$ modinfo rt61
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
license:        GPL
description:    Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS CVS
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     180F8980D3385B365E8F654
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)
parm:           ifname:Network device name (default ra%d) (charp)
schwim@schwim-basement:~/serial_monkey/rt61-cvs-2007101921/Module$ 
I rebooted.

On reboot, My wireless network was again detected.  It utilizes a WEP key, but no WPA.  I entered the WEP key and hit enter.  After about a minute, the same thing happened that always happens, no connection established.

ifconfig:
> 
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:2A:9C:DF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:0A:E6:2A:9C:DF  
          inet addr:169.254.9.32  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:632 (632.0 b)  TX bytes:632 (632.0 b)

ra1       Link encap:Ethernet  HWaddr 00:1C:10:E3:51:37  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:776 errors:3 dropped:0 overruns:0 frame:0
          TX packets:533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66624 (65.0 KiB)  TX bytes:144 (144.0 b)
          Interrupt:20 
iwconfig:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"SchwimNet"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=98/100  Signal level:-33 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
I sure would appreciate any help in the matter if someone could help me figure out what else I might try from here to get wireless working.

thanks,
json

---

### Post by schwim on 2007-10-20
I have tried everything I can think of without success.  I have tried manually entering the data, assigning a static IP(which makes it look like it's working, but it's not) and have had no luck.

Any suggestions would be greatly appreciated, as I'm going batty!

thanks,
json

---

### Post by unisol on 2007-10-20
try this from a terminal:

ifconfig wlan0 up
iwconfig wlan0 mode managed
iwconfig wlan0 essid "my network"
iwconfig wlan0 channel your channel
iwpriv wlan0 set NetworkType=Infra
iwpriv wlan0 set AuthMode=WPAPSK
iwpriv wlan0 set EncrypType=TKIP
iwpriv wlan0 set WPAPSK="mykey"
iwpriv wlan0 set SSID="my network"
dhclient wlan0 

don't forget to put sudo in front of these commands.

---

### Post by schwim on 2007-10-20
thank you very much for your reply.

Can I ask a few questions before I attempt to implement this?

I'm incredibly ignorant when it comes to networking.  I open my Win laptop, it tells me that a connection was found, I choose it, enter my WEP key and I'm connected.

I did set up the network, but there are some aspects of your instructions that I never had to deal with:

channel: I've not seen this anywhere
WPA: I don't use WPA(just WEP), so would I leave out all ofthe WPA entries?
SSID vs. ESSID: My home network is called mshome, and my wireless connection is labeled SchwimNet.  Would that be my SSID/ESSID respectively?
WEP: I don't see a command for this.  Should there be one?

Thanks very much for your time, and I'm sorry for what's probably stupid questions.

thanks,
json

---

### Post by kevdog on 2007-10-20
Did I summarize rt73 somewhere?? I dont remember.

essid = SchwimNet for you

---

### Post by schwim on 2007-10-20
Hi there kevdog,

What about all the WPA related entries and channel?

thanks,
json

---

### Post by schwim on 2007-10-21
[EDIT]Disregard, No need to reply any further.

thanks,
json
[/EDIT]

---

### Post by kevdog on 2007-10-21
I know you are having a problem with the rt61 driver - I get that -- I know you cant connect -- I get that.  But what exactly are you trying??

Are you trying to use network manager, or connect from the command line???

To the best of my knowledge the ra chipset cards dont interact well with the network manager gui.

Can you post all the ra associated modules loaded??
lsmod | grep rt

Then can you confirm the rt61 module is the one you compiled
modinfo rt61

Then are you trying to use the command line to complete the connection, or some graphic utiltity like wicd, rutilt.  I would not recommend using network manager if you can avoid it.

---

