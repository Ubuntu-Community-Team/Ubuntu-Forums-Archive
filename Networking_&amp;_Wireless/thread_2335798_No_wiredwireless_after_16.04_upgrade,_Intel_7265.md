---
title: "No wired/wireless after 16.04 upgrade, Intel 7265"
date: 2016-09-01
forum: Networking &amp; Wireless
---

### Post by phloem on 2016-09-01
Upgrading to Ubuntu 16.04.1 LTS from 14.04.3 LTS, my laptop can detect wired/wifi sources but cannot connect. It tries to connect and fails after a few seconds. Tried rebooting, restarting network-manager to no avail. Copied firmware from [Intel website]("http://www.intel.com/content/www/us/en/support/network-and-i-o/wireless-networking/000005511.html") to /lib/firmware, also to no avail. Windows 10 dual-booted on the same computer works fine. I made sure to shut down Windows completely before starting Ubuntu.

I do not have a working wired connection from laptop in question, but can download packages from a different Windows machine and transfer via external storage.


wireless-info script output at [http://pastebin.ubuntu.com/23119973/](http://pastebin.ubuntu.com/23119973/)

Thanks in advance for help!

---

### Post by chili555 on 2016-09-01
We see a few issues in your paste. First:> ##### iw reg get ########################

Region: America/New_York (based on set time zone)

[COLOR="#FF0000"]country 00: DFS-UNSET[/COLOR]
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)
I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS

```
Of course, substitute your country code if not Iceland. Set it permanently:

    ```
gksudo gedit /etc/default/crda
```

Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

   ```
 REGDOMAIN=IS

```
Proofread carefully, save and close the text editor.

Next, we see:> ##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_enThis is conspicuous because of what it doesn't show. Do you have a file iwlwifi.conf?```
ls /etc/modprobe.d
```If not, you need it. Please open a terminal and do:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Add the following:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
```Spelling, spacing, etc. are very important. Please proofread carefully twice. Save and close the text editor. Reboot the computer.

Next, I am suspicious about this:>  Copied firmware from Intel website to /lib/firmware, also to no avail. Let's see what you have:```
ls -al /lib/firmware | grep 7265
```And, let's see what firmware loaded:```
dmesg | grep iwl
```

---

### Post by phloem on 2016-09-01
OK, wrote the regulatory domain and iwlwifi.conf. Here's the firmware info:

```

songela@carbons:~$ ls -al /lib/firmware | grep 7265
-rw-r--r--  1 root    root     736844 Apr 25 08:55 iwlwifi-7265-10.ucode
-rw-r--r--  1 root    root     880604 Apr 25 08:55 iwlwifi-7265-12.ucode
-rw-r--r--  1 root    root     885224 Apr 25 08:55 iwlwifi-7265-13.ucode
-rw-rw-r--  1 songela songela 1180224 Jul  1  2015 iwlwifi-7265-14.ucode
-rw-r--r--  1 root    root    1180356 Jul 12 15:33 iwlwifi-7265-16.ucode
-rw-r--r--  1 root    root     690452 Apr 25 08:55 iwlwifi-7265-8.ucode
-rw-r--r--  1 root    root     697828 Apr 25 08:55 iwlwifi-7265-9.ucode
lrwxrwxrwx  1 root    root         21 Jul 12 15:33 iwlwifi-7265D-10.ucode -> iwlwifi-7265-10.ucode
-rw-r--r--  1 root    root    1002800 Apr 25 08:55 iwlwifi-7265D-12.ucode
-rw-r--r--  1 root    root    1008692 Apr 25 08:55 iwlwifi-7265D-13.ucode
-rw-rw-r--  1 songela songela 1384256 Jul  1  2015 iwlwifi-7265D-14.ucode
-rw-r--r--  1 root    root    1384500 Jul 12 15:33 iwlwifi-7265D-16.ucode
drwxr-xr-x  2 songela songela    4096 Aug 27 12:01 iwlwifi-7265-ucode-25.30.14.0
-rw-r--r--  1 songela songela    2041 Dec 29  2013 LICENSE.iwlwifi-7265-ucode
-rw-r--r--  1 songela songela    4899 Jul  1  2015 README.iwlwifi-7265-ucode
songela@carbons:~$ dmesg | grep iwl
[    4.898407] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[    4.898651] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[    4.898942] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-7265D-17.ucode failed with error -2
[    4.903884] iwlwifi 0000:04:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    5.152294] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    5.152634] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.153090] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.221676] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    5.693083] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.693642] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.754862] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.755465] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled

```

So it looks like firmware threw errors when it tried to load. Am I reading that correctly?

---

### Post by ajgreeny on 2016-09-01
*Thread moved to **Ubuntu Development Version**.* which is more appropriate for the problem.

---

### Post by phloem on 2016-09-01
Sorry, my mistake - this is indeed 16.04.1 LTS, not 16.10 development version. Can admin please move back to Networking & Wireless - and, if possible, update thread topic to read 16.04? Thanks.

---

### Post by chili555 on 2016-09-01
> So it looks like firmware threw errors when it tried to load. Am I reading that correctly?Yes, but not really. The driver attempts to load -19, can't find it; tries to load -18, can't find it, etc. until it finds -16:> iwlwifi 0000:04:00.0: loaded firmware version [COLOR="#FF0000"]16[/COLOR].242414.0 op_mode iwlmvmSo it finds workable firmware.> drwxr-xr-x  2 songela songela    4096 Aug 27 12:01 iwlwifi-7265-ucode-25.30.14.0I assume this is a directory from which you transferred this:> -rw-rw-r--  1 songela songela 1180224 Jul  1  2015 iwlwifi-7265-14.ucode
-rw-r--r--  1 songela songela    2041 Dec 29  2013 LICENSE.iwlwifi-7265-ucode
-rw-r--r--  1 songela songela    4899 Jul  1  2015 README.iwlwifi-7265-ucodeOrdinarily, we'd want the ownership to be corrected to root; however, this is the -14 7265 firmware and the driver already finds the -16 7265[COLOR="#FF0000"]D[/COLOR] and uses it. We shall not waste any steps that haven't any effect.

Frankly, I don't see anything wrong and therefore fixable here. Let's dig deeper. With the ethernet detached, click on your network and try to connect. Then show us:```
cat /var/log/syslog | grep wlan0 | tail -n 20
```wlan0, eh? Interesting....

---

### Post by phloem on 2016-09-01
```

songela@carbons:~$ cat /var/log/syslog | grep wlan0 | tail -n 20
Aug 31 22:51:29 carbons NetworkManager[5948]: <info>  [1472698289.1278] device (wlan0): supplicant interface state: ready -> inactive
Aug 31 22:52:11 carbons NetworkManager[2402]: <info>  [1472698331.6812] devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/wlan0, iface: wlan0)
Aug 31 22:52:11 carbons NetworkManager[2402]: <info>  [1472698331.6813] device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 31 22:52:11 carbons NetworkManager[2402]: <info>  [1472698331.8152] (wlan0): using nl80211 for WiFi device control
Aug 31 22:52:11 carbons NetworkManager[2402]: <info>  [1472698331.8170] device (wlan0): driver supports Access Point (AP) mode
Aug 31 22:52:11 carbons NetworkManager[2402]: <info>  [1472698331.8181] manager: (wlan0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/0)
Aug 31 22:52:11 carbons NetworkManager[2402]: <info>  [1472698331.8192] device (wlan0): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Aug 31 22:52:11 carbons kernel: [    4.285892] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 31 22:52:11 carbons kernel: [    4.381237] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 31 22:52:11 carbons NetworkManager[2402]: <info>  [1472698331.9608] device (wlan0): supplicant interface state: init -> starting
Aug 31 22:52:11 carbons wpa_supplicant[2584]: Could not read interface p2p-dev-wlan0 flags: No such device
Aug 31 22:52:12 carbons NetworkManager[2402]: <info>  [1472698332.0060] device (wlan0): supplicant interface state: starting -> ready
Aug 31 22:52:12 carbons NetworkManager[2402]: <info>  [1472698332.0060] device (wlan0): state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Aug 31 22:52:12 carbons kernel: [    4.472660] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 31 22:52:15 carbons NetworkManager[2402]: <info>  [1472698335.2992] device (wlan0): supplicant interface state: ready -> inactive
Aug 31 22:52:39 carbons wpa_supplicant[2584]: wlan0: Failed to initiate sched scan
Aug 31 22:53:12 carbons wpa_supplicant[2584]: wlan0: Failed to initiate sched scan
Aug 31 22:53:55 carbons wpa_supplicant[2584]: wlan0: Failed to initiate sched scan
Aug 31 22:54:50 carbons wpa_supplicant[2584]: wlan0: Failed to initiate sched scan
Binary file (standard input) matches

```

What's interesting about wlan0?

---

### Post by slickymaster on 2016-09-01
> **phloem said:**
> Sorry, my mistake - this is indeed 16.04.1 LTS, not 16.10 development version. Can admin please move back to Networking & Wireless - and, if possible, update thread topic to read 16.04? Thanks.

Moved back to the **Networking & Wireless** sub-forum and thread title edited.

---

### Post by Keith_Helms on 2016-09-01
> **phloem said:**
> 
What's interesting about wlan0?

What's interesting is that the latest releases of Ubuntu don't use that name any more.  You would expect to see something like wlp3s0 instead.  It looks to me like the upgrade didn't update everything it needed to, so some pieces are still using wlan0 and other's are not.

For example these messages appear to be saying that wlan0 is not recognized everywhere:
```
Aug 31 22:52:11 carbons NetworkManager[2402]: <info>  [1472698331.6813] device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 31 22:52:11 carbons wpa_supplicant[2584]: Could not read interface p2p-dev-wlan0 flags: No such device
```

I suspect you need to reconfigure something to get everything using the new correct name for that device, but I don't know what the command(s) are.  Hopefully one of the networking gurus will chime in and say "oh, you just need to do this -".

---

### Post by chili555 on 2016-09-01
> What's interesting is that the latest releases of Ubuntu don't use that name any more. You would expect to see something like wlp3s0 instead. Exactly!

Let's see if we can fix it. We see this in your paste:> [/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15a2 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x095b (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"It says that the device at a certain MAC address (redacted in the wireless_script for security) using the driver iwlwifi shall be known as wlan0. This is not the case in the usual 16.04 installation. In mine, the file doesn't exist. Let's set the file aside, reboot and see what happens:```
cd /etc/udev/rules.d/
sudo mv 70-persistent-net.rules  /home/songela/
```That moves the file into your home directory so that it is ineffective but so that it can be recovered if needed. 

Reboot with your fingers crossed. If wired and wireless are not working correctly, please give us a new paste as above.

---

### Post by phloem on 2016-09-01
Removing the file didn't work. Here's a new paste:
[http://pastebin.ubuntu.com/23122426/](http://pastebin.ubuntu.com/23122426/)

I noticed that
```
[COLOR=#FF0000]*country 00: DFS-UNSET*[/COLOR]
```

is still present. I had set my regulatory domain using:
```
sudo vim /etc/default/crda
```

using sudo since I did not have gksudo installed, setting the last line to:
```
REGDOMAIN=US
```

but am unsure why that didn't set the regulatory domain explicitly on reboot.


Also, dmesg shows:
```
songela@carbons:~$ dmesg | grep iwl[    4.606287] iwlwifi 0000:04:00.0: loaded firmware version 19.324151.0 op_mode iwlmvm
[    4.667281] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    4.667629] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    4.668083] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    4.754638] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.829185] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
[    5.528898] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.529348] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.591225] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[    5.591677] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   85.039471] iwlwifi 0000:04:00.0 wlp4s0: disabling HT as WMM/QoS is not supported by the AP
[   85.039474] iwlwifi 0000:04:00.0 wlp4s0: disabling VHT as WMM/QoS is not supported by the AP

```

Thanks so much!

---

### Post by chili555 on 2016-09-01
> am unsure why that didn't set the regulatory domain explicitly on reboot.Is the package wireless-regdb installed?```
sudo dpkg -s wireless-regdb
```Your readings looks awesome, actually. We know the wireless scans and sees networks. What happens when you click on yours and try to connect?

It appears that you have been connected at least once:> [[/etc/NetworkManager/system-connections/lockon7745 1]] (600 root)
[connection] id=[COLOR="#FF0000"]lockon7745[/COLOR] 1 | type=wifi | permissions=user:guest-glixyo:;
[wifi] mac-address=<MAC 'wlp4s0' [IF2]> | mac-address-blacklist= | ssid=lockon7745
[ipv4] method=auto
[ipv6] method=auto

---

### Post by phloem on 2016-09-01
> Is the package wireless-regdb installed?
Yes, it is. Just realized that I can't set the domain temporarily, either. After trying to set it:
```
$ sudo iw reg set US
$ sudo iw reg get
country 00: DFS-UNSET
(and some more stuff)
```

When I try to connect to my wireless, it acts like it's connecting for ~20 seconds, then says disconnected. I deleted the connection from my list, rebooted, and tried again; the first time, it kept asking for password and got stuck after I entered the PW. Then I restarted the network-manager:

```
sudo service networking-manager restart
```

Then it tries to connect for ~20 seconds and disconnects, twice before it gives up.

When I plug in Ethernet, it also tries to connect for some tens of seconds before saying disconnected.

---

### Post by phloem on 2016-09-01
Tried connecting with a guest account. First thing I see when I log in is an error in a graphical pop-up.
```
upstart-udev-bridge crashed with SIGABRT in __libc_start_main()
```

Since I had my Ethernet cable already plugged in, I tried to connect it with the same results as my main user: connecting for ~20 seconds, then disconnects.

When I try to connect to wireless, a graphical error pops up saying:

```
Connection failure
Failed to add/activate connection
(2) Active connection removed before it was initialized
```

---

### Post by chili555 on 2016-09-02
> **phloem said:**
> Tried connecting with a guest account. First thing I see when I log in is an error in a graphical pop-up.
```
upstart-udev-bridge crashed with SIGABRT in __libc_start_main()
```

Since I had my Ethernet cable already plugged in, I tried to connect it with the same results as my main user: connecting for ~20 seconds, then disconnects.

When I try to connect to wireless, a graphical error pops up saying:

```
Connection failure
Failed to add/activate connection
(2) Active connection removed before it was initialized
```I suspect strongly that these are significant to your inability to connect. I do not, however, have any ideas as to a fix. I suggest that you post a question here: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331) and here: [http://askubuntu.com/questions](http://askubuntu.com/questions)

I regret that I haven't any better suggestion.

---

