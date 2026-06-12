---
title: "wireless.info.text results. Red highlighted entries."
date: 2017-12-16
forum: Networking &amp; Wireless
---

### Post by pointy2 on 2017-12-16
WiFi went away immediately after update.

What do the red highlighted entries mean on this recent scan?  The questionable results are highlighted BOLD.

SSID                    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
McDonalds Free WiFi     <MAC 'McDonalds Free WiFi' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
eBOS                    <MAC 'eBOS' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
--                      <MAC **'\00**' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
McDonalds Free WiFi     <MAC 'McDonalds Free WiFi' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  --           no        
McDonalds Free WiFi_5G  <MAC 'McDonalds Free WiFi_5G' [AC13]>  Infra  149   5745 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  --           no        
attwifi                 <MAC 'attwifi' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  81      &#9602;&#9604;&#9606;&#9608;  --           yes     * 
--                      <MAC '' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2         no        
USCC-MF975U-8FD7        <MAC 'USCC-MF975U-8FD7' [AN8]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2    no        
attwifi                 <MAC 'attwifi' [AC15]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
BIG_STOP_wifi           <MAC 'BIG_STOP_wifi' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
NewportOTR-Guest WiFi   <MAC 'NewportOTR-Guest WiFi' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  --           no        
Rhfoster-BYOD           <MAC 'Rhfoster-BYOD' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2    no        
RHFoster                <MAC 'RHFoster' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2    no        
--                     ** <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00**' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  WPA2 802.1X  no        
WHOPPERWIFI             <MAC 'WHOPPERWIFI' [AC14]>  Infra  1     2412 MHz  54 Mbit/s  22      &#9602;___  --           no        
witech2                 <MAC 'witech2' [AC8]>  Infra  1     2412 MHz  54 Mbit/s  14      &#9602;___  WPA1         no        

....and

...........Cell 05 - Address: <MAC **'\00**' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a0ee845132
                    Extra: Last beacon: 856ms ago
          Cell 06 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00**'** [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:[COLOR=#b22222]"[/COLOR][COLOR=#000000]\x**00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00**"[/COLOR][COLOR=#b22222][/COLOR]
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000317363e8006
                    Extra: Last beacon: 828ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x

The full report is here ..... 
       [ https://paste.ubuntu.com/26197624/]("https://paste.ubuntu.com/26197624/")

I'd like to fix this once and for all, as it seems to be a recurring problem with disappearing wifi.

---

### Post by chili555 on 2017-12-16
Why would you surmise that the highlighted scan result has anything to do whatever with your dropping wireless??

Let's have a look at the scan results which are redacted for security purposes in the wireless info:```
SSID                    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
McDonalds Free WiFi     <MAC 'McDonalds Free WiFi' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
eBOS                    <MAC 'eBOS' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
--                      <MAC '\00' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --           no        
McDonalds Free WiFi     <MAC 'McDonalds Free WiFi' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  --           no        
McDonalds Free WiFi_5G  <MAC 'McDonalds Free WiFi_5G' [AC13]>  Infra  149   5745 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  --           no        
[COLOR="#FF0000"]attwifi                 <MAC 'attwifi' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  81      &#9602;&#9604;&#9606;&#9608;  --           yes     * [/COLOR]
--                      <MAC '' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2         no        
USCC-MF975U-8FD7        <MAC 'USCC-MF975U-8FD7' [AN8]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2    no        
attwifi                 <MAC 'attwifi' [AC15]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
BIG_STOP_wifi           <MAC 'BIG_STOP_wifi' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  --           no        
NewportOTR-Guest WiFi   <MAC 'NewportOTR-Guest WiFi' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  --           no        
Rhfoster-BYOD           <MAC 'Rhfoster-BYOD' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2    no        
RHFoster                <MAC 'RHFoster' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2    no        
--                      <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  WPA2 802.1X  no        
WHOPPERWIFI             <MAC 'WHOPPERWIFI' [AC14]>  Infra  1     2412 MHz  54 Mbit/s  22      &#9602;___  --           no        
witech2                 <MAC 'witech2' [AC8]>  Infra  1     2412 MHz  54 Mbit/s  14      &#9602;___  WPA1         no        
```You are connected to *attwifi.* Somewhere in scan range is an 802.1x access point: [https://en.wikipedia.org/wiki/IEEE_802.1X#GNU.2FLinux](https://en.wikipedia.org/wiki/IEEE_802.1X#GNU.2FLinux) It's SSID is not readable by Network Manager. Maybe it's too far away. Maybe the SSID is in Chinese or Klingon. Who knows and who cares. It is not relevant to attwifi.

You appear to be connected perfectly well:> [   61.302077] wlp1s0: send auth to <MAC 'attwifi' [AC1]> (try 1/3)
[   61.307170] wlp1s0: authenticated
[   61.308016] wlp1s0: associate with <MAC 'attwifi' [AC1]> (try 1/3)
[   61.309826] wlp1s0: RX AssocResp from <MAC 'attwifi' [AC1]> (capab=0x401 status=0 aid=31)
[   61.312848] wlp1s0: associated
[   61.314038] wlp1s0: Limiting TX power to 20 dBm as advertised by <MAC 'attwifi' [AC1]>

---

### Post by pointy2 on 2017-12-16
And that is what is frustrating. Yes, NM shows me connected and with good signal, however, the hotspot portal doesn't pup up to allow for the connection to the internet. I've had the same problem before with NM, only last time it seemed to be a corruption in DNS. 

I read the highlighted red entries as an alarm that something was amiss. Pardon my lack of understanding code language and technical jargon, if I was wrong in assuming this., I get :

Inspecting the connection details in NM I get :

Signal Strength   Excellent
Link Speed  54Mb/S
Security  None
ipv4  192.168.67.0
ipv6  
Hardware Address
Defult Route
DNS  192.168.6.1 64.134.255.2.64 134.255.10

DNS lists 3 address, is this common with a VPN?

---

### Post by chili555 on 2017-12-16
I am not at all familiar with VPN; that's my Klingon.

Three DNS addresses are unusual but not impossible. It reflects what is given by the DHCP server, usually a router.

Your address of 192.168.67.0 seems very unlikely. Was it given by DHCP or entered manually in Network Manager?

---

### Post by pointy2 on 2017-12-16
Thanks for this. The DNS was given automatically, as I've not entered anything manually. Why does 192.168.67.0 seem unlikely?

---

### Post by pointy2 on 2017-12-16
I've had it with this ubuntu network manager. Can I install WICD replacement manager without wifi from the repository using a liveUSB?

I;'ve been through 4 installs of this OS and keep coming up with different problems with the NM all surrounding the captive poirtal refusing to display.

---

### Post by chili555 on 2017-12-16
> Why does 192.168.67.0 seem unlikely?Because normally, xx.0 is the router address: [https://www.lifewire.com/192-168-1-0-818388](https://www.lifewire.com/192-168-1-0-818388) Typically, they assign addresses by DHCP from xx.2 to xx.253. > I've had it with this ubuntu network manager. Can I install WICD replacement manager without wifi from the repository using a liveUSB?In my brief experience over 16 years in Linux and thousands of forum posts, I am unaware of any problem that was solved with Wicd. Is Wicd different? Yes. Is it demonstrably more capable? No.> the captive poirtal refusing to display.I don't understand. Is that a VPN thing? Please explain.

---

### Post by pointy2 on 2017-12-16
Captive portal is a splash screen (on 17.10) that acts as a gatekeeper between you and a public wifi spot, forcing you to acknowledge the TOS before accessing wifi. On most OS's, the captive portal will display on the browser page, however, with 17.10, the captive portal is a splash screen that pops up independently of the browser. when you accept TOS and close the splash screen, the wifi connects to the internet. 

I suppose the splash screen allows for VPN connection before the browser is opened....just my guess.

---

### Post by chili555 on 2017-12-17
Ahhh! Gotcha! I wondered if you were referring to some VPN-specific feature about which I admit I know nothing.

What browser are you using? Chromium and the latest Firefox block popups by default.

---

### Post by pointy2 on 2017-12-17
I'm using the latest FF. The splash screen on 17.10 is independent of a browser, and will launch before any browser is open. I've just found a thread that allows for a remake/remodel of the NM. I'm trying to install 
Network Manager 1.8.4.1ubuntu3.debian.tar.z. When clicking on the package, it asks for the directory to install it to. I'll have to seek out that answer.

This is the list of files that will be installed.

/etc/NetworkManager/NetworkManager.conf
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
/etc/NetworkManager/dispatcher.d/01-ifupdown
/etc/dbus-1/system.d/nm-dispatcher.conf
/etc/dbus-1/system.d/org.freedesktop.NetworkManager.conf
/etc/init.d/network-manager
/lib/systemd/system/NetworkManager-dispatcher.service
/lib/systemd/system/NetworkManager-wait-online.service
/lib/systemd/system/NetworkManager.service
/lib/systemd/system/network-manager.service
/lib/udev/rules.d/84-nm-drivers.rules
/lib/udev/rules.d/85-nm-unmanaged.rules
/usr/bin/nm-online
/usr/bin/nmcli
/usr/bin/nmtui
/usr/bin/nmtui-connect
/usr/bin/nmtui-edit
/usr/bin/nmtui-hostname
/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf
/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf
/usr/lib/NetworkManager/nm-dhcp-helper
/usr/lib/NetworkManager/nm-dispatcher
/usr/lib/NetworkManager/nm-iface-helper
/usr/lib/pppd/2.4.7/nm-pppd-plugin.so
/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so
/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so
/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so
/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so
/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-ppp-plugin.so
/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ibft.so
/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so
/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-wwan.so
/usr/sbin/NetworkManager
/usr/share/apport/package-hooks/source_network-manager-applet.py
/usr/share/apport/package-hooks/source_network-manager.py
/usr/share/bash-completion/completions/nmcli
/usr/share/dbus-1/system-services/org.freedesktop.nm_dispatcher.service
/usr/share/doc/network-manager/AUTHORS
/usr/share/doc/network-manager/NEWS.Debian.gz
/usr/share/doc/network-manager/NEWS.gz
/usr/share/doc/network-manager/README.Debian
/usr/share/doc/network-manager/README.gz
/usr/share/doc/network-manager/changelog.Debian.gz
/usr/share/doc/network-manager/copyright
/usr/share/doc/network-manager/examples/server.conf
/usr/share/man/man1/nm-online.1.gz
/usr/share/man/man1/nmcli.1.gz
/usr/share/man/man1/nmtui-connect.1.gz
/usr/share/man/man1/nmtui-edit.1.gz
/usr/share/man/man1/nmtui-hostname.1.gz
/usr/share/man/man1/nmtui.1.gz
/usr/share/man/man5/NetworkManager.conf.5.gz
/usr/share/man/man5/nm-settings-keyfile.5.gz
/usr/share/man/man5/nm-settings.5.gz
/usr/share/man/man5/nm-system-settings.conf.5.gz
/usr/share/man/man7/nmcli-examples.7.gz
/usr/share/man/man8/NetworkManager.8.gz
/usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy
/usr/share/polkit-1/rules.d/60-network-manager.rules
/var/lib/polkit-1/localauthority/10-vendor.d/org.freedesktop.NetworkManager.pkla

---

