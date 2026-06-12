---
title: "Broadcom BCM4312"
date: 2014-04-14
forum: Networking &amp; Wireless
---

### Post by dec2 on 2014-04-14
Hi,

I'm just recently after making the move from Xp to Lubuntu on a Dell  Inspiron 1501.  After hours of meddling I managed to get the issue with  the wireless sorted. (Although I tried so many steps I'm still unsure  which one did the trick! [IMG]http://b-static.net/vbulletin/images/smilies/rolleyes.png[/IMG]).  I find it great, laptop has become practically silent while running and is working great for the basics.

My question is as follows and I'd be grateful for the help, I have tried  to use a Lubuntu Live USB on another Dell laptop with the same broadcom  issue, is it possible to copy a certain set of folders from the laptop  that is working and move them across? 

I saw it mentioned on another site while searching the initial problem but cannot remember where!

Thanks.

---

### Post by chili555 on 2014-04-14
It is possible; however, it may or may not properly drive the device! Are the devices in the respective devices exactly the same?```
lspci -nn | grep 0280
```Is the kernel version the same?```
uname -mr
```If there are differences, then even if you copy over the driver, it probably won't work.

Let's start by hearing the details of each from the commands above.

---

### Post by dec2 on 2014-04-17
Hi Chili,

Ok the result of the commands are

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

&

3.11.0-12-generic i686.

That's from the Dell Inspiron 1525.  IIRC the device in the 1501 was not the same, it was 4311.

Would I be correct in saying that linux-firmware-nonfree would be the solution for both of those problems?

---

### Post by chili555 on 2014-04-17
> **dec2 said:**
> Hi Chili,



Would I be correct in saying that linux-firmware-nonfree would be the solution for both of those problems?Correct. Are you all set or do you need additional guidance?

---

### Post by Bucic on 2014-04-17
I still can't connect even after installing linux-firmware-nonfree.
I tried:
- unloading all drivers and loading only b43 per [url]http://wireless.kernel.org/en/users/Drivers/b43#Switching_between_drivers
- previously installed sta ; purged now[/url]

Acer aspire one
lubuntu 14.04, updated
```

~$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
uz1@aspireone:~$ uname -mr
3.13.0-24-generic i686

```

I have limited access to this computer so I've acquired as much info as I could; please take a look at the attachment.[https://onedrive.live.com/redir?resid=66CF2646234394FC!3305&authkey=!AKF2us4qCopaFxk&ithint=file%2c.txt](https://onedrive.live.com/redir?resid=66CF2646234394FC!3305&authkey=!AKF2us4qCopaFxk&ithint=file%2c.txt)

---

### Post by chili555 on 2014-04-17
It actually looks pretty good. Please reboot with the ethernet detached. Then do some checks. Is a wireless interface created, ideally wlan0?```
iwconfig
```Is the wireless switch or key combination set to enable wireless?```
rfkill list all
```Does the interface scan and see networks?```
sudo iwlist wlan0 scan
```Generally, if it scans, it can connect.

---

### Post by Bucic on 2014-04-18
```

~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
hso0      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.



~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hso-0: Wireless WAN
	Soft blocked: no
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: acer-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
4: acer-threeg: Wireless WAN
	Soft blocked: no
	Hard blocked: no


```

Wireless networks are detected. Still no tray icon though. I also don't remember how to connect to a chosen network from terminal, sorry.


Thanks for bearing with me!

---

### Post by chili555 on 2014-04-18
Does the icon appear if you open a terminal and do:```
nmm-applet &
```If so, can you click the icon, see your network and connect? If so, we'll work on the mystery of the disappearing Network Manager icon.

If not, is Network Manager even running?```
ps aux | grep network-manager
```If not, does it start?```
sudo service network-manager start
```Please see attached.

---

### Post by dec2 on 2014-04-19
Chili thanks very much for the assistance! I think (at least I hope!) I've a better understanding of it now!

---

### Post by Bucic on 2014-04-22
nm-applet & 
started the applet. Without sudo. No wifis listed. Added new wifi conn. via 'Modify...' I had to manually select wlan0 IP ...5) from the drop down list. It didn't connect.

sudo iwlist wlan0 scan
still shows available networks.

---

### Post by chili555 on 2014-04-22
> **Bucic said:**
> nm-applet & 
started the applet. Without sudo. No wifis listed. Added new wifi conn. via 'Modify...' I had to manually select wlan0 IP ...5) from the drop down list. It didn't connect.

sudo iwlist wlan0 scan
still shows available networks.Do you have a wireless interface, ideally wlan0?```
iwconfig
```What modules (drivers) are loading?```
lsmod | grep -e wl -e b43
```Are there informative messages in the log?```
dmesg | grep -e wl -e b43
```Thanks.

---

### Post by Bucic on 2014-04-22
```

xxx@aspireone:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
hso0      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.


```

```

xxx@aspireone:~$ lsmod | grep -e -wl -e b43
b43                   356470  0 
bcma                   42043  1 b43
mac80211              545990  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43

```

```

xxx@aspireone:~$ dmesg | grep -e wl -e b43
[   13.231226] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   13.272130] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   19.336146] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   24.897718] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.909873] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by chili555 on 2014-04-22
Everything looks good so far! > Added new wifi conn. via 'Modify...' I had to manually select wlan0 IPAre all those manual settings still there? They should be removed. Anything here?```
cat /etc/network/interfaces
```Or here?```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```Ideally, run with any ethernet detached as Network Manager is designed to prefer ethernet over wireless.

---

### Post by Bucic on 2014-04-22
I always run with ethernet cable disconnected. Can't remove the card as it is a netbook.


```

~$ cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
Apr 22 17:31:28 aspireone NetworkManager[727]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 22 17:31:28 aspireone NetworkManager[727]: <info> (eth0): bringing up device.
Apr 22 17:31:28 aspireone NetworkManager[727]: <info> (eth0): preparing device.
Apr 22 17:31:28 aspireone NetworkManager[727]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 22 17:31:28 aspireone NetworkManager[727]: <info> Added default wired connection 'Po&#322;&#261;czenie przewodowe 1' for /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/eth0
Apr 22 17:31:28 aspireone NetworkManager[727]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 22 17:31:28 aspireone NetworkManager[727]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 22 17:31:28 aspireone NetworkManager[727]: <info> urfkill disappeared from the bus
Apr 22 17:31:28 aspireone NetworkManager[727]: <info> ModemManager available in the bus
Apr 22 17:31:28 aspireone NetworkManager[727]: <warn> (ttyHS0): unusable modem detected
Apr 22 17:31:29 aspireone NetworkManager[727]: <info> wpa_supplicant started
Apr 22 17:31:29 aspireone NetworkManager[727]: <info> (wlan0) supports 4 scan SSIDs
Apr 22 17:31:29 aspireone NetworkManager[727]: <warn> Trying to remove a non-existant call id.
Apr 22 17:31:29 aspireone NetworkManager[727]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 22 17:31:29 aspireone NetworkManager[727]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 22 17:31:29 aspireone NetworkManager[727]: <info> (wlan0): supplicant interface state: ready -> disconnected
Apr 22 17:31:29 aspireone NetworkManager[727]: <info> (wlan0) supports 4 scan SSIDs
Apr 22 17:31:29 aspireone wpa_supplicant[1245]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 22 17:31:30 aspireone NetworkManager[727]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Apr 22 17:31:33 aspireone NetworkManager[727]: <info> WiFi hardware radio set enabled

```

I rebooted and commented out the interfaces in
cat /etc/network/interfaces
(there were lo, loop etc.)
Didn't change anything.

EDIT:
'Po&#322;&#261;czenie przewodowe 1' is Polish name for 'Wired connection 1'.

---

### Post by Bucic on 2014-04-24
Sorry for rushing you like that but could you by any chance drop me some new trail?

---

### Post by chili555 on 2014-04-24
Sorry for the delay in my reply. 

You have the correct driver and firmware fr your device; it loads; you can scan for networks. I think your real problem is this:> Wireless networks are detected. **Still no tray icon though.** This is a known bug in 14.04, I have found. Please check here: [http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html) and here: [http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing](http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing)

Please undertake the fix and then give us your report.

---

### Post by Bucic on 2014-04-25
In post #10 I wrote that even when nm-applet starts it does not list any networks. A popup says 'offline mode'. iwlist shows networks in the terminal, the applet doesn't.

Edit:
When I used Rodol's answer I get 'waiting for network configuration......... Booting without network configuration.'
This also happens with wired ethernet cable connected. On another note, it seems that network manager service does not start at system boot. Network is available after another 40 seconds or so.

It doesn't change the fact however that even when everything has started no wifis are listed in the applet.

---

### Post by chili555 on 2014-04-25
> when nm-applet starts it does not list any networks. A popup says 'offline mode'. iwlist shows networks in the terminal, the applet doesn't.Weird! Let's have a look at:```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```Thanks.

---

### Post by Bucic on 2014-04-26
```
~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
#iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
wpa-ssid HELIPORT
wpa-psk <mywifipassword>
```

```
~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

```

Weird indeed. With these even with ethernet I don't get a connection sooner than after a minute after boot process has finished.

---

### Post by chili555 on 2014-04-26
Your file is just a bit faulty. I suggest:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid HELIPORT
wpa-psk <mywifipassword>
```After making this change, reboot and tell us if things have improved.

Of course, you could also remove the wlan0 lines and simply let NM do all the work:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
#auto wlan0
#iface wlan0 inet dhcp
#wpa-ssid HELIPORT
#wpa-psk <mywifipassword>
```Then you should see networks in NM and use it to connect. It's your choice.

If this is a stay-at-home computer that doesn't need to roam down to the coffee shop or University, I'd probably stick with the first method; that is, the wlan0 details declared in *interfaces*.

---

### Post by Bucic on 2014-04-26
It's alive! Thank you very much!

I went for just these lines in interfaces:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

It may be that I broke the file along the way while troubleshooting the driver problem. I recall I tried deleting it at some point to make sure it's clean and correct but it didn't work (system didn't boot).

---

### Post by chili555 on 2014-04-26
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

### Post by Bucic on 2014-04-26
I didn't start the thread so I think the option is simply not available to me.

---

### Post by chili555 on 2014-04-26
> **Bucic said:**
> I didn't start the thread so I think the option is simply not available to me.Yep! Thanks for confirmation in any event.

---

### Post by Bucic on 2014-04-27
Please stop saying 'thank you'. I feel bad. You've helped me with a second computer already! :)

---

### Post by Bucic on 2014-05-06
It stopped working again for me. I haven't used the netbook for a while. Then:
- took it to work : couldn't connect to any wifi
- took it back home : couldn't connect to any wifi
- acquired troubleshooting information (attached)
- looked into interfaces ; its contents have changed from the contents as in post #21 to
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
#iface lo inet loopback
```
- tried restoring the interfaces contents per post #21 as well as per your post #20 with SSID and password specified - to no avail

---

### Post by chili555 on 2014-05-06
> - tried restoring the interfaces contents per post #21 as well as per your post #20 with SSID and password specified - to no availPlease remove those settings. Please restore */etc/network/interfaces* to:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```Then reboot and tell me if you connected. If not, pease let me see a new report as above.

---

### Post by Bucic on 2014-05-07
It has gotten worse. It doesn't even scan now.

One dmesg is attached. Here's another one after removing all remembered wifis (via applet > Modify networks...) and a second reboot 
```

~$ dmesg | grep -e wl -e b43
[   11.429062] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   11.508808] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   19.268150] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   24.885441] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.889090] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
uz1@aspireone:~$ dmesg | grep -e wl -e b43
[   11.429062] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   11.508808] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   19.268150] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   24.885441] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.889090] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  625.241937] wlan0: authenticate with 00:24:d1:7a:23:d9
[  625.253077] wlan0: direct probe to 00:24:d1:7a:23:d9 (try 1/3)
[  625.456173] wlan0: direct probe to 00:24:d1:7a:23:d9 (try 2/3)
[  625.660171] wlan0: direct probe to 00:24:d1:7a:23:d9 (try 3/3)
[  625.864170] wlan0: authentication with 00:24:d1:7a:23:d9 timed out
[  633.198417] wlan0: authenticate with 00:24:d1:7a:23:d9
[  633.209033] wlan0: direct probe to 00:24:d1:7a:23:d9 (try 1/3)
[  633.412170] wlan0: send auth to 00:24:d1:7a:23:d9 (try 2/3)
[  633.616173] wlan0: send auth to 00:24:d1:7a:23:d9 (try 3/3)
[  633.820165] wlan0: authentication with 00:24:d1:7a:23:d9 timed out

```

---

### Post by chili555 on 2014-05-07
> b43-phy0 warning: Forced PIO by use_pio module parameter. This should not be needed and will result in lower performance.This is pretty unusual; I think I'd look around in the BIOS to see if there is any unusual setting. Typically, the BIOS can be set to defaults and work correctly in Linux. If you dual-boot with Windows and are using UEFI, Please proceed with caution. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you have a conf file that forces the parameter?```
ls /etc/modprobe.d
```If you find something, we need to have a look at it and probably remove it.

---

### Post by Bucic on 2014-05-07
BIOS is updated, at defaults and in the same state as before when wifi started working.
I don't recall fiddling with modules.

```

~$ ls /etc/modprobe.d
alsa-base.conf              blacklist-modem.conf         fbdev-blacklist.conf
blacklist-ath_pci.conf      blacklist-oss.conf           iwlwifi.conf
blacklist.conf              blacklist-rare-network.conf  libpisock9.conf
blacklist-firewire.conf     blacklist-watchdog.conf      mlx4.conf
blacklist-framebuffer.conf  dkms.conf    

NOTE:
blacklist-oss.conf highlighted, cyan


/etc/modprobe.d/blacklist-oss.conf
blacklist ac97
blacklist ac97_codec
blacklist ac97_plugin_ad1980
blacklist ad1848
blacklist ad1889
blacklist adlib_card
blacklist aedsp16
blacklist ali5455
blacklist btaudio
blacklist cmpci
blacklist cs4232
blacklist cs4281
blacklist cs461x
blacklist cs46xx
blacklist emu10k1
blacklist es1370
blacklist es1371
blacklist esssolo1
blacklist forte
blacklist gus
blacklist i810_audio
blacklist kahlua
blacklist mad16
blacklist maestro
blacklist maestro3
blacklist maui
blacklist mpu401
blacklist nm256_audio
blacklist opl3
blacklist opl3sa
blacklist opl3sa2
blacklist pas2
blacklist pss
blacklist rme96xx
blacklist sb
blacklist sb_lib
blacklist sgalaxy
blacklist sonicvibes
blacklist sound
blacklist sscape
blacklist trident
blacklist trix
blacklist uart401
blacklist uart6850
blacklist via82cxxx_audio
blacklist v_midi
blacklist wavefront
blacklist ymfpci
blacklist ac97_plugin_wm97xx
blacklist ad1816
blacklist audio
blacklist awe_wave
blacklist dmasound_core
blacklist dmasound_pmac
blacklist harmony
blacklist sequencer
blacklist soundcard
blacklist usb-midi



# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```

---

### Post by Bucic on 2014-05-10
Hi chili!
I would really appreciate some input. Please don't get me wrong, I wouldn't want to rush you. You do a great job on the forums. It's just that the owner of the netbook asks me whether Linux is possible on his netbook or does he need to look elsewhere.

---

### Post by chili555 on 2014-05-11
Please try a driver parameter:```
sudo -i
echo "options b43 pio=1 qos=0"  >  /etc/modprobe.d/b43.conf
exit
```Reboot and let's see your script again.

This is a very unusual problem. This card/driver/firmware combination almost always work perfectly.

---

### Post by Bucic on 2014-05-11
This made the network work after reboot. Wifi connected. After a second reboot it stopped working. I re-aplied post #32 rebooted and it started working again. Another reboot, not working again. Another reboot, still not working. I'm re-installing the system and I will follow the wiki instructions to the point this time.

I'm not sure what you meant by 'my script', sorry.

---

### Post by chili555 on 2014-05-11
> I'm re-installing the system and I will follow the wiki instructions to the point this time.Just be certain to *NOT* install Additional Drivers. It installs the wrong driver. You, instead, want the package linux-firmware-nonfree.

---

### Post by Bucic on 2014-05-13
Just started clean with 14.04. Issued
```

sudo apt-get install firmware-b43-installer

```
and restarted.

It got me where I was recently with the previous 14.04 install we struggled with.

I'll try with the linux-firmware-nonfree now... How do I uninstall the driver from firmware-b43-installer to install the linux-firmware-nonfree?

---

### Post by chili555 on 2014-05-13
>  How do I uninstall the driver from firmware-b43-installer to install the linux-firmware-nonfree?You needn't do so. I actually doubt that firmware-b43-installer is available in 14.04. If and when it fails, please try linux-firmware-nonfree. 

They are essentially the same; they intend to install the proprietary firmware needed to make the native b43 driver work.

---

### Post by Bucic on 2014-05-14
The phy was not but the firmware-b43-installer was available. Anyway, the nonfree firmware didn't work either. All same. Networks listed in the applet, selected, icon animation, connection is not established.

Does it make sense to attach another batch of my system info? Isn't it the high time to submit a bug report (launchpad)?

EDIT:
Bug reported on launchpad
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/1319491](https://bugs.launchpad.net/ubuntu/+source/linux-firmware-nonfree/+bug/1319491)

---

### Post by Bucic on 2014-05-17
It seems the bug has been marked as confirmed by the bot but no other info has been posted.

EDIT:
And here's how it went on Fedora :/
[https://ask.fedoraproject.org/en/question/46860/how-to-setup-broadcom-4312-wireless/](https://ask.fedoraproject.org/en/question/46860/how-to-setup-broadcom-4312-wireless/)

---

### Post by Bucic on 2014-05-25
Confirmed on Manjaro with b43. I slowly loose hope with this. The launchpad bug doesn't seem to attract too much attention. It's 'hotness' is only 12.

---

