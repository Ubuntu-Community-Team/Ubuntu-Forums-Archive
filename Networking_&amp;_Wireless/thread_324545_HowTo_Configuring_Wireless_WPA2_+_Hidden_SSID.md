---
title: "HowTo: Configuring Wireless WPA2 + Hidden SSID"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by SugarDaddy on 2006-12-23
[FONT=Tahoma]First off, thanks to [**[COLOR=Sienna]luca_linux[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=263136") [/FONT][FONT=Tahoma] :) for getting me started. Check out luca_linux's [/FONT][**[COLOR=Sienna]HowTo: WPA with wpa_supplicant[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=263136")[FONT=Tahoma] post for installing wpa_supplicant and setting up /etc/network/interfaces file. I am creating this post to help those who are struggling to set up wpa_supplicant.conf for the following security settings in Edgy Eft:

[/FONT]1. ESSID broadcast disabled
[FONT=Tahoma]2. WPA2 Personal AES or TKIP+AES encryption

I am running a Dell Inspiron 600m with an Intel Pro/Wireless 2200 WiFi card that is connecting to a Linksys WRT54GL v3.0 with Firmware Update v4.30.5. Note that I did not have to use ndiswrapper because the default driver ipw2200 works fine.

First, when SSID broadcast is disabled on your router, the AP_SCAN=2 within the /etc/wpa_supplicant.conf file must be set. The default setting is AP_SCAN=0 (e.g. if it's commented out with #) and the WiFi card will not look for hidden SSIDs. However, when AP_SCAN=2, the security policy for the key_mgmt, pairwise, group, and proto variables must be explicitly set (i.e. only one option in the lists) in each network block. A complete description of the variables within the configuration file is found in the following link, the second being a detailed description:

[/FONT][COLOR=Sienna][URL="http://hostap.epitest.fi/wpa_supplicant/"][B]http://hostap.epitest.fi/wpa_supplicant/
[/B][/URL] [URL="http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain"][B]http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain
[/B][/URL] [/COLOR]
In the second link above you will find that the proto variable must be set to RSN for WPA2 encryption. And you need to make sure that this is the only variable in the list i.e. delete WPA or any others you might have. The other variables need to be set to CCMP (for AES) or TKIP (for TKIP+AES) only i.e. delete one or the other, don't include both. Below is my wpa_supplicant.conf file as an example where I am using TKIP+AES in my router encryption. If TKIP doesn't work for you or gives a slow connection, try CCMP. Thanks to Weiman01 for pointing out the difference between CCMP and TKIP. Note however, that I have note tested the AES encryption with the CCMP setting.

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
    ssid="yours here, I prefer ASCII in quotes vs hexadecimal"
    scan_ssid=1
    proto=RSN
    key_mgmt=WPA-PSK
    group=TKIP
    pairwise=TKIP
    psk="yours here, again I prefer ASCII keys in quotes"
}
```It wasn't until I set AP_SCAN=2 and explicitly set my security settings by deleting out the other variables in the lists that I got my WiFi card to work. Also, I am running dhcp versus a static ip configuration in my interfaces file:

```
auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```Anyway, hope this helps!

---

### Post by wieman01 on 2006-12-24
TKIP stands for WPA1, not WPA1. AES (CCMP) is the correct encryption algorithm that you ought to use.
> group=CCMP
pairwise=CCMP

---

### Post by SugarDaddy on 2006-12-24
>  I am running a Dell Inspiron 600m with an Intel Pro/Wireless 2200 WiFi card that is connecting to a Linksys WRT54GL v3.0 with Firmware Update v4.30.5.Even though the security settings in the router indicate WPA2 with TKIP+AES, the CCMP setting has a speed reminiscent of the days of baud, so something is clearly afoot. To be sure, I am far from finished hacking at my network connections because I connect to multiple APs (home, work, hotels, etc.) as well as wired connections. But the main thrust of my thread was to let people know how I got my card working and:

1. The importance of AP_SCAN=2 for hidden SSIDs
2. Exclusive security settings when AP_SCAN=2

None of the threads on this forum are clear on these two points until I read the sample configuration file at;

[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain](http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain)

But I am starting to feel ubuntu is not for me since it seems that you gotta be wireless techie as well with the almost endless list of TLAs that remind me of the acronym PCMCIA==people can't memorize computer industry acronyms.

---

### Post by wieman01 on 2006-12-25
> **SugarDaddy said:**
> But I am starting to feel ubuntu is not for me since it seems that you gotta be wireless techie as well with the almost endless list of TLAs that remind me of the acronym PCMCIA==people can't memorize computer industry acronyms.
You're right in that Ubuntu is not perfect, in particular in this respect. I was a bit confused & fairly annoyed in the beginning as well, but once you have understood the concept it's less difficult than it appears. Other operating systems do a better job as they hide the complexity from the users. Sadly Ubuntu requires you to put up with command line for the time being, especially if you want to hide network ID. 

As far as hidden ESSID is concerned, please also take a look at the howto in my signature. Don't want to hijack your HOWTO (it's clear & easy to follow), but this howto also specifically mentions "hidden ESSID". Let me know what you think. Further in the back of the thread there is also mention of a "new network manager" that has been developed by a user of this forum. It might be the right tool for you.

---

### Post by SugarDaddy on 2006-12-26
Weiman01,

I looked at your HowTo when I first began researching how to set up my WiFi but found it irrelevant for my needs for the following reasons:

1. It starts out leading users to think they need a long list of requirements like MAC filtering turned off, ndiswrapper, etc, which I felt immediately ruled me out and began searching other threads. As I mentioned in my original post I do not use ndiswrapper and I have MAC Address Filtering enabled on my router.

2. It leads users into thinking that configuring wpa_supplicant in the /etc/network/interfaces file is sufficient versus network blocks in the wpa_supplicant.conf file. While for the average user who only logs onto a single router this may be OK, for more mobile users who log onto multiple APs (home, office, school, hotels, etc.), they will need to configure individual network blocks for each AP using the priority flag in the network block.

3. While it does mention that ap_scan=2 needs to be set for hidden SSID there is no mention of explicit security settings in the variable lists which some of your examples contain. You might want to update your HowTo to reflect this fact as I have found this to be a major stumbling block.

4. I prefer [luca_linux]("http://ubuntuforums.org/showthread.php?t=263136")'s post because it gives command lines on using the -dd flag to debug wpa_supplicant which I found crucial to getting my WiFi to connect (e.g. incorrect SSID, WPA-PSK key, etc.):

```
sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd

```But, bottomline, I have yet to find a thread sufficient in documenting how to fully configure the network devices to allow for connecting to wired APs, secure SSIDs, unsecure SSIDs, etc., i.e. an ALL-IN-ONE setup vs single purpose. If you know of any thread, please post a reply.

---

### Post by SugarDaddy on 2006-12-26
Weiman01, I have updated my original thread per your first reply on the correct settings for AES=CCMP. I haven't had a chance to test yet (I am still using TKIP+AES in my router), but I will change the setting to AES only soon, test with CCMP and post the results. As noted above TKIP+AES does not seem to work properly with CCMP. It could be that the Intel Pro/Wireless 2200BG doesn't support AES encryption. Should know soon.

---

### Post by wieman01 on 2006-12-26
IPW2200 does support AES, however, I don't know what firmware version you have got. But I am using it on a IPW2200, so I am sure it's no problem.

As for the improvements you have proposed, I will take them seriously. I know that the documentation is far from perfect. What would you change right away & which section should be revised & how? Will incorporate your comments immediately... Thanks a lot for the discussion.

---

### Post by SugarDaddy on 2006-12-26
Some minor suggestions with the last two probably pointless:

1. Does MAC Address Filtering really need to be disabled? I found that this wasn't the case for me, and I prefer the added security MAC Address Filtering provides.
2. Explicit security settings for ap_scan=2.
3. Some debugging commands to help users who obviously have to choose among the setups suggested and may not get it right the first time, I know I didn't!
4. Some links to the wpa_supplicant site that can provide more detailed information for the more savvy/curious among us.
5. Perhaps some links to threads on how to configure wpa_supplicant within the wpa_supplicant.conf file versus the /etc/network/interfaces.

Anyway, I know it's hard to find a one-size-fits-all approach for a HowTo, so feel free to use or ignore my suggestions as you feel fit. Thanks for the discussion.

---

### Post by wieman01 on 2006-12-26
Ok, I'll try to be a bit more explicit. Disabling MAC filtering was mentioned as very often people cannot connect to their local networks because of it. No more, no less. I have MAC filtering enabled, but had it disabled in the first place to eliminate a potential source of trouble. It works fine now.

I'll think about your comments and update the guide in the next few days. I guess it needs an overhaul anyway as it started off as a WPA2 guide. It has been enhanced since.

---

### Post by SugarDaddy on 2006-12-26
I had to reinstall Ubuntu 6.10 after screwing something up (unrelated to this forum). However, this time after my FRESH install I decided to ONLY install wpa_supplicant (i.e. no network manager, connection manager, ndiswrapper, windows drivers, wifi radar, etc) because I noticed that my WiFi card was hitchhiking on a unsecured network during the install and after reboot. Amazingly I connected just fine in CCMP mode (after changing my router's WPA2 PSK encryption setting to AES only vs TKIP+AES previously) with TKIP in the list as well. Therefore, the exclusive security setting under ap_scan=2 only seems to be an issue when network manager is installed concurrently?

Also, I was able to leave all other references in the /etc/network/interfaces uncommented, which in the past I had to comment out the reference to my Broadcom ethernet card (eth0). Below are the current settings for my wpa_supplicant.conf file and /etc/network/interfaces file, in that order:

```
ctrl_interface=/var/run/wpa_supplicant 
ap_scan=2 
 
network={ 
    ssid=<removed> 
    scan_ssid=1 
    proto=RSN 
    key_mgmt=WPA-PSK 
    group=CCMP TKIP 
    pairwise=CCMP TKIP 
    psk=<removed> 
}
``````
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf 
post-down killall -q wpa_supplicant
```This is quite encouraging because I feel I am closer to configuring for my multiple APs solution than I was previously.

I will post an update to this to this once I have an opportunity to fully configure my APs for wired and wireless because complete mobility is my number one priority rather than single purpose solutions.

---

### Post by wieman01 on 2006-12-27
How do you use this to configure multiple APs then? Would you put related information in one single file (e.g. "/etc/wpa_supplicant.conf")? What about global information in that case (i.e. ap_scan=2)?

Would be cool to know since I own a laptop PC as well.

---

### Post by SugarDaddy on 2006-12-27
I have successfully configured multiple APs using wpa_supplicant and tested the results. Rather than posting what I did here, I have created a new post.

[URL="http://ubuntuforums.org/showthread.php?p=1938086"]http://ubuntuforums.org/showthread.php?p=1938086
[/URL]

---

