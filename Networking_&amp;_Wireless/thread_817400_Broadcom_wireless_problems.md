---
title: "Broadcom wireless problems"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by antonija on 2008-06-03
It all worked fine and dandy until my former router decided to call it a day. So I went out and bought brand new shiny Linksys WRT54GL. I installed tomato firmware, set it up to WPA2 and booted my laptop into windows to see in wireless works. Connection on first attempt, we are good to go. Reboot into ubuntu 8.04, open wicd GUI, set up network (it found it without problems, even guesed encryption). And voila! Connection established, all bars are green to the top!!! Except they aren't...

You see, while my ubuntu box is happily showing me green bars, my signal strenght and all other stuff I really wanted to see, my router shows laptop connected but no IP assigned to interface.

Router's DHCP is switched off, ubuntu box is set to static address. Network manager is wicd, so /etc/interfaces file only contains "auto lo" bit.
Interface is "Broadcom BCM4309 801.11a/b/g (rev 02)"
lshw -C network says my "wlan0" interface uses driver "ndiswrapper+bcmwl5" and module "ndiswrapper".

I did manage to connect to router earlier today when no encryption was enabled, but now even that results in connection on ubuntu box but no IP (and hence no internet) on router.

Any idea how to fix this?

---

### Post by vexingmodstwo on 2008-06-03
> **antonija said:**
> It all worked fine and dandy until my former router decided to call it a day. So I went out and bought brand new shiny Linksys WRT54GL. I installed tomato firmware, set it up to WPA2 and booted my laptop into windows to see in wireless works. Connection on first attempt, we are good to go. Reboot into ubuntu 8.04, open wicd GUI, set up network (it found it without problems, even guesed encryption). And voila! Connection established, all bars are green to the top!!! Except they aren't...

You see, while my ubuntu box is happily showing me green bars, my signal strenght and all other stuff I really wanted to see, my router shows laptop connected but no IP assigned to interface.

Router's DHCP is switched off, ubuntu box is set to static address. Network manager is wicd, so /etc/interfaces file only contains "auto lo" bit.
Interface is "Broadcom BCM4309 801.11a/b/g (rev 02)"
lshw -C network says my "wlan0" interface uses driver "ndiswrapper+bcmwl5" and module "ndiswrapper".

I did manage to connect to router earlier today when no encryption was enabled, but now even that results in connection on ubuntu box but no IP (and hence no internet) on router.

Any idea how to fix this?

Log into the router and manually assign the IP address to your laptop.

I'm definitely seeing a trend here.  The whole DHCP exchange is spotty at best.  It's a crap shoot.

---

### Post by buntunub on 2008-06-03
This has happened to me a time or two. All you really need to do is just restart networking and reconnect. You should be good after that.

---

### Post by antonija on 2008-06-03
I tried with uninstaling wicd with --purge, I even deleted its leftover files in /opt.

Reboot, reinstall and connection to unprotected network worked after I assigned static IP to wireless mac address. However after trying WPA I got connection with no IP assigned to it by router. It worked fine in windows so I guess it is not router related issue (in wins it even works without manual IP assigning).

Any other advice apart from restarting my network (which does not work) or manual IP assigning (which also fails, sadly)?

---

### Post by vexingmodstwo on 2008-06-03
> **antonija said:**
> I tried with uninstaling wicd with --purge, I even deleted its leftover files in /opt.

Reboot, reinstall and connection to unprotected network worked after I assigned static IP to wireless mac address. However after trying WPA I got connection with no IP assigned to it by router. It worked fine in windows so I guess it is not router related issue (in wins it even works without manual IP assigning).

Any other advice apart from restarting my network (which does not work) or manual IP assigning (which also fails, sadly)?

I would suggest trying another network manager.  I got it to work with wifiradar after having similar issues with WICD.

---

### Post by antonija on 2008-06-03
I'm going to try wifiradar and default ubuntu network manager tomorow... wish me luck! I'll be back here with results.

---

### Post by antonija on 2008-06-04
Here's the current situation:

If I follow commands given in the 4th post of [[COLOR="Blue"]_this thread_[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-527159.html") I get a really nice WPA encrypted connection with my Linksys. If I then attempt the same with either wicd or wifi-radar I get the old situation with "connected to <ssid>" but no IP showing on router device list.

I know I could probably make a bash script and run it everytime I'd need wireless at home, but since we're talking laptops I'd prefer a bit of mobility.

So far I'm quite sure router is working well and my laptop hardware is working well. The problem is clearly with network managers as manual connection works like a charm.

Which network manager would you suggest I try? I have trid wicd and wifi-radar for WAP connection. Original manager was uninstalled quite fast after failing to conncet to unencrypted network.

---

### Post by antonija on 2008-06-04
I never thought I'd say this but... I think I know what is wrong with wicd.

When I attempted manual WAP connection I set up custom wpa_supplicant.conf file which looked like this:
```

ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="MySSID"
	scan_ssid=0
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=TKIP
	group=TKIP
	psk="my_passphrase_in_quotes"

```

When wicd attempts connection it also creates wpa_supplicant file in /opt/wicd/encryption/configurations/<MAC_address_without_collons>, which in my case lookes like this:
```

[COLOR="Red"]ap_scan=1[/COLOR]

network={
	ssid="MySSID"
	scan_ssid=0
	proto=WPA [COLOR="Red"]RNS[/COLOR]
	key_mgmt=WPA-PSK
	pairwise=[COLOR="Red"]CCMP[/COLOR] TKIP
	group=[COLOR="Red"]CCMP[/COLOR] TKIP
	psk=[COLOR="Red"]<passphrase_hex_string_no_quotes>[/COLOR]

```
Diffrences are marked with red and wicd file is missing first line from wpa_supplicant.conf.

I do not claim to know what each of those lines or parameters within them means and does, but I have read (can't find that thread) somewhere that ```
ap_scan=1
``` breaks wpa_supplicant.

Also "CCMP" and "RNS" were said to cause problems with some dodgy wifi drivers (and me using ndiswrapper for my broadcom chip is very dodgy) and adviced not to use it in wpa_supplicant.conf file.

I tried to manually edit wicd config files, but it just rewrites then every time it attempts to connect. Any idea how to get wicd to its senses and use "proper" config files?

---

