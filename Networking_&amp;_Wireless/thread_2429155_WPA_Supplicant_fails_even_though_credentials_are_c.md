---
title: "WPA_Supplicant fails even though credentials are correct."
date: 2019-10-14
forum: Networking &amp; Wireless
---

### Post by abasel on 2019-10-14
I have worked through the following tutorial [https://www.linuxbabe.com/command-line/ubuntu-server-16-04-wifi-wpa-supplicant]("https://www.linuxbabe.com/command-line/ubuntu-server-16-04-wifi-wpa-supplicant").

When I run the following:
> sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i wlp1s0

I get
> Successfully initialized wpa_supplicant
wlp1s0: SME: Trying to authenticate with 24:a4:3c:03:ee:72 (SSID='PrivateHotspot' freq=5785 MHz)
wlp1s0: Trying to associate with 24:a4:3c:03:ee:72 (SSID='PrivateHotspot' freq=5785 MHz)
wlp1s0: Associated with 24:a4:3c:03:ee:72
wlp1s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
wlp1s0: CTRL-EVENT-DISCONNECTED bssid=24:a4:3c:03:ee:72 reason=3 locally_generated=1
wlp1s0: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
wlp1s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="PrivateHotspot" auth_failures=1 duration=10 reason=WRONG_KEY
wlp1s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
nl80211: send_and_recv->nl_recvmsgs failed: -33


My wpa_supplicant.conf look as follows
> 
network={
        ssid="PrivateHotspot"
        #psk="Password!"
        psk=1safda0d495f96b8756a2acf24851af3fecb313531980596b821b176f15788e3
}

I have also tried the uncommenting the first "psk" and commenting out the second one i.e. using the unencrypted PSK.

The password is correct

Not sure where else to look or what to try.

---

### Post by abasel on 2019-10-15
My hardware is
 
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter
	Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter
	Physical Slot: 0
	Flags: bus master, fast devsel, latency 0, IRQ 41
	I/O ports at 2000 [size=256]
	Memory at f0b00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8821ae
	Kernel modules: rtl8821ae

---

### Post by abasel on 2019-10-15
Using dmesg I discovered that the connection was being deauthorised which on googling I found out was because the correct driver was not installed.

The solution for my card was found [here]("https://ubuntuforums.org/showthread.php?t=2398917")

i.e.

```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh
```

---

### Post by abasel on 2019-10-15
After all that I also discovered that I need to use netplan as discussed [here]("https://djanotes.blogspot.com/2018/03/connecting-to-wifi-network-with-netplan.html") and install network manager 

> sudo apt-get install network-manager

---

