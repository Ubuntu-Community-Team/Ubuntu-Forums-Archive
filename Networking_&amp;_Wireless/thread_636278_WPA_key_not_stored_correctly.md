---
title: "WPA key not stored correctly"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by viralbus on 2007-12-09
Hi,

I'm using Ubuntu 7.10, and I have a small problem with my wireless connection:

I'm using Sky's standard broadband (in the UK), which comes with a wireless router already set up, and it comes with an SSID and a network key consisting of 8 uppercase letters.

It works beautifully when I select the password type "WPA Personal".  However, every time I reboot, I need to configure my network again and reenter the network password.

The relevant bit from /etc/network/interfaces looks as follows:

iface ath0 inet dhcp
wpa-psk ea009e97304ad73733867d58a6a778433bfe0c485b165da2fbc788e7c9ca985d
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid SKY36647

The wpa-ssid is my SSID (and I never need to reenter that bit anyway). I'm wondering, however, what exactly has happened to the 8-letter network key I entered, and whether the problem is that it's stored in the wrong format.  Do I need to change the password type?  Or is there another way for me to store my netword password between sessions?

Thanks a lot,

Thomas

---

### Post by Manad on 2007-12-09
Your 8-character network key is still there, it's just encrypted, which is why it appears as a long hex string.

I had the same problem as you. For whatever reason, the network manager refuses to login to the network until I go sudo and reinput the key. I've tried both the Xubuntu and Kubuntu manager and it's the same. 

I solved it by installing WICD as my network manager. I don't think they really tested the distro network managers thoroughly.

---

