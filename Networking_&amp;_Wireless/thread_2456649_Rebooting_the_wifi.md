---
title: "Rebooting the wifi"
date: 2021-01-16
forum: Networking &amp; Wireless
---

### Post by robert99999 on 2021-01-16
I'm running 20.04 on an older HP Compaq laptop.
Every so often, the wifi will suddenly shut down. I'll be on the internet, and suddenly there's no connection, and I'll see that the wifi LED has stopped blinking. I don't think it's an OS issue, because I seem to recall that this was also happening when I was running Windows on this machine. So, I assume that it's either a hardware or firmware problem. The only way I know to get the wifi back up and running, is to reboot the computer. Is there some way just to reboot the wifi without completely rebooting the computer?

---

### Post by tea for one on 2021-01-16
> **robert99999 said:**
>  So, I assume that it's either a hardware or firmware problem. The only way I know to get the wifi back up and running, is to reboot the computer. Is there some way just to reboot the wifi without completely rebooting the computer?

Yes, there is a little shortcut.

You have to find the driver which is used by your wifi:-
```
sudo lshw -C network 2>&1 | grep wireless | grep driver
```
My result is:-
```
redact@redact:~$ sudo lshw -C network 2>&1 | grep wireless | grep driver
[sudo] password for redact: 
       configuration: broadcast=yes driver=[COLOR="#0000FF"]iwlwifi[/COLOR] driverversion=5.4.0-62-generic firmware=29.1654887522.0 latency=0 link=no multicast=yes wireless=IEEE 802.11

```
Then, via the terminal:-
```
sudo modprobe -r [COLOR="#0000FF"]iwlwifi[/COLOR] && sudo modprobe [COLOR="#0000FF"]iwlwifi[/COLOR]
```

The second command will unload and reload the kernel module [COLOR="#0000FF"]iwlwifi[/COLOR] (Intel wifi in this example)

Substitute the answer from step one in step two.

Any joy?

---

### Post by robert99999 on 2021-01-16
Thanks. In my case I get  **iwl3945**. I modified the terminal command line accordingly. When I run the command line (while wifi is working), the wifi LED goes out, then a few seconds later it comes back on, and everything is working. So, it appears to be doing what it's supposed to. I won't know if this fixes it for sure until the problem actually crops up. It only occurs every one or two days, but picks the most inopportune time to happen.

---

### Post by tea for one on 2021-01-16
Yes, it sounds like it's behaving as expected.

---

### Post by robert99999 on 2021-01-16
Unfortunately, it didn't work. A few minutes ago, the wifi shut down, and I tried the **modprobe** command, but it didn't do anything. I had to reboot the computer to get it going. I was curious about the wifi  hardware interface, i.e., pci, internal usb, etc. So, I ran the lshw command again, but without the grep, and got this:
[COLOR=#0000ff]
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlp16s0
       version: 02
       serial: 00:19:d2:2f:30:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=5.8.0-38-generic firmware=15.32.2.9 ip=192.168.1.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:30 memory:f4000000-f4000fff
[/COLOR]
So now I'm wondering if there's something with the PCI bus that needs to be reset.

---

### Post by tea for one on 2021-01-17
Not quite the right solution - that's a pity.

I notice that you use the 5.8 kernel in your output. 
There are some recent forum posts about this kernel causing problems with Internet, Sound, Virtual machines etc.

Do you have another kernel that you can pick when booting the device?

---

### Post by chili555 on 2021-01-17
I'd much rather diagnose and fix the reason it's dropping rather than slapping a band-aid on it. May we see:

```
sudo dmesg | grep -e iwl -e wlp
```

You might also look at the settings in your router. 

Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable pwer saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddnely changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda

```
Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.    

Is there any improvement?

---

### Post by robert99999 on 2021-01-17
Thanks for the suggestions. Here's what I get from the dmesg command:

[COLOR=#0000cd]sudo dmesg | grep -e iwl -e wlp
[   21.163361] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   21.163364] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   21.163365] iwl3945: hw_scan is disabled
[   21.163441] iwl3945 0000:10:00.0: can't disable ASPM; OS doesn't have ASPM control
[   21.217154] iwl3945 0000:10:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   21.217158] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   21.217526] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   23.825839] iwl3945 0000:10:00.0 wlp16s0: renamed from wlan0
[   84.321984] iwl3945 0000:10:00.0: loaded firmware version 15.32.2.9
[  129.461967] wlp16s0: authenticate with 00:1c:10:46:3c:4b
[  129.465028] wlp16s0: send auth to 00:1c:10:46:3c:4b (try 1/3)
[  129.466856] wlp16s0: authenticated
[  129.467762] iwl3945 0000:10:00.0 wlp16s0: disabling HT/VHT/HE as WMM/QoS is not supported by the AP
[  129.469271] wlp16s0: associate with 00:1c:10:46:3c:4b (try 1/3)
[  129.471902] wlp16s0: RX AssocResp from 00:1c:10:46:3c:4b (capab=0x411 status=0 aid=5)
[  129.474945] wlp16s0: associated
[  129.754956] IPv6: ADDRCONF(NETDEV_CHANGE): wlp16s0: link becomes ready
[  129.755672] iwl3945 0000:10:00.0: Enabling power save might cause firmware crashes[/COLOR]

Hmm, that last line looks rather ominous.
I had also wondered if it might be a power management issue, but didn't know where to look. I'll try disabling the power saving and report back later. I'll also check the router settings and report back.

---

### Post by chili555 on 2021-01-18
May we also see the results of the wireless script? [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by robert99999 on 2021-01-19
Here is the router configuration info:

[COLOR=#0000cd]Mode: Mixed 11/54Mbps             
SSID: xxxxxxxxx            
DHCP Server: Enable            
Channel: 6             
Encryption Function: Enabled, WPA2-personal AES (was previously TKIP+AES)
Wireless Network Mode: Auto (B or G, N not available)
Wireless Network Name (SSID): xxxxxxxxx             
Wireless Channel: 6 - 2.437GHz     
Wireless SSID Broadcast: Enabled[/COLOR]

I also ran the wireless script, but it produces a huge file, which I'd rather not post in its entirety, because I'd have to go through it and edit out some private information. Which info do you need to see from it?

---

### Post by chili555 on 2021-01-19
> I also ran the wireless script, but it produces a huge file, which I'd rather not post in its entirety, because I'd have to go through it and edit out some private information.The script is supposed to redact private information like this:

> Mode:Managed  Frequency:5.745 GHz  Access Point: [COLOR="#FF0000"]<MAC 'GBR5' [AC1]>[/COLOR]   

> nx2.4  [COLOR="#FF0000"]<MAC 'nx2.4' [AC3]> [/COLOR] Infra  6     2437 MHz  195 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no    

> Cell 06 - Address: [COLOR="#FF0000"]<MAC 'MC5' [AC6]>[/COLOR]
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"MC5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

> wlp3s0: associate with [COLOR="#FF0000"]<MAC 'GBR5' [AC1]> [/COLOR](try 1/3)There are no passwords.

We need it all.

The whole point of the script is to avoid asking for the results of a command or two and, then, based on the response, ask for a couple more data points and so forth until we've been working on a case for 20-30 posts and still haven't the needed information. A few smart users and one other not so much devised the script to gather everything at once.

I am unaware of any sensitive details that are gathered. If you find some, please let me know and we'll revise the script.

---

### Post by robert99999 on 2021-01-20
I agree that there are no passcodes, and the MAC addresses have been redacted (sort of), but the SSID's of 16 of my  neighbours' networks are in the file, as are a number of non-redacted IP addresses, and some sha512 encryption stuff (keys & signatures) that I don't know the significance of. I don't feel comfortable making these  public. So, I'll have to go through the file and delete them before  posting the file. Hopefully by tomorrow.

---

### Post by chili555 on 2021-01-20
> as are a number of non-redacted IP addresses

Are any of them public IP addresses? I strongly suspect that all are private addresses, 192.168.x.y, 172.xx, 10.10.xx and the like. Again, if you find any public IPs, please let me know so that we may amend the script.

> but the SSID's of 16 of my neighbours' networks are in the file

By broadcasting the SSIDs, aren't we all willingly published? Isn't that information available to anyone on your block? 

> and some sha512 encryption stuff (keys & signatures) that I don't know the significance of. 

I suspect that they are all the validation key associated with kernel modules, like this:

```
$modinfo iwlwifi

filename:       /lib/modules/5.8.0-38-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
<snip>
srcversion:     4BEB092F11F7A5F4C35B322
alias:          pci:v00008086d00007AF0sv*sd00000A10bc*sc*i*
alias:          pci:v00008086d00007AF0sv*sd00000510bc*sc*i*
alias:          pci:v00008086d00007AF0sv*sd00000310bc*sc*i*
<snip>
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       5.8.0-38-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        27:0B:3C:50:C7:00:AC:F0:A7:99:F4:70:9D:E6:9A:31:9B:92:85:A4
sig_hashalgo:   sha512
signature:      8C:BC:4B:A2:EF:88:0D:B4:7D:34:A7:53:EB:A8:23:EE:84:11:EF:1B:
		4A:CD:54:9F:15:FF:3E:FD:7A:8D:4A:93:AA:5B:E0:4D:CC:23:0C:03:
		6A:21:0C:79:EA:86:F9:DA:95:BB:77:15:5A:C4:B0:D7:61:9D:55:9C:
		38:91:90:C8:9A:51:26:C7:B6:AD:4D:99:B2:C0:F1:C7:F7:CE:CE:BF:
		BB:B9:AC:88:19:E8:74:91:AC:D2:C8:43:32:7F:0A:8A:F9:1D:2E:5A:
		C0:5B:FB:2B:93:98:B3:D7:A1:AE:AB:A7:67:19:99:35:D1:47:83:8E:
		35:D3:7A:07:11:F7:B9:5C:24:E4:08:F6:6A:C3:E1:71:D0:9C:D0:84:
		10:BD:C0:53:10:5E:34:73:51:92:4D:41:32:F5:99:C0:FE:C2:49:F0:
		58:3A:F4:CC:F5:67:7F:08:6E:D8:98:D9:9B:D7:58:27:9E:B7:0C:4E:
		A4:14:13:54:7A:E0:06:51:91:72:46:6E:AA:7F:9B:1C:3D:A4:E7:9B:
		0D:C4:DD:1C:9F:2E:EF:24:98:55:52:17:23:8B:8E:72:13:B8:6E:2F:
		1F:79:F6:3A:E4:37:9F:CD:A7:FD:0E:19:37:35:63:67:3B:FA:00:81:
		D3:4B:E4:50:CC:48:7E:11:8F:DA:69:98:AD:C9:61:0B:37:83:9B:12:
		A3:D7:64:84:5F:97:2C:39:C6:F2:F1:B1:11:D9:73:CE:D0:E9:3D:72:
		27:72:E8:5D:BE:9A:4C:34:7E:C2:60:E0:C6:04:56:32:78:42:FE:71:
		FB:2A:5A:81:DB:DA:1A:57:A5:77:E0:E4:20:AD:4D:01:82:7D:89:D0:
		AA:83:AC:50:92:9F:85:7D:80:F3:E4:83:4C:AC:DD:0B:0F:B1:C4:69:
		3D:38:8F:13:E2:1F:4C:9E:29:C7:D8:DF:88:CA:A0:98:51:6D:F6:3B:
		EE:C4:28:33:E0:12:51:21:5C:4A:D9:55:CE:C3:FA:45:9C:35:13:AE:
		33:72:60:C6:2D:C1:80:12:DC:A3:3D:F0:BD:8C:EF:F9:DC:29:2F:FD:
		CC:60:5A:D0:C3:99:13:3D:21:F8:38:14:DD:D7:82:3B:68:E1:97:C6:
		26:03:C2:22:FC:E8:C4:74:DC:68:B3:8B:77:18:F1:8F:A4:1F:2D:D4:
		B8:00:EF:D5:76:C9:D1:46:27:8E:B0:4D:41:07:D2:25:8A:92:81:FA:
		13:F4:9C:48:12:CA:90:EB:8C:F3:9A:87:DA:94:38:93:BF:96:22:35:
		28:46:6B:DF:50:3E:A2:2B:C9:63:A0:F3:E5:15:69:DC:08:ED:4B:A9:
		0E:57:BA:3D:1D:8C:FA:82:86:FE:BB:8D
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
<snip>
```

This is part of the module information, hence modinfo, on every recent Ubuntu version. It is not unique to your installation alone.

I will, however, ask the authors of the script to remove it; not because it's secret but because it takes up too much space.

---

### Post by robert99999 on 2021-01-20
I realize that the SSIDs are broadcast publicly, but some of them contain people's first and last names. So, I redacted them. There were also a couple of non local IP addresses, probably related to gateways and DNS, which I deleted. If you're going to be contacting the developer to suggest changes. I think it would be a good idea to have the option of restricting the information to specific networks, or else alter the SSIDs.

I'm probably being excessively paranoid, but I figure it's not a bad thing when it comes to computer security.

If I've accidentally removed something that's required, please let me know.

[https://paste.ubuntu.com/p/BNt6xGG6Tv/](https://paste.ubuntu.com/p/BNt6xGG6Tv/)

BTW, It's now been 3 days since I changed the wifi power management settings, and there have been no more shutdowns.

---

### Post by chili555 on 2021-01-21
I don't see anything in the paste that I'd be ready to change, especially in view of:

> It's now been 3 days since I changed the wifi power management settings, and there have been no more shutdowns.I suggest that you use thread tools at the top to mark Solved. If there are any further drops, post back and we'll dig deeper.

---

### Post by robert99999 on 2021-01-21
Thanks very much for the help.

It does appear that the power setting changes have fixed the problem,  but just to be sure, I'll wait a couple more days before marking it  solved. Murphy's Law, and all that.

---

