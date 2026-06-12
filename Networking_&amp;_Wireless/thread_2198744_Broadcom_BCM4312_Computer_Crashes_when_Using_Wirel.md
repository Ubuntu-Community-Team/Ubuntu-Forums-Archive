---
title: "Broadcom BCM4312: Computer Crashes when Using Wireless."
date: 2014-01-10
forum: Networking &amp; Wireless
---

### Post by rudolf.almeida on 2014-01-10
I am a ubuntu 12.04 user. I installed the wireless driver on my PC via the command line "$ sudo apt-get --reinstall install bcmwl-kernel-source".
After installing this driver however my PC has started hanging up whenever I try to use Wireless. When I disconnect from my Wifi, suddenly a black screen appears 
with some text  which goes after some time by pressing Enter and if in that same session I try to connect to Wifi again the Screen again goes Black with some text that says "Panic occured!" and "Switching to text-mode" and it never goes or responds until I remove my laptop Battery.
Same happens when I use Bluetooth to connect to my phone and access the Internet. However if it is bluetooth it only happens if I use the connection to connect my PC to the Internet but does not happen if I use it to Browse my phone. My Wireless card is a Broadcom BCM4312. Please Help.

---

### Post by chili555 on 2014-01-10
I suggest you try:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-lpphy-installer
```Reboot and tell us how it's working.

---

### Post by Panawe on 2014-01-10
Take a look at the thread "Wired connection with 12.04 and Dell 1545". Don't be put off by the "wired" - I installed 12.05 on a Dell laptop which has the Broadcomm 4312 card and evetually got it working by loading bcmwl-kernel-source from Synaptic Package manage.

Don't know why it works but it's rock solid!

Good luck.

---

### Post by rudolf.almeida on 2014-01-12
I tried your suggestion  @chili555 but it still isnt working. Still hangs up and doesnt connect.

---

### Post by chili555 on 2014-01-12
Are there any interesting clues?```
cat /var/log/syslog | grep -e wlan -e b43 | tail -n25
```

---

### Post by rudolf.almeida on 2014-01-13
The Wireless problem seems to be solved but the computer still hangs when I disconnect Bluetooth. 
Should I hide something before I post the output of the above command. Like IP address of anything?

---

### Post by chili555 on 2014-01-13
> **rudolf.almeida said:**
> The Wireless problem seems to be solved but the computer still hangs when I disconnect Bluetooth. 
Should I hide something before I post the output of the above command. Like IP address of anything?If you have a public IP address; i.e. you are connected directly to your ISP, then yes,please obscure it. If you are connected to a router and have a private IP address like 192.168.x.x or 10.x.x.x, then it is not necessary. I believe passwords are already obscured and you might also obscure MAC addresses; I suggest changing this: 88:D7:19:41:54:99 to this xx:D7:19:41:54:xx for example.

---

### Post by rudolf.almeida on 2014-01-13
After quite a lot of tries to get the log after the computer goes blank the first time, I managed to run your command after the screen initially goes blank and returns. This is the output of it.
Jan 13 11:17:22 rudolph NetworkManager[865]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jan 13 11:17:22 rudolph NetworkManager[865]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 13 11:17:23 rudolph NetworkManager[865]: <info> (wlan0): using nl80211 for WiFi device control
Jan 13 11:17:23 rudolph NetworkManager[865]: <warn> (wlan0): driver supports Access Point (AP) mode
Jan 13 11:17:23 rudolph NetworkManager[865]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan 13 11:17:23 rudolph NetworkManager[865]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 13 11:17:23 rudolph NetworkManager[865]: <info> (wlan0): now managed
Jan 13 11:17:23 rudolph NetworkManager[865]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 13 11:17:23 rudolph NetworkManager[865]: <info> (wlan0): bringing up device.
Jan 13 11:17:23 rudolph NetworkManager[865]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 13 11:17:23 rudolph kernel: [   20.310238] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 13 11:19:45 rudolph kernel: [   13.052872] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
Jan 13 11:19:45 rudolph kernel: [   13.096243] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
Jan 13 11:19:51 rudolph NetworkManager[872]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ssb0:0/net/wlan0, iface: wlan0)
Jan 13 11:19:51 rudolph NetworkManager[872]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 13 11:19:51 rudolph NetworkManager[872]: <info> (wlan0): using nl80211 for WiFi device control
Jan 13 11:19:51 rudolph NetworkManager[872]: <warn> (wlan0): driver supports Access Point (AP) mode
Jan 13 11:19:51 rudolph NetworkManager[872]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan 13 11:19:51 rudolph NetworkManager[872]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 13 11:19:51 rudolph NetworkManager[872]: <info> (wlan0): now managed
Jan 13 11:19:51 rudolph NetworkManager[872]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 13 11:19:51 rudolph NetworkManager[872]: <info> (wlan0): bringing up device.
Jan 13 11:19:51 rudolph NetworkManager[872]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 13 11:19:51 rudolph kernel: [   20.731396] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 13 11:36:19 rudolph kernel: [ 1008.648631] Modules linked in: ppp_deflate(F) zlib_deflate(F) bsd_comp(F) ppp_async(F) crc_ccitt(F) bnep(F) rfcomm(F) parport_pc(F) ppdev(F) arc4(F) joydev(F) b43(F) snd_hda_codec_hdmi(F) snd_hda_codec_idt(F) snd_hda_intel(F) uvcvideo(F) snd_hda_codec(F) binfmt_misc(F) videobuf2_core(F) videodev(F) mac80211(F) videobuf2_vmalloc(F) videobuf2_memops(F) coretemp(F) snd_hwdep(F) snd_pcm(F) cfg80211(F) snd_seq_midi(F) snd_rawmidi(F) btusb(F) snd_seq_midi_event(F) i915(F) snd_seq(F) bluetooth(F) psmouse(F) microcode(F) hp_wmi(F) bcma(F) snd_timer(F) serio_raw(F) sparse_keymap(F) snd_seq_device(F) lpc_ich(F) drm_kms_helper(F) drm(F) snd(F) wmi(F) soundcore(F) mac_hid(F) snd_page_alloc(F) i2c_algo_bit(F) video(F) lp(F) parport(F) ssb(F) ahci(F) libahci(F) r8169(F)

---

