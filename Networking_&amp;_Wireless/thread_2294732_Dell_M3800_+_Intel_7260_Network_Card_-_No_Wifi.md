---
title: "Dell M3800 + Intel 7260 Network Card - No Wifi"
date: 2015-09-12
forum: Networking &amp; Wireless
---

### Post by Wiggly_Woogly on 2015-09-12
The laptop came with Ubuntu preinstalled. Sadly I forgot to make a dell recovery stick. Installed Win7 and reinstalled Ubuntu on a separate partition. Wifi was always sketchy, but since the partition it has been alarming. Ubuntu fails to connect to wifi most of the time; at first it wouldn't connect at all. Then I began connecting it to my router with the ethernet-to-usb adapter. After long periods surfing the net error-free through the cable, it sometimes manages to connect to the wifi, and then I can unplug the ethernet. However it always loses the wifi connection after suspending and resuming. Usually the next time I can use it is after a reboot and another long period of waiting.

Could it be that I don't have correct drivers for the Intel 7260 network card? I did forget to make the Dell stick, so now am I using generic ones? Where can I find the correct drivers for this card?

I should mention that wifi and everything else works fine on the Win7 partition.

Many thanks!

---

### Post by Wiggly_Woogly on 2015-09-13
I have made 2 "wireless-into" files, one for when the wifi was working, and one for when I couldn't manage to connect.

I also made a pastebin of my syslog file covering the period when WIFI was working > I closed my laptop lid > WIFI didn't work anymore (I closed the lid around 21:56 I believe). [http://pastebin.com/Zzb19avJ](http://pastebin.com/Zzb19avJ)

Thanks and regards, everybody.

[ATTACH]264394[/ATTACH]

[ATTACH]264395[/ATTACH]

---

### Post by chili555 on 2015-09-13
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot.

Finally, I'd love to see what version of the firmware is requested and loaded:```
dmesg | grep iwl
```

---

### Post by Wiggly_Woogly on 2015-09-13
These are the only knobs I have to twiddle in my router setup. Can't find how to change from WPA2. Also I have 300 and 140 mbps to choose from in channel width, which doesn't make sense to me.
I will later try your second suggestion.
[IMG]http://i61.tinypic.com/idghs8.jpg[/IMG]

---

### Post by Wiggly_Woogly on 2015-09-14
> **chili555 said:**
> I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router.

So as I showed, I can't really work out how I'm supposed to change many of those things on my DLink router - it looks like I don't have an option to c

> **chili555 said:**
> Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.
Did this.

> **chili555 said:**
> If these changes do not help, please try:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot.

Finally, I'd love to see what version of the firmware is requested and loaded:```
dmesg | grep iwl
```
Did this too. Still no luck. I had some limited luck with the temporary solution here: [http://zeroset.mnim.org/2014/04/22/unstable-wifi-connection-on-ubuntu-14-04-trusty-tahr-ctrl-event-disconnected-reason4-locally_generated1/](http://zeroset.mnim.org/2014/04/22/unstable-wifi-connection-on-ubuntu-14-04-trusty-tahr-ctrl-event-disconnected-reason4-locally_generated1/) but now this has stopped working too.

```
dmesg | grep iwl
``` Returns the following...
```

[    6.795807] iwlwifi 0000:06:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
[    6.809975] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    6.810045] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    6.810297] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    7.136161] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    7.166753] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    7.167018] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled

```

---

### Post by chili555 on 2015-09-14
>  I had some limited luck with the temporary solution here:Let's try it here:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the last line from:```
options iwlwifi 11n_disable=8
```To read:```
options iwlwifi 11n_disable=1  
```Proofread carefully, save and close the text editor.> These are the only knobs I have to twiddle in my router setup.  All you can do is all you can do. If your router or access point provides for fine-grained tuning,then I recommend you do so; if not,then do all you *can* do. We'll just do the best we can do with whatever tools we have to work with.

Reboot and tell me if it is improved.

---

