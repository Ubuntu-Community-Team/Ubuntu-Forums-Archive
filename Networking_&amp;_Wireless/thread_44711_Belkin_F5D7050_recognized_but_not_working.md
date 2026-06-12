---
title: "Belkin F5D7050 recognized but not working"
date: 2005-06-27
forum: Networking &amp; Wireless
---

### Post by spanishwasabi on 2005-06-27
hi,

I've bought a Belkin f5d7050 from a friend.

I've plugged it in my system and the "networking" configuration tool does not seem to recognize it.

I did a quick iwconfig:
root@wasabi:~ # iwconfig sit0
sit0      no wireless extensions.

and I was surprised to see that it does not have wireless extension.

I then tried ifconfig on it:
root@wasabi:~ # ifconfig sit0 192.168.1.1
root@wasabi:~ # ifconfig sit0
sit0      Link encap:IPv6-in-IPv4
          inet addr:192.168.1.1  Mask:255.255.255.0
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          inet6 addr: ::192.168.0.3/96 Scope:Compat
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

The system recognizes the card though:
Bus 004 Device 001: ID 050d:7050 Belkin Components
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000


Do I have to install something or modify something to make it work?

I've seen people installing drivers, but as Ubuntu seems to recognize the driver, I don't know if it's necessary.

Any help or link is apreciated,

Thanks.

G

---

### Post by spanishwasabi on 2005-06-30
Anwering part of my question.

After this, my eth0 seemed to disapear.

When I was trying to insmod ipw2200 I had the fllowing error:
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt

When doing a find:
guille@wasabi:~$ find /lib -name "ipw2200*" -print
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ipw2200
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ipw2200/ipw2200.ko

I then removed the files ending in .ko as well as the ones ieee80211*.ko and
installed the driver again, but the problem seemed to not be resolved, even
with the reinstallation of the drivers and with the installation of the new
firmware.

I then realized some files where doubled. Indeed, when doing the
desinstallation of the driver some directories where not removed. Thos where
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ipw2200/ and
/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211/

I the did the uninstalling manually:
rm -rf /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ipw2200*
rm -rf /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211*
and I reinstalled the drivers.

ater a reboot it simply worked.

Now, I am trying to make work my card with ndiswrapper and the windows drivers.

I get a bit lost among so much information, sometimes contradictory...

To be followed.

G

---

### Post by spanishwasabi on 2005-07-01
Hi,

I eventually installed the card without problems.
For that, I had to ask a friend to install the drivers for me in one of his windows machines, but I managed it.

I then did a:

# ndiswrapper -i bknUSB.inf
ls: /etc/ndiswrapper: No such file or directory
Installing bknusb

# ndiswrapper -l
Installed ndis drivers:
bknusb  driver present, hardware present

# insmod ndiswrapper

# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:2 Mb/s
          RTS thr:2347 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:84/100  Signal level:-79 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:34  Invalid misc:2657   Missed beacon:0

# ndiswrapper -m 


Now, the problem is when I put the USB card, the eth0 becomes off power, and I don't know how to solve that.

Furthermore, I don't know how to put out the USB card without freezing the system. When I put it out, it's what happen, the system freezes.

Any ideas?

Thanks,

G

---

