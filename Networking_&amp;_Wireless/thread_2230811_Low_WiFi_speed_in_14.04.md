---
title: "Low WiFi speed in 14.04"
date: 2014-06-21
forum: Networking &amp; Wireless
---

### Post by dagavi2 on 2014-06-21
Hi, few days ago I noticed that Ubuntu 14.04 is limiting my wireless speed.

I have a ~3'4 MB/s conection and wireless is only getting 2 MB/s (tested with downloads and speed tests). Over ethernet is working fine (it gets full speed) and Windows 8 or Ubuntu 12.04 is working fine over wireless.

I tested again Ubuntu 14.04 with the live cd and it is limiting too (is not some software or configuration that I made or installed)

I executed the "wireless-script" that I found in other posts to get information: [https://dl.dropboxusercontent.com/u/1501117/wireless-info.tar.gz](https://dl.dropboxusercontent.com/u/1501117/wireless-info.tar.gz)

¿Any idea or fix? I supose, since I tested with 14.04 and 12.04 live cd's that is a problem/incompatibility introduced in some version > 12.04 (I don't checked 12.10 or 13.x)

---

### Post by varunendra on 2014-06-26
Hi, Welcome to the forums!

Not sure about the deal with Ubuntu 12.04, but you can try a few tweaks both in the router and Ubuntu to optimize the speed.

In Ubuntu -

[list][*] Set "IPv6" to "Ignore" in Network Manager
[*] Explicitly define the country code for RegDomain settings. Assuming (from your language code settings - "es_ES") you are in Spain, please open a terminal (Ctrl-Alt-T) and run the following code in it to do that -
```
sudo sed -i 's/^REG.*=$/&ES/' /etc/default/crda
```
..followed by a reboot. If you are in a different country, please refer to this table for country code : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)
[*] Run the following code in the terminal to use two common driver parameters that sometimes help the connectivity and speed -
```
echo "options iwlwifi bt_coex_active=N swcrypto=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
..followed by a reboot.[/list]

All of the above steps are needed to be done only once, no repeating.

In the router/access-point -
[list][*] Change the channel from 9 (or "auto") to 1 or 11.
[*] If 'WMM' support (usually under 'QoS', if available) is enabled, try disabling it. Also try disabling QoS itself for a test, if required.[/list]

**PS:**
By the way, you can (should) bump your post after 24 hours if nobody responds. Potentially helpful people may not be active when you post or bump (depending upon your timezone and time of posting), so bumping at an interval of about 30-36 hrs. may also get attention from those who can help.

---

### Post by dagavi2 on 2014-06-28
Thank you for your reply, but it doesn't worked :(

I will try another Ubuntu distribution (xubuntu, etc.) to test if has the same problem, and try to find a 13.10 distribution to test too. As I said, Ubuntu 12.04 works fine.

---

### Post by varunendra on 2014-06-28
I would like to see a fresh report with the recommended changes applied.

The performance of a device depends almost entirely on the driver and the drivers would be same across all distros using the same kernel version. So I doubt trying a different flavour would make any difference. But go ahead if that is easy for you, and let us know what you found.

---

### Post by Vladlenin5000 on 2014-06-29
Hi, varunendra. :p

First of all let me thank you for all the work and help you've been providing here, no doubt at the expense of some of your leisure time. I've learned a lot just by reading your suggestions.

Even so I would like to comment about RegDomain: From experience it changes nothing and it's only logical it doesn't. AFAIK its intended use is only to specify the country where the user is in order to conform with local legislation concerning the use of radio spectrum. As such it *might* be of use for someone in US where channels 12 and 13 aren't to be used. In Europe as in most of the world you can use all up to 13. IMO this can only affect a US user (RegDomain set to US) traveling across Europe if - and only if - the network he/she's trying to connect to happens to be in 12 or 13. It shouldn't matter otherwise. 
Likewise any European country code as well as the generic 00 should work.

Please correct me if I'm wrong. Thank you, and again, good job. Cheers.

---

### Post by varunendra on 2014-06-29
Hello Vlad,

Productive discussions like this are my main source of knowledge. I have no background IT education or training or other source of knowledge other than experimenting myself and searching the net when I don't know the answer to a question/problem. Whatever I suggest here has been learnt from the forum itself or from sources I found while troubleshooting some problem on the forum.

Setting country code is a kind of experiment about which I am still learning (unfortunately, don't have time now to dig up authentic sources and be sure what I am doing really makes sense and where).

I knew for a long time that the country code is supposed to be set dynamically, but never gave much thought to why it often defaults to '00'. In other words, I used to ignore it until a few months ago. The recommendation to explicitly set it when it defaults first came from my wireless guru **chili555** (of course he doesn't need an introduction here). The reason he gave made sense to me (card belongs to one country, AP to another, maybe because one of them was imported, their corresponding settings don't match, so regdomain code gets defaulted to something which is *supposed* to work everywhere, but apparently, it doesn't).

The logical explanation to why this default setting may be a problem is my own assumption and I may be completely wrong (dr. chili555 may have an authentic explanation for this too, I just didn't ask).

Let's share my assumption and try to explain the problem on the basis of that assumption taking this very thread as an example.

The defaulted (country code : 00) regdomain settings are :
```
country 00:
        (2402.000 - 2472.000 @ 40.000), (3.00, 20.00)
        (**2457.000 - 2482.000 @ [COLOR="#FF0000"]20.000[/COLOR]**), (3.00, 20.00), PASSIVE-SCAN, NO-IBSS
        (2474.000 - 2494.000 @ 20.000), (3.00, 20.00), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170.000 - 5250.000 @ 40.000), (3.00, 20.00), PASSIVE-SCAN, NO-IBSS
        (5735.000 - 5835.000 @ 40.000), (3.00, 20.00), PASSIVE-SCAN, NO-IBSS
```

Those for country code 'ES' are :
```
country ES:
        (2402.000 - 2482.000 @ **[COLOR="#FF0000"]40.000[/COLOR]**), (N/A, 20.00)
        (5170.000 - 5250.000 @ 40.000), (N/A, 20.00)
        (5250.000 - 5330.000 @ 40.000), (N/A, 20.00), DFS
        (5490.000 - 5710.000 @ 40.000), (N/A, 27.00), DFS
```
Now as you can notice in the highlighted part, all the channels in Spain (as per the regdomain setting) are allowed to operate at 40 MHz bandwidth, while the defaulted setting won't allow channels falling between frequency range 2457.000 - 2482.000 (Mhz, or 2.457 - 2.482 GHz) to operate above 20 MHz. Upto 2.472 GHz part of this range is overlapping (lies in both 20 and 40 MHz bw) in the defaulted settings. I don't know how it may affect the performance, but I see a possibility of fluctuation between both bandwidths which if really happens, can definitely cause problems.

Now suppose the AP is built for Spain and is currently operating exclusively at 40 MHz bandwidth, at some channel that falls in the 2.457 - 2.482 GHz frequency range. Result = possible problem for the defaulted setting (definite problem for 2.472 - 2.482 GHz range).

In OP's case here, the report shows the channel to be operating at 2.452 GHz, slightly below the "problem range". But I simply don't believe such outputs especially when these devices are designed to dynamically adjust some settings (including channels). Maybe the channel is set to "auto", may be it is just momentarily below the 'standard' frequency, maybe iwconfig is not reporting perfectly.. Better just make it what is supposed to work perfectly in all situations (in that environment).

I must admit that I have made it a habit to just set it as per which country the user is in without always analyzing which frequency the channel is operating at and whether the default settings are okay or not for that. It may cause trouble, in case the router is imported and was originally made for some other country. But we have to make some assumptions and we always go with what is more obvious. If things go worse instead of improving, we can always step back. Not all users are smart enough to determine their router's country settings and not all routers even display (or allow changing) that setting.

So far I only have a few (probably less than 5) instances here on the forums that suggest that explicitly defining the country code for regdomain settings helps, and at least one or two of them were solved only by doing that. Since no other change (to my knowledge) was involved, I may call them 'Proof of the concept', but couldn't find time to analyze them deeply and see if they can also corroborate  my assumptions.

So this is all I have seen, know and believe about regdomain settings. I don't mind being proven stupid, because the person doing so will be sharing something that will make me more knowledgeable about the stuff where I was wrong. So please feel free to share anything that proves me wrong or proves that these changes don't matter at all.

Regards. :)

---

### Post by Vladlenin5000 on 2014-06-29
Thank you for such detailed explanation.

No, I don't have anything to rebut. What I told you before was from experience and that experience being it works (or don't) regardless of that setting. However I must add such 'experiments' were all in Europe where *I suppose* everything is the same.

I'll keep an eye on this sub-forum, especially in threads like this, hoping to be surprised by the feedback.

---

### Post by chili555 on 2014-06-29
> So far I only have a few (probably less than 5) instances here on the forums that suggest that explicitly defining the country code for regdomain settings helps, and at least one or two of them were solved only by doing that. Since no other change (to my knowledge) was involved, I may call them 'Proof of the concept',Likewise, I have also solved a handful of cases by this method. Since it takes just a moment to do and, for the skeptical, another moment to undo, I always recommend it when there is trouble in a usually reliable driver. As Varun says, sometimes it helps and sometimes not.

This difference:```
country 00:
        (2402.000 - 2472.000 @ 40.000), (3.00, 20.00)
        (2457.000 - 2482.000 @ 20.000), (3.00, 20.00), [COLOR="#FF0000"]PASSIVE-SCAN, NO-IBSS[/COLOR]
        (2474.000 - 2494.000 @ 20.000), (3.00, 20.00), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170.000 - 5250.000 @ 40.000), (3.00, 20.00), PASSIVE-SCAN, NO-IBSS
        (5735.000 - 5835.000 @ 40.000), (3.00, 20.00), PASSIVE-SCAN, NO-IBSS
```Versus:```
country ES:
        (2402.000 - 2482.000 @ 40.000), (N/A, 20.00)
        (5170.000 - 5250.000 @ 40.000), (N/A, 20.00)  [COLOR="#FF0000"]<--Passive scan and IBSS not mentioned[/COLOR]
        (5250.000 - 5330.000 @ 40.000), (N/A, 20.00), DFS
        (5490.000 - 5710.000 @ 40.000), (N/A, 27.00), DFS
```...seem more significant to me than the presence or absence of channels 12 and 13.

@Varun-- Will you experimentally try 11n_disable?

---

### Post by varunendra on 2014-06-29
> **chili555 said:**
> @Varun-- Will you experimentally try 11n_disable?
I didn't already? Looks like attention-wise I am getting older than you. :p

**@dagavi2,**

Please also try this one of the most common tricks done with intel cards in low speed problems. Open a terminal and run the following code to apply "11n_disable=1" parameter temporarily -
```
sudo modprobe -rv iwldvm iwlwifi
sudo modprobe -v iwlwifi 11n_disable=1
sudo modprobe -v iwldvm
```
The first and last commands are simple unload/reload of modules (disabling/re-enabling the wifi), the second one will disable 'N' channel on the card (disabling higher than 54 Mbps speed), but it often helps getting practically better transfer speeds (upto 54 Mbps).

This would be a temporary change, and if it helps, let us know and we'll make it permanent. If it doesn't, please post back a fresh report with all the changes (including this one) applied that I have recommended so far.


**PS:**
> **chili555 said:**
> This difference:```
country 00:
        (2402.000 - 2472.000 @ 40.000), (3.00, 20.00)
        (2457.000 - 2482.000 @ 20.000), (3.00, 20.00), [COLOR="#FF0000"]PASSIVE-SCAN, NO-IBSS[/COLOR]
        (2474.000 - 2494.000 @ 20.000), (3.00, 20.00), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170.000 - 5250.000 @ 40.000), (3.00, 20.00), PASSIVE-SCAN, NO-IBSS
        (5735.000 - 5835.000 @ 40.000), (3.00, 20.00), PASSIVE-SCAN, NO-IBSS
```
Versus:```
country ES:
        (2402.000 - 2482.000 @ 40.000), (N/A, 20.00)
        (5170.000 - 5250.000 @ 40.000), (N/A, 20.00)  [COLOR="#FF0000"]<--Passive scan and IBSS not mentioned[/COLOR]
        (5250.000 - 5330.000 @ 40.000), (N/A, 20.00), DFS
        (5490.000 - 5710.000 @ 40.000), (N/A, 27.00), DFS
```...seem more significant to me than the presence or absence of channels 12 and 13.
More things that I kept ignoring so far, but I'm glad this discussion started and now I know a bit about these. :)

For the curious ones -

**Passive (vs Active) Scan :** [http://www.my80211.com/home/2010/1/11/80211-client-active-and-passive-scanning.html](http://www.my80211.com/home/2010/1/11/80211-client-active-and-passive-scanning.html)

**IBSS (Independent Basic Service Set) :** [https://en.wikipedia.org/wiki/Independent_Basic_Service_Set#Basic_service_set](https://en.wikipedia.org/wiki/Independent_Basic_Service_Set#Basic_service_set)

**OFDM (Orthogonal Frequency Division Multiplexing) :** [http://www.radio-electronics.com/info/rf-technology-design/ofdm/ofdm-basics-tutorial.php](http://www.radio-electronics.com/info/rf-technology-design/ofdm/ofdm-basics-tutorial.php) (easier than wikipedia explanation, which has too many crosslinks), and [http://mobiledevdesign.com/learning-resources/orthogonal-frequency-division-multiplexing-ofdm-faq-tutorial](http://mobiledevdesign.com/learning-resources/orthogonal-frequency-division-multiplexing-ofdm-faq-tutorial)

**DFS (Dynamic Frequency Selection) :** [http://wifi-insider.com/wlan/dfs.htm](http://wifi-insider.com/wlan/dfs.htm) (quick explanation) and, [https://en.wikipedia.org/wiki/Dynamic_Frequency_Selection](https://en.wikipedia.org/wiki/Dynamic_Frequency_Selection) (explanation and DFS vs FCA)

I'm not sure if absence of a declaration means implementation/non-implementation of the related stuff, but it sure leaves scope for doubts, possibly as well for drivers as for human minds.

I also know (both by personal experience and wisdom of ancestors) that 'Half knowledge is a dangerous thing', so I just consider these as tiny additions to my knowledge bank, not judging or concluding anything on basis of these (they're never sufficient for that without evidence and experimental proof).

**EDIT:**
To see the country code wise settings on Ubuntu, the method I know is the command -
```
regdbdump /lib/crda/regulatory.bin
```
or
```
regdbdump /lib/crda/regulatory.bin | less
```

---

### Post by jeremy31 on 2014-06-30
Ok, this somewhat confirms what I thought before I asked Varunendra about it in another post but has anybody used the cfg80211 parameter  ieee80211_regdom:IEEE 802.11 regulatory domain code (charp) as this seems to be one that defaults to 00

I tried the option and didn't notice any difference on my laptop

---

