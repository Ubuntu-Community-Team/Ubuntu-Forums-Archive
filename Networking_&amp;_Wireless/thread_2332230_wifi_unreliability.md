---
title: "wifi unreliability"
date: 2016-07-29
forum: Networking &amp; Wireless
---

### Post by chopra on 2016-07-29
Hi all,
I've been having inermittent wifi problems for a while now at work with my laptop, and others have not been having the same problems, even those who are in the same vicinity as I am.  Several times throughout the day, the internet freezes, and I have to disconnect and reconnect again, as well as kill any ssh sessions that got frozen.  This has begun to happen at my wifi at home as well, though it's worse at work.  I don't know how much of it is my machine, and how much is the wifi systems.
I'm using a Toshiba Satellite laptop, Ubuntu 14.04.4 LTS.

I followed the instructions on this board, doing sudo apt-get update and sudo apt-get dist-upgrade, but the problem does not seem to have been resolved.

Here is some output at the tail end of the apt-get update command:

```
: There is no public key available for the following key IDs:
*************
W: There is no public key available for the following key IDs:
*************
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  U
nable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong 
sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used
 instead.
```

It should be mentioned, that I had initially downloaded Google chrome, before realizing that i couls use chromium, so I first installed chromium, meaning they coexisted, then uninstalled both, and reinstalled chrome (I usually use firefox at home and work, however)

Here are also some error messages from my /var/log/syslog file:

```
Jul 29 11:43:24 Satellite-E45-B kernel: [    0.000000] ACPI Error: Gpe0Block - 32-bit FADT register is too long (32 bytes, 256 bits) to convert to GAS struct - 255 bits max, truncating (20131115/tbfadt-202)
Jul 29 11:43:24 Satellite-E45-B kernel: [   12.379373] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
Jul 29 11:43:36 Satellite-E45-B NetworkManager[786]: <error> [1469810616.123400] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq
': no such name
Jul 29 11:43:24 Satellite-E45-B bluetoothd[771]: Failed to init deviceinfo plugin
Jul 29 11:43:24 Satellite-E45-B bluetoothd[771]: Failed to init proximity plugin
Jul 29 11:43:24 Satellite-E45-B bluetoothd[771]: Failed to init time plugin
Jul 29 11:43:24 Satellite-E45-B bluetoothd[771]: Failed to init alert plugin
Jul 29 11:43:24 Satellite-E45-B bluetoothd[771]: Failed to init thermometer plugin
Jul 29 11:43:24 Satellite-E45-B bluetoothd[771]: Failed to init gatt_example plugin
Jul 29 11:43:25 Satellite-E45-B bluetoothd[771]: hci0: Set Powered (0x0005) failed: <unknown status> (0x12)
Jul 29 11:43:26 Satellite-E45-B NetworkManager[786]: <warn> failed to allocate link cache: (-12) Object not found
Jul 29 11:43:29 Satellite-E45-B wpa_supplicant[866]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 29 11:43:36 Satellite-E45-B NetworkManager[786]: <warn> DNS: plugin dnsmasq update failed
Jul 29 11:43:49 Satellite-E45-B NetworkManager[786]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul 29 11:43:52 Satellite-E45-B wpa_supplicant[866]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 29 11:44:35 Satellite-E45-B wpa_supplicant[866]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 29 11:45:38 Satellite-E45-B wpa_supplicant[866]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 29 11:47:01 Satellite-E45-B wpa_supplicant[866]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 29 11:50:44 Satellite-E45-B wpa_supplicant[866]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 29 11:52:44 Satellite-E45-B wpa_supplicant[866]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 29 11:54:44 Satellite-E45-B wpa_supplicant[866]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 29 11:56:44 Satellite-E45-B wpa_supplicant[866]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Jul 29 11:58:44 Satellite-E45-B wpa_supplicant[866]: nl80211: send_and_recv->nl_recvmsgs failed: -33

```

Finally, i did run the wireless-info script, which I've attached the output of, although after performing the wget command, I got this at the end of the output:
Last-modified header missing -- time-stamps turned off.

Maybe nothing, not sure.

Thanks, Chopra

[ATTACH]270426[/ATTACH]

---

### Post by praseodym on 2016-07-31
Wow:

```
Channel occupancy:

      8   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      5   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.22 GHz (Channel 44)
      6   APs on   Frequency:5.24 GHz (Channel 48)
      3   APs on   Frequency:5.26 GHz (Channel 52)
      3   APs on   Frequency:5.2 GHz (Channel 40)
      3   APs on   Frequency:5.32 GHz (Channel 64)
      5   APs on   Frequency:5.52 GHz (Channel 104)
      4   APs on   Frequency:5.54 GHz (Channel 108)
      5   APs on   Frequency:5.56 GHz (Channel 112)
      13   APs on   Frequency:5.5 GHz (Channel 100)
      6   APs on   Frequency:5.66 GHz (Channel 132)
      5   APs on   Frequency:5.68 GHz (Channel 136)
      8   APs on   Frequency:5.765 GHz (Channel 153)
      5   APs on   Frequency:5.785 GHz (Channel 157)
      1   APs on   Frequency:5.805 GHz (Channel 161)
```
Which network(s) do you want to connect to? Obviously, too much traffic around. Lets try disabling the queue of the wireless driver:

```
echo "options iwlwifi wd_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi-wd.conf
```
Reboot.

---

### Post by chopra on 2016-08-09
Hi thaks for the reply.  Oddly, I didn't see it until now, although it's dated shortly after I posted. I've done as you said. So far things seem to be okay in terms of wifi. The only netwoks that I use are the fgz, guest, and my home ATT network.

---

