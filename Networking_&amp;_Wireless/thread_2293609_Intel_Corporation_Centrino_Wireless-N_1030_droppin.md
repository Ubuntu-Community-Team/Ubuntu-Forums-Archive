---
title: "Intel Corporation Centrino Wireless-N 1030 dropping connection."
date: 2015-09-06
forum: Networking &amp; Wireless
---

### Post by Henka44 on 2015-09-06
Hello guys!

So my connection randomly drops and it can drop as soon as I load something up and it can drop after I've watched a stream on twitch.tv for 30 minutes, its really random but most of the time it does not drop while completely idle, atleast not what I've noticed.
I've had Ubuntu on my computer for just a few weeks so I'm a real newb, I had no issues the first 1-2 weeks and then it just came from nowhere.

To get my connection back I have to press the WiFi icon and click "Enable Networking" to disable it and then I have to click "Enable Networking" again to reenable it and then click "Connect to Hidden WiFi Network...".

I've searched and tried a few different things but none have been a permanent solution and its starting to annoy me that I can't use my laptop like I want to.

I included a log from the wireless script.

Also it might be worth nothing, I have two computers on wired net that has no issues and 2 phones + Ipad that has no issues with the WiFi.

Sorry if this post is sloppy but I had written a longer post but when I went to post, it said my token had expired and I had to refresh which erased my post... :-k

---

### Post by chili555 on 2015-09-06
We don't necessarily need longer posts, Just a simple 'my wireless drops for no apparent reason; here is my wireless info' is usually enough.

When I need to write a long post, in violation of my own rules (!!!), I write a text document in gedit and refine it and double-check it and then click 'post reply' or whatever, and copy and paste from gedit to the forum.

I notice this:> IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSKThe driver iwlwifi seems particularly sensitive to settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. > ##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

country 00: DFS-UNSETI recommend that your regulatory domain be set explicitly. Check yours:```
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

Reboot and tell us if it is improved.

---

### Post by Henka44 on 2015-09-07
Thank you for your post, I read everything you wrote carefully and followed all the steps, I will now proceed to reboot and I'll get back in probably 24~ hours or so, I wont know if its fixed in just a few minutes anyway.

Edit: It only took a few minutes before the connection dropped again so unfortunately it did not solve my issue.

---

### Post by chili555 on 2015-09-07
May we see a fresh, new *wireless_info*, please?

---

### Post by Henka44 on 2015-09-07
> **chili555 said:**
> May we see a fresh, new *wireless_info*, please?

Sure, attached it to this post.

Edit: Connection dropped again.
Edit2: Connection dropped once again.

---

### Post by chili555 on 2015-09-07
This is very interesting:> wlan0: deauthenticated from <MAC 'free wifi' [AC1]> (Reason: 4=DISASSOC_DUE_TO_INACTIVITY)Googling the reason yields various issues and bug reports and almost every one is an Intel chipset. 

I am quite confident that it is not an issue for every Intel chip. I have and use two without any issues. Moreover, in my years on this and other forums, I have seen this issue only a very few times.

In the results I Googled up, there seems to be no clear solution so I'm afraid we're on our own here.

First, I suggest you do:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot. Any improvement? If so, stop and proceed no further. There is no need to stack up unproven experiments on top of a now working wireless driver.

If there is no or little improvement, then do:```
sudo -i
echo "options mac80211 probe_wait_ms=1000"  >  /etc/modprobe.d/mac80211.conf
exit
```Reboot. Any improvement?

Depending on your report, I will have another suggestion or two.

---

### Post by Henka44 on 2015-09-08
> **chili555 said:**
> This is very interesting:Googling the reason yields various issues and bug reports and almost every one is an Intel chipset. 

I am quite confident that it is not an issue for every Intel chip. I have and use two without any issues. Moreover, in my years on this and other forums, I have seen this issue only a very few times.

In the results I Googled up, there seems to be no clear solution so I'm afraid we're on our own here.

First, I suggest you do:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot. Any improvement? If so, stop and proceed no further. There is no need to stack up unproven experiments on top of a now working wireless driver.

If there is no or little improvement, then do:```
sudo -i
echo "options mac80211 probe_wait_ms=1000"  >  /etc/modprobe.d/mac80211.conf
exit
```Reboot. Any improvement?

Depending on your report, I will have another suggestion or two.

Interesting that it believes that I'm inactive when I'm not, also I've never had issues while I had Windows installed on the laptop.
Anyway, just did what you told me, going to reboot and start a stream and got to sleep and report back later.

Edit: The first part did not work as my internet just died again.
Edit2: None of the two things worked :/

---

### Post by chili555 on 2015-09-09
Please do:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line from:```
options iwlwifi 11n_disable=8
```To:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close the text editor.

Reboot.

If it is still dropping, please let us see:```
dmesg | hrep -e wlan -e iwl
```

---

### Post by Henka44 on 2015-09-09
> **chili555 said:**
> Please do:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line from:```
options iwlwifi 11n_disable=8
```To:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close the text editor.

Reboot.

If it is still dropping, please let us see:```
dmesg | hrep -e wlan -e iwl
```

Alright I did the first part and am gonna reboot now and keep an eye on the net for a while, if it drops again I will do the last part BUT I want to make sure, is it [COLOR=#000000][FONT=Ubuntu Mono]dmesg | hrep -e wlan -e iwl? [/FONT][/COLOR] should it not be grep instead of hrep? (It looks like a typo?) [COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by chili555 on 2015-09-09
> should it not be grep instead of hrep? (It looks like a typo?) You are quite right; sorry.

*wiping glasses*

---

### Post by Henka44 on 2015-09-10
> **chili555 said:**
> You are quite right; sorry.

*wiping glasses*

Alright it's still dropping, this is how my [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep -e wlan -e iwl[/FONT][/COLOR] looks.

```
henka@Laptop:~$ dmesg | grep -e wlan -e iwl[    2.866845] iwlwifi 0000:09:00.0: loaded firmware version 18.168.6.1 op_modeiwldvm
[    2.917417] iwlwifi 0000:09:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.917423] iwlwifi 0000:09:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.917427] iwlwifi 0000:09:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.917430] iwlwifi 0000:09:00.0: Detected Intel(R) Centrino(R) Wireless-N 1030 BGN, REV=0xB0
[    2.918052] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[    2.951574] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    7.214127] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[    7.220978] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[    7.289523] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[    7.296376] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[    8.012238] wlan0: authenticate with 00:26:5a:d0:07:28
[    8.016906] wlan0: send auth to 00:26:5a:d0:07:28 (try 1/3)
[    8.019397] wlan0: authenticated
[    8.019595] wlan0: waiting for beacon from 00:26:5a:d0:07:28
[    8.069335] wlan0: associate with 00:26:5a:d0:07:28 (try 1/3)
[    8.072912] wlan0: RX AssocResp from 00:26:5a:d0:07:28 (capab=0x431 status=0 aid=3)
[    8.075807] wlan0: associated
[27663.587235] wlan0: deauthenticating from 00:26:5a:d0:07:28 by local choice (Reason: 3=DEAUTH_LEAVING)
[27663.637741] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27665.192875] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[27665.199801] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[27665.266336] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[27665.273280] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[27713.774606] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27716.331492] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[27716.338292] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[27716.406377] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[27716.413207] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[27717.153916] wlan0: authenticate with 00:26:5a:d0:07:28
[27717.163487] wlan0: send auth to 00:26:5a:d0:07:28 (try 1/3)
[27717.175977] wlan0: authenticated
[27717.179613] wlan0: associate with 00:26:5a:d0:07:28 (try 1/3)
[27717.182723] wlan0: RX AssocResp from 00:26:5a:d0:07:28 (capab=0x431 status=0 aid=4)
[27717.190442] wlan0: associated
[27723.284323] wlan0: deauthenticating from 00:26:5a:d0:07:28 by local choice (Reason: 3=DEAUTH_LEAVING)
[27725.834808] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[27725.841598] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[27725.907159] iwlwifi 0000:09:00.0: L1 Disabled - LTR Disabled
[27725.913982] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[27726.575501] wlan0: authenticate with 00:26:5a:d0:07:28
[27726.576454] wlan0: send auth to 00:26:5a:d0:07:28 (try 1/3)
[27726.581214] wlan0: authenticated
[27726.584429] wlan0: associate with 00:26:5a:d0:07:28 (try 1/3)
[27726.587495] wlan0: RX AssocResp from 00:26:5a:d0:07:28 (capab=0x431 status=0 aid=4)
[27726.589848] wlan0: associated
[27731.348686] wlan0: deauthenticating from 00:26:5a:d0:07:28 by local choice (Reason: 3=DEAUTH_LEAVING)
[27731.967830] wlan0: authenticate with 00:26:5a:d0:07:28
[27731.968635] wlan0: send auth to 00:26:5a:d0:07:28 (try 1/3)
[27731.970472] wlan0: authenticated
[27731.971220] wlan0: associate with 00:26:5a:d0:07:28 (try 1/3)
[27731.974341] wlan0: RX AssocResp from 00:26:5a:d0:07:28 (capab=0x431 status=0 aid=4)
[27731.984768] wlan0: associated
[27731.992572] wlan0: deauthenticating from 00:26:5a:d0:07:28 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[27732.000267] wlan0: authenticate with 00:26:5a:d0:07:28
[27732.000721] wlan0: send auth to 00:26:5a:d0:07:28 (try 1/3)
[27732.004659] wlan0: authenticated
[27732.007253] wlan0: associate with 00:26:5a:d0:07:28 (try 1/3)
[27732.014266] wlan0: RX AssocResp from 00:26:5a:d0:07:28 (capab=0x431 status=0 aid=4)
[27732.015904] wlan0: associated
henka@Laptop:~$ i



```

---

### Post by Henka44 on 2015-09-11
Weird I just came back to my laptop (I only use it in bed before falling to sleep) and it still has a connection :D

---

### Post by Henka44 on 2015-09-15
Internet has not dropped once in 4-5 days, I would consider my issue solved.
Thank you so much for your help chili555!

---

