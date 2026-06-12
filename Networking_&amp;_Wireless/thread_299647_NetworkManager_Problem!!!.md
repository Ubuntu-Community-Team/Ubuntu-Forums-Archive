---
title: "NetworkManager Problem!!!"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by Markus78 on 2006-11-14
Hi folks!

I installed Edgy and wanted to setup my wireless network. After installing networkmanager-gnome i always get the message "The NetworkManager could not find some required ressources. It cannot continue".

When I start nm-applet in the terminal I get the following messeges:

** (nm-applet:5495): WARNING **: Icon nm-vpn-lock missing: Icon 'nm-vpn-lock' not present in theme

(nm-applet:5495): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

I tried several Icon Themes but always get this failure

---

### Post by n1xt3r on 2006-11-14
I believe your problem might be addressed here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by Markus78 on 2006-11-15
That helped! Thank you, everything is working smoothly right now, WLAN+WPA!

---

### Post by Geoff2077 on 2006-11-18
My network-manager reports "no network connection", even though I have a wired and a wireless connection. 


the only way I can get network is using with System/Administration/Networking and enabling the desired connection (wireless ra0).

I tried editing the /etc/network/intefaces file and leaving only the entry for lo and restarting. However this did not have any effect on network-manager - still no connection. In addition I lost the ability to use the above Networking options.

Interesting enough, when I first installed network-manager, I had only the wired connection and I was able to successfully connect and even get the vpn connection operational (network-manager-pptp.
However after I went through the installation of the RT61 drivers for my wmp54g wireless card, the network-manager could not see the wireless connection. Only way I could enable the wireless was with Admin/Networking. Network-manager applet continued to report no network connection (even though the wireless connection was operational, and in addition I lost the vpn option.

Any ideas ???

Does anyone have a suggestion here please...

---

### Post by huygens on 2006-11-19
The ralink RT61 is not explictly named in the [supported list of hardware from NetworkManager]("http://live.gnome.org/NetworkManagerHardware"). However, the Ralink rt2x00 (which is from the same manufacturer) as some incompatibilities with NetworkManager, that could explain your problem...

Huygens

---

### Post by Geoff2077 on 2006-11-19
> **huygens said:**
> The ralink RT61 is not explictly named in the [supported list of hardware from NetworkManager]("http://live.gnome.org/NetworkManagerHardware"). However, the Ralink rt2x00 (which is from the same manufacturer) as some incompatibilities with NetworkManager, that could explain your problem...

Huygens

Huygens..
I dont think this is the issue at all - the wireless network card works just fine when I issue the manual command after boot up:
dhclient ra0 

Also the vpn under nm-applet works just fine with the wireless connection.

My thinking is that at the time nm-applet loads, the wireless card is not active and hence not seen. Somehow I need to get the wireless operational (dhclient ra0) before the nm-applet is started, so that it is then able to recognise the network connection.

Geoff

:confused:

---

### Post by huygens on 2006-11-20
> **Geoff2077 said:**
> the wireless network card works just fine when I issue the manual command after boot up:
dhclient ra0
This is normal and has nothing to do with NetworkManager. As long as your driver (or module) is OK, you can get a network connection. But it does not mean that it is compatible with NetworkManager.

> **Geoff2077 said:**
> Also the vpn under nm-applet works just fine with the wireless connection.
I thought from your first post that VPN worked only with the wired connection and not with the wireless. Could you detail more? :confused: 

> **Geoff2077 said:**
> My thinking is that at the time nm-applet loads, the wireless card is not active and hence not seen. Somehow I need to get the wireless operational (dhclient ra0) before the nm-applet is started, so that it is then able to recognise the network connection.
This seems unlikely, :-k the wireless connection is establishing during boot time and usually if your DHCP server is fast enough, upon end of boot time the connection is up and running. NetworkManager is launch only during login period: so after you typed your login and password. At that time, one could expect that the wireless connection is already up and running.
So I would say that the event you described is unlikely.
In addition, doing a bit of Google-ing gave me a few results that NetworkManager does not see/handle the ra0 interface, so you cannot use it with the module. However, some people reported that using the ndiswrapper instead, they could see the RT61 card in NetworkManager, but as a "wired card"!!!

I hope I am clearer now :-)

Huygens

---

### Post by Geoff2077 on 2006-11-20
Huygens,
Thanks for the input. Looks like I will have to ditch nm-manager and revert to manual setup of vpn. Keep running into dead-ends with Ubuntu.

Maybe you can tell me why I cannot get 
dhclient ra0
to run as a script during startup please.

I tried the usual suggestion of putting it into the /etc/init.d folder as a file S33rt61up with the one line entry: dhclient ra0
but this had no effect. I still have to manually enter the command as su after bootup.

Cheers

---

### Post by huygens on 2006-11-20
> **Geoff2077 said:**
> Maybe you can tell me why I cannot get 
dhclient ra0
to run as a script during startup please.

I am using the "interfaces" facility. It is quite convenient and do the trick. You just have to modify the file /etc/network/interfaces.
This is well described (probably better than I could do it) in section "Now add the interface with your settings to /etc/network/interfaces" from this post: [http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)
Choose the second option for DHCP.

After, you can always play on the command line to bring up or down the ra0 connection. You can use 'sudo ifup ra0' or 'sudo ifdown ra0' to respectivelly bring up or bring down the interface.

Huygens

---

