---
title: "WPA gone downhill"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by neko on 2005-11-18
Hi,

I have a Dell laptop with a Broadcom wireless card.  Until yesterday I was using Fedora Core 1 with ndiswrapper and wpa_supplicant.  It worked perfectly.  I could associate with my acces point in about 2 seconds.

Yesterday I installed Ubuntu 5.10, since it has had so many positive writeups.  The install went easily enough..... until I tried getting my wireless access going.

ndiswrapper is installed and appears to be fine.  I also installed the wpasupplicant package.

My wireless card is detected when I run the System->Administration->Networking app.  When I try to activate the wireless connection, it takes about 2 minutes before it returns, saying the interface is now active.

Running iwconfig *sometimes* displays the mac address of my AP.  Sometimes it does not.  Haven't figured out why this is.  The routing table is empty.  ifconfig shows that my wlan0 interface does not have a inet addr.  wpa_cli cannot connect to wpa_supplicant (even though it is running).

There have been many helpful people posting their configs to various forums.  The problem is they're all slightly different.  The one that looks "official" in this forum didn't really help either.


So here's what I've got:

cat /etc/wpa_supplicant.conf:

[FONT="Fixedsys"]
ctrl_interface=/var/run/wpa_supplicant # for wpa_cli support
ap_scan=2

network={
  ssid="MySSID"
  psk="MyPSK"
  key_mgmt=WPA-PSK
  group=TKIP
  proto=WPA
  pairwise=TKIP
}
[/FONT]

This is what I had with FC1 installed, it worked a treat.  (By the way, the configuration of my AP has not been changed).

cat /etc/network/interfaces:

[FONT="Fixedsys"]
auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
pre-up modprobe ndiswrapper || true
pre-up /usr/local/bin/wpa_supplicant -Dndiswrapper -Bw -i$IFACE -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
wireless-essid dekinet
gateway=192.168.1.1
#name Wireless LAN card
#netmask=255.255.255.0
#network 192.168.1.0
#broadcast 192.168.1.255
dns-nameservers 10.0.0.138
[/FONT]


and /etc/default/wpasupplicant has:

[FONT="Fixedsys"]
ENABLED=1
OPTIONS="-w -D ndiswrapper -B -i wlan0 -c /etc/wpa_supplicant.conf"
[/FONT]


So I guess my questions are:

[LIST=1]
[*]Why is it taking so long to associate?
[*]Am I actually associating if I don't get an IP address from my DHCP server?
[*]Is there actually an "official" configuration that is recommended by the Ubuntu people?
[/LIST]



thanks for any advice!

---

### Post by christianbrahms on 2005-11-19
Hi,

I don't use ndiswrapper but ipw since I've got a Centrino laptop... I needed some testing, too when switching from Mandrake to Kubuntu...

Try the following steps and report back the Output (if any) here, maybe that helps...

When the card is ready (detected, radio kill-switch off, the driver running etc.) do:

/etc/init.d/wpasupplicant restart
this shouldn't print anything I guess... After that, try

dhclient wlan0
this will try to get an IP address from the DHCP server... This will probably print some output if it doesn't work. 

Good Luck
Christian

---

### Post by neko on 2005-11-21
[QUOTE=christianbrahms]Hi,

I don't use ndiswrapper but ipw since I've got a Centrino laptop... I needed some testing, too when switching from Mandrake to Kubuntu...

Try the following steps and report back the Output (if any) here, maybe that helps...

When the card is ready (detected, radio kill-switch off, the driver running etc.) do:

/etc/init.d/wpasupplicant restart
this shouldn't print anything I guess... After that, try

dhclient wlan0
this will try to get an IP address from the DHCP server... This will probably print some output if it doesn't work. 

Good Luck
Christian[/QUOTE]

Thanks for the advice Christian.  Somehow I've managed to get it working :confused: .  Not sure really what I did.....  I did have "wireless-essid" instead of "wireless_essid" in my /etc/network/interfaces file.  However, fixing that did not make it magically spring to life.  Several reboots later it did magically spring to life, though.

---

### Post by vivedekananda on 2005-11-22
Neko, I am just guessing here, but I think that the problem was that because
you had "wireless-essid" in you config file, the essid of your network was not
associated with your wlan0 interface and it was trying to find
a wireless network essid to associate with automaticaly?

Anyway if you want to investigate this further you might want to
run wpa_supplicant (kill the old wpa_supplicant after the boot up) manualy without the "-B" option and take a look at the output.

Try to set "ap_scan=1", I dont know what "2" does but but "1" lets wpa_supplicant scan for access points, "0" ndiswrapper scans.

---

