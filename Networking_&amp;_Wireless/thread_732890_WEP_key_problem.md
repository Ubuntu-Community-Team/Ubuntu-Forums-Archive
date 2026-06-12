---
title: "WEP key problem"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by plasmic on 2008-03-23
Hey all, linux newbie here, trying to get ubuntu 7.10 to access the internet, but to connect to the router where I live I need to set up all 4 wep key indexes. NetworkManager doesn't have the option, and I tried WiFi-radar, but if it did have the option for 4 before, only seems to have the option for 1 now (unless there's some command line/manual settings I don't know about?), and all the manual wireless configs only seem to use one key index at a time? 

I know wep sucks, and using more the one key isn't much better, if at all, but changing the wireless router's config isn't really an option (it's my gf's stepdad's router, he doesn't want to change the setup). Any help would be appreciated :)

---

### Post by rustybronco on 2008-03-23
The router can generate up to four keys, but it only uses one key at a time.

what kind of wireless device are you using? (usb, pci, pcmcia, ect.)

---

### Post by plasmic on 2008-03-23
I'm using a belkin wireless usb adaptor on my desktop, connecting to something similar to netgear I think, I'm not at home atm so I can't check.

I tried using each key individually, in both network manager and wifi-radar, but it didn't work, and it wouldn't work on xp/vista if I only had one key put in. In my searches I read somewhere that there is a setting that uses all 4 keys in rotation or something, not too sure about the validity of that tho. 

Anyways, settings include open authentication, and 128-bit HEX keys. And both network manager and wifi-radar both detect all the wireless networks around. 

It could be possible that it's set to use key index 4, if it does only use one, that's what shows up in vista. Could that be it? use iwconfig wlan0 key [4] my_key and then iwconfig wlan0 key [4] ? I tried looking in etc/network/interface but all it had was that lo entry. And if those iwconfig commands will do the trick, how do I make them permanent? I have removed networkmanager already (I think, used synaptic package manager and marked networkmanager for removal, but there was another option below it that seemed a little more extreme?)

---

### Post by rustybronco on 2008-03-23
It's only going to use one at a time.
xp/vista doesn't recognize it also? are you sure of the key being in hex or ascII? 
enter **lsusb** and **lshw -C network** then cut and paste to output back here. its very likely your belkin is not being recognized correctly.
some reading material for you to look at also. [http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

---

### Post by chili555 on 2008-03-23
> It could be possible that it's set to use key index 4, if it does only use one, that's what shows up in vista. Could that be it? use iwconfig wlan0 key [4] my_key and then iwconfig wlan0 key [4] ? I tried looking in etc/network/interface but all it had was that lo entry. And if those iwconfig commands will do the trick, how do I make them permanent?It is certainly possible. Please try the following in a terminal:```
sudo iwconfig wlan0 key 096c7fxxxxxxx [4]
sudo dhclient wlan0
```Substitute your correct key. Did you connect or time out?

You can make these permanent, if they work, by amending /etc/network/interfaces to add wlan0 lines like this:```
auto wlan0
iface wlan0 inet dhcp
wireless-essid your_ssid
wireless-key 096c7fxxxx [4]
```You can do the changes with *sudo gedit*,  be sure to save and exit.

Let us know.

---

### Post by plasmic on 2008-03-23
It works in xp/vista, after I set up all 4 keys, it wouldn't work when I set up just the first one, so maybe it is set to use key 4 (the last one entered)?

If the adapter wasn't being recognized properly would it still be able to detect networks? I did run iwconfig in terminal once, I can't remember what it said exactly but I'm pretty sure it had a device name listed for wlan. Though I guess that doesn't mean it's the right one, it'd be nice to have an unsecured network to test.

I'll give those commands a go when I get back home, thanks guys.

---

### Post by plasmic on 2008-03-23
Ok, after trying those commands and doing more searching, I eventually hooked up my comp to my gf's laptop with a cable to use internet connection sharing to get internet from her vista comp (interesting in itself), but didn't get anywhere with the wireless. Just timed out. Tried editing etc/network/interface to add the wireless-key entries in there, but didn't work. 
Not sure if this matters but when I go to network tools, it lists that lo one, eth0, eth1, and eth1-avail? eth0 i can configure, can't configure eth1 (button greyed out), and eth1-avail gives error can't find adaptor i think. 
Also, shouldn't my wireless device show up as wlan instead of eth?


Output of iwconfig
```
north@north-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid
             Bit Rate=1 Mb/s
            Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lsusb

```
north@north-desktop:~$ lsusb
Bus 005 Device 004: ID 050d:705c Belkin Components 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 046d:c01d Logitech, Inc. 
Bus 001 Device 004: ID 045e:00dd Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  


```

lshw -C network

```
north@north-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:50:8d:f3:b4:f4
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=0 mingnt=255 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:11:50:b3:0b:4a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g


```

---

### Post by kevdog on 2008-03-23
If you are getting avahi you got an error with the driver not being loaded.  Check dmesg to see if it gives you any clues.

---

