---
title: "Wireless drops out &amp; also often can't connect on log-in - Lenovo Z570 &amp; BCM4313"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by peGGi on 2013-10-03
Hello,

 [COLOR=#ff8c00]**SYSTEM INFO**[/COLOR]
 I recently installed **Ubuntu Studio 13.04 64 bit** on my system (a **Lenovo IdeaPad Z570** - just over 2 years old, 2nd gen Core i5, **Broadcom BCM4313** wireless card, Nvidia Optimus graphics (disabled in UEFI though so only using the Intel graphics card)).  My router is a **Netgear N300 (WNR2200)**.

 [COLOR=#ff8c00]**PROBLEM**[/COLOR]
 There are two problems with the wireless: connection drops a lot and often unable to access network.  
 
[LIST=1]
[*]Problem 1 - connection drops a     lot: For example, streaming video or audio freezes; pages become     unable to load; torrent downloads go from being fast and normal to     zero; Skype calls drop. These problems sometimes resolve after 5 min     or so, or if I close and restart Firefox (or for the torrent,     sometimes asking for new trackers works). 
[*]Problem 2 - unable to access network: I have been having     problems with the WiFi password credential too. Sometimes when I log     in, it repeatedly asks me for the WiFi password, never letting me     onto the network. On a few occasions, I have spent 20+min logging in and out until     it let me onto the network.  Other times it let's me onto the network no problem. 
[/LIST]
  [B][COLOR=#ff8c00]
FURTHER SYSTEM INFO[/COLOR][/B]
 This is a dual-boot set-up with Windows 7. I don't have these problems in Windows. My flatmate hasn't been experiencing any problems with our wireless on her mac. And my phone hasn't been having any problems with the wireless either.

 Like I mentioned, this is Ubuntu Studio 13.04 (64bit), so I'm using the 3.8.0-31-lowlatency x86_64 kernel and XFCE.

 **[COLOR=#ff8c00]STEPS TAKEN & RESEARCH[/COLOR]**
            
[LIST]
[*]I have gone through the [Ubuntu documentation and troubleshooting about wireless]("http://help.ubuntu.com/13.04/ubuntu-help/net-wireless-troubleshooting-hardware-check.html") but can't find anything that helps nor come to a solution.  Using *NDISwrapper* would be a 'last resort, I'd hope. 
[*]I had the option to enable the proprietary Broadcom BCM4313 802.11 b/g/n Wireless LAN Controller in *Settings/**Software & Updates/Additional Drivers* . However, when I enabled this, I couldn't connect to any network at all - it said that I'm not connected and nothing showed up in *Network Connections*. So I disabled it and went back to the generic Linux driver.  That was a few weeks ago.   Now it doesn't even let me enable the proprietary driver.  Underneath its listing it says “This device is not working.” 
[/LIST]
[INDENT][ATTACH=CONFIG]246715[/ATTACH]
[/INDENT]

[LIST]
[*]I blacklisted the *acer-wmi* module, as described in [this ]("http://ubuntuforums.org/showthread.php?t=1959458")[thread]("http://ubuntuforums.org/showthread.php?t=1959458").  I could be imagining this, but it seems to have improved the 'ask-for-password' problem. Before, the 'ask-for-password' problem happened approx. 1 in 4 times; now it feels more like 1 in 8. 
[*][This thread]("http://ubuntuforums.org/showthread.php?t=2149757&highlight=lenovo+z570+wireless") describes the connection-dropping problem on a similar machine, but this fix: 
[/LIST]
[INDENT=2][FONT=courier new]sudo modprobe -r iwlwifi 
[/FONT][/INDENT]
[INDENT=2][FONT=courier new]sudo modprobe iwlwifi 11n_disable=1 [/FONT]
[/INDENT]
[INDENT]then causes another problem, so I thought I'd ask for advice first before trying it.
[/INDENT]

[LIST]
[*]The [HardwareSupportComponentsWirelessNetwrokCardsBroadcom Ubuntu Community]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom") page says that my BCM4313 is supported out of the box, although that seems to be over 2 years old and is based on Ubuntu 11.04. 
[*]The [relevant Wireless Linux Wiki page]("http://wireless.kernel.org/en/users/Drivers/b43#supported") says that my card is *not* supported, with the following information: 
[/LIST]
[INDENT][TABLE="class: grid, width: 500"]
[TR]
[TD]PCI-ID[/TD]
[TD]Supported?[/TD]
[TD]Chip ID[/TD]
[TD]Modes[/TD]
[TD]PHY Version[/TD]
[TD]Alternative[/TD]
[/TR]
[TR]
[TD]14e4:4727[/TD]
[TD]no (WIP)[/TD]
[TD]BCM4313[/TD]
[TD]b/g/n[/TD]
[TD]LCN (r1)[/TD]
[TD]wl/[brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211")[/TD]
[/TR]
[/TABLE]
It also says below: “BCM4313 - chipset uses unsupported LCN PHY,  we work on it “.  I don't know how up-to-date this information is.
  [/INDENT]

[LIST]
[*]There are several drivers that I could possibly try listed in [this Ubuntu Community document]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"), but I don't want to try them all yet in case there is a more obvious solution first.  **The fact that my wireless does connect more often than not, and it works well (excluding the dropouts, obviously!) makes me think that there is an easier solution.  Just one that's beyond me!** 
[*]I've read through the various problems and solutions in [the sticky thread about BCM43xx cards]("http://ubuntuforums.org/showthread.php?t=2090138"), but many of those users are using a different 43xx card, most of them are using an older kernel and most of them can't access wireless at all.  In short their problems are different to mine. 
[/LIST]
 [COLOR=#ff8c00][B]
FURTHER INFO – TERMINAL OUTPUTS ABOUT SYSTEM & WIRELESS[/B][/COLOR]
 I have included the outputs of [FONT=courier new]sudo lshw -C network, lspci, lsusb, ifconfig, iwconfig, lsmod, iwlist scan[/FONT] in the attached files.  One file has the outputs when the wireless connection is working and the other is for when it doesn't connect and repeatedly asks for the password.
[ATTACH]246714[/ATTACH]
[ATTACH]246713[/ATTACH]

 I haven't included the output of dmesg because it is huge, even after using [FONT=courier new]grep[/FONT].  Please let me know if needed.
[FONT=courier new]sudo /etc/init.d/networking restart[/FONT] stopped my network, but didn't restart it.  I couldn't get it to restart until I rebooted.
 
[COLOR=#ff8c00]**DESPERATE PLEA**[/COLOR]
 Can anyone help me please? My system is so close to being one that I can use as my everyday machine but obviously I can't continue with this wireless problem indefinitely.

---

### Post by wildmanne39 on 2013-10-03
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by peGGi on 2013-10-03
Hello,  I've attached the 'wireless-info.txt'.

At the point in time when I created it, the wireless was connected to the internet.  

Would you like me to do it when the Network Connections manager won't accept my password?  

And would it be a good idea to create another one during one of the 'dropouts'?

---

### Post by wildmanne39 on 2013-10-03
Your signal strength and link quality is low.

Please disable UFW temporarily and see if that helps.

Also please set your wireless settings to match the screenshots.

There was a bug with this driver and it may still be causing issues, I will look more into it tomorrow it is getting late here.

Did you leave the parameters enabled you mentioned in your post they do not apply to your driver only to the iwlwifi driver.
Thanks

---

### Post by peGGi on 2013-10-04
Hi again,

Thank you for helping me. 

Yes I left those parameters alone - didn't do the iwlwifi thing.

I disabled ufw and changed the wireless settings as per your screenshots, and I rebooted.  My settings don't have the 'Available to all users' option, although underneath the 'general' tab there is an option (which is selected) to 'enable this network for all users'.
[ATTACH=CONFIG]246731[/ATTACH]
[ATTACH=CONFIG]246732[/ATTACH]

The dropouts are still happening.  Actually they've been very frequent for the past 45min.  I was running a youtube video and a torrent download.  I tried to collect some 'wireless-info.txt' files during the dropouts (attached).  Dropouts still happening with torrent stopped.  
[ATTACH]246730[/ATTACH][ATTACH]246729[/ATTACH][ATTACH]246728[/ATTACH]

I haven't logged in and out a few times to check if the 'asking-for-password' problem is still happening.  I will do so and post another reply.

---

### Post by peGGi on 2013-10-05
I'm still having trouble logging-in.  Just spent 15 minutes logging in and out until it accepted the password and let me on to the wireless. 

Dropping out a lot too.  

Does anyone have any advice?  I'm beginning to despair!

---

### Post by The Spectre on 2013-10-05
A couple of other things to check and try.

Do you have the latest Firmware installed for your Router?
[http://support.netgear.com/product/wnr2200](http://support.netgear.com/product/wnr2200)

Have you tried setting the Router to operate on a different channel?

Maybe there are other devises in your area that are effecting the reliability the wireless single going to your Laptop.

I recently installed a new Netgear Wireless Router at my Uncles house and my Lenovo G560 Laptop would not connect to it when it was set to channel 11.

---

### Post by wildmanne39 on 2013-10-05
We are going to try some different drivers as an experiment, they are suppose to work with this device.

Please do:
```
sudo apt-get install linux-firmware-nonfree
```
watch for errors then do:
```
sudo modprobe -rv brcmsmac
sudo modprobe b43
```
Thanks

---

### Post by wmalam2 on 2014-04-11
I'm having the same symptoms in Xubuntu 13.10,  Kubuntu 13.10 and Mint, all with Network Manager. Couldn't get it to take the password in Mint. I just  swapped NM for WiCD in Xubuntu. King's X, so far. NM reported that the signal strength is low (not true). WiCD correctly reports excellent signal.

---

