---
title: "Wifi slow with new router. all other devices blazing fast."
date: 2018-04-15
forum: Networking &amp; Wireless
---

### Post by veswill3 on 2018-04-15
I just got a massive internet upgrade and needed to buy a new router (Linksys EA8300) to handle the change. All other devices are blazing fast, except my laptop, which is painfully slow. This laptop's wifi speed is fine with other networks, so there must be something about my network config and router setup that are not playing well together. This has happened occasionally in the past when connecting to other random networks (like at airports) but now it's my home network so I cannot ignore the issue.

[http://paste.ubuntu.com/p/4BRKzzgM8N/](http://paste.ubuntu.com/p/4BRKzzgM8N/)

Any ideas?

---

### Post by chili555 on 2018-04-15
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=8

```
If it helps, make it permanent:

```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit

```
Finally, Network Manager will default to ethernet if it's available. Please make your tests with the ethernet detached.

Useful information: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

---

### Post by jeremy31 on 2018-04-15
See the instructions at [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
Ninja'd by chili

---

### Post by ajgreeny on 2018-04-15
Make sure that the router is set to use WPA2 only, not any of the other options available.

I am not good at figuring out from the wifi-info output what you are using at present but it looks as if you may have it set to WPA1/WPA2.

---

### Post by veswill3 on 2018-04-15
Thanks for the help, but unfortunately it does not appear that any of this has helped.

Quick summary of what I did:


- switched from WPA2/WPA mixed to WPA2 Personal
- Made sure I am using "mixed" instead of n only (it already was)
- forced 2.4 GHz to use channel 6 instead of auto (scanner app showed lowest activity)
- forced 2.4 GHz to use 20 MHz instead of auto
- rebooted the router
- forcibly set the regulatory domain REGDOMAIN=US
- set IPv6 to Ignore in Network Manager for this network
- and I did whatever this does: echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
- rebooted the laptop

Note: this is the end result. I did each step in turn with many reboots and checks inbetween. Same end results.


After all that...


other devices are still fast (160 Mbps down / 160 Mbps up)
My ubuntu laptop is still slow (6 Mbps down / 1.76 up)

[http://paste.ubuntu.com/p/JNBdhHZn8H/](http://paste.ubuntu.com/p/JNBdhHZn8H/)



Any other ideas?

---

### Post by chili555 on 2018-04-15
May we also see: ```
dmesg | grep iwl
```  Thanks.

---

### Post by veswill3 on 2018-04-15
Here is the output:

```

vesper@vesper-Z835:~$ dmesg | grep iwl
[   15.983094] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   16.059414] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 35138 op_mode iwldvm
[   16.175780] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.175788] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.175794] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.175800] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   16.178401] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   16.233154] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.800532] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[   25.959360] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   25.966888] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   25.966998] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[   26.002754] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   26.010785] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   26.010904] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3

```

I haven't changed anything, but a recent speed test shows 27 Mbps down and 7Mbps up, which is not great.
This machine is getting a bit old. Is this just the max it can handle? I can take it somewhere else tomorrow to run another speed test and see what it gets on another network.

---

### Post by veswill3 on 2018-04-16
I was unable to find another network to test with at the moment. I will try again later.
At this point the wifi is usable on this laptop, but every other device (even a cheap chromebook) gets at least 2x the download and 7x the upload.

---

### Post by praseodym on 2018-04-16
Lets deactivate the power management:
```

sudo iwconfig wlp2s0 power off
```

---

### Post by veswill3 on 2018-04-16
It does not seem to have made any difference. Is there something I need to do to reset things after running that command?

---

### Post by mc4man on 2018-04-17
you could consider getting a usb dual band dongle so your older device can use the 5g band & get your upgraded speeds
Had to do that here after the cable co. upgraded us, my main laptop was only device that couldn't do 5g, performance suffered after the upgrade on the 2.4 band.
(- also I am in a congested area for 2.4..

---

### Post by veswill3 on 2018-04-18
I was finally able to run a speed test on another network and what I got was comparable to my home wifi now, so even though its not ridiculously fast like the other newer devices, it appears normal, and is now usable. I believe the first set of instructions contained the answer that took it from super slow to normal.

Thanks a bunch for the help chili555, jeremy31, ajgreeny, praseodym, and mc4man. I will mark this as solved ASAP

---

### Post by Hadaka on 2018-04-18
Hi even though this thread has been marked Solved, The first pastebin report,
line #118 and the second pastebin wireless diagnostic report, line #121 both
indicate #-> "Power Management-[COLOR=#ff0000]**on**[/COLOR]" this will greatly reduce the speed and may be
turned off with the command...
*Please copy and paste.
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
We await your report that the speed has improved.
Thanks

---

### Post by veswill3 on 2018-04-19
cool. updated. i was wondering how to make that permanent. Thanks Hadaka.

---

### Post by mikehardy on 2018-08-12
I'm posting this in a few threads because it may be pertinent, the TL;DR is that an upgrade to the kernel, using the UKUU package, choosing kernel 4.17.14 which is the most current at the moment, fixed slow iwlwifi speeds independent of everything else and was otherwise painless. Maybe interesting even though this one is marked as solved?

[https://unix.stackexchange.com/a/462175/304207](https://unix.stackexchange.com/a/462175/304207)

---

