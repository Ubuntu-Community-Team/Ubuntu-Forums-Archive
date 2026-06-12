---
title: "Atheros AR9485 drop connection  Ubuntu 15.10"
date: 2016-03-16
forum: Networking &amp; Wireless
---

### Post by ipgd-bali on 2016-03-16
Dear fellows,

I'm new to ubuntu.
I'd like to master it.
Anyway, I install Ubuntu on my laptop, it seems that my connection is not good. 
My Wifi is connected to internet. 
Sometime I can connect to internet and sometime can't.
But it is still connected to wifi. 
When it can't connect to internet, my internet browser took a long time , and ends without any page opened. 

I hope you guys can help me with my problem.
I'm sorry for my English.
Thank You.

[ATTACH=CONFIG]267839[/ATTACH]

---

### Post by chili555 on 2016-03-16
I only see a few things to suggest here. First, you have presented your wireless card and driver with a very difficult problem. It is here:> CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                      BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
DIRECT-FTSCX-3400 Series  <MAC 'DIRECT-FTSCX-3400 Series' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        
[COLOR="#FF0000"]IPGD's Home  [/COLOR]             <MAC 'IPGD's Home' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
[COLOR="#FF0000"]IPGD's Home[/COLOR]               <MAC 'IPGD's Home' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
DRPD1N3                   <MAC 'DRPD1N3' [AC4]>  Infra  10    2457 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1       no        
There are two SSIDs with the same name. Your card is attempting to roam from among them, trying to find the best signal:> [18841.249233] wlan0: deauthenticating from <MAC 'DRPD1N3' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[18842.222223] wlan0: authenticate with <MAC 'IPGD's Home' [AC1]>
[18842.243900] wlan0: direct probe to <MAC 'IPGD's Home' [AC1]> (try 1/3)
[18842.445698] wlan0: direct probe to <MAC 'IPGD's Home' [AC1]> (try 2/3)
[18842.649959] wlan0: direct probe to <MAC 'IPGD's Home' [AC1]> (try 3/3)
[18842.854197] wlan0: authentication with <MAC 'IPGD's Home' [AC1]> timed out
[18843.011119] wlan0: authenticate with <MAC 'IPGD's Home' [AC3]>
[18843.054996] wlan0: send auth to <MAC 'IPGD's Home' [AC3]> (try 1/3)I suggest, if this is your router or routers, that you change the name of one.

I have worked on more than one case here where spaces in the name have caused difficulties connecting. I suggest you go to the administration pages of your router and change the name from IPGD's Home to IPGD's-Home or IPGD'sHome or something without spaces and see if you can then properly connect. 

I also suggest that you change one of them to IPGD'sHome2.

I also recommend that you check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

After these changes, please tell us if the wireless is fixed.

---

### Post by ipgd-bali on 2016-03-18
Hi Chili555,

I've been trying what have you sugested.
And There is a big differences.
Now my connection is far better than before. 

But There is small problem when I leaved my PC for a moment.
It seems hard to connect again. 
Are there anyway to solve this ?
Or it just feature like Power Management ?

Anyway I've change 
```
REGDOMAIN=IS
``` to My Country.
But I Still Get
```
cfg80211:  DFS Master region: unset
```
when I dmesg.

Is that a serius problem, or I can leave it as is ?

Thank you for your Response.
It helps me a lot.



> **chili555 said:**
> I only see a few things to suggest here. First, you have presented your wireless card and driver with a very difficult problem. It is here:There are two SSIDs with the same name. Your card is attempting to roam from among them, trying to find the best signal:I suggest, if this is your router or routers, that you change the name of one.

I have worked on more than one case here where spaces in the name have caused difficulties connecting. I suggest you go to the administration pages of your router and change the name from IPGD's Home to IPGD's-Home or IPGD'sHome or something without spaces and see if you can then properly connect. 

I also suggest that you change one of them to IPGD'sHome2.

I also recommend that you check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

After these changes, please tell us if the wireless is fixed.

---

### Post by chili555 on 2016-03-18
> But There is small problem when I leaved my PC for a moment.
It seems hard to connect again.
Are there anyway to solve this ?
Or it just feature like Power Management ?Is power management set to On or Off here?```
iwconfig
```Here is an example from my computer:```
wlp3s0    IEEE 802.11bgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:2B:B0:DC:45:xx  
          Bit Rate=144.4 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          [COLOR="#FF0000"]Power Management:off[/COLOR]
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:104   Missed beacon:0

```If yours is on, which I doubt, I will have some further suggestions.> Anyway I've change
Code:

REGDOMAIN=IS

to My Country.
But I Still Get
Code:

cfg80211:  DFS Master region: unset

when I dmesg.Let's have a look:```
dmesg | grep DFS
```Is your country code really IS? Iceland? May I see:```
cat /etc/default/crda
```

---

### Post by grayscale2 on 2016-03-19
I have the same adapter and issues with connection on high traffic load.
Did you see somethng like this in dmesg?
ath: phy0: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x02000020 DMADBG_7=0x0002ad00

---

