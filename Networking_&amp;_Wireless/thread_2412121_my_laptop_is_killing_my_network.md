---
title: "my laptop is killing my network"
date: 2019-02-08
forum: Networking &amp; Wireless
---

### Post by TechnoJunky on 2019-02-08
I have a Dell INSPIRON 5577.  I've had it for a year, with Kubuntu (18.04 and 18.10) on it the whole time and have had no issues with it.  Due to some hard drive issues I had to reinstall Kubuntu 18.10. After installing all my desired applications and updating, it looked like all was good except no one on my home network could access the internet.  I have the Network Monitor widget on my desktop and could see that it was sending (and receiving) large amounts of data, 10-13 Mbps up AND down.  Disconnecting from the wifi resolves the issue and everyone can browse the net again.  It happens very sporadically.  It may not happen for an hour or it might start within a minute of rebooting or reconnecting to the wifi.  I decided to start again with a new install hoping that it wouldn't happen again, but it did.  I then installed Neon 5.14, same issue.  My next thought was that it might be something in my profile, I had to copy it to my new hard drive.  Maybe something didn't copy right?  So I renamed my home directory and created a new clean one (last night).  Everything seemed ok, but this morning the NIC was chatting up a storm, reset the wifi connection and within a minute it restarted.  Disconnected for a couple minutes and it hasn't restarted but I know it's only time before it does occur again.  Any ideas on how to troubleshoot this?

---

### Post by chili555 on 2019-02-08
Let's find out some details about the wireless device; specifically, the driver and interface name. You can find both in this terminal command:```
sudo lshw -C network
```In this example from my machine, I've highlighted both:> 
*-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: [COLOR="#FF0000"]wlp3s0[/COLOR]
       version: 83
       serial: xx:c5:d4:0e:64:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=[COLOR="#FF0000"]iwlwifi [/COLOR]driverversion=4.18.0-14-generic firmware=17.948900127.0 ip=192.168.0.9 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:29 memory:f0400000-f0401fffIn order to troubleshoot, I suggest that you check the logs for both instances, for example, in my case:```
dmesg | grep -e iwlwifi -e wlp3s0
```Of course, substitute your details here. Post the dmesg result and let's see what's going wrong.

---

### Post by TechnoJunky on 2019-02-08
Here's the output you asked for.
```
sudo lshw -C network =

*-network
       description: Wireless interface
       product: Wireless 3165
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 79
       serial: 74:e5:f9:53:d6:7b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-45-generic firmware=29.1044073957.0 ip=192.168.1.203 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:131 memory:df100000-df101fff

```
```
dmesg | grep -e iwlwifi -e wlp3s0=

[    4.710853] iwlwifi 0000:03:00.0: enabling device (0000 -> 0002)
[    4.722716] iwlwifi 0000:03:00.0: loaded firmware version 29.1044073957.0 op_mode iwlmvm
[    4.823707] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[    4.846505] iwlwifi 0000:03:00.0: base HW address: 74:e5:f9:53:d6:7b
[    5.041316] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[    6.281497] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    6.401552] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    6.471745] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    9.943617] wlp3s0: authenticate with 58:ef:68:69:0f:be
[    9.952138] wlp3s0: send auth to 58:ef:68:69:0f:be (try 1/3)
[    9.955042] wlp3s0: authenticated
[    9.956076] wlp3s0: associate with 58:ef:68:69:0f:be (try 1/3)
[    9.958437] wlp3s0: RX AssocResp from 58:ef:68:69:0f:be (capab=0x1511 status=0 aid=5)
[    9.960980] wlp3s0: associated
[    9.992143] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   10.062184] wlp3s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 58:ef:68:69:0f:be
```

---

### Post by chili555 on 2019-02-08
Boy, oh boy! My favorite kind of problem: everything looks just perfect except it doesn't work!

Let's try the usual Intel-related steps.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Reboot and let us know if there is any improvement.

---

### Post by TechnoJunky on 2019-02-09
Followed your suggestions, but no change.   One thing that I noticed is that when it acts up, it's sending nearly the exact amount of data as it receives.  The Network Monitor gadget shows incoming and outgoing traffic with separate colors.  When it's acting up, it shows both mirroring each other.

---

### Post by chili555 on 2019-02-09
Please try:

```
sudo -i
echo "options iwlwifi disable_11ac"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

Reboot and let us hear your report.

---

### Post by TechnoJunky on 2019-02-10
I made the change you mentioned, and also disabled IPV6, which I normally do but hadn't until now.  My VPN doesn't support IPV6 and when I go to [http://www.whatsmyip.org/](http://www.whatsmyip.org/), it'll show my real IPV6 address. It's been about 24 hours now with no incident.  Fingers are crossed that it will continue to not act up.

---

### Post by chili555 on 2019-02-10
> Fingers are crossed that it will continue to not act up.I regret that my command was faulty. I intended:

```
sudo -i
echo "options iwlwifi disable_11ac[COLOR="#FF0000"]=Y[/COLOR]"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Please amend your iwlwifi.conf file accordingly.

I apologize for my mis-step.

---

### Post by TechnoJunky on 2019-02-11
The laptop had another episode this morning.  I came here to update you but see you have an update for me :).  I've updated the iwlwifi.conf file with =Y, we'll see if that fixes things.  Thanks for all the help, BTW.

---

### Post by TechnoJunky on 2019-02-11
I may have a lead on the issue.  Up until now, I've killed the wifi connection to resolve the issue (disconnect or airplane mode).  It's occurred 4 times this morning.  Odd how it only occurred once all day yesterday.  Anyway, after the first instance, I decided to run top and see if anything popped up the next time, nothing has.  Second instance, I tried killing my VPN, but it didn't stop the activity.  Third time, I killed Firefox and the activity stopped right away.  I had deleted my profile previously but the activity still occurred, and I thought that sometimes it occurred even when the browser was closed, but can't swear to it.  I've been using Firefox Nightly for months so after the third instance, I thought maybe it was Nightly and then opened the official release instead, but the forth instance occurred with it open, so maybe it's just Firefox in general, not sure.  BTW, when I closed it, the activity stopped.  I have Chromium installed but try to stay away from anything Google.  For investigative sake, I'll just run Chromium for a day or 2 to see.

---

### Post by TechnoJunky on 2019-02-11
Since I posted the last comment, I've been thinking, if it turns out to be Firefox at fault, I'll reach out to them.  What's the first thing they'll ask me to do?  Disable all extensions.  It's probably an extension installed vs actually being Firefox's fault.  I'm going to disable all the extensions and see how that does.

---

### Post by TechnoJunky on 2019-02-18
As previously mentioned, I disabled all my addons, but that didn't help.  The issue continued to recur.  I switched to Chromium for a couple days and had no issues.  I realized that when I renamed my Firefox profile, that that was all that I renamed.  I later renamed my entire .mozilla folder and now it's been 3 days or more with no issues.  So the only thing I can figure is that a file in the .mozilla folder was corrupted when I copied it from the dying hard drive.

---

