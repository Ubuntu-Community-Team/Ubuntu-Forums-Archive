---
title: "Asus W7S connected to D-Link router but no internet connection in Ubuntu 14.04LTS"
date: 2015-07-17
forum: Networking &amp; Wireless
---

### Post by diane9 on 2015-07-17
Hi, 

I am a new user of ubuntu.  I tried to connect my laptop to my router and it was successful.  However, I cannot browse on internet even when it is connected.  Anyone can help? Thanks.  

[ATTACH=CONFIG]263247[/ATTACH]

---

### Post by Vladlenin5000 on 2015-07-17
Hi and welcome.

Connected how? Ethernet or WiFi?

---

### Post by chili555 on 2015-07-17
> wlan0     IEEE 802.11abgn  ESSID:"\xEF\xBC\xA4\xEF\xBD\x89\xEF\xBD\x81\xEF\xBD\x8E\xEF\xBD\x85"  
          [COLOR="#FF0000"]Mode:Ad-Hoc [/COLOR] Frequency:2.412 GHz  Cell: <MAC 'ïŒ€ïœ‰ïœïœŽïœ…' [AC1]>   
          Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:offYour wireless is set to Ad Hoc; in other words, it is waiting for another computer to connect to it for a computer-to-computer transfer or similar. This often happens when you follow the 'Create New WiFi Network' process.

Please click the Network Manager icon and select 'Edit Connections.' Select WiFi and Edit. Change the mode to Infrastructure and it should connect properly.

[ATTACH=CONFIG]263251[/ATTACH]

---

### Post by diane9 on 2015-07-18
Thanks chil555,

Yes I notice its Ad Hoc too.  However, when I select it to "infrastructure", the connection drop out!!! Seems it can only connect to the router while it is set to "ad hoc".  Is there anything I can do? It connects perfect when it is wired, and the router works perfect with other Windows OS and Android phones too.

---

### Post by diane9 on 2015-07-18
Hi Valdlenin5000,

It connects perfectly with wired but I want it to connect to Wifi.  Is there anything I can do to make it connected to internet?

---

### Post by chili555 on 2015-07-18
> **diane9 said:**
> Thanks chil555,

Yes I notice its Ad Hoc too.  However, when I select it to "infrastructure", the connection drop out!!! Seems it can only connect to the router while it is set to "ad hoc".  Is there anything I can do? It connects perfect when it is wired, and the router works perfect with other Windows OS and Android phones too.But it is not connected to the router at all. Please check here:> wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          [COLOR="#FF0000"]inet addr:10.42.0.1[/COLOR]  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10341 (10.3 KB)Check all the other devices on your network. Do they have an IP address in the 10.42.0.xx range? Or are they in the 192.168.0.x range?

As I said:>  it is waiting for another computer to connect to it for a computer-to-computer transfer or similar. This often happens when you follow the 'Create New WiFi Network' process.That is not what you want.

Connection dropping is a whole different issue. First, I suspect this is your router since its signal strength is 70/70 or 100%:> Cell 04 - Address: <MAC '' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000142ee5180
                    Extra: Last beacon: 12200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSKFirst, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot with the mode set to Infrastructure and let us know how it's working.

---

### Post by diane9 on 2015-07-18
Thank you so much for your help.  I found that was because my router was set to TKIP therefore ubuntu does not support.  Now a weird problem occurred.  The router was set to "Hidden" therefore I tried to connect it through the "Connect to a hidden Wi-Fi Network" tab.  Seems the computer can now receive the signal of my router, but then it ask for the Network password again and again, and cannot connect to it.  I'm pretty sure the Network key I typed was correct...

---

### Post by chili555 on 2015-07-18
Could you please verify it? Does it connect or is the behavior the same, if you un-hide the SSID? Many Linux drivers have trouble with hidden networks and hiding only offers very little protection. The simplest tools can detect the name pretty easily. Of course, the WPA2-AES password is another matter altogether.

---

### Post by diane9 on 2015-07-18
Thanks for your advice.  However, even I change the router setting and un-hide the SSID, the same thing happen (ubuntu can receive the Wi-Fi signal but keep asking me for the Network key and I cannot connect it to the router).  Anything I can do?

---

### Post by diane9 on 2015-07-20
In additional, I tried to remove all the securities option and set the router as an open network, ubuntu still ask me for the network password when it receive the network signal.  I was running an upgrade from 12.04 and I was having no problem to connect to this router.  Can anyone help? Its really annoying the laptop cannot connect to the Wifi network.  Thanks!!

---

### Post by chili555 on 2015-07-20
Let's try a driver parameter to see if it helps. From a terminal:```
sudo -i
modprobe -r iwl4965
modprobe iwl4965 11n_disable=1
echo "options iwl4965 11n_disable=1"  >  /etc/modprobe.d/iwl4965.conf
exit
```Any improvement?

---

### Post by diane9 on 2015-07-21
Thank you so much!!! Finally connect the laptop to the Wifi!!!

---

