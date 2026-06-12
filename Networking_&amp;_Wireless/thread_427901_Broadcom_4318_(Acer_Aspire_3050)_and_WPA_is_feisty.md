---
title: "Broadcom 4318 (Acer Aspire 3050) and WPA is feisty?"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by FooAtari on 2007-04-29
[COLOR="Black"]I am able to get wireless working with WEP or no encryption using [THIS]("http://ubuntuforums.org/showthread.php?t=340689") guide 

But I am unable to connect using WPA.  I know there is sticky at the top of the page and several posts about this but I am having little success, after much messing about I lost my wireless connection completely.  I have reinstalled to clean up the mess I created...

The closest I have come to getting this working is the guide above and then performing the steps [HERE]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-fe1ec89e4caea9768f41bf6c7bd9c52d29dbec9d")

I am able to see all wireless networks in range but when I enter my WPA code it tries to connect for a long time but eventually fails.  Im entering the password in Ascii.  Any ideas why its not connecting? Or is there a nother method I should be using?[/COLOR]

---

### Post by pleurastic on 2007-05-07
Here's my atheros chipset interfaces file before feisty.

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


auto ath0
iface ath0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid **************
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk ***************************
wireless-essid ****************
<done>
After feisty I had to comment out the line "wpa-conf managed".  Good luck.

---

### Post by FooAtari on 2007-05-08
Hmmm, I'll give that a go.

I reinstalled XP to get my wireless working again, but I am going to dual boot to try and get linux working....

---

### Post by Derspankster on 2007-05-09
> **FooAtari said:**
> Hmmm, I'll give that a go.

I reinstalled XP to get my wireless working again, but I am going to dual boot to try and get linux working....
I have WPA working with Feisty but I usually have a tough time connecting. Eventually, I can connect but it may take 5-6 tries to make it happen.  I use WPA TKIP and SSID.  I've read that connecting improves by disabling SSID. I don't want to do that, however. I am interested in wireless security. I have a workstation (wife's XP machine)  and another laptop (Mac) connecting via wireless here at the house. My main Feisty workstation is wired to the router. 

I haven't read anything anywhere yet that improves the reliability of my connection. Best bet is to read all you can find in this forum and elsewhere. Wireless connectivity, especially with the Broadcom chip is a major Ubuntu issue.  It will be resolved, have faith.

---

