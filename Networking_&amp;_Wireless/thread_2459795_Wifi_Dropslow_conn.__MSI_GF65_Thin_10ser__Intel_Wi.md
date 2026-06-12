---
title: "Wifi Drop/slow conn. | MSI GF65 Thin 10ser | Intel WiFi 6 AX201 14.3 | Ubuntu 20.04.2"
date: 2021-03-26
forum: Networking &amp; Wireless
---

### Post by juliolt on 2021-03-26
Hi there!

I have been struggling with wifi problems in the past 1.5 month. I did a fresh Kubuntu install on a brand new MSI laptop (GF65 Thin 10ser 884xes 15.6''), the `lsb_release -a` gives back:

```

[FONT=monospace][COLOR=#b2b2b2]&#9654;[/COLOR][COLOR=#000000] lsb_release -a [/COLOR]
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 20.04.2 LTS 
Release:        20.04 
Codename:       focal[/FONT]

```

The symptoms are: 

- I boot up the device, `NetworkManager` launches correctly and I can connect to my WiFi connection (both 2.4 and 5GHz, visible networks with WPA/WPA2 Personal secured)
- Randomly, webpages start to freeze or completely prevent to being loaded either with Firefox 87.0 or Chrome [COLOR=#5F6368][FONT=Roboto]89.0.4389.90[/FONT][/COLOR]. Maybe it is a new google search being loaded forever or a refresh page in Jira/Github

I have checked my router configuration and channels, which seems ok as the rest of devices and laptop can connect smoothly. Even I my previous laptop (which was another MSI), with the very same router and Wifi connections, worked perfectly well. So I end up thinking about drivers or some specific problem in the new MSI. 

Some more information:

```

[FONT=monospace][COLOR=#b2b2b2]&#9654;[/COLOR][COLOR=#000000] dmesg | grep iwlwifi [/COLOR]
[    3.354582] **iwlwifi** 0000:00:14.3: enabling device (0000 -> 0002) 
[    3.376121] **iwlwifi** 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 58.3.35.22 
[    3.376123] **iwlwifi** 0000:00:14.3: Found debug destination: EXTERNAL_DRAM 
[    3.376124] **iwlwifi** 0000:00:14.3: Found debug configuration: 0 
[    3.376322] **iwlwifi** 0000:00:14.3: loaded firmware version 50.3e391d3e.0 op_mode iwlmvm 
[    3.395971] **iwlwifi** 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x354 
[    3.407249] **iwlwifi** 0000:00:14.3: Applying debug destination EXTERNAL_DRAM 
[    3.407651] **iwlwifi** 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor. 
[    3.559420] **iwlwifi** 0000:00:14.3: base HW address: 90:cc:df:f7:d2:4e 
[    3.572863] **iwlwifi** 0000:00:14.3 wlo1: renamed from wlan0 
[    4.679607] **iwlwifi** 0000:00:14.3: Applying debug destination EXTERNAL_DRAM 
[    4.826374] **iwlwifi** 0000:00:14.3: FW already configured (0) - re-configuring 
[ 1080.953902] **iwlwifi** 0000:00:14.3: reached 10 old SN frames from f4:69:42:40:ef:ef on queue 7, stopping BA session on TID 1 
[ 1341.941682] **iwlwifi** 0000:00:14.3: reached 10 old SN frames from f4:69:42:40:ef:ef on queue 8, stopping BA session on TID 1 
[ 1733.836242] **iwlwifi** 0000:00:14.3: No beacon heard and the time event is over already... 
[ 1760.519551] **iwlwifi** 0000:00:14.3: No beacon heard and the time event is over already... 
[ 1761.498167] **iwlwifi** 0000:00:14.3: No beacon heard and the time event is over already... 
[ 1844.453065] **iwlwifi** 0000:00:14.3: No beacon heard and the time event is over already... 
[ 2044.202728] **iwlwifi** 0000:00:14.3: Unhandled alg: 0x707 
[ 2044.259979] **iwlwifi** 0000:00:14.3: Unhandled alg: 0x707 
[ 2063.668064] **iwlwifi** 0000:00:14.3: reached 10 old SN frames from f4:69:42:40:ef:ef on queue 8, stopping BA session on TID 0
...
[/FONT]

```

```

[FONT=monospace][COLOR=#b2b2b2]&#9654;[/COLOR][COLOR=#000000] lsmod | grep iwl [/COLOR]
[COLOR=#000000]**iwl**mvm                380928  0 
mac80211              847872  1 **iwl**mvm 
**iwl**wifi               331776  1 **iwl**mvm 
cfg80211              704512  3 **iwl**mvm,**iwl**wifi,mac80211 [/COLOR]
[/FONT]

```

```

[FONT=monospace][COLOR=#b2b2b2]&#9654;[/COLOR][COLOR=#000000] iwconfig   [/COLOR]
[FONT=monospace][COLOR=#000000]wlo1      IEEE 802.11  ESSID:"XXXX"   [/COLOR]
          Mode:Managed  Frequency:2.462 GHz  Access Point: XXX    
          Bit Rate=144.4 Mb/s   Tx-Power=22 dBm    
          Retry short limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=56/70  Signal level=-54 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0
[/FONT][/FONT]

```

```

[FONT=monospace][COLOR=#b2b2b2]&#9654;[/COLOR][COLOR=#000000] lshw -C network  [/COLOR]
WARNING: you should run this program as super-user. 
  *-network                  
       description: Wireless interface 
       product: Wi-Fi 6 AX201 
       vendor: Intel Corporation 
       physical id: 14.3 
       bus info: pci@0000:00:14.3 
       logical name: wlo1 
       version: 00 
       serial: XX
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-70-generic firmware=50.3e391d3e.0 ip=192.168.1.69 latency=0 link=yes multicast=yes wireless=IEEE 802.11 
       resources: irq:16 memory:c5414000-c5417fff[/FONT]


```

I have already tried some solutions I found on the Internet/Intel forums but with no luck at all. As you can see, I have the `power management` of the card set to off. I have also tried seting the wireless connection to hidden, fixed IPs, requiring `IPv4` for the current connection (2.4GHz) and some other more. 

Of course, there is no problem if I connect through Ethernet but that solution is not possible in my actual office.

Can anyone help me with the issue?

Thank you!

Julio

---

### Post by juliolt on 2021-04-06
Can anyone please help? :(

---

### Post by chili555 on 2021-04-06
First, I suggest that you check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

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

Here is an interesting reference: [https://community.intel.com/t5/Wireless/Intel-Wi-Fi-6-AX201-Linux-Xubuntu-20-04-Slow-speeds-and/m-p/1256461#M34119](https://community.intel.com/t5/Wireless/Intel-Wi-Fi-6-AX201-Linux-Xubuntu-20-04-Slow-speeds-and/m-p/1256461#M34119)

---

