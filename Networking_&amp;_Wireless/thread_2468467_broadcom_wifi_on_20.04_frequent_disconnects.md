---
title: "broadcom wifi on 20.04 frequent disconnects"
date: 2021-10-30
forum: Networking &amp; Wireless
---

### Post by tgross on 2021-10-30
I've got a Dell XPS15 with a Broadcom WiFi that's frequently disconnecting from my WiFi on the 5GHz channel and having trouble connecting on the 2.4GHz channel. The problem presents itself with a kernel warning (see below), followed by disconnecting from the 5GHz channel and then not being able to get a strong enough connect to re-auth. I get an authentication failure error at that point and it might take 10 minutes of retrying before the connection can be restored. I've also tried rebooting just in case there's a hardware fault that gets cleared that way, and it doesn't seem to make a difference.

I've got current firmware and drivers. Trying to debug at this point whether the hardware might be going bad, as the machine is 5+ years old.


```

$ lspci -nn -d 14e4:
06:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)

```

Logs for the kernel warning below (full "wireless-info.txt" bundle is attached). Fossal source for that function is [https://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/focal/tree/net/wireless/sme.c#n956](https://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/focal/tree/net/wireless/sme.c#n956) (as of right now), but honestly I don't have enough of a driver development background to follow what's going on there.

```

Oct 30 14:51:59 durandal kernel: ------------[ cut here ]------------
Oct 30 14:51:59 durandal kernel: WARNING: CPU: 3 PID: 1962 at net/wireless/sme.c:975 cfg80211_roamed+0x210/0x230 [cfg80211]
Oct 30 14:51:59 durandal kernel: Modules linked in: xt_conntrack xt_MASQUERADE nf_conntrack_netlink xfrm_user xfrm_algo xt_addrtype br_netfilter btrfs blake2b_generic xor raid6_pq ufs qnx4 hfsplus hf>
Oct 30 14:51:59 durandal kernel:  snd_seq_midi wl(POE) nfc mei_hdcp dell_smm_hwmon videobuf2_v4l2 kvm snd_seq_midi_event dell_wmi videobuf2_common ecc dell_smbios snd_rawmidi dcdbas input_leds snd_se>
Oct 30 14:51:59 durandal kernel:  xhci_pci xhci_pci_renesas wmi video
Oct 30 14:51:59 durandal kernel: CPU: 3 PID: 1962 Comm: wl_event_handle Tainted: P        W  OE     5.11.0-38-generic #42~20.04.1-Ubuntu
Oct 30 14:51:59 durandal kernel: Hardware name: Dell Inc. XPS 15 9530/XPS 15 9530, BIOS A08 01/08/2015
Oct 30 14:51:59 durandal kernel: RIP: 0010:cfg80211_roamed+0x210/0x230 [cfg80211]
Oct 30 14:51:59 durandal kernel: Code: 00 00 00 49 8d 4d 70 4c 89 f7 45 0f b6 85 90 00 00 00 6a 02 48 8b 36 e8 0e 3c fd ff 48 89 43 08 5a 48 85 c0 0f 85 36 fe ff ff <0f> 0b eb 85 0f 0b 48 8b 73 08 49>
Oct 30 14:51:59 durandal kernel: RSP: 0018:ffffa1d300d8fdc0 EFLAGS: 00010246
Oct 30 14:51:59 durandal kernel: RAX: 0000000000000000 RBX: ffffa1d300d8fe08 RCX: ffff91ca20a294f8
Oct 30 14:51:59 durandal kernel: RDX: 0000000000000002 RSI: 00000000fffffe01 RDI: ffffffffc0e9031f
Oct 30 14:51:59 durandal kernel: RBP: ffffa1d300d8fdf0 R08: ffff91ca0ec740c0 R09: 0000000000000003
Oct 30 14:51:59 durandal kernel: R10: ffff91ca0ec7501a R11: fffffffeff3b152f R12: 0000000000000cc0
Oct 30 14:51:59 durandal kernel: R13: ffff91ca04e33400 R14: ffff91ca0ec74300 R15: dead000000000100
Oct 30 14:51:59 durandal kernel: FS:  0000000000000000(0000) GS:ffff91cd1fac0000(0000) knlGS:0000000000000000
Oct 30 14:51:59 durandal kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 30 14:51:59 durandal kernel: CR2: 00007fca3415a030 CR3: 0000000154610005 CR4: 00000000001706e0
Oct 30 14:51:59 durandal kernel: Call Trace:
Oct 30 14:51:59 durandal kernel:  wl_bss_roaming_done.isra.0+0xd6/0x110 [wl]
Oct 30 14:51:59 durandal kernel:  ? wl_bss_roaming_done.isra.0+0xd6/0x110 [wl]
Oct 30 14:51:59 durandal kernel:  wl_notify_roaming_status+0x46/0x60 [wl]
Oct 30 14:51:59 durandal kernel:  ? down_interruptible+0x38/0x60
Oct 30 14:51:59 durandal kernel:  wl_event_handler+0x6c/0x150 [wl]
Oct 30 14:51:59 durandal kernel:  ? wl_notify_scan_status+0x250/0x250 [wl]
Oct 30 14:51:59 durandal kernel:  kthread+0x12b/0x150
Oct 30 14:51:59 durandal kernel:  ? set_kthread_struct+0x40/0x40
Oct 30 14:51:59 durandal kernel:  ret_from_fork+0x22/0x30
Oct 30 14:51:59 durandal kernel: ---[ end trace 88e5cd0f9e23a70d ]---
Oct 30 14:52:04 durandal kernel: ERROR @wl_cfg80211_get_station :
Oct 30 14:52:04 durandal kernel: Wrong Mac address, mac = 48:5d:36:81:48:68   profile =48:5d:36:81:48:6a
Oct 30 14:52:04 durandal kernel: ERROR @wl_cfg80211_get_station :
Oct 30 14:52:04 durandal kernel: Wrong Mac address, mac = 48:5d:36:81:48:68   profile =48:5d:36:81:48:6a



```



Some environment issues:


[LIST]
[*]The AP is on the 3rd floor of the house and disconnects happen most frequently on the 1st floor.
[*]We have a Chromebook that connects to the 2.4GHz channel there with no problem, and our phones connect on the 5GHz channel there no problem.
[*]This is a dense urban area so there's a _lot_ of other APs in the area and finding a totally clear channel is all but impossible.
[/LIST]

---

### Post by chili555 on 2021-10-30
Is it disconnecting to roam to the stronger 2.4 gHz segment of the router? If you have administrative priveleges for the router, you might try renaming the SSIDs to something like ThothNet2.4 and ThothNet5. Connect to ThothNet5 and the roaming will probably stop.

Note that part of the error in the log is:

> RIP: 0010:cfg80211_[COLOR="#FF0000"]roamed[/COLOR]+0x210/0x230 [cfg80211]



---

### Post by tgross on 2021-10-30
That sounds like a good hypothesis. Those last lines of the log snippet has two MAC addresses: the :6a address is the 2.4GHz and the :68 address is the 5GHz. I do have administrative access to the router and can change the channel IDs. I'll give that a go when I have a window of opportunity and report back soon. Thanks!

---

### Post by chili555 on 2021-10-30
I suggest that you also address these steps (none are specific to Intel devices) if not already set: [https://askubuntu.com/questions/1263315/dual-system-win10-can-connect-to-wireless-but-ubuntu-18-04-cannot-and-keep-aski/1263553#1263553](https://askubuntu.com/questions/1263315/dual-system-win10-can-connect-to-wireless-but-ubuntu-18-04-cannot-and-keep-aski/1263553#1263553)

We look forward to your report!

---

### Post by tgross on 2021-10-31
It looks like splitting the channels onto their own SSIDs did the job. I had some trouble connecting on 2.4GHz (see logs below) but the new SSID for 5GHz worked just fine. Unfortunately I haven't been able to reproduce the failure on 2.4GHz again, but the roaming has been solved at least, which seems to be good enough for the moment.

```

Oct 30 21:27:13 durandal wpa_supplicant[2583]: wlp6s0: Trying to associate with 48:5d:36:81:48:6a (SSID='ThothNet' freq=2462 MHz)
Oct 30 21:27:14 durandal wpa_supplicant[2583]: wlp6s0: CTRL-EVENT-ASSOC-REJECT bssid=00:00:00:00:00:00 status_code=16
Oct 30 21:27:14 durandal wpa_supplicant[2583]: wlp6s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="ThothNet" auth_failures=1 duration=10 reason=CONN_FAILED
Oct 30 21:27:14 durandal NetworkManager[2524]: <info>  [1635643634.0741] device (wlp6s0): supplicant interface state: scanning -> associating
Oct 30 21:27:14 durandal NetworkManager[2524]: <info>  [1635643634.0745] device (wlp6s0): supplicant interface state: associating -> disconnected
Oct 30 21:27:24 durandal NetworkManager[2524]: <info>  [1635643644.0650] device (wlp6s0): supplicant interface state: disconnected -> scanning
Oct 30 21:27:28 durandal wpa_supplicant[2583]: wlp6s0: CTRL-EVENT-SSID-REENABLED id=0 ssid="ThothNet"
Oct 30 21:27:28 durandal wpa_supplicant[2583]: wlp6s0: Trying to associate with 48:5d:36:81:48:6a (SSID='ThothNet' freq=2462 MHz)
Oct 30 21:27:28 durandal NetworkManager[2524]: <info>  [1635643648.0097] device (wlp6s0): supplicant interface state: scanning -> associating
Oct 30 21:27:28 durandal wpa_supplicant[2583]: wlp6s0: CTRL-EVENT-ASSOC-REJECT bssid=00:00:00:00:00:00 status_code=16
Oct 30 21:27:28 durandal wpa_supplicant[2583]: wlp6s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="ThothNet" auth_failures=2 duration=20 reason=CONN_FAILED
Oct 30 21:27:28 durandal NetworkManager[2524]: <info>  [1635643648.0947] device (wlp6s0): supplicant interface state: associating -> disconnected
Oct 30 21:27:35 durandal NetworkManager[2524]: <warn>  [1635643655.5772] device (wlp6s0): Activation: (wifi) association took too long
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5773] device (wlp6s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5780] sup-iface[0x5638355b3920,wlp6s0]: wps: type pbc start...
Oct 30 21:27:35 durandal NetworkManager[2524]: <warn>  [1635643655.5816] device (wlp6s0): Activation: (wifi) asking for new secrets
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5861] device (wlp6s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5872] device (wlp6s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5883] device (wlp6s0): Activation: (wifi) connection 'ThothNet' has security, and secrets exist.  No new secrets needed.
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5884] Config: added 'ssid' value 'ThothNet'
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5884] Config: added 'scan_ssid' value '1'
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5885] Config: added 'freq_list' value '2412 2417 2422 2427 2432 2437 2442 2447 2452 2457 2462 2467 2472 2484'
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5885] Config: added 'bgscan' value 'simple:30:-65:300'
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5886] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256'
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.5886] Config: added 'psk' value '<hidden>'
Oct 30 21:27:35 durandal NetworkManager[2524]: <info>  [1635643655.6168] device (wlp6s0): supplicant interface state: disconnected -> scanning

```


> I  suggest that you also address these steps (none are specific to Intel devices) if not already set: [https://askubuntu.com/questions/1263...263553#1263553](https://askubuntu.com/questions/1263...263553#1263553)

Aye. I've already got 20MHz width set for the 2.4GHz channel. The 5GHz channel has auto N/AC but the 2.4GHz channel doesn't, so I'll give that a go but if I can't reproduce the 2.4GHz failure it's hard to tell whether or not it worked. It doesn't look like I can set the regulatory domain; the AP/router is an embedded Linux device from my ISP and it's kind of a wasteland when it comes to tools available on the box. :(

I haven't set to a specific channel but I suspect that'd cause more problems than it'd solve. There are APs that appear and disappear with some frequency in the area and so finding a channel without a lot of APs on it is tricky (and we're packed close enough together that my next door neighbors APs often have the same dB as my own).

---

### Post by tgross on 2021-10-31
Unfortunately it looks like the problem is intermittent and came back even with that change. I'm observing that the signal strength is a bit on the low side for 5GHz and I'll get a disconnect. But at that point the 2.4GHz channel won't connect either even though it's showing a middling signal strength (-58dB). It took a dozen tries to get a connection and then it's dropping packets. Given that I only really see the problem at the extreme end of range within the house, this is smelling more like an issue of noisy radio environment vs power vs distance combined with maybe this antenna is on the lower-powered side compared to other devices in the house. I've been putting off getting a repeater because that just contributes to the radio noise issue in the neighborhood.

---

### Post by chili555 on 2021-11-01
I still think you will connect easier and stay connected with a fixed channel.

> I haven't set to a specific channel but I suspect that'd cause more problems than it'd solve. There are APs that appear and disappear with some frequency in the area and so finding a channel without a lot of APs on it is trickyIt's actually pretty easy. Run the terminal command:

```
nmcli device wifi list
```That will show a list of all the APs that your wireless device sees. Here is a redacted version of mine as an example:

```
IN-USE  BSSID              SSID   MODE   CHAN  RATE        SIGNAL  BARS  SECURITY  
       xx:86  GBR1   Infra  6     195 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2      
*       yy:85  GBR5   Infra  149   405 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2      
        zz:8A  nx2.4  Infra  11    195 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2 
        aa:EE Infra  11    130 Mbit/s  52      &#9602;&#9604;__  WPA2      
        bb:EF  MC5    Infra  153   405 Mbit/s  37      &#9602;&#9604;__  WPA2  
```Now compare the channels that your wireless card is capable of using with the command:

```
iwlist chan
```here's mine:

```
32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz

```Everyone near me is on channels 6, 11, 149 and 153. If I were setting a fixed channel with the least interference, I'd pick channel 1 or 48. This all depends on what the router can do.

Finally:
> It doesn't look like I can set the regulatory domain; the AP/router is an embedded Linux device from my ISP and it's kind of a wasteland when it comes to tools available on the box.The setting is in your Ubuntu computer, not the router.

---

