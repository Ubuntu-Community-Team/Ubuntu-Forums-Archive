---
title: "Intel AC 7260 problem."
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by kirkwoodjoshua on 2014-02-04
Hi,

I am running Ubuntu 12.10 with kernel 3.12.6 and am having issues with the card detecting any wireless networks. From what I understand this kernel version should allow this card to work. The interface shows up when running the iwconfig command. I have read other threads but cant find any problems similar. Any help would be appreciated.

**iwconfig**
```
wlan0     IEEE 802.11abgn  ESSID:"N7198"
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


lo        no wireless extensions.


eth0      no wireless extensions.
```



**lshw -C network**
```
  *-network
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: ec:a8:6b:fe:a2:39
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.15-4 ip=10.0.0.33 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:f7d00000-f7d1ffff memory:f7d29000-f7d29fff ioport:f080(size=32)
  *-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 73
       serial: 0c:8b:fd:cc:44:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.12.6-031206-generic firmware=22.0.7.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:f7c00000-f7c01fff

```
[B]dmesg | grep iwl
[/B]```
[   26.142843] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[   26.283174] iwlwifi 0000:02:00.0: loaded firmware version 22.0.7.0 op_mode iwlmvm
[   26.519601] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   26.519670] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   26.519815] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   26.799840] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   32.105027] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   32.105182] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   49.446956] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   49.447106] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   50.430364] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   50.430515] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1061.507859] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1061.508011] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1092.266800] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1092.266950] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1092.363525] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1092.363677] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1100.123938] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1100.124089] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S

```


Thanks

---

### Post by chili555 on 2014-02-04
Are you using the latest firmware? [http://askubuntu.com/questions/411475/problem-with-the-intel-wireless-7260-driver/411515#411515](http://askubuntu.com/questions/411475/problem-with-the-intel-wireless-7260-driver/411515#411515)

---

### Post by kirkwoodjoshua on 2014-02-04
I have run those steps but the same things is happening. if it's any consolation I had to run
```
lsmod | grep iwlwifi


iwlwifi               147847  1 iwlmvm
cfg80211              408981  3 iwlwifi,mac80211,iwlmvm
compat                 13003  4 cfg80211,iwlwifi,mac80211,iwlmvm

```
and remove the dependent modules before i was able to remove iwlwifi. 
Not sure why compat is showing up.

---

### Post by chili555 on 2014-02-04
Let's see another:```
dmesg | grep iwl
```And also:```
rfkill list all
sudo iwlist wlan0 scan
```With the ethernet detached, please.

---

### Post by kirkwoodjoshua on 2014-02-04
Thanks chili555. I have added the output below. 

dmesg | grep iwl
```


[   18.552338] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[   18.695287] iwlwifi 0000:02:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[   18.856864] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[   18.857716] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   18.857862] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   19.121413] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   22.926180] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   22.926332] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S

```

rfkill list all
```



0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

sudo iwlist wlan0 scan
```
wlan0     No scan results

```

---

### Post by chili555 on 2014-02-05
Man! My favorite kind of problem; everything looks just great except it doesn't work! We see the new firmware loaded correctly. Previously, we saw:> loaded firmware version 22.0.7.0 op_mode iwlmvmAnd now:> loaded firmware version 22.[COLOR="#FF0000"]1[/COLOR].7.0 op_mode iwlmvmHowever, we see nothing wrong (read: fixable) so far. Please detach the ethernet. Reboot so we have a clean slate. Open a terminal and run:```
dmesg > wifi.txt
cat /var/log/syslog | grep -e wlan -e iwl | tail -n25  >>  wifi.txt
```Attach the ethernet so that you can post the result. Find the file wifi.txt in your user directory and paste it here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)  Please give us the link in your reply.

I love a mystery!

---

### Post by kirkwoodjoshua on 2014-02-05
Yeah its had me stumped for ages. I've attached as below.

[http://paste.ubuntu.com/6879512/](http://paste.ubuntu.com/6879512/)

---

### Post by chili555 on 2014-02-05
I see this strange entry:> 0000:02:00.0: System wakeup disabled by ACPIBus #02:00 is the bus used by your wireless card. Please see: > iwlwifi 0000:[COLOR="#FF0000"]02:00[/COLOR].0: irq 44 for MSI/MSI-XI'm not quite sure what that means, but I suggest you have a look in the BIOS to see if there are any settings available for wireless networking. By the way, generally, but not always, the BIOS can be reset to defaults and work perfectly in Ubuntu.

I also see this:> cfg80211: World regulatory domain updated:In this case, a blank means it was set to a one-size-maybe-fits-all guess, just like my old orange jumpsuit! You might try setting the domain explicitly as I explain here: [http://askubuntu.com/questions/412936/another-wifi-dropping-thread/](http://askubuntu.com/questions/412936/another-wifi-dropping-thread/)

Also, may I see:```
cat /etc/network/interfaces
```

---

### Post by kirkwoodjoshua on 2014-02-05
BIOS reset hasn't appeared to fix the issue. The device is an Intel NUC DCCP847DYE with the Intel AC 7260 mini PCIe. I have just set the domain explicitly but after reboot am having the same issues. 

cat /etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by chili555 on 2014-02-05
Boo hoo hoo!! Why do I get all the hard ones??

I noticed this boot parameter:> i915.i915_enable_rc6=0Did you add that yourself or did the installation magically create it? Was it needed to boot? Install? Have you tried without it? My NUC doesn't require it.

It appears you are using BIOS version 040 and 048 is available: [https://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Desktop+Boards&ProductLine=Intel%C2%AE+NUC+Boards+and+Kits&ProductProduct=Intel%C2%AE+NUC+Board+DCP847SKE](https://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Desktop+Boards&ProductLine=Intel%C2%AE+NUC+Boards+and+Kits&ProductProduct=Intel%C2%AE+NUC+Board+DCP847SKE)  I suggest you update. I've updated the BIOS on mine and it's simple.

Yours seems to take a long time to boot:> [   [COLOR="#FF0000"]37[/COLOR].769161] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSOHere is mine:> [    [COLOR="#FF0000"]7[/COLOR].285586] ahci 0000:00:1f.2: port does not support device sleepYours seems to pause at:> [    7.388739] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    7.388746] EXT4-fs (sda1): write access will be enabled during recovery
[   14.919923] EXT4-fs (sda1): recovery complete
[   14.925352] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)Was that an anomaly or the usual time? Are you using an SSD?

Does it sound like I'm grasping at straws?? Everything actually looks pretty good but I can't see why it doesn't start and run.

---

### Post by kirkwoodjoshua on 2014-02-06
I added > i915.i915_enable_rc6=0 manually. 

I'm trying to run this as a media center and if i set the default session to XBMC all i get is a black screen unless I add that exact boot parameter. 

I'll give the BIOS update a go and let you know how it goes.

Also its probably taking a while to boot as its installed to a USB not an SSD. Don't think the media center should need the SSD as it wont be doing much. Haha. But thanks for the help so far. Much appreciated.

---

### Post by kirkwoodjoshua on 2014-02-06
Just ran the BIOS update. Now running 0048 but having the same issues. Removed i915.i915_enable_rc6=0 which also has the same issues. I noticed in the BIOS I can adjust the PCI Latency timer for the AC 7260 which was set to 32. Changed it to 64 but also exact same issues.

I.E wont list any SSID's.

---

### Post by chili555 on 2014-02-06
The ideas and tricks are getting harder to find my friend! I did notice this:> rfkill1: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ieee80211/phy0/rfkill1) (driver iwlwifi)So Ubuntu thinks, just because it's built with essentially laptop parts, that it's a ... laptop with a hardware switch or key combination maybe? Let's see:```
cat /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ieee80211/phy0/rfkill1 
```Whatever it returns, either 1 or 0, let's reverse it:```
sudo -i
echo X  >  /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ieee80211/phy0/rfkill1
exit
```Where X is the opposite of what you found in the previous command. And check the log:```
cat /var/log/syslog | grep -e iwl -e 02:00 | tail -n10
```Also, please post:```
rfkill list all
```Is your BIOS set to UEFI or legacy mode? Mine would only install in legacy although I didn't scour the earth trying to find a way with UEFI. I just tried legacy and it worked.

Whatever yours is set to, I suggest you try reversing it.

---

### Post by kirkwoodjoshua on 2014-02-10
Sorry for the delay as I was away for the weekend. 

```
cat /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ieee80211/phy0/rfkill1
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]Gave a reply saying that 'rfkill1' was a directory. That directory contains the below.[COLOR=#000000][FONT=Ubuntu Mono][FONT=arial]
[/FONT]
[/FONT][/COLOR]```
 
user@computer/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ieee80211/phy0/rfkill1
ls
claim hard name power state type
device index persistent soft subsystem uevent
```
[COLOR=#000000]
[FONT=arial]The WiFi is still not soft or hard blocked. [/FONT]

[FONT=arial]I am going to try a live USB of Lubuntu 13.10 to see if the WiFi is working and will post what I find. [/FONT]

[/COLOR]

---

### Post by kirkwoodjoshua on 2014-02-10
Having the exact same problems with Lubuntu 13.10 . Is it possible its a hardware related issue? 

Also not 100% sure what you mean by legacy mode. I have set the SATA configuration to IDE but that shouldn't affect a USB should it? 

I haven't had any issues installing the OS as of yet.

---

### Post by chili555 on 2014-02-10
By legacy, I mean this: [https://communities.intel.com/servlet/JiveServlet/showImage/2-215440-234379/IMG_20131207_154127192.jpg](https://communities.intel.com/servlet/JiveServlet/showImage/2-215440-234379/IMG_20131207_154127192.jpg)  My NUC boots perfectly with 'legacy' *only* checked. What is your setting? Have you tried both?

I'm a little mystified as to how and why the machine would boot correctly with *both* checked as in the picture; then again, I know little about the intricacies of UEFI. >  Is it possible its a hardware related issue?Anything is possible. Did you double-check that both antenna wires are securely in place? [http://cdn.pcper.com/files/imagecache/article_max_width/review/2012-12-06/18.jpg](http://cdn.pcper.com/files/imagecache/article_max_width/review/2012-12-06/18.jpg) I actually don't think it matters if the black or gray is attached to either Main or Aux; just that they are both connected securely.> user@computer/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ieee80211/phy0/rfkill1
ls
claim hard name power state type
device index persistent soft subsystem ueventWhat does this tell us?```
cat /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ieee80211/phy0/rfkill1/state
```

---

### Post by kirkwoodjoshua on 2014-02-10
Just reseated both antenna wires and everything is working flawlessly. Annoyed now as that was the fix haha. Thanks so much. Do you accept donations for your trouble?

---

### Post by chili555 on 2014-02-10
Awesome! Glad it's working. 

It was no trouble. I do this because I enjoy it and I love a good mystery. Please use thread tools at the top to mark Solved.

---

