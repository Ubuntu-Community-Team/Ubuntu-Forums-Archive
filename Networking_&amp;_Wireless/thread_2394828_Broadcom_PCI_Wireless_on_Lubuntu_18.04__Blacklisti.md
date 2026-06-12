---
title: "Broadcom PCI Wireless on Lubuntu 18.04 / Blacklisting"
date: 2018-06-22
forum: Networking &amp; Wireless
---

### Post by gbe++ on 2018-06-22
Hi, this post [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) details steps to troubleshoot driver issues. 

By device (14e4:4727) falls under _Special case #1_ however. 

This is my first time using Linux so I'm wondering how to reverse the steps suggested here:

```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```

Any info appreciated, if you know how to get my device working that'd be amazing but I'm just looking to undo what I've done so I can try other things suggested elsewhere. 
Like here [https://ubuntuforums.org/showthread.php?t=2226102](https://ubuntuforums.org/showthread.php?t=2226102)

---

### Post by chili555 on 2018-06-22
Unless I have mis-read the thread you linked, it suggests that you blacklist b43 and ssb so that the correct driver, brcmsmac loads and drives your device.

Unless I mis-read your post above, you are asking how to *UN*-blacklist these drivers so that you can follow the linked thread that suggests that you blacklist them.

I'm confused.  :confused: :confused:

What am I missing here?

As your system sits now, does the correct driver load?```
lsmod | grep brcm
```Are there any clues in the log?```
dmesg | grep brcm
```Is the wireless switch set to enable the wireless radio?```
rfkill list all
```

---

### Post by gbe++ on 2018-06-22
Hi chili, sorry for the confusion I'm just starting to wrap my head around things. 

Just as an aside I used this to remove the blacklisting lines mentioned in your original post.
```
sudo sed -i '/^blacklist b43$/d' /etc/modprobe.d/blacklist.conf
sudo sed -i '/^blacklist ssd$/d' /etc/modprobe.d/blacklist.conf
```

I've since blacklisted b43, ssb, wl, bcma and brcmfmac  leaving brcmsmac up. 

```
sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
sudo modprobe brcmsmac
```

The actual problem I have is that most wifi is working, but the wifi  network I used during install hasn't connected since and doesn't show in  the list of available networks but other networks do and they work, i.e. my mobile hotspot works, other router show up, but my router doesn't. 

```
nmcli dev wifi
```


Anyway, to answer your questions:

```
lsmod | grep 
brcmbrcmsmac              565248  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
bcma                   57344  2 brcmsmac
mac80211              778240  1 brcmsmac
cfg80211              622592  2 brcmsmac,mac80211


``` 

  ```
dmesg | grep brcm
[ 3097.792055] brcmsmac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 16
[ 3097.798497] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 499
[ 3097.801182] brcmsmac bcma0:1 wlp2s0b1: renamed from wlan0
[ 3098.086782] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 3098.086793] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[ 3482.005077] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 3482.005083] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 3482.057599] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 159/256 dur 1778/1504
[ 3482.067088] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 137/256 dur 1602/1504
[ 3484.914727] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 3502.582825] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 3502.582832] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 3502.582834] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)



``` ```
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
9: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by jeremy31 on 2018-06-22
Please visit the wireless script link in my signature and post your results.  I have a wifi device with the same ID on my Linux Mint laptop and have not had to blacklist anything, it also happens to work fine with bcmwl-kernel-source installed but you might have a version of this card that isn't fully supported according to [https://wireless.wiki.kernel.org/en/users/drivers/brcm80211](https://wireless.wiki.kernel.org/en/users/drivers/brcm80211)
> Please note: at least BCM4313 is not fully supported. Some models appears to work (users reported success), but some don't, and there's no indication that this is going to change. For example: [http://marc.info/?t=138817851800006&r=1&w=2](http://marc.info/?t=138817851800006&r=1&w=2)



---

### Post by gbe++ on 2018-06-22
[http://paste.ubuntu.com/p/VzgpktddNb/](http://paste.ubuntu.com/p/VzgpktddNb/)

---

### Post by chili555 on 2018-06-22
I see. You un-blacklisted the drivers and then re-blacklisted them. Correct?

We see this: ```
[/etc/netplan/01-netcfg.yaml]
network:
  version: 2
  renderer: networkd
  wifis:
    wlp2s0b1:
      dhcp4: yes
      access-points:
        NETGEAR83:
          password: littlecurtain347

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager
```You have conflicting directives here. If you want Network Manager to handle networking, and in a desktop machine, that's what I recommend, then delete the first file. Let's back it up first:```
sudo cp /etc/netplan/01-netcfg.yaml  ~/01-netcfg.yaml 
sudo rm /etc/netplan/01-netcfg.yaml 
```Reboot.

Next, we see this:```
wlp2s0b1  11 channels in total; available frequencies :
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
```By any chance, is the missing SSID on a channel not listed here? 13? 49? 153? 21,493???

---

### Post by gbe++ on 2018-06-22
Oh, yes my router is on channel 13 #-oI changed it to 11 and the ssid shows now! Thanks for pointing that out. It makes no sense to me that I could receive channel 13 on my previous install and also during lubuntu install but not after completing it but I won't worry about it. 

I removed 01-netcfg.yaml and rebooted. It's added a "System Tray" applet to my panel weirdly? Its a nearly identical clone of the network tray menu next to it? Not a big deal, I can remove it.

Wifi is working now! Thanks a bunch chili, might have been simple but the community was right, you really know your stuff \\:D/

---

### Post by chili555 on 2018-06-23
> Oh, yes my router is on channel 13 I changed it to 11 and the ssid shows now! Let's, just for the learning experience, see if we can automagically resurrect channels 12 and 13.

Please set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Now what are the available channels?```
sudo iwlist freq
```In a very few cases, the regulatory domain is somehow hard-coded into the wireless chip. I have a little USB wireless that steadfastly refuses any domain except CN. You will probably have better luck.

---

### Post by jeremy31 on 2018-06-24
There is a patch that should allow brcmsmac to use channels over 11- [https://github.com/hak5/wifipineapple-openwrt/blob/master/package/kernel/mac80211/patches/850-brcmsmac-remove-extra-regulation-restriction.patch](https://github.com/hak5/wifipineapple-openwrt/blob/master/package/kernel/mac80211/patches/850-brcmsmac-remove-extra-regulation-restriction.patch)

I don't ever remember seeing a Broadcom wifi device in Linux being able to use a channel in 2.4Ghz over 11

---

