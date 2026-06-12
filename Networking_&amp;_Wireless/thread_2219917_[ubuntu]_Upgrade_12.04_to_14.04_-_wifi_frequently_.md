---
title: "[ubuntu] Upgrade 12.04 to 14.04 - wifi frequently disconnects with no auto reconnect"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by Tony_Bennett on 2014-04-25
I updated my Dell Inspiron laptop from 12.04 to 14.04 a couple of days ago and have noticed 
that sometimes, after the system has been idle for a while (idle only, not powered off, and not suspended,
and without the lid being closed, and with the power still plugged in) the wifi indicator on
the top line of the screen shows no power.
If I run "nmcli list" it shows:

```
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         disconnected    enabled         enabled    enabled         disabled  
```

Then if I run "sudo iwlist scan" Wifi will "reconnect" and begin working.

I never had this issue in the 8 months I ran 12.04 on this laptop.

Does anyone have any thoughts???

Thanks

---

### Post by varunendra on 2014-04-27
Welcome to the forums Tony_Bennett!

Please check the output of -
```
iwconfig
```
Does it show "Power Management" as "on" ? If yes, please try -
```
sudo iwconfig wlan0 power off
```
(assuming your wireless interface is named "wlan0") and see if it makes the problem go away. If not try creating a blank file in '/etc/pm/power.d' directory to disable the default wireless power management script. Following command will create the file -
```
sudo touch /etc/pm/power.d/wireless
```

Even if that doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Tony_Bennett on 2014-04-27
Thanks for the reply, here is what you requested and a bit more:

```
trb@Dell-Laptop:~/Downloads$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"BennettWireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:81:A2:1B   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:371   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

```

Here is the the output from dmesg when the problem occurs, followed by what dmesg shows when
I run "sudo iwlist scan":
```
[241615.896135] wlan0: authenticate with 00:13:10:81:a2:1b
[241615.908306] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[241615.911258] wlan0: authenticated
[241615.911635] iwlwifi 0000:09:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[241615.911645] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[241615.911651] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[241615.912014] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[241615.914503] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[241615.919911] wlan0: associated
[244074.793657] wlan0: deauthenticated from 00:13:10:81:a2:1b (Reason: 7)     
[244090.503481] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[244140.000418] wlan0: authenticate with 00:13:10:81:a2:1b                            <<<< From here on were after I ran: sudo iwlist scan
[244140.009347] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[244140.012682] wlan0: authenticated
[244140.012906] iwlwifi 0000:09:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[244140.012912] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[244140.012917] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[244140.014611] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[244140.018856] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[244140.021012] wlan0: associated
[244140.021032] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[244140.037671] wlan0: deauthenticating from 00:13:10:81:a2:1b by local choice (reason=2)
[244140.043536] wlan0: authenticate with 00:13:10:81:a2:1b
[244140.052025] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[244140.570470] wlan0: authenticated
[244140.573220] iwlwifi 0000:09:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[244140.573230] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[244140.573236] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[244141.081274] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[244142.130039] wlan0: associate with 00:13:10:81:a2:1b (try 2/3)
[244142.130339] wlan0: associate with 00:13:10:81:a2:1b (try 3/3)
[244143.722427] wlan0: association with 00:13:10:81:a2:1b timed out
[244144.281501] wlan0: authenticate with 00:13:10:81:a2:1b
[244144.291103] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[244144.298343] wlan0: authenticated
[244144.298788] iwlwifi 0000:09:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[244144.298794] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[244144.298797] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[244144.298803] wlan0: waiting for beacon from 00:13:10:81:a2:1b
[244144.393785] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[244144.398772] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[244144.404710] wlan0: associated

```

Here is the output of running your script:
[ATTACH]252582[/ATTACH]

If you need any other info, just let me know...
Thanks in advance.

-tony

---

### Post by varunendra on 2014-04-27
Can you please try changing the encryption type in the router/access-point to WPA2-PSK with AES (CCMP)? Currently you are using WPA(1) with TKIP which is a problem in itself. TKIP is outdated, less secure and inefficient encryption algorithm which can severely affect network performance sometimes.

Apart from that, check if there is a feature called "WMM" in the router. It is related to "QoS" and is usually located right under its settings. If it is there, make sure it is disabled. It is supposed to help in some particular cases, but usually causes problem instead. Disable "QoS" also if it is enabled. Save the changes and reboot the router.

---

### Post by Tony_Bennett on 2014-04-27
FYI: My router is a Linksys WRT54G

I have changed my encryption type from WPA/TKIP to WPA2-PERSONAL/AES.

Although my router showed both wired and wireless QOS (quality of service) as
disabled, I changed it to "enabled" then back to "disabled" and updated it.

Next I "Disconnected" my wireless (using the wireless icon in the title bar), then
reconnected it the same way... Here are the last 100 lines  in ```
dmesg | awk '/wlan0/ || /iwlwifi/' | tail -100
```

```
[260505.628211] wlan0: associated
[284011.350959] wlan0: deauthenticated from 00:13:10:81:a2:1b (Reason: 7)
[284027.252305] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[310294.501850] wlan0: authenticate with 00:13:10:81:a2:1b
[310294.511571] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[310294.519945] wlan0: authenticated
[310294.520080] iwlwifi 0000:09:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[310294.520083] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[310294.520086] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[310294.520528] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[310294.523700] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=5)
[310294.528936] wlan0: associated
[310294.528951] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[310294.546494] wlan0: deauthenticating from 00:13:10:81:a2:1b by local choice (reason=2)
[310294.553913] wlan0: authenticate with 00:13:10:81:a2:1b
[310294.562254] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[310295.634863] wlan0: send auth to 00:13:10:81:a2:1b (try 2/3)
[310296.173933] wlan0: authenticated
[310296.177966] iwlwifi 0000:09:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[310296.177980] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[310296.177989] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[310296.657305] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[310297.631133] wlan0: associate with 00:13:10:81:a2:1b (try 2/3)
[310298.625583] wlan0: associate with 00:13:10:81:a2:1b (try 3/3)
[310299.687622] wlan0: association with 00:13:10:81:a2:1b timed out
[310300.255469] wlan0: authenticate with 00:13:10:81:a2:1b
[310300.264432] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[310300.267292] wlan0: authenticated
[310300.267661] iwlwifi 0000:09:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[310300.267667] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[310300.267671] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[310300.267675] wlan0: waiting for beacon from 00:13:10:81:a2:1b                                                            
[310300.354208] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[310300.356838] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=5)
[310300.363256] wlan0: associated
[317012.372091] wlan0: deauthenticated from 00:13:10:81:a2:1b (Reason: 7)
[317012.431863] wlan0: authenticate with 00:13:10:81:a2:1b
[317012.440929] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[317012.442839] wlan0: authenticated
[317012.443271] iwlwifi 0000:09:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[317012.443283] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[317012.443292] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[317012.447203] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[317012.449723] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=12 aid=0)
[317012.449728] wlan0: 00:13:10:81:a2:1b denied association (code=12)
[317012.465574] wlan0: deauthenticating from 00:13:10:81:a2:1b by local choice (reason=3)
[317013.480792] wlan0: authenticate with 00:13:10:81:a2:1b
[317013.481811] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[317013.488743] wlan0: authenticated
[317013.489177] iwlwifi 0000:09:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[317013.489188] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[317013.489194] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[317013.489985] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[317013.492472] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=12 aid=0)
[317013.492481] wlan0: 00:13:10:81:a2:1b denied association (code=12)
[317013.507086] wlan0: deauthenticating from 00:13:10:81:a2:1b by local choice (reason=3)
[317015.036610] wlan0: authenticate with 00:13:10:81:a2:1b
[317015.044776] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[317015.047875] wlan0: authenticated
[317015.048036] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[317015.048040] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[317015.048273] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)                                                           
[317015.050684] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=2)
[317015.052759] wlan0: associated
[317144.983638] wlan0: deauthenticated from 00:13:10:81:a2:1b (Reason: 7)
[317145.009920] wlan0: authenticate with 00:13:10:81:a2:1b
[317145.018653] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[317145.020796] wlan0: authenticated
[317145.020939] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[317145.020942] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[317145.021424] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[317145.023843] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[317145.025254] wlan0: associated
[317149.576426] wlan0: deauthenticated from 00:13:10:81:a2:1b (Reason: 7)
[317150.169107] wlan0: authenticate with 00:13:10:81:a2:1b
[317150.181792] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[317150.186592] wlan0: authenticated
[317150.186843] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[317150.186851] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[317150.187825] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[317150.191097] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[317150.193189] wlan0: associated
[317151.111641] wlan0: deauthenticated from 00:13:10:81:a2:1b (Reason: 7)
[317151.821061] wlan0: authenticate with 00:13:10:81:a2:1b
[317151.824427] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[317151.840804] wlan0: authenticated
[317151.841160] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[317151.841166] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[317151.842016] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[317151.867209] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[317151.876415] wlan0: associated
[317226.820083] wlan0: deauthenticating from 00:13:10:81:a2:1b by local choice (reason=3)                                   
[317235.382235] wlan0: authenticate with 00:13:10:81:a2:1b
[317235.390740] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[317235.403656] wlan0: authenticated
[317235.403802] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[317235.403806] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[317235.406109] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[317235.412161] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[317235.415139] wlan0: associated

```

---

### Post by Tony_Bennett on 2014-04-27
FYI: Changing from WPA-TKIP to WPA2-AES did not eliminate the problem

It just happened again...

Here is an unfiltered tail of dmesg -T:

```
[Sun Apr 27 15:48:15 2014] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[Sun Apr 27 15:48:15 2014] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[Sun Apr 27 15:48:15 2014] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[Sun Apr 27 15:48:15 2014] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[Sun Apr 27 15:48:15 2014] wlan0: associated
[Sun Apr 27 17:29:12 2014] wlan0: deauthenticated from 00:13:10:81:a2:1b (Reason: 7)
[Sun Apr 27 17:29:12 2014] cfg80211: Calling CRDA to update world regulatory domain
[Sun Apr 27 17:29:12 2014] cfg80211: World regulatory domain updated:
[Sun Apr 27 17:29:12 2014] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[Sun Apr 27 17:29:12 2014] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 17:29:12 2014] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 17:29:12 2014] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 17:29:12 2014] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 17:29:12 2014] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 17:29:12 2014] wlan0: authenticate with 00:13:10:81:a2:1b
[Sun Apr 27 17:29:12 2014] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[Sun Apr 27 17:29:12 2014] wlan0: authenticated
[Sun Apr 27 17:29:12 2014] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[Sun Apr 27 17:29:12 2014] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[Sun Apr 27 17:29:12 2014] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[Sun Apr 27 17:29:12 2014] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[Sun Apr 27 17:29:12 2014] wlan0: associated
[Sun Apr 27 18:31:17 2014] perf samples too long (2504 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[Sun Apr 27 20:26:05 2014] wlan0: deauthenticated from 00:13:10:81:a2:1b (Reason: 7)
[Sun Apr 27 20:26:05 2014] cfg80211: Calling CRDA to update world regulatory domain
[Sun Apr 27 20:26:05 2014] cfg80211: World regulatory domain updated:
[Sun Apr 27 20:26:05 2014] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[Sun Apr 27 20:26:05 2014] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 20:26:05 2014] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 20:26:05 2014] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 20:26:05 2014] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 20:26:05 2014] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 20:26:21 2014] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[Sun Apr 27 20:28:45 2014] wlan0: authenticate with 00:13:10:81:a2:1b
[Sun Apr 27 20:28:45 2014] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[Sun Apr 27 20:28:45 2014] wlan0: authenticated                                                                                        
[Sun Apr 27 20:28:45 2014] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[Sun Apr 27 20:28:45 2014] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[Sun Apr 27 20:28:45 2014] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[Sun Apr 27 20:28:45 2014] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[Sun Apr 27 20:28:45 2014] wlan0: associated
[Sun Apr 27 20:28:45 2014] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[Sun Apr 27 20:28:45 2014] wlan0: deauthenticating from 00:13:10:81:a2:1b by local choice (reason=2)
[Sun Apr 27 20:28:46 2014] wlan0: authenticate with 00:13:10:81:a2:1b
[Sun Apr 27 20:28:46 2014] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[Sun Apr 27 20:28:46 2014] cfg80211: Calling CRDA to update world regulatory domain
[Sun Apr 27 20:28:46 2014] cfg80211: World regulatory domain updated:
[Sun Apr 27 20:28:46 2014] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[Sun Apr 27 20:28:46 2014] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 20:28:46 2014] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 20:28:46 2014] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 20:28:46 2014] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 20:28:46 2014] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[Sun Apr 27 20:28:46 2014] wlan0: authenticated
[Sun Apr 27 20:28:46 2014] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[Sun Apr 27 20:28:46 2014] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[Sun Apr 27 20:28:46 2014] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[Sun Apr 27 20:28:48 2014] wlan0: associate with 00:13:10:81:a2:1b (try 2/3)
[Sun Apr 27 20:28:50 2014] wlan0: associate with 00:13:10:81:a2:1b (try 3/3)
[Sun Apr 27 20:28:51 2014] wlan0: association with 00:13:10:81:a2:1b timed out
[Sun Apr 27 20:28:51 2014] wlan0: authenticate with 00:13:10:81:a2:1b
[Sun Apr 27 20:28:51 2014] wlan0: send auth to 00:13:10:81:a2:1b (try 1/3)
[Sun Apr 27 20:28:51 2014] wlan0: authenticated
[Sun Apr 27 20:28:51 2014] iwlwifi 0000:09:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[Sun Apr 27 20:28:51 2014] iwlwifi 0000:09:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[Sun Apr 27 20:28:51 2014] wlan0: waiting for beacon from 00:13:10:81:a2:1b
[Sun Apr 27 20:28:51 2014] wlan0: associate with 00:13:10:81:a2:1b (try 1/3)
[Sun Apr 27 20:28:51 2014] wlan0: RX AssocResp from 00:13:10:81:a2:1b (capab=0x411 status=0 aid=1)
[Sun Apr 27 20:28:51 2014] wlan0: associated

```

Anything else I can furnish to attempt to solve this...???

-tony

---

### Post by tfrue on 2014-04-28
My thought is that you should try and delete the connection info for you connection to your router by clicking on the wireless icon on the top right, going to "Edit Connections", and then highlight your connection to your router and delete it.

You should also try and enable the WPA2 and disable QoS in your router again, and then try and connect to your router from a fresh start, I guess we could say.

Also, is the firmware in your router up-to-date? Check the manufactures support page. Here is the link:
[http://support.linksys.com/en-us/support/routers/WRT54G/](http://support.linksys.com/en-us/support/routers/WRT54G/)

---

### Post by varunendra on 2014-04-28
With the recommended changes applied, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Tony_Bennett on 2014-04-28
Thank you for your responses.

I have:
[LIST]
[*]Deleted the connection (via top-bar, wireless icon, edit connection, delete) 
[*]Reconnected to my router (I was challenged for my passphrase) 
[*]Went to the Linksys website and upgraded my routers firmware (BTW recall there was no problems with 12.04 LTS) 
[*]Verified the firmware was upgraded on the router 
[*]Verified that QOS was turned off on the router 
[*]Verified the router is using WPA2-AES 
[*]Once again deleted the connection (same as above) 
[*]Once again reconnected to my router (challenged for my passphrase) 
[/LIST]
Ran the wireless_script... the file is attached.



Thanks again,
-tony

---

### Post by varunendra on 2014-04-28
Please try some driver parameters as suggested in this post : [http://ubuntuforums.org/showpost.php?p=12943350](http://ubuntuforums.org/showpost.php?p=12943350)
(you are using "iwldvm" instead of "iwlmvm", which doesn't have any parameters available. So try only those that are applicable to "iwlwifi")

If they don't seem to help, you can revert the changes by deleting the conf files created by the commands suggested in the post linked above. For example -
```
sudo rm /etc/modprobe.d/iwlwifi.conf
```

By the way, which country are you located in? Sometimes it may also help to explicitly declare the country code for local regdomain (Regulatory Domain) settings. Currently it has been defaulted to "00".

For example, if you are located in US, you can apply the US specific regdomain settings with the following command -
```
sudo iw reg set US
```
To find your country code, please refer to this page : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

Use the following command to check if the command was run and accepted correctly -
```
iw reg get
```
It should show "US"... followed by the details of settings specific to US.

---

### Post by Tony_Bennett on 2014-04-28
I have made the change to set the country code to "US":
```
trb@Dell-Laptop:~/Downloads/wifi_script_dir$ iw reg get
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


```

Before I make the changes based upon the LINK you sent, I wanted to show the
current contents of /etc/modprobe.d/iwlwifi.conf to make sure that deleting it
won't cause an issue:
```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```

---

### Post by varunendra on 2014-04-28
The current contents of the "iwlwifi.conf" file are the defaults that come with the OS, and no custom entries I suggested exist in it. It is supposed to do what it says in the comments, although I haven't yet noticed any change with or without it.

Anyway, since no custom parameters exist in it, you may leave it as it is. If doubtful, you may also just move it so that you can restore it later if required. For example, to move it to your Desktop, simply open a terminal and run -
```
sudo mv /etc/modprobe.d/iwlwifi.conf Desktop/
```

---

### Post by Tony_Bennett on 2014-04-28
Varun,

I have done:
```
trb@Dell-Laptop:~/Downloads/wifi_script_dir$ sudo mv /etc/modprobe.d/iwlwifi.conf ./
trb@Dell-Laptop:~/Downloads/wifi_script_dir$ echo "options iwlmvm power_scheme=1" | sudo tee /etc/modprobe.d/iwlmvm.conf
options iwlmvm power_scheme=1
trb@Dell-Laptop:~/Downloads/wifi_script_dir$ echo "options iwlwifi bt_coex_active=N swcrypto=1 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
options iwlwifi bt_coex_active=N swcrypto=1 11n_disable=1
trb@Dell-Laptop:~/Downloads/wifi_script_dir$ ls /etc/modprobe.d
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf  mlx4.conf
blacklist-ath_pci.conf   blacklist-modem.conf         fbdev-blacklist.conf     oss-compat.conf
blacklist.conf           blacklist-oss.conf           iwlmvm.conf              osspd.conf
blacklist-firewire.conf  blacklist-rare-network.conf  iwlwifi.conf             vmwgfx-fbdev.conf


```

Followed by a reboot.
I will advise if the problem still exists.

-tony

---

### Post by Tony_Bennett on 2014-05-01
FYI: I have not lost Connections in the last two days.

      I'm marking it as solved.

---

### Post by Lidan_Ai on 2014-07-11
Hi, I am having the same issues.  What exactly did you do that fixed the problem?

---

### Post by varunendra on 2014-07-11
Welcome to the forums Lidan_Ai!

Are you sure you have exactly the same card and OS version? If yes, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

If unsure of the card model, please start a new thread with a suitable title, and post back in it the details of the problem you are having along with the wireless_script report asked above. Then give me the link to your thread here or in a PM.

---

### Post by Moulik on 2015-02-25
Hi Varun,

I installed Ubuntu 14.04 a week ago. The wifi is intermittently disconnecting. I tried the steps mentioned in this thread and wifi worked fine for a day. And again it got disconnected. I works for sometime when i reboot. But this problem persists. 

Laptaop Details :
Lenovo Z50 - 70
Realtek RLT8723BE wifi driver.

I am attaching the wireless script that was in your signature. Please assist me.

-- Moulik

---

### Post by Beliriel on 2015-03-16
The wifi script doesn't seem to be working on my Lenovo X61. This is the output it generates, while although a wireless-info.txt file gets created it is blank:

```
hacku@hackusure:~$ ./wireless_script


        **** PLEASE WAIT WHILE THE SCRIPT GENERATES THE REPORT ****
  
  If this takes more than 1 minute, you may abort the script by pressing
  "Ctrl+Z" on your keyboard.
  
  (Type your Login Password when asked, then press 'Enter')

[sudo] password for hacku: 
sed: -e expression #1, char 184: unknown command: `*'


    ########################################################################

    DONE! All results saved in -

         File Name:     "wireless-info.txt" 
         Directory:     "/home/hacku"

    Please upload the above file or its contents where you are seeking help.

    ------------------------------------------------------------------------
    NOTE: Although we have taken full precaution to filter out all sensitive
          information, it is recommended to take a look at the file yourself
          to be double sure that it contains no sensitive data.
    ------------------------------------------------------------------------

    ########################################################################
```

What does sed: -e expression mean?

---

### Post by wildmanne39 on 2015-03-16
Run the script that is in my signature it works great and please start a new thread with the results.
Thanks

---

### Post by Beliriel on 2015-03-22
> **Wild Man said:**
> Run the script that is in my signature it works great

I don't see a signature?

---

### Post by wildmanne39 on 2015-03-22
Will I guess the signature did not show up because I was on my cell phone when I posted that message, but I am on my laptop now so you should see it.
Thanks

---

### Post by darek334 on 2016-02-13
Hi On model of Lenovo with realtek wifi chip **RTL8723BE** :
```
  *-network                      description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: d8:5d:e2:1f:a4:3b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.13.0-77-generic firmware=N/A ip=92.168.1.132 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:32 ioport:3000(size=256) memory:f0b00000-f0b03fff



```
I had the same problem, often temporary disconnecting with no auto and manual connect restore, for me helps this simple topic with few steps :
[http://www.dedoimedo.com/computers/ubuntu-trusty-realtek.html](http://www.dedoimedo.com/computers/ubuntu-trusty-realtek.html)

Only difrend what I did was run not : ```
git clone http://github.com/lwfinger/rtl8723be
```
only ```
git clone http://github.com/lwfinger/rtlwifi_new
```

However if you download first path or second, firs read README.md from where I took new path , after next steps My WIFI works now excellent , thank for this guy for his tip and good advise !

---

