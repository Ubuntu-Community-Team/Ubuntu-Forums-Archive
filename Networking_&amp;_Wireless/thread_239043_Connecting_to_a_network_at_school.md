---
title: "Connecting to a network at school"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by aglc2005 on 2006-08-18
Ok my school only supports Windows XP Service Pack 2 for wireless connections at school so I cannot get help from them and was wondering if anyone on here could help me out. These are the steps they give for connecting in windows.

1 Install your wireless card according to the manufacturers instructions.

2 Go to Control panel and then Network Connections.  You may need to click 5 on "Switch to Classic View".

3 Right Click on the connection labeled "Wireless Network Connection" and choose Properties.

4 Click on the tab labeled "Wireless Networks".  Make sure the box labeled "Use Windows to configure my wireless network settings:" is checked.  Then  click on the Add button under "Preferred Networks".

If your wireless card supports the Wi-Fi Protected Access (WPA) mode (Check with your manufacturer) follow the instructions for WPA.  If your wireless card does NOT support WPA or you are unsure follow the instructions for 802.1x.

_**WPA**_
   1. For "Network name (SSID):" fill in Stormwatch (This is case sensitive!).
   2. For "Network Authentication:" set it to WPA.
   3. Under "Data Encryption:" set it to TKIP.
[B][U]
802.1x[/U][/B]
1  For "Network name (SSID):" fill in Stormwatch (This is case sensitive!).
2 For "Network Authentication:" set it to OPEN.
3 Under "Data Encryption:" set it to WEP.
4 Make sure the box "The Key is provided for me automatically" is checked.

# The rest is for ALL cards

6 Click on the Authentication Tab.  Make sure "Enable IEEE 802.1x authentication for this network" is Checked (for WPA it will be selected and grayed out).  For "EAP Type" selected Protected EAP (PEAP).  Then uncheck "Authenticate as computer...".

7 Click the Properties button under "EAP Type".

8 Uncheck "Validate Server Certificate:".  Make sure "Select Authentication Method:" is set to Secured Password (EAP-MSCHAP v2) and uncheck "Enable Fast Reconnect".

9 Click the Configure... button under "Select Authentication Method:".

10 Uncheck the box for "Automatically use my Windows Logon..."

11 Click OK, OK, OK

12 Click OK and then reboot your computer.

13 After the reboot when you get to your desktop after a few seconds you should see a ballon pop-up on the bottom right asking for you to "Click here to select a certificate or other credentials for connection to the network Stormwatch".  Click on the ballon.

14 Fill out the "Enter Credentials" window with your email address for "User name:" and your password for "Password:".  Leave "Logon Domain:" blank.



I would really like to be able to use the wireless in Ubuntu and don't want to have to switch back to windows, so any help at all would be greatly appreciated.

---

### Post by groberts1980 on 2006-09-05
My school uses a similiar setup. I've heard xsupplicant will work with this, but I haven't tried it yet. Anybody?

---

### Post by Beliar on 2006-09-06
You can also use WPA Supplicant, I had a working config with gentoo, but I lost it when I installed Ubuntu x(

But the wpa_supplicant thats installed has no wpa_supplicant.conf
(see [http://www.ubuntuforums.org/showthread.php?t=248023)](http://www.ubuntuforums.org/showthread.php?t=248023)).

I tried to create one and call wpa supplicant manually, but the config is still not working. I am at school and I bootet windows to google around, I found something in the gentoo forums last year.

I'll tell you if I have found a solution.

greets,
Beliar

---

### Post by Beliar on 2006-09-06
Ok its working.

This is my wpa_supplicant.conf (int /etc/wpa_supplicant.conf), but this WLAN is different from yours! so dont copy ;)

[PHP]
ctrl_interface=/var/run/wpa_supplicant

network={
  ssid="TGM"
  scan_ssid=1
  key_mgmt=IEEE8021X
  eap=PEAP
  phase1="peaplabel=1"
  identity="user"
  password="pw"
  phase2="auth=MSCHAPV2"
}
[/PHP]

The Problem is, that you have to start wpa supplicant and dhclient yourself :(

sudo wpa_supplicant [-B for daemon mode, -d[d] for debug output] -Dwext -ieth1 -c/etc/wpa_supplicant.conf

sudo dhclient eth1

Youre config should look something like this:

[PHP]
ctrl_interface=/var/run/wpa_supplicant

network={
  ssid="Stormwatch"
  scan_ssid=1
  key_mgmt=WPA-EAP
  eap=PEAP
  group=TKIP
  pairwise=TKIP
  identity="user"
  password="pw"
  phase1="peaplabel=1"
  phase2="auth=MSCHAPV2"
}
[/PHP]

peaplabel can also be 0, I read that old Radius servers need that. 
So start wpa_supplicant with -dd and have a look, it will take awhile and some failed auth. Mine couldnt find an AP, but after some scans it found it, so dont worry.

I'm not quite sure with the WPA part, here we have just WEP and I never use WPA with PEAP. But try it and come back if you have problems

If somebody knows how to avoid starting wpa_supplicant and dhclient manually, please tell me!
At home I use the network manager applet, because there I have WPA PSK.
A combination would be nice.

greets, Belir

---

### Post by groberts1980 on 2006-09-22
I tried using that setup with the wpa_suppliant, no-go. dhpclient said it didn't find any networks or something.

Any other ideas on how to connect to a university wireless setup using peap authentication? It seems to me that a fair number of universities are using this system, and it'd really help if we could all connect using Ubuntu.

---

