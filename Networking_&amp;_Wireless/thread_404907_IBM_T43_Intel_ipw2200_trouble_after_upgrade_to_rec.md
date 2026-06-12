---
title: "IBM T43 Intel ipw2200 trouble after upgrade to recent ubuntu?"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by HolyJoe on 2007-04-09
I cannot use my wireless after upgrade to the recent ubuntu release, but before upgrade my wireless device working correctly.

1. lsmod | grep ipw2200    output like this:
ipw2200               107308  0
ieee80211              37064  1 ipw2200

2. /etc/wpa_supplicant.conf like this:
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
        ssid="dlink-18201"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        #psk=imathome
psk=7215d6f065203b5834449b645ca1c4cec6d05fe71a4174665b30e669b67c5cb5
}

3. /etc/network/interfaces like this:
# This is file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface mapping
#mapping hotplug
#       script grep
#       map eth0

mapping eth0
        script guessnet-ifupdown
        map default: none
        map timeout: 10
        map verbose: true
        map inet-wired-office
        map inet-wired-jxboc
        map inet-wired-hotol

# The wired network at office
iface inet-wired-office inet static
        address 192.168.16.44
        netmask 255.255.255.0
        gateway 192.168.16.1
        dns-nameservers 127.0.0.1 192.168.0.250 218.2.135.1
        test peer address 192.168.16.1 mac 00:0F:E2:1E:8D:34

# The wired network at jxboc
iface inet-wired-jxboc inet static
        address 22.220.14.241
        netmask 255.255.248.0
        gateway 22.220.8.2
        dns-nameservers 127.0.0.1 22.220.1.30
        test peer address 22.220.8.2 mac 00:00:0C:07:AC:00

# The wired network at hotol
iface inet-wired-hotol inet static
        address 10.5.50.129
        netmask 255.255.255.0
        gateway 10.5.50.1
        broadcast 10.5.50.255
        dns-nameservers 127.0.0.1 10.5.50.1 202.101.224.69
        test peer address 10.5.50.1 mac 00:E0:4C:E3:B3:74
        broadcast 10.5.50.255
        dns-nameservers 127.0.0.1 10.5.50.1 202.101.224.69
        test peer address 10.5.50.1 mac 00:E0:4C:E3:B3:74

# The wireless network interface mapping
mapping eth1
        script guessnet-ifupdown
        map inet-wireless-home
        map inet-wireless-hotol

iface inet-wireless-home inet dhcp
        wireless-essid dlink-18201
        wireless-key s:imathome



#pre-up wpa_supplicant -Bw -Dwext -i eth1 -c /etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant

iface none inet dhcp

iface disconnected inet static
        test missing-cable

4. /etc/network/if-pre-up.d/wireless-tools like this:
#!/bin/sh

IWCONFIG=/sbin/iwconfig

if [ ! -x $IWCONFIG ]; then
  exit 0
fi


Problems:
1. why my /etc/network/if-pre-up.d/wireless-tools  has 'EOF' error?
2. how to detect wireless device actived?

---

### Post by msmalin on 2007-04-11
My wireless stopped working this morning after downloading and installing the new ubuntu updates.  If I remember correctly the updates were linux headers, which may have interfered with the wireless; I don't know.  I removed the ipw2200 driver and the ieee80211 software, then recompiled and reinstalled the newest versions of both, and I'm online again.  Here's the address of the ipw2200 driver site if you want to give this a shot:
[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

---

### Post by HolyJoe on 2007-04-13
Hi, msmalin.

Thank you for your reply. I'll try.

---

### Post by loicp on 2007-04-16
Hi,

I have a similar problem with latest feisty updates.
I can associate myself to an AP (channel 11, wep, dhcp), however only small sized packets are working (ping, dns requests, traceroute)

Everything else (web browsing, pop, imap) doesn't work, only a few websites are working randomly , like google. 

I thought it was a MTU issue, but after setting it to a lower value than 1500 it doesn't work better.

Have you similar symptoms ?

---

