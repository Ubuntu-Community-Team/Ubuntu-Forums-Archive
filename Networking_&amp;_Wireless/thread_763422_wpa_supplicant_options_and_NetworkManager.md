---
title: "wpa_supplicant options and NetworkManager"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by marlier on 2008-04-23
Hi, there --

Technically a kubuntu question, about the Hardy RC, but I suspect that it's more generally relevant so I'm posting it to this (more general) forum.

Working on getting my Dell 1500 miniPCI wireless card running; it's based on the Broadcom4328 chipset (grr).  Of course, to make things interesting, my home network uses WPA2 as its encryption scheme.

I've install wpa_supplicant, network-manager and network-manager-kde, ndiswrapper, and the windows drivers for the card.  The card is seen just fine:
```
ian@marlier-linux:/usr/share/doc/wpasupplicant$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:130 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Scanning, I can see my network, and it correctly advertises itself and its capabilities:
```
ian@marlier-linux:/usr/share/doc/wpasupplicant$ iwlist scan
          Cell 07 - Address: 00:19:E3:33:00:D8
                    ESSID:"medium"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:100/100  Signal level:-30 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

So far, so good.

However, trying to connect to the network using the NetworkManager applet fails; the progress bar gets to 28%, I'm asked for the network password, but the connection isn't ever established.

To debug, I created a wpa_supplicant.conf file manually, and tried using it.  This is the conf file that I first created:
```
ian@marlier-linux:/usr/share/doc/wpasupplicant$ cat /etc/wpa_supplicant.conf.orig
ap_scan=1
network={
        ssid="medium"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk= <snip>
}
```

However, invoking wpa supplicant with debug turned on (wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -w -d) showed that it would connect to the network but never really make the connection.  Eventually an authentication timeout would occur.

Having seen a note somewhere on the wiki, I tried changing the ap_scan parameter to 0, giving me a wpa_supplicant config that looked like this:
```
ian@marlier-linux:/usr/share/doc/wpasupplicant$ cat /etc/wpa_supplicant.conf
ap_scan=0
network={
        ssid="medium"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk= <snip>
}
```

And, AHA!  It worked!  wpa_supplicant was able to authenticate just fine.

But, that still leaves me with this question: How do I get NetworkManager to set the ap_scan=0 parameter to wpa_supplicant when it invokes that helper?  There's got to be a way...doesn't there?

(And, yes, I could just manage things another way...but I'd kinda rather fix this way, or figure out why it's not working, at least...)

Thanks!

- Ian

---

### Post by kutjara on 2008-04-23
Congratulations on getting that damned card to work with WPA. It's a pretty unpleasant experience, to say the least.

What I don't understand from your post is why you need to make Network Manager set the ap_scan=0 parameter at all. After all, that command is right there in your wpa_supplicant.conf file, so when NM calls wpa-supplicant, wpa-supplicant looks at the conf file and executes whatever is in it. Or are you saying that isn't happening?

I guess what I'm asking is what exactly you have to do every time you boot to get WPA working?

---

### Post by marlier on 2008-04-23
So, the thing is, NetworkManager doesn't appear to use the wpa_supplicant.conf file at all.  I'm a little confused about the exact mechanism, but it looks like wpa_supplicant is basically called by NetworkManager as a helper app, with a conf file that's either dynamically generated or stored somewhere obscure (I think the former, as there is a wpa_supplicant process created that points to /var/run/wpasupplicant and not to anywhere else).

The upshot of this is that getting the card to work at boot can be done, but it can't be managed with NetworkManager as far as I can tell, unless that parameter can be set.  The non-NM management options, configuring through the /etc/network/interfaces file or otherwise, are an option.

That said, for me (who needs to connect to 3 or 4 different wireless networks in any given day), the convenience factor of NM is pretty high.  Thus, the question about having that dynamically-generated wpa_supplicant file (or whatever the mechanism is) set that parameter...

---

### Post by kutjara on 2008-04-23
> **marlier said:**
> So, the thing is, NetworkManager doesn't appear to use the wpa_supplicant.conf file at all.  I'm a little confused about the exact mechanism, but it looks like wpa_supplicant is basically called by NetworkManager as a helper app, with a conf file that's either dynamically generated or stored somewhere obscure (I think the former, as there is a wpa_supplicant process created that points to /var/run/wpasupplicant and not to anywhere else).

The upshot of this is that getting the card to work at boot can be done, but it can't be managed with NetworkManager as far as I can tell, unless that parameter can be set.  The non-NM management options, configuring through the /etc/network/interfaces file or otherwise, are an option.

That said, for me (who needs to connect to 3 or 4 different wireless networks in any given day), the convenience factor of NM is pretty high.  Thus, the question about having that dynamically-generated wpa_supplicant file (or whatever the mechanism is) set that parameter...

Ah, ok, I see what you're saying. Yes, I noticed that strange call to /var/run/wpa_supplicant when I configured wpa_supplicant.conf (we must have used the same HOWTO). I thought it was strange, since there doesn't seem to be an instance of wpa_supplicant in that directory. I don't think that's related to the config file, though. When you set up wpa_supplicant, you no doubt typed something like "wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf." That associated wpa_supplicant with the wext enabler for WPA encryption (the preferred method with Broadcom cards), with your wireless lan interface (wlan), and with the wpa_supplicant.conf file you created. The /var/run/wpa_supplicant command basically just tells wpa_supplicant to run.

I found Network Manager to be a pain to use. It would always default to connecting to my neighbor's unsecured wifi network, no matter what I did to try to force it onto my own home network. So I switched to WICD. Not only does WICD let you specify your preferred network, it also has a set up panel in Preferences that lets you specify directly the wpa_supplicant scheme you want to use (there's a dropdown box with "ralink," "madwifi," "broadcom," "ndiswrapper," "wext," etc. You need to use the "wext" option (Broadcom and Ndiswrapper are seemingly put there solely to play with your mind).

WICD also has a nice interface for setting up multiple wireless connections, specifying alternative DNS settings, setting up and clearing static IP addresses. It just feels more fully developed at this time than NM.

If you want to give it a try, just type sudo apt-get install wicd. It'll uninstall Network Manager as part of the process, but that's ok, since you can easily reinstall it from the repositories if you need to.

---

