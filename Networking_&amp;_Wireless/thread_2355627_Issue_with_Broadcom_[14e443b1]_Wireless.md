---
title: "Issue with Broadcom [14e4:43b1] Wireless"
date: 2017-03-14
forum: Networking &amp; Wireless
---

### Post by ezsrac on 2017-03-14
Hi all, hopefully somebody can help with this. I'm running Ubuntu 16.04.2 LTS and I'm having WiFi issues. 

I've followed all of the broadcom specific instructions for drivers that are really helpfully linked in the forums but I'm still getting a dropping or poor performing WiFi connection.

Connection runs fine for a while (up to a couple hours) and then starts to degrade after a while. During this, the WiFi connection appears to be still active but there is no internet connectivity.

As I said, I've followed chili555's great guide here: [https://ubuntuforums.org/showthread.php?t=2214110]("https://ubuntuforums.org/showthread.php?t=2214110") but it hasn't made a difference.

Any help would be greatly appreciated!

Pastebin link: [http://paste.ubuntu.com/24178965/]("http://paste.ubuntu.com/24178965/")

---

### Post by chili555 on 2017-03-14
We see this error frequently and, so far, no solution.> ERROR @wl_dev_intvar_get : error (-1)I am hopeful that you are willing to help us with some experiments.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
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

Reboot and test. If you continue to have instability, please post back and include:```
dmesg | grep wl
```Are you using the 2.4 or the 5 gHz channels on your network? Is the instability the same with either? Have you tried lower channels on 5 gHz; 40 or 44 perhaps? Have you tried disabling AC speeds altogether?

---

### Post by ezsrac on 2017-03-14
Thanks so much for the quick response, unfortunately after reboot connection dropped almost immediately.

> **chili555 said:**
> 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```


Results:
```
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)
```


> **chili555 said:**
> 
Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.
Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

temp set to Ireland with: sudo iw reg set IE
Perm set using:REGDOMAIN=IE

> **chili555 said:**
> 
Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Done: [http://imgur.com/a/hZBg7]("http://imgur.com/a/hZBg7")

> **chili555 said:**
> 
Reboot and test. If you continue to have instability, please post back and include:```
dmesg | grep wl
```


```
[    4.045996] wl: module license 'MIXED/Proprietary' taints kernel.
[    4.047687] wl: module verification failed: signature and/or required key missing - tainting kernel
[    4.152349] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[    4.288526] wl 0000:04:00.0 wlp4s0: renamed from wlan0
[    5.132371] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
```

> **chili555 said:**
> 
Are you using the 2.4 or the 5 gHz channels on your network? Is the instability the same with either? Have you tried lower channels on 5 gHz; 40 or 44 perhaps? Have you tried disabling AC speeds altogether?


Router is locked to 2.4 gHz - channel is fixed to 11 and checked clean from other channel crossover.

---

### Post by chili555 on 2017-03-14
Please disable power saving in Network Manager:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo service network-manager restart
```

Let's look at the logs a bit deeper:```
dmesg | grep wl
cat /var/log/syslog | grep wl | tail -n20
```[http://paste.ubuntu.com](http://paste.ubuntu.com) please.

---

### Post by ezsrac on 2017-03-14
> **chili555 said:**
> Please disable power saving in Network Manager:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo service network-manager restart
```

Let's look at the logs a bit deeper:```
dmesg | grep wl
cat /var/log/syslog | grep wl | tail -n20
```[http://paste.ubuntu.com](http://paste.ubuntu.com) please.

My pleasure, thanks again!

[URL="http://paste.ubuntu.com/24179671/"]
http://paste.ubuntu.com/24179671/[/URL]

---

### Post by chili555 on 2017-03-14
> [ 1300.927607] ERROR @wl_notify_scan_status : wlp4s0 Scan_results error (-22)
[ 1743.677075] Modules linked in: rfcomm bnep binfmt_misc dell_wmi sparse_keymap wl(POE) snd_hda_codec_hdmi uvcvideo btusb videobuf2_vmalloc btrtl btbcm videobuf2_memops snd_usb_audio btintel videobuf2_v4l2 bluetooth videobuf2_core v4l2_common snd_hda_codec_realtek videodev snd_hda_codec_generic snd_usbmidi_lib media snd_hda_intel intel_rapl snd_hda_codec x86_pkg_temp_thermal intel_powerclamp kvm_intel snd_hda_core snd_hwdep kvm snd_pcm snd_seq_midi snd_seq_midi_event cfg80211 irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_rawmidi aesni_intel snd_seq rtsx_pci_ms memstick aes_x86_64 lrw gf128mul glue_helper ablk_helper joydev cryptd snd_seq_device input_leds serio_raw snd_timer mei_me lpc_ich snd mei soundcore shpchp ie31200_edac edac_core wmi soc_button_array dell_smo8800 dell_rbtn
[ 1743.677135] CPU: 3 PID: 662 Comm: wl_event_handle Tainted: P           OE   4.4.0-66-generic #87-Ubuntu
[ 1743.677211]  [<ffffffffc0930055>] wl_notify_roaming_status+0xc5/0x140 [wl]
[ 1743.677245]  [<ffffffffc092f6b0>] wl_event_handler+0x60/0x1d0 [wl]
[ 1743.677276]  [<ffffffffc092f650>] ? wl_notify_scan_status+0x320/0x320 [wl]Yikes!!!

Again, we see many reports of this scan results error and no firm solution. As a matter of fact, in Googling, I keep running into my own posts! Welcome to the Twilight Zone!

I'm grasping at straws a bit here, but please try changing the router to 802.11B and G only; not B, G and N. Reboot the router and check again:```
cat /var/log/syslog | grep wl | tail -n20
```We're looking for entries with later timestamps than the previous you pasted.

I know, I know; you didn't buy an 802.11B,G,N and AC card to disable down to G but we are trying to get it to work reliably as opposed to not working at all.

Does your router have a 5 gHz channel? Is it disabled? Or at least is the SSID different? Something like chili2.4 and chili5, or some such?

---

### Post by ezsrac on 2017-03-15
Sorry for the delay in getting back to you - r/l and all that.

Ok, I set the router to G only and still the same issues. Here is the log:

```
~$ cat /var/log/syslog | grep wl | tail -n20
Mar 15 19:59:23 SH002 NetworkManager[1146]: <info>  [1489607963.0356] device (wlp10s0): state change: config -> ip-config (reason 'none') [50 70 0]
Mar 15 19:59:23 SH002 NetworkManager[1146]: <info>  [1489607963.0360] dhcp4 (wlp10s0): activation: beginning transaction (timeout in 45 seconds)
Mar 15 19:59:23 SH002 NetworkManager[1146]: <info>  [1489607963.0369] dhcp4 (wlp10s0): dhclient started with pid 5334
Mar 15 19:59:23 SH002 dhclient[5334]: DHCPREQUEST of 192.168.1.3 on wlp10s0 to 255.255.255.255 port 67 (xid=0x51394e70)
Mar 15 19:59:23 SH002 avahi-daemon[1105]: Joining mDNS multicast group on interface wlp10s0.IPv4 with address 192.168.1.3.
Mar 15 19:59:23 SH002 avahi-daemon[1105]: New relevant interface wlp10s0.IPv4 for mDNS.
Mar 15 19:59:23 SH002 NetworkManager[1146]: <info>  [1489607963.2794] dhcp4 (wlp10s0): state changed unknown -> bound
Mar 15 19:59:23 SH002 avahi-daemon[1105]: Registering new address record for 192.168.1.3 on wlp10s0.IPv4.
Mar 15 19:59:23 SH002 NetworkManager[1146]: <info>  [1489607963.2801] device (wlp10s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Mar 15 19:59:23 SH002 NetworkManager[1146]: <info>  [1489607963.2806] device (wlp10s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Mar 15 19:59:23 SH002 NetworkManager[1146]: <info>  [1489607963.2810] device (wlp10s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Mar 15 19:59:23 SH002 NetworkManager[1146]: <info>  [1489607963.2839] policy: set 'eircom19770694' (wlp10s0) as default for IPv4 routing and DNS
Mar 15 19:59:23 SH002 dnsmasq[2345]: using nameserver 8.8.8.8#53(via wlp10s0)
Mar 15 19:59:23 SH002 dnsmasq[2345]: using nameserver 8.8.4.4#53(via wlp10s0)
Mar 15 19:59:23 SH002 NetworkManager[1146]: <info>  [1489607963.2883] device (wlp10s0): Activation: successful, device activated.
Mar 15 19:59:23 SH002 nm-dispatcher: req:1 'up' [wlp10s0]: new request (1 scripts)
Mar 15 19:59:23 SH002 nm-dispatcher: req:1 'up' [wlp10s0]: start running ordered scripts...
Mar 15 19:59:24 SH002 avahi-daemon[1105]: Joining mDNS multicast group on interface wlp10s0.IPv6 with address fe80::260a:64ff:fe96:1171.
Mar 15 19:59:24 SH002 avahi-daemon[1105]: New relevant interface wlp10s0.IPv6 for mDNS.
Mar 15 19:59:24 SH002 avahi-daemon[1105]: Registering new address record for fe80::260a:64ff:fe96:1171 on wlp10s0.*.
```

Unfortunately my router doesn't have a different frequency or second SSID. It's one of those locked down ones from an ISP but it does work flawlessly everywhere else. I'm very limited on when I can mess with the setting and reboot it as the rest of the family has it in constant use!

---

