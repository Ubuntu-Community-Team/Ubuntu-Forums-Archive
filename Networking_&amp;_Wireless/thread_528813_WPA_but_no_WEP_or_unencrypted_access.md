---
title: "WPA but no WEP or unencrypted access"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by atrus on 2007-08-18
I seem to have the exact opposite problem as most people, so I'm having alot of trouble googling for it.

My networkmanager connects fine to wpa networks, but utterly fails on WEP networks, or even completely wide-open unencrypted networks. I can connect to the WEP or unencrypted networks fine by hand, or by using wifi-radar, but switching back and forth all the time is proving highly annoying. (not to mention the problems that network-manager-aware applications have when it reports no network available).

I'm on an IPW3945 wireless device, and have had this problem on feisty, and now on gutsy as well.

Any fix/debugging suggestions would be greatly appreciated. Thanks.

---

### Post by kevdog on 2007-08-18
Just to see if you really cant connect to unencrypted networks, I want you to try to establish a connection manually.  This example assumes your wireless interface to be wlan0 (it may be something else like eth1).  Check lshw -C network -- go to your wireless section, search for logical name and it will reveal the interface name

Some of these commands may be overkill -- just worried what happens at the end:
```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo ifconfig wlan0 essid <"ESSID_in_QUOTES">
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

---

### Post by atrus on 2007-08-18
Sorry if I wasn't clear.

I definitely can (and out of neccesity, do) connect to unencrypted and WEP networks by hand, or with wifi-radar. No problem there.

The problem is that network-manager can't.

---

### Post by walkerk on 2007-08-18
Not sure why network-manager isn't working. Have you given WICD a try? It should correct this. Follow the instructions in my signature or [go here]("http://wicd.sourceforge.net")

---

### Post by atrus on 2007-08-18
> **walkerk said:**
> Not sure why network-manager isn't working. Have you given WICD a try? It should correct this. Follow the instructions in my signature or [go here]("http://wicd.sourceforge.net")

Eck. I'm trying to install it now, but this definately isn't a long-term solution. Binary packages should not be installing their contents in /opt, and conflicting with network-manager AND wifi-radar seems like a phenomenally bad idea.

---

### Post by imdano on 2007-08-18
It would be a bad idea to not have wicd conflict with network-manager and wifi-radar.  Having multiple connection management apps is likely to cause problems.  Future releases aren't going to install in /opt, the directory structure is changing to meet linux conventions.

---

### Post by kevdog on 2007-08-18
Couple things to try with network manager

You either need to put network manager in roaming mode, or comment out the interfaces you want network manager to control in the /etc/network/interfaces file.

If you could post your interfaces file, it might help.  Does network manager work with WPA??

If everything works "manually", there should be no reason network manager shouldnt work!

---

### Post by atrus on 2007-08-18
> **kevdog said:**
> Couple things to try with network manager

You either need to put network manager in roaming mode, or comment out the interfaces you want network manager to control in the /etc/network/interfaces file.

If you could post your interfaces file, it might help.  Does network manager work with WPA??

If everything works "manually", there should be no reason network manager shouldnt work!

```
auto lo
iface lo inet loopback
```

Everything else is commented out.

Network-manager does work with wpa, on at least 2 different WPA networks i have access to.

i'm not familiar with a "roaming" mode for network manager.

---

### Post by atrus on 2007-08-18
> **imdano said:**
> It would be a bad idea to not have wicd conflict with network-manager and wifi-radar.  Having multiple connection management apps is likely to cause problems.  Future releases aren't going to install in /opt, the directory structure is changing to meet linux conventions.

Hopefully it'll mature well in future anyways.

I wonder if it would be possible to provide the facilities for network status detection that network-manager does, so that network-manager aware applications could know they're online by wicd's status?

---

### Post by atrus on 2007-08-18
I'm not particularly familiar with the output of NetworkManager in daemon.log, but here's what I've been able to extract from it. This is on a WEP network, which successfully connects with wifi-radar with the following config: (Actual WEP key is faked here, but consistent in usage):

```
[BlackTower]
prescript = 
use_wpa = no
postscript = 
mode = 
key = 123456789A
use_dhcp = yes
security = 
channel = 
```

When successfully connected with wifi-radar, iwconfig says:

```
eth1      IEEE 802.11g  ESSID:"BlackTower"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:9A:CB:19:38   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:1234-5678-9A   Security mode:open
          Power Management:off
          Link Quality=73/100  Signal level=-62 dBm  Noise level=-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:702   Missed beacon:0
```

While network-manager is attempting to connect (after providing nm-applet with the key 123456789A for WEP 64/128-bit Hex, Open System authentication), iwconfig says:

```
eth1      IEEE 802.11g  ESSID:"BlackTower"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:9A:CB:19:38   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:1234-5678-9A   Security mode:open
          Power Management:off
          Link Quality=73/100  Signal level=-63 dBm  Noise level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:47  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:751   Missed beacon:0
```

From selection of the network in nm-applet to failure to connect, /var/log/daemon.log says:

```
Aug 18 18:24:58 kedri NetworkManager: <debug> [1187483098.470092] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'BlackTower' 
Aug 18 18:24:58 kedri NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / BlackTower 
Aug 18 18:24:58 kedri NetworkManager: <info>  Deactivating device eth1. 
Aug 18 18:24:58 kedri NetworkManager: <info>  Device eth1 activation scheduled... 
Aug 18 18:24:58 kedri NetworkManager: <info>  Activation (eth1) started... 
Aug 18 18:24:58 kedri NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 18 18:24:58 kedri NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Aug 18 18:24:59 kedri NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Aug 18 18:24:59 kedri NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Aug 18 18:24:59 kedri NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Aug 18 18:24:59 kedri NetworkManager: <info>  Activation (eth1/wireless): access point 'BlackTower' is encrypted, but NO valid key exists.  New key needed. 
Aug 18 18:24:59 kedri NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'BlackTower'. 
Aug 18 18:24:59 kedri NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Aug 18 18:25:20 kedri NetworkManager: <info>  Activation (eth1) New wireless user key for network 'BlackTower' received. 
Aug 18 18:25:20 kedri NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 18 18:25:20 kedri NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Aug 18 18:25:21 kedri NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Aug 18 18:25:21 kedri NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Aug 18 18:25:21 kedri NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Aug 18 18:25:21 kedri NetworkManager: <info>  Activation (eth1/wireless): access point 'BlackTower' is encrypted, and a key exists.  No new key needed. 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant^I' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: response was 'OK' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: response was 'OK' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: response was '0' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 426c61636b546f776572' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: response was 'OK' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: response was 'OK' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: response was 'OK' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: response was 'OK' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Aug 18 18:25:22 kedri NetworkManager: <info>  SUP: response was 'OK' 
Aug 18 18:25:22 kedri NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Aug 18 18:27:22 kedri NetworkManager: <info>  Activation (eth1/wireless): association took too long (>120s), asking for new key. 
Aug 18 18:27:22 kedri NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'BlackTower'. 
Aug 18 18:27:25 kedri NetworkManager: <info>  Activation (eth1) New wireless user key request for network 'BlackTower' was canceled. 
Aug 18 18:27:25 kedri NetworkManager: <info>  Activation (eth1) failure scheduled... 
Aug 18 18:27:25 kedri NetworkManager: <info>  Activation (eth1) failed for access point (BlackTower) 
Aug 18 18:27:25 kedri NetworkManager: <info>  Activation (eth1) failed. 
Aug 18 18:27:25 kedri NetworkManager: <info>  Deactivating device eth1. 
Aug 18 18:27:25 kedri NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Aug 18 18:27:25 kedri NetworkManager: <info>  SUP: response was 'OK' 
Aug 18 18:27:25 kedri NetworkManager: <info>  nm_policy_device_change_check:: !old_dev && !new_dev!! 
~

```

---

### Post by wieman01 on 2007-08-19
I can confirm that Network Manager has issues with 64-bit WEP networks. 128-bit work just fine, so are WPA ones. Unencrypted is no issue at all on my end... 64-bit is a headache for a reason unknown to me.

---

### Post by atrus on 2007-08-19
> **wieman01 said:**
> I can confirm that Network Manager has issues with 64-bit WEP networks. 128-bit work just fine, so are WPA ones. Unencrypted is no issue at all on my end... 64-bit is a headache for a reason unknown to me.

Haven't heard anything like this before. Anyways, I don't have a 128-bit wep network to test against.

---

### Post by imdano on 2007-08-19
> **atrus said:**
> =I wonder if it would be possible to provide the facilities for network status detection that network-manager does, so that network-manager aware applications could know they're online by wicd's status?It is possible with the way wicd is designed, and I think one of the other devs is looking into it.  I'm not 100% sure, but I think that third-party programs have to be written specifically to check for NM's connection status, so either third party apps would have to add checks for wicd into their software or we'd have to try to imitate NM.

---

### Post by atrus on 2007-09-05
The problem persists on creation of a new user. I'm not sure where else network-manager might be keeping state about networks, if there's anything else to erase.

I'm filing a bug on it now: [http://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/137571](http://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/137571)

---

### Post by kevdog on 2007-09-05
Are you running network manager in roaming mode??  Its found under system->admin->networks.

Select and activate your wireless interface.  There should be a box if you go back into the setup that states enable roaming mode (at least with Feisty) that you can select.

Again, I havent read this thread for a while.  Originally had problems with connecting to unencrypted networks, now you are talking about WEP.  Are you having a problem with both of them?

---

### Post by atrus on 2007-09-05
> **kevdog said:**
> Are you running network manager in roaming mode??  Its found under system->admin->networks.

Select and activate your wireless interface.  There should be a box if you go back into the setup that states enable roaming mode (at least with Feisty) that you can select.


Yes, roaming is enabled.

---

### Post by kevdog on 2007-09-05
Ok roaming in enabled.....and
non-encrypted networks still do not connect, or is it only wep?  Also I think the ESSID needs to be broadcast on the router also.

---

### Post by atrus on 2007-09-05
> **kevdog said:**
> Ok roaming in enabled.....and
non-encrypted networks still do not connect, or is it only wep?  Also I think the ESSID needs to be broadcast on the router also.

Non-encrypted and WEP both still fail. The ESSID is being broadcast afaik. It's listed on the client by "iwlist scannning", and network-manager does see it in the little nm-applet list.

---

### Post by kevdog on 2007-09-05
But you are telling me you can connect through the command line??

What driver are your using??
And I think from a previous post, the only thing listed in the interfaces file are the "lo" entries".  Network Manager just spins I take it!  The router shows up in the nm-applet correct??  Im basically trying to avoid you typing anything.

---

### Post by atrus on 2007-09-05
> **kevdog said:**
> But you are telling me you can connect through the command line??
Yep.

> **kevdog said:**
> What driver are your using??
ipw3945
> **kevdog said:**
> And I think from a previous post, the only thing listed in the interfaces file are the "lo" entries".  Network Manager just spins I take it!
Yep.
> **kevdog said:**
> The router shows up in the nm-applet correct??
Also correct.
> **kevdog said:**
>   Im basically trying to avoid you typing anything.
Well, there's that. there's the fact that some apps watch network-manager to detect if the network is available, and fail when it's not. And the whole 'start your network connection this way in room A, this way in room B' thing is pretty 80's. :)

---

### Post by kevdog on 2007-09-05
Ive never heard of this problem.  Youve powered down and possibly reset the router.  Did wifi radar or wicd work for you??

---

