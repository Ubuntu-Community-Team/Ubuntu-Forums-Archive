---
title: "Ubuntu WiFi not working with WPA Authentication - intermittent connection"
date: 2015-04-02
forum: Networking &amp; Wireless
---

### Post by robertzito on 2015-04-02
I am learning Ubuntu and Linux s I go along and I am seeing ton's of questions and answers with WiFi and WPA. There are so many post that I do not know which applies to me! 

I recently upgraded my service through my provider and was given a new modem with built in router. The router security mode is set at "WPA2-PSK (AES)" and I am running Ubuntu 14.04 on my Dell 17R and when I connect to my WiFi using "WPA2-PSK (AES)" I am able to connect to the internet for maybe minute or so right after reboot. 

But the odd part is that there are times I am able to connect to the router running WPA2-PSK (AES) and stay connected for the duration of my session and times I can not. 

Here is the info I was able to find when I connect to using my old router with WEP security..

[SIZE=2]**Network Controller**[/SIZE]

01:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d0500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi

[SIZE=2]**wpa:**[/SIZE]

eth0      no wpa key information.


lo        no wpa key information.


wlan0     2 key sizes : 40, 104bits
          4 keys available :
Error reading wpa keys (SIOCGIWENCODEEXT): Operation not supported







Is there any other information I can post to assist in helping isolate and correct why I am unable to connect to my router when using WPA2-PSK (AES) security mode, if I set the security mode to none on the router I connect with no issues.

Where I am getting confused is why would it work for the first couple of minutes? But after that I am no longer able to connect to any of my netwrok devices or the internet. If I go ahead and connect to my old SSIS that is using WEP there is no issue, when I attempt to switch back, I get the message unable to connect to the SSID.


The other thing I just noticed is that when I am locked up to the new router using that is using WPA2 is that can not connect to my work network through VPN (Cisco Anyconnect), it is only when I switch back to the older router running WEP that VPN will work.

---

