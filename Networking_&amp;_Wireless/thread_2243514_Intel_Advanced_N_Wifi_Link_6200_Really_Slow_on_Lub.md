---
title: "Intel Advanced N Wifi Link 6200 Really Slow on Lubuntu 14.04"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by fantasma3 on 2014-09-09
Hi all

I just got an Intel Advanced N Wifi Link 6200 network card (For a normal pc btw), but the internet speed is really slow on Lubuntu 14.04. 
The fastest it goes is 54Mb/s (Which I guess is just G instead of N) and when refreshing/loading a page it just drops to 6Mb/S or just drops completely. 
Router is standing 3 meters away.

My router should be an N enabled (CBN CH6643E) (Some router you get with my "local" Internet Provider.)

I tried some things on from [this link]("http://ubuntuforums.org/showthread.php?t=2205733")  but it doesn't seem to be doing anything here.

Router Security Settings:
5Ghz security protocol:  WPA 2 PSK  (Otherwise I can pick: WEP/WPA PSK or WPA/WPA 2 PSK
WPA Encryption: AES
No WPS
No Mac-Filtering
Router also says my pc is connected on the 2.4Ghz.

Help would be much appreciated!

---

### Post by chili555 on 2014-09-09
I have the exact same device. I connect at N speeds with no dropping. I suggest you check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

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

I would also like to see the current readings for:```
cat /etc/modprobe.d/iwlwifi.conf
```We may need to make an amendment or two.

---

### Post by fantasma3 on 2014-09-09
So that's WPA2 PSK? 
Wireless Networkprotocol = WPA2 PSK than?
WPA encryption = AES
Just disabled 5Ghz and put it on 20mhz and put it on a fixed channel.

> sudo iw reg get 
Gives me > sudo iw: command not found


Second thing:
> # /etc/modprobe.d/iwlwifi.conf

# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


Question: I didn't install Lubuntu when I had the wifi card, does that matter?

---

### Post by chili555 on 2014-09-09
> Wireless Networkprotocol = WPA2 PSK than?
WPA encryption = AESCorrect.> sudo iw: command not foundJust go ahead and look up your CRDA and amend /etc/default/crda as above. Let's assume, as it in in 90% of all cases, that it's not specified.> # /etc/modprobe.d/iwlwifi.conf

# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system. When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211Looks fine so far.>  I didn't install Lubuntu when I had the wifi card, does that matter?Not in this case. If it boots and connects at all, we should be fine.

After these changes, reboot the router and the computer and tell us if it's better.

---

### Post by fantasma3 on 2014-09-10
Right forgot about that country code :D

The max speed is only 52Mb/s now, but it seems to be it doesn't drop to 1Mb/s as often as it did before. (But not sure if that's true.)

---

### Post by chili555 on 2014-09-10
> **fantasma3 said:**
> Right forgot about that country code :D

The max speed is only 52Mb/s now, but it seems to be it doesn't drop to 1Mb/s as often as it did before. (But not sure if that's true.)I suggest you watch it for a while and report. We can dig a bit deeper if needed.

---

### Post by fantasma3 on 2014-09-11
But 52Mb/s is still really really slow though...
That's like my 6 year old router, this one is like a year old.

---

### Post by chili555 on 2014-09-11
And what is your ISP speed? 150 Mb/s? I bet that's expensive!

I don't have any other suggestions.

---

### Post by fantasma3 on 2014-09-11
But I mean the speed from the PC to the Router, shouldn't it be something like 130Mb/s?

---

### Post by chili555 on 2014-09-11
Not necessarily all the time. The wireless card and driver will negotiate with the router and adjust as needed. Sometimes I see speeds as low as 1 Mb/s when I am doing nothing; that is, not sending and receiving traffic and sometimes I see 130 Mb/s. Right this second, I see:```
wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:D7:19:41:54:xx   
          Bit Rate=[COLOR="#FF0000"]115.6 Mb/s[/COLOR]   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  

```What is a bit confusing is that in Windows, what is reported is the maximum rate that bits will move across the network link. That's not always the actual rate that is now negotiated: [http://www.smallnetbuilder.com/wireless/wireless-basics/30664-5-ways-to-fix-slow-80211n-speed](http://www.smallnetbuilder.com/wireless/wireless-basics/30664-5-ways-to-fix-slow-80211n-speed)

What is also a factor is how far you are from the router. The further the distance, the lower the speeds. Radio frequency interference also plays a role. To reduce the effect of interference, you might experiment with different channels; usually 1, 6 and 11 are least affected. Since most routers come from the factory defaulted to channel 6, most of your neighbors will be on channel 6. Therefor, I'd try 1, 11 and if it's available in your country, 12 or 13.

---

### Post by jeremy31 on 2014-09-11
I wonder if this is another card that would be helped with 11n_disable=8

---

