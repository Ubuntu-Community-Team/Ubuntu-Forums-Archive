---
title: "Effectively disable one of two Wi-Fi cards?"
date: 2024-07-05
forum: Networking &amp; Wireless
---

### Post by &amp;KyT$0P# on 2024-07-05
Using Xubuntu 22.04 on a desktop computer with two Wi-Fi+Bluetooth cards (one built in, the other is PCIe).  I would like to (primarily) use the PCIe card for Wi-Fi and the built-in card for Bluetooth, and disable other wireless functionality when not in use.

For Bluetooth this is workable after backporting blueman 2.4.2.  Having trouble doing this with Wi-Fi.

Tried to soft-block the individual unused Wi-Fi device with [FONT=monospace]rfkill[/FONT] in Terminal, but turns out NetworkManager treats this state as if all Wi-Fi radios were soft-blocked, and [there is no way to work around it]("https://gitlab.freedesktop.org/NetworkManager/NetworkManager/-/issues/76").

While investigating I ran the [wireless-info script]("https://github.com/UbuntuForums/wireless-info") (not posting the full result because it contains quite a bit of personal information - not just my personal info about my system/network, but also neighbors' real names).  The [FONT=monospace]wireless-info.txt[/FONT] shows both of my Wi-Fi devices use the [FONT=monospace]iwlwifi[/FONT] kernel module, so [FONT=monospace]blacklist[/FONT]ing a kernel module isn't an option.

Another idea that came up in search is to set the unused Wi-Fi card as unmanaged in NetworkManager.  If I do that, would the card do nothing unless I explicitly use it (i.e. not transmit or receive anything, not adding Wi-Fi noise in the proximity of my other card)?

---

### Post by #&amp;thj^% on 2024-07-05
This is most likely not the most elegant suggestion, but my effort to help.
To see a List of devices using ip link:
```

ip link

```
Then disable your choice:
```
ip link set <DEVICE> down
```
If needed again:
```
ip link set <DEVICE>  up
```
I'll use an "alias" to ease this method.
```
ip link|grep wlp4s0
4: wlp4s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop[COLOR="#FF0000"] state DOWN mode DEFAULT [/COLOR]group default qlen 1000

```
EDIT:
```
 sudo ip link set wlp4s0 up
[sudo] password for me: 
RTNETLINK answers: Operation not possible due to RF-kill

```

---

### Post by &amp;KyT$0P# on 2024-07-05
Thanks 1fallen!  After running [FONT=monospace]sudo ip link set wlo1 down[/FONT], the interface shows as "disconnected" in NetworkManager, and [FONT=monospace]ip a[/FONT] gives
```
wlo1: <BROADCAST,MULTICAST> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether xx:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff permaddr xx:xx:xx:xx:xx:xx
```
And I still have connection on the other Wi-Fi card.  Seems promising :)

However, NetworkManager brings it back up when for example running
```
nmcli dev wifi list --rescan yes
```

Looks like I'll need to **both** do [FONT=monospace]sudo ip link set wlo1 down[/FONT] (to have the Wi-Fi card do nothing when unused) **and** set it unmanaged in NetworkManager (so that NetworkManager won't bring it up when I'm trying to do stuff with the other Wi-Fi card).

---

### Post by #&amp;thj^% on 2024-07-05
How weird, mine won't do that on a rescan:
```
nmcli dev wifi list --rescan yes
IN-USE  BSSID  SSID  MODE  CHAN  RATE  SIGNAL  BARS  SECURITY 

```
but still shows:
```
 ip link|grep wlp4s0
4: wlp4s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop[COLOR="#FF0000"] state DOWN[/COLOR] mode DEFAULT group default qlen 1000

```
I also use rfkill:
```
 rfkill list|grep -e Wireless -e "Soft blocked"
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Soft blocked: no
	Soft blocked: no
	Soft blocked: no
4: phy0: Wireless LAN
	Soft blocked: yes

```

---

### Post by &amp;KyT$0P# on 2024-07-05
So to implement this solution, I created a systemd template service [FONT=monospace]/etc/systemd/system/set-network-interface-down@.service[/FONT] -
```
[Unit]
Description=Set network interface %i down
After=network-pre.target network.target NetworkManager.service sys-subsystem-net-devices-%i.device

[Service]
ExecStart=/usr/bin/ip link set %i down

[Install]
WantedBy=multi-user.target
```

Then enabled it for the interface -
```
sudo systemctl enable set-network-interface-down@wlo1
```

Then created [FONT=monospace]/etc/NetworkManager/conf.d/custom-unmanaged.conf[/FONT] with the following contents -
```
[device]
match-device=mac:xx:xx:xx:xx:xx:xx
managed=false
```
(of course using the actual permanent MAC address copy-pasted from [FONT=monospace]ip a[/FONT] output)

After rebooting, [FONT=monospace]ip a[/FONT] shows the interface down and this time it stays down when running the above nmcli command.

And when I want to temporarily use the second Wi-Fi card, can re-enable it with
```
nmcli dev set wlo1 managed yes
```

Thanks again 1fallen for the solution :KS

---

### Post by #&amp;thj^% on 2024-07-05
You did the work, I just offered a suggestion.

Nicely Done halogen2

---

