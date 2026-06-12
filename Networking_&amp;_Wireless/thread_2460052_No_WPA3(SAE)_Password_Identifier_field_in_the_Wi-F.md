---
title: "No WPA3(SAE) Password Identifier field in the Wi-Fi manager"
date: 2021-04-01
forum: Networking &amp; Wireless
---

### Post by darkingdoom on 2021-04-01
[COLOR=#000000][FONT=&amp]Hey,[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]The latest WPA3(SAE Dragonfly)[802.11-2016, section 12.4] standard defines Password Identifiers as a way to tell the access point (AP) which password is being used, this allows for a single SSID to support multiple passwords, but when I tried to connect to WPA3 AP I was asked only for the password.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]In the Wi-Fi supplicant there is an option for [COLOR=#3C4043][FONT=Roboto]"Password Identifiers" [search for "sae_password_id" in [/FONT][/COLOR][LINK]("https://w1.fi/cgit/hostap/plain/wpa_supplicant/wpa_supplicant.conf")[COLOR=#3C4043][FONT=Roboto]] 
[/FONT][/COLOR]Quote from the Link:
"
[FONT=Verdana]# sae_password_id: SAE password identifier
[/FONT][/FONT][/COLOR]
# This parameter can be used to set an identifier for the SAE password. By
# default, no such identifier is used. If set, the specified identifier value
# is used by the other peer to select which password to use for authentication.
"[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]So my question is where I can find the "Password Identifier" field in order to specify to the AP which password I am using ? since no such option in the Wi-Fi manager

System Settings:
[/FONT][/COLOR]No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04 LTS
Release:	20.04
Codename:	focal

Linux wallet 5.8.0-48-generic #54~20.04.1-Ubuntu SMP Sat Mar 20 13:40:25 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

Wi-Fi card: Intel 6 AX200





[COLOR=#000000][FONT=&amp]
Image for the Wi-Fi manager in WPA3 settings:

[/FONT][/COLOR][IMG]https://i.ibb.co/rM6GB7c/wpa3-pwd-id.png[/IMG][COLOR=#000000][FONT=&amp]

[/FONT][/COLOR]

---

### Post by darkingdoom on 2021-04-02
Any suggestions ?

---

### Post by chili555 on 2021-04-03
> The latest WPA3(SAE Dragonfly)[802.11-2016, section 12.4] standard defines Password Identifiers as a way to tell the access point (AP) which password is being used, this allows for a single SSID to support multiple passwords, but when I tried to connect to WPA3 AP I was asked only for the password.I don't believe that this feature yet exists in Ubuntu's Network Manager. I suggest that you file a bug report. [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

In any case, when you supply the password, do you connect as expected?

---

### Post by darkingdoom on 2021-04-03
Hey,
I will file a bug,
If I supply the default password that is mapped to the "null" password identifier(This password is defined on the AP without password identifier) it will connect

---

