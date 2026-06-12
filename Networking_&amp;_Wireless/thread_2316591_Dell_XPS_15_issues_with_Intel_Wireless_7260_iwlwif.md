---
title: "Dell XPS 15 issues with Intel Wireless 7260 iwlwifi"
date: 2016-03-09
forum: Networking &amp; Wireless
---

### Post by M1GEO on 2016-03-09
Hello All.

I'm having some trouble with my Intel Wireless 7260 (rev 6b) wireless adapter inside my 2015 Dell XPS 15 laptop.  The machine is single boot Xubuntu, and I use the machine daily. I am just finishing my Ph.D (ironically, in wireless sensor networks) and so find myself working in libraries with Wi-Fi.

Although the Wi-Fi in the laptop works, it fails frequently. I have read mention that the driver is crashing, but I haven't yet been able to confirm this. As I write now, the connection has been stable for around 10 minutes; sometimes, however, it falls over within a minute of connecting. I will check dmesg next time to see what happens. I find that forcing a re-scan of wireless (sudo iwlist wlan0 scan) usually fixes the problem, and it reconnects. Other times, it requires me to use the nm-applet to disable and enable Wi-Fi before it will reconnect.  The issue seems worse after the machine has been suspended/hibernating. The network seems more reliable following a proper boot.

As I am a bit out of my depth with this, and most of the related posts seem to be from 2013, I figured I'd ask for some advice, rather than waste my life faffing around!  Standard Xubuntu kernel, machine up to date, no messing/witchcraft or terminal wizardry, latest BIOS, etc.

For my Kernel (3.19+), [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi#Firmware](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi#Firmware) seems to suggest that "iwlwifi-7260-ucode-25.17.12.0.tgz" is the latest firmware, which is what iwlwifi appears to load?

lspci:
```

george@ada:~$ lspci | grep -i wireless
06:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)

```


iwlwifi firmware
```

george@ada:~$ dmesg | grep iwl | grep firmware
[    4.727550] iwlwifi 0000:06:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm

```

lsmod
```

george@ada:~$ lsmod | grep iw
iwlmvm                278528  0 
mac80211              724992  1 iwlmvm
iwlwifi               196608  1 iwlmvm
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm

```

uname -a
```

Linux ada 3.19.0-51-generic #58-Ubuntu SMP Fri Feb 26 21:22:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

Any help greatly appreciated!

George :)

---

### Post by Hadaka on 2016-03-09
Hi, please post a wireless info diagnostic to helps us 
determine what your wireless card is doing. please go here
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
This builds a file in your home directory - wireless-info.txt
please post that back here.
thanks

---

### Post by chili555 on 2016-03-09
As it happens, I have and use a 7260 myself. 

I suggest the following steps and I suggest that you try each in succession, stopping if the first fixes your issue.

I notice this:> iwlwifi 0000:06:00.0: loaded firmware version 25.17.[COLOR="#FF0000"]12[/COLOR].0 op_mode iwlmvmOn my machine, I see:> iwlwifi 0000:03:00.0: loaded firmware version [COLOR="#FF0000"]17[/COLOR].265642.0 op_mode iwlmvm
So, the firmware my driver loads is five generations newer! Your driver may load a few generations newer if it is available and it might solve your issue. Let's get the latest firmware and see if it helps. From a terminal:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/OpenELEC/iwlwifi-firmware.git
cd iwlwifi-firmware/firmware
sudo cp iwlwifi-7260*  /lib/firmware
```Reboot and see which firmware loads.```
dmesg | grep iwl
```If it is, as I suspect, later than -12, is your issue solved?

If it is not solved, or only partly solved, let's try a driver parameter:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot. Better?

If not, let's install a later driver version.```
sudo apt-get install linux-headers-generic build-essential
```If either or both of these is already installed, that's fine, just install the missing one, if any.```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz
tar tar zxvf backports-4.4.2-1.tar.gz
cd backports-4.4.2-1
make defconfig-iwlwifi
make
sudo make install
```Reboot. Any improvement.

Please be certain to post back your experience as I will probably have one or more additional steps.

---

### Post by M1GEO on 2016-03-09
Thanks, Hadaka.

Apparently the text file was too big so it got gzipped (and is attached: [ATTACH]267717[/ATTACH]). The paste can also be found here: [http://paste.ubuntu.com/15334854/](http://paste.ubuntu.com/15334854/)

The machine is currently performing a dist-upgrade from 15.04 to 15.10, as suggested.

Once the update finishes, I will try and update the driver, as suggested by chili555 - would have done that, but following links from the Intel site I found the latest version of the driver mentioned was the one I had; hence asking for help.

Thanks both!

---

### Post by M1GEO on 2016-03-09
Okay,

Following the upgrade, I appear to be using a different driver:

```

george@ada:~$ dmesg | grep iwl | grep firmware
[    4.663989] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2
[    4.664126] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-7260-14.ucode failed with error -2
[    4.667248] iwlwifi 0000:06:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm

```

I re-run the script Hadaka mentioned: [ATTACH]267718[/ATTACH] [http://paste.ubuntu.com/15335017/](http://paste.ubuntu.com/15335017/)

The machine is now running Kerne 4.2, VERSION="15.10 (Wily Werewolf)".

```

Linux ada 4.2.0-30-generic #36-Ubuntu SMP Fri Feb 26 00:58:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

I need to live with the PC for a few hours, and see what happens. Things seem good at the minute, but, they were okay when posting. After the machine has been suspended a few times, it's behaviour gets worse ;)

Thanks for the help! I should have upgraded to 15.10 before posting!

---

### Post by chili555 on 2016-03-09
It doesn't appear that you successfully upgraded the firmware as I suggested. Were there any errors, hiccups, etc.?

> [    4.663989] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2
[    4.664126] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-7260-14.ucode failed with error -2-14 and -15 and even newer are in the package I linked.

---

### Post by M1GEO on 2016-03-09
No, sorry. I hadn't form the git repo you mentioned at that point.

I have now, and here's what I get in dmesg:

```

george@ada:~$ dmesg | grep iwl
[    4.596526] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[    4.602633] iwlwifi 0000:06:00.0: loaded firmware version 15.195093.0 op_mode iwlmvm
[    4.638015] iwlwifi 0000:06:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    4.638088] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    4.638334] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    4.859246] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    5.217957] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    5.218214] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    5.418750] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled
[    5.418993] iwlwifi 0000:06:00.0: L1 Enabled - LTR Enabled

```

---

### Post by chili555 on 2016-03-09
> iwlwifi 0000:06:00.0: loaded firmware version [COLOR="#FF0000"]15[/COLOR].195093.0 op_mode iwlmvmMuch better!

How is the stability? Better?

---

### Post by M1GEO on 2016-03-09
> How is the stability? Better?

I shall have to see now. It was okay sometimes before! I will try and suspend and re-wake it a few times, and see if it is fixed :)

Next job is to fix this insane resolution on the screen. The mouse pointer is less than 2mm high! ;)

Thanks for the help, all!

---

### Post by M1GEO on 2016-03-09
When the machine wakes from sleep, lightdm asks me to log in.

I log in, and see that in the nm-applet, Wi-Fi is disabled:

[IMG]http://www.george-smart.co.uk/temp/image1.png[/IMG]

When I select the 'Enable Wi-Fi' option, no APs are listed, despite there being several in range.

[IMG]http://www.george-smart.co.uk/temp/image2.png[/IMG]

I have to scan using the terminal ("sudo iwlist wlan0 scan") before anything is listed.

[IMG]http://www.george-smart.co.uk/temp/image3.png[/IMG]

Once the scan completes, the card re-associates with the AP last connected, and we're in business.

It hasn't dropped while in use yet; although this may come later...

---

### Post by chili555 on 2016-03-09
When you awake from sleep, does it help to simply do:```
sudo service network-manager restart
```

---

### Post by M1GEO on 2016-03-09
Yes; When I open the lid, log in, the network manager applet shows as disconnected. For completeness, I waited 2 minutes, and nothing happened.

Restarting network-manager as you suggested does indeed fix the issue. The nm-applet reloads (disappears and reappears within ~100ms) and perhaps 10 seconds later, the Wi-Fi is connected.

How weird. I guess the network manger isn't told to re-scan/re-connect when the machine wakes?

Appreciate the help :)

---

### Post by Hadaka on 2016-03-09
Hi, your country code is currently at default 00
which causes a slight delay in driver load while it makes an adjustment
along with other network problems the default 00 can cause.Please copy 
and paste to set and correct your code.
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
then please post to verify it set correctly.
```
iw reg get
cat /etc/default/crda
```
You can also save some processor and wireless load time by clicking the network icon
then > edit connections, edit your wireless connection and set IPv6 to Ignore
thanks.

---

### Post by M1GEO on 2016-03-09
Hadaka;

Thanks for the info. I have set that, as suggested:

```

george@ada:~$ iw reg get
country GB: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A)
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
	(5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)

```

```

george@ada:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=GB

```

I also set IPv6 to ignore, as suggested.

Thanks. I will see how that performs tomorrow!

Much appreciated, both! :)

---

### Post by chili555 on 2016-03-09
> **M1GEO said:**
> Yes; When I open the lid, log in, the network manager applet shows as disconnected. For completeness, I waited 2 minutes, and nothing happened.

Restarting network-manager as you suggested does indeed fix the issue. The nm-applet reloads (disappears and reappears within ~100ms) and perhaps 10 seconds later, the Wi-Fi is connected.

How weird. I guess the network manger isn't told to re-scan/re-connect when the machine wakes?

Appreciate the help :)This suggestion assumes you are using Ubuntu 15.10, the first release that uses the rather new *systemd*, for which most processes, but evidently not all, work better.

Please open a terminal and do:

```
sudo gedit  /etc/systemd/system/wifi-resume.service
```

Use nano or kate or leafpad if you don't have the text editor gedit. A new empty file will open. Add the following:

```
[Unit]
Description=Local system resume actions
After=suspend.target

[Service]
Type=oneshot
ExecStart=/bin/systemctl restart network-manager.service

[Install]
WantedBy=suspend.target
```

Proofread carefully twice, save and close the text editor. Now do:

```
sudo chmod +x  /etc/systemd/system/wifi-resume.service
```

And next:

```
sudo systemctl enable wifi-resume.service
```

Reboot and let us know if the problem is solved.

---

### Post by M1GEO on 2016-03-09
Done

```

george@ada:~$ sudo systemctl enable wifi-resume.service
Created symlink from /etc/systemd/system/suspend.target.wants/wifi-resume.service to /etc/systemd/system/wifi-resume.service.

```

Seems to work soo far.

Thanks very much! I think we can call this solved! :)

---

