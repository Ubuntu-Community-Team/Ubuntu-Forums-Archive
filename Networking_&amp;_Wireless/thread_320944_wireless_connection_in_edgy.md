---
title: "wireless connection in edgy"
date: 2006-12-18
forum: Networking &amp; Wireless
---

### Post by vaineh on 2006-12-18
having trouble getting connected to wep protected wireless netoworks

its a clean install of ubuntu edgy on a laptop and im using a netgear pcmcia wg511t wireless card. the card is recognised and works, "iwlist scan" finds the wireless networks. but i cant get connected to any of them. 

network-manager just shows "wired network" as an option, nothing else. and i tried specifying the ap using iwconfig but no joy.

why is it such a pain

---

### Post by hal10000 on 2006-12-18
Please post the output of [COLOR="Red"]iwconfig[/COLOR] and [COLOR="Red"]ifconfig[/COLOR] Do you use dhcp or do you have a static ip-address? Look into /etc/resolv.conf to see if your nameservers are correct.

---

### Post by vaineh on 2006-12-18
root@evan-laptop:/home/evan# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:5B:48:BA  
          inet6 addr: fe80::20f:b5ff:fe5b:48ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:D0:59:B8:39:E1  
          inet addr:169.254.248.39  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::2d0:59ff:feb8:39e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4958 (4.8 KiB)  TX bytes:76068 (74.2 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-5B-48-BA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:200401 errors:0 dropped:0 overruns:0 frame:1785
          TX packets:12875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:18178364 (17.3 MiB)  TX bytes:678809 (662.8 KiB)
          Interrupt:11 Memory:d0b40000-d0b50000 
root@evan-laptop:/home/evan# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"cariss-wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:7867-2DF6-EE60-8697-D721-47EF-E5   Security mode:restricted
          Power Management:off
          Link Quality=32/94  Signal level=-63 dBm  Noise level=-95 dBm
          Rx invalid nwid:92334  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


nameserver is correct. using dhcp

---

### Post by hal10000 on 2006-12-18
Your wirelwss card is not associated to any Access Point (AP). This can happen due to various reasons.
1. too much distance from the Accesspoint ----> get closer to AP
2. check all of your settings:
     mode---> Managed or adhoc
     essid--->must be the same in your AP
     encryption key ----> must be the same in your AP

If this is all correct and it still doesn't work, then post the output of [COLOR="Red"]lspci -v[/COLOR]
Do you have the [COLOR="Red"]pcmciautls[/COLOR] and [COLOR="Red"]udev[/COLOR] packages installed (I suppose yes)?

---

### Post by vaineh on 2006-12-18
shouldn't the wireless networks just show up in network-manager?
i dont want to have to mess around on the cli whenever i want to connect to different networks

---

### Post by DREMA on 2006-12-18
Hello! Try deleting everything except the loopback lines in your /etc/network/interfaces file, then restart and check if the network-manager displays the wireless options now.

---

### Post by hal10000 on 2006-12-18
The netgear wg511t card needs the madwifi-drivers which are provided by the package [COLOR="Red"]linux-restricted-modules[/COLOR]. They are supposedly installed, but to be sure they are, you can try an [COLOR="Red"]sudo apt-get install linux-restricted modules$(uname -r)[/COLOR].

---

### Post by vaineh on 2006-12-18
couldn't find package linux-restricted-modules2.6.17-10-generic
](*,)

[edit]was missing a -
says its already the newest version installed, and the card does seem to be working cos as i said i can iwlist and it will list the networks within range[/edit]

---

### Post by n00b@linux on 2006-12-18
As hal10000 said, you're out of range or it's your WEP key. Try configuring it manually with iwconfig.
 
Or try gnome-network-manager (you'll have to install it from the repos) if you want to use a GUI.

---

### Post by vaineh on 2006-12-18
> **n00b@linux said:**
> As hal10000 said, you're out of range or it's your WEP key. Try configuring it manually with iwconfig.
 
Or try gnome-network-manager (you'll have to install it from the repos) if you insist on using a GUI.

what am i looking for? wlan, wlan_wep, wlan_scan_sta, ath+pci and some other athblahblah ones are there

---

### Post by hal10000 on 2006-12-18
If you have windows installed, boot windows try to get a conection under windows
and then look into the wireless and network settings; note the essid, wep-key and mode (managed, adhoc) dhcp or static ip and nameserver. Choose the same configuration entries in ubuntu using network-manager (network-manager-gnome).
Have you configured your Accesspoint (under windows or linux)? If not, then your mode is supposedly adhoc and your essid is set to manufacturer default.

You have to go step-by-step to figure out what's going wrong.

I try to recapitulate (tell me if I'm wrong):
1. Your network card is recognized from ubuntu (see iwconfig)
2. You AP is working and is connected to your router or to your dsl-line (or whatever).
3. if 1. and 2. are true, then the problem must reside in the settings (mode, essid, wep-key, nameserver, dhcp, etc.)

---

### Post by vaineh on 2006-12-18
i installed network manager using automatix, but like i said the only thing that shows up in it is a wired connection. i expected to be able to click on the icon in the taskbar, then it list all the networks its found and i be able to just click on one to connect.

---

### Post by Supersaiyan.IV on 2006-12-18
I suggest you follow this:

Open a few terminal windows, and run this in each of them:

> 
% sudo watch -n1 "iwlist ath1 scan"
% sudo watch -n1 "iwconfig ath1"


Now you have a scan of available networks, and your signal and associated AP (upon auto-association) will turn up in the iwconfig cmd.

To associate manually with wep:

> 
% sudo ifconfig ath1 up
% sudo iwconfig essid "your essid"
% sudo iwconfig key "wep key in hex"


That should do it. If you still cannot associate try:

> 
% sudo sleep 20


Hope it helps 
peace!

---

### Post by vaineh on 2006-12-19
why doesnt gnome-network-manager pick up any wireless networks?

---

### Post by pgilmon on 2006-12-20
I had a similar problem and did what it says [here]("http://www.ubuntuforums.org/showpost.php?p=1902075&postcount=6"). Now network manager can configure the wireless connection.

Of course, I recommend you to do a backup of /etc/network/interfaces before modifying it.

---

### Post by atonaldenim on 2006-12-20
on my machine, I usually have to enter the command ```
sudo iwconfig eth1 essid any
``` before NetworkManager will show any nearby networks. (replace eth1 with the name of your card) I think this happens after I associate to a particular wireless network, it expects to find that network again and won't look for other ones. 

anybody know a way to make "essid any" the default setting? typing "any" in as the network name in the NetworkManager applet doesn't seem to do the trick.

---

### Post by Supersaiyan.IV on 2006-12-20
> **atonaldenim said:**
> on my machine, I usually have to enter the command ```
sudo iwconfig eth1 essid any
``` before NetworkManager will show any nearby networks. (replace eth1 with the name of your card) I think this happens after I associate to a particular wireless network, it expects to find that network again and won't look for other ones. 

anybody know a way to make "essid any" the default setting? typing "any" in as the network name in the NetworkManager applet doesn't seem to do the trick.

Yes there is:

> 
% sudo iwconfig eth1 ap auto



That will auto-associate with any (essid) Access-point upon detection.
If essid function is still blocking try either:

> 
% sudo iwconfig eth1 essid off


or

> 
% sudo iwconfig eth1 essid on


Alternatively you have to enable it in your hardware by doing modprobe:

> 
(This works only for Intel 2200BG, for other models change 'ipw2200' to corresponding model, and check modinfo for parameters)

% sudo modprobe ipw2200 associate=1

(For more info)
% sudo modinfo ipw2200


This will autoassociate when scanning, and hopefully will act as if essid=any.
And of course variable 'eth1' is not absolute, some computers have 'ath1'.

Hope it works.
peace

---

