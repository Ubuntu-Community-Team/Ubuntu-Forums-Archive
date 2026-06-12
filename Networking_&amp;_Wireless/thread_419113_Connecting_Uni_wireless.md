---
title: "Connecting Uni wireless"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by cyran on 2007-04-22
From what I could gather from searching, I'll need to use the wpa_supplicant program instead of the simple 'Network Manager' that came with Feisty in order to use the network here. The settings that the program on Windows used was:
> 
SSID: school_802.1x
Connection type: Infrastructure
Wireless mode: Auto

Wireless Security type: IEEE 802.1x
Access point authentication: Open

Data encryption: WEP
EAP type: PEAP
Tunneled authentication: Authentication protocol: GTC

Validate server certificate: No


Now from what I could gather from the examples I could find thanks to Professor Google (not many people use GTC compared to "MS-CHAP-V2", do they?), I'm supposed to make a .conf file that looks like this:

> 
ctrl_interface=/var/run/wpa_supplicant
# ctrl_interface_group=0
# eapol_version=1
# ap_scan=1
fast_reauth=1

network={
        ssid="school_802.1x"
        mode: 0                # 0: Infrastructure
        auth_alg: OPEN
        key_mgmt=IEEE8021X     
        eap=PEAP          
        identity="user"    
        password="pass"        
        phase2="auth=GTC"    
}


My main question is can I save this as a file in my home directory instead of in /etc/wpa_supplicant? Since it's going to contain my username and password, I'd think it should be tied to my account on the computer.

Then, how do I set up wpa_supplicant with a GUI / applet?

And since I know i have to use a phase2 in the configuration file, do I still need an explicit phase1?


My school is ridiculously unsupportive of alternative operating systems, so I haven't managed to find anyone who knows anything about this stuff on the tech help team.

---

### Post by spd106 on 2007-04-23
Yes you can put the conf file wherever you like as long as you make sure it's secured. It should only be accessed with root privileges so it kinda make more sense to put it with the other wpa files under /etc.

I suggest you check out the wpa_supplicant website for such an advanced configuration. It is possible to have more than one network defined in the wpa_supplicant.conf and it will connect to the first one it finds. You can then just use the old ifup/down commands.

There are other GUI based apps out there, wifi-radar, Wicd etc. Maybe give one of them a try.

I haven't any real world experience with 2 phase networks so I can't answer you last question.

---

