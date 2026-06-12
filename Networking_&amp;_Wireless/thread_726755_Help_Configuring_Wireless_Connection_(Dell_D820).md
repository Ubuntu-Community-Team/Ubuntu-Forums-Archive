---
title: "Help Configuring Wireless Connection (Dell D820)"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by ilych on 2008-03-17
I am using Ubuntu 7.10, and the last line of 'lspci' on my Dell Latitude D820 is:
```
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) 
```

Following this documentation, [WifiDocs/Driver/bcm43xx/Gutsy]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy"), I successfully installed the firmware code.

I am having problems connecting to a wireless network. In **WinXP**, this network appears in the list of available wireless networks as, let's say, "College Network." Its configuration is as follows:
[INDENT]Network Authentication: WPA
Data encryption: AES
EAP type: Protected EAP (PEAP)
"Validate server certificate" is unchecked[/INDENT]
After it is configured, the wireless utility prompts me to input a username and password (e.g., username: bob; password: test), and after that is entered, the wireless network becomes functional.

In **Ubuntu**, I tried creating a 'New Wireless Network' with the following settings:
[INDENT]Network Name: College Network
Wireless Security: WPA2 Enterprise
EAP Method: PEAP
Key Type: TKIP
Phase2 Type: None (Default)
Identity: bob
Password: test
Anonymous Identity: (None)
Client Certificate File: (None)
CA Certificate File: (None)
Private Key File: (None)
Private Key Password: (None)[/INDENT]
But after hitting 'Connect', the connection stalls at 0%. Can someone help me configure this wireless network, perhaps based on my Windows settings?

Thanks for any help!

---

### Post by ilych on 2008-03-18
Can someone please help me out or point me in the right direction? Thanks again!

---

