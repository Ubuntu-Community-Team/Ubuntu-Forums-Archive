---
title: "Cannot connect when wirless router does not broadcast the SSID"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by OpenSourceHippo on 2007-06-18
I have a wireless router from work which is setup not to broadcast the SSID.
The connection is secured via WEP with a 128 bit hexadecimal key.

Ubuntu 7.04 will not connect to the router.
Since I’m a Linux newbie I simply entered the WEP key information etc. into the default GUI network tool.

The connection does work using Windows XP and Simply MEPIS.
Therefore the problem is not with the wireless card (which is Linux friendly without needing any drivers).

Searching your forums I found that this is a known issue with Ubuntu 7.04 and routers that don't broadcast the SSID.

In some posts users said that not broadcasting the SSID is stupid and not helping to secure the connection.
While I may agree with this argument, this does not help me, because the router belongs to my work and I can’t change its settings.

So I am looking for a way to allow Ubuntu to connect to my router without changing the router settings.
I have a feeling this is possible but not using the GUI tool I used so far.

Any help would be appreciated.

---

### Post by dardack on 2007-06-18
Uninstall network-manager and install wicd 1.2.9 wicd.sourceforge.net

works for me

(well that is when my wireless is working)

---

### Post by kevdog on 2007-06-18
Can you see the router??? 

Try this command:
iwlist *interface name* scanning

Substitute eth0, eth1 or wlan0 for interface name depending on your setup?

---

### Post by OpenSourceHippo on 2007-06-19
> **dardack said:**
> Uninstall network-manager and install wicd 1.2.9 wicd.sourceforge.net

works for me

(well that is when my wireless is working)

Thanks. I tried wicd 1.2.9 but this does not work for me. 

I click on the 'Hidden Network' button and enter the SSID of my router but this just brings me back to the list of networks unchanged. 

I can see two WEP networks without a name next to them. I tried putting my WEP key into them but neither connects. So I think my router doesn't actually appear in the list.

I also tried changing the settings in Preferences but nothing seems to work.

---

### Post by dardack on 2007-06-19
Did you at first uninstall network manager tho?  That was my issue when i first tried wicd.  Not saying it will work, i'm a newbie myself, but wicd works for me for both WEP/WPA and not broadcasting or broadcasting the id.

Also might want to check out:
[http://ubuntuforums.org/showthread.php?t=324545&highlight=essid+broadcast+disabled](http://ubuntuforums.org/showthread.php?t=324545&highlight=essid+broadcast+disabled)

I know it relates to WPA and not WEP, but it might help out.  It has something to do with setting a flag to AP_SCAN=2 or something.  (btw wicd can use wpa_suppliment or something, where NM can't, so don't know if that would help)

---

### Post by OpenSourceHippo on 2007-06-21
> **kevdog said:**
> Can you see the router??? 

Try this command:
iwlist *interface name* scanning

Substitute eth0, eth1 or wlan0 for interface name depending on your setup?

Thanks for the tip. I can see my router using iwlist:

```

eric@eric-desktop:~$ sudo iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:90:4C:7E:00:6E
                    ESSID:""
                    Mode:Master
                    Frequency:2.462 GHz
                    Signal level=37/100  
                    Encryption key:on
                    Extra:tsf=000000000681a189

```

But how do I connect to it?

---

### Post by OpenSourceHippo on 2007-06-21
> **dardack said:**
> Did you at first uninstall network manager tho?  That was my issue when i first tried wicd.  Not saying it will work, i'm a newbie myself, but wicd works for me for both WEP/WPA and not broadcasting or broadcasting the id.

Also might want to check out:
[http://ubuntuforums.org/showthread.php?t=324545&highlight=essid+broadcast+disabled](http://ubuntuforums.org/showthread.php?t=324545&highlight=essid+broadcast+disabled)

I know it relates to WPA and not WEP, but it might help out.  It has something to do with setting a flag to AP_SCAN=2 or something.  (btw wicd can use wpa_suppliment or something, where NM can't, so don't know if that would help)


Yes, I have uninstalled network manager before installing wicd. Wicd seems to recognize my router even though there is no SSID next to it. 

I also managed to get it to connect but it says "connected at 0%". Have you even seen that?
This is after I put a static IP address in the Advanced settings plus the WEP key.

Sadly, this still leaves me without an internet connection.

---

### Post by ForwardProgress on 2007-06-22
I am running into the same issue with a Gateway Laptop that has Wubi 7.04 installed under Vista.  I have a LinkSys wireless router and the laptop connects with non-broadcast SSID using WEP-128.

In network manager I did the following:

1) I first added a new wireless network.  Specifying the non-broadcast SSID and the WEP 128 key.

2) When I complete this I am still not connecting to the network.

3) When I go into the Network Manager drop-down top-right in my 'launcher bar' and select the wireless network connection I just added it appears to find my SSID because I get prompted to enter a security key for the SSID (even though I already configured it).

4) After I enter the key I get the signal strength bars up top but it appears with no signal indicated.  When I hover over the bars I get the same "Connected at (0%)" message displayed with no network connection.

This same laptop connects fine in Vista using the same WEP-128 key and SSID.  I have not tried switching my Router to broadcast the SSID and would prefer not to.

Any ideas or help would be greatly appreciated.

Thanks - Brian

---

### Post by ForwardProgress on 2007-06-23
At least now I am able to connect to a broadcast SSID.  I found out I didn't have the required BroadCom driver installed - I was faked out because it did seem to be detecting my network and requesting that I enter the WEP key.  But, I followed the instrauctions in [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)
and do now have wireless access - only with a broadcast SSID..

It appears the fact that the NetworkManager will not work with non-broadcast SSID is a known problem.  See [https://bugs.launchpad.net/baltix/+source/knetworkmanager/+bug/50214](https://bugs.launchpad.net/baltix/+source/knetworkmanager/+bug/50214).

For now, I will run with broadcast SSID and keep my eyes open for a bug fix.

Thanks - Brian

---

### Post by OpenSourceHippo on 2007-06-26
> **ForwardProgress said:**
> At least now I am able to connect to a broadcast SSID.  I found out I didn't have the required BroadCom driver installed - I was faked out because it did seem to be detecting my network and requesting that I enter the WEP key.  But, I followed the instrauctions in [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)
and do now have wireless access - only with a broadcast SSID..

It appears the fact that the NetworkManager will not work with non-broadcast SSID is a known problem.  See [https://bugs.launchpad.net/baltix/+source/knetworkmanager/+bug/50214](https://bugs.launchpad.net/baltix/+source/knetworkmanager/+bug/50214).

For now, I will run with broadcast SSID and keep my eyes open for a bug fix.

Thanks - Brian


Thanks for the information Brian. I think I will do the same - wait for a bug fix, i don't really want to recompile my kernel or look for a different one on the web.
In the meanwhile I am using Simply MEPIS which works out of the box. I might decide to stick with it and just upgrade to version 6.5.

---

### Post by OpenSourceHippo on 2007-06-26
> **ForwardProgress said:**
> At least now I am able to connect to a broadcast SSID.  I found out I didn't have the required BroadCom driver installed - I was faked out because it did seem to be detecting my network and requesting that I enter the WEP key.  But, I followed the instrauctions in [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)
and do now have wireless access - only with a broadcast SSID..

It appears the fact that the NetworkManager will not work with non-broadcast SSID is a known problem.  See [https://bugs.launchpad.net/baltix/+source/knetworkmanager/+bug/50214](https://bugs.launchpad.net/baltix/+source/knetworkmanager/+bug/50214).

For now, I will run with broadcast SSID and keep my eyes open for a bug fix.

Thanks - Brian


Thanks for the information Brian. I think I will do the same - wait for a bug fix, i don't really want to recompile my kernel or look for a different one on the web.
In the meanwhile I am using Simply MEPIS which works out of the box. I might decide to stick with it and just upgrade to version 6.5.

---

### Post by t4thfavor on 2007-06-26
#!/bin/bash
sudo iwconfig eth2 essid "Cloaked SSID In Quotes" key D24443F4E872556065AE2C7B6B3
sudo dhclient eth2

Works everytime for me.

---

