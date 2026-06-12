---
title: "Newbie Wireless help!"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by blarg on 2008-11-12
Hi, 

Firstly, I think I should mention that I'm what one would call a linux "noob", and don't know how to effectively use ubuntu. 

I've been trying to connect to wireless services with the integrated wlan card in my computer: 
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


By following the instructions on this site: [http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/#before](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/#before)
I have been able to get my computer to find the wireless networks, and get it to attempt to access the network, but all it ever does is keep searching, and never actually connect. 

If this helps, when i went to System->Administration->Hardware testing, when the test got up to the internet connecting stage it gave me the following error:

ERROR:root:Could not find def gateway info in /proc 
Traceback (most recent call last): 
  File "/usr/share/hwtest/scripts/internet_test", line 132, in <module> 
    sys.exit(main(sys.argv[1:])) 
  File "/usr/share/hwtest/scripts/internet_test", line 118, in main 
    host = route.get_default_gateway() 
  File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway 
    t1 = self._get_default_gateway_from_bin_route() 
  File "/usr/share/hwtest/scripts/internet_test", line 69, in _get_default_gateway_from_bin_route 
    if def_gateway: 
UnboundLocalError: local variable 'def_gateway' referenced before assignment 



If anyone could help me get the wireless working properly it wold be much appreciated.

-Thanks
Blarg.

---

### Post by superprash2003 on 2008-11-12
[http://ubuntuforums.org/showthread.php?t=766169&page=2](http://ubuntuforums.org/showthread.php?t=766169&page=2)

---

### Post by blarg on 2008-11-13
Thanks superprash, but problem is still unresolved.

Its not that I can't detect wireless networks, it just cannot connect to them. the little bar next to the name of the network is completely empty, although when I plug in my belkin wireless USB, the bar is filled up. 

If anyone could tell me how to get the Atheros card to connect to the wireless internet, it would be really appreciated.

---

### Post by enigmageek on 2008-11-13
Hello. They way I got my Atheros wireless working was to first go to System/Administration/Hardware Drivers Manager and "uncheck" the support for atheros cards and hal. Then download the madwifi-hal from [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/)
Install it as per the other post. You will need the build-essentials package to compile software in Ubuntu as well. I then installed DKMS so when you upgrade the kernel the wireless driver is rebuilt and you shouldn't lose the capability. Intrepid is supposed to have DKMS installed by default. I have the dkms conf and commands for madwifi-hal also if needed. If you get your wireless to connect there are a few tweaks to get the most out of it. I hope this helps. Please let me know.
Regards, Ray
Ubuntu Hardy 8.0.4.1-2.6.27.5

---

### Post by blarg on 2008-11-15
Hey thanks for that. I've followed the instructions, and I can detect the wireless networks, but it keeps acting as if I'm out of range, even though I can still connect with a wireless USB adaptor, do you know why this is?

---

### Post by enigmageek on 2008-11-15
Hello blarg. What does your /etc/network/interfaces file look like? Mine looks like:

auto lo
iface lo inet loopback

Have you run the command iwconfig in a Terminal? Also check System/Administration/Network and see if the wireless interface is visible and see if roaming is enabled. If your Atheros driver (ath0) doesn't show up in the iwconfig output run the command

sudo modprobe ath_pci

I'm assuming the Realtek adapter is a wired interface? Good luck, we can get this working I'm sure there's a reason we may be overlooking. Hang in there.

---

### Post by blarg on 2008-11-17
Hello enigmageek,
F
Ok, I've done as you've suggested, and here's what I got when I did it. 

For the etc/network/interfaces, my file gave me this:  

auto lo
iface lo inet loopback


When I went to have a look at the system/admin/network it showed that roaming was enabled.

 Finally, the terminal. I typed in "iwconfig" and here is the full output, just for your enjoyment :):

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Do you know what this means and what is going on? 
I also think I sould say that I'm very grateful that your helping me, so thanks for the assistance, it really is appreciated.

---

### Post by blarg on 2008-11-17
Uh, oh, that wasn't supposed to happen.

Sorry about all the random smilies in the terminal output, I'll just post the output again for you:


```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


Sorry about that.

---

### Post by enigmageek on 2008-11-18
Hello blarg. n/p about the smileys. I wonder if the scanning module is getting loaded. Issue this command in Terminal:

sudo modprobe wlan_scan_sta

Then:

sudo ifconfig ath0 up

and finally:

 wlanconfig ath0 list scan

See if any essid comes up, something like this:
SSID            BSSID              CHAN RATE  S:N   INT CAPS
linksys           00:11:95:78:66:20    6   54M 21:0   100 ESs
enigmanet          00:0d:88:b7:06:8e    6   54M  5:0   100 EPS  ATH

If you can get a list then we should be able to connect to an access point. Also on your router do you have it configured properly? Be sure the network ID isn't hidden. If you see your network name in the list use command:

sudo iwconfig ath0 essid "your network"

To get an IP using DHCP issue:

sudo dhclient ath0

I hope this helps. Please let me know.

---

### Post by blarg on 2008-11-19
Okay, 

I type in sudo modprobe wlan_scan_sta, followed by sudo ifconfig ath0 up, and then wlanconfig ath0 list scan, and....
unfortunately nothing happened, nothing showed up.

I suppose that this would be a bad thing, do you know any ways around it?

---

### Post by ambless on 2008-11-19
you can use windows driver,1stly you disable hardware driver in system>> hardware driver ,then install ndisgtk(ndiswrapper) if you get driver in gigabyte home page (super wireless driver) even for 64 bit

---

### Post by enigmageek on 2008-11-19
Hello again blarg. The only other thing I can recommend if you cannot get the latest madwifi-hal snapshot to work is what ambless suggests. But first please make sure you remove all instances of madwifi drivers/modules and be sure they are unloaded. First you want to download the Windows (sic) driver and ndiswrapper of course. I also see posts touting Wicd instead of Network Manager as a viable solution. Good luck! I can package the driver files from Windows called ar5211.sys, net5211.cat, and net5211.inf if you want me to. These are the one my Vista uses.

---

### Post by blarg on 2008-11-24
Thanks, I would like it if you could package the drivers.
Thanks!

---

### Post by enigmageek on 2008-12-07
Hello again blarg. Sorry took so long. I can email the package to you if you want. Also, if you haven't already, install ndiswrapper-common and ndisgtk via Synaptic. The gui makes setup so easy. Good luck and sorry the other methods didn't work for you.

---

