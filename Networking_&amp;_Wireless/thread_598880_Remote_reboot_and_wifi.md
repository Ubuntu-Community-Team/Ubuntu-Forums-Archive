---
title: "Remote reboot and wifi"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by pug on 2007-10-31
OK, so my problem is the following:

I have an Ubuntu 7.10 box setup with wifi using keyring.

It works beautifully when I sit in front of the machine and manually login, since then the keyring password is automatically handed over by the login process. All good.

Now, what does NOT work is when I need to reboot the machine remotely. The machine will reboot, but since it requires manual intervention to login and/or to open the keyring I can now no longer connect to the box.

How do I solve this and is there a solution at all?

Enabling autologin removes the automatic handover of credentials from login to pam keyring... so doing that doesn't work, still requires me to be in front of the box.

Help!

---

### Post by pug on 2007-11-03
No solution to this problem?

---

### Post by rtg on 2007-11-03
Could you please check whether the workaround in [http://ubuntuforums.org/showthread.php?p=3679330](http://ubuntuforums.org/showthread.php?p=3679330) helps you?

---

### Post by pug on 2007-11-04
I'm 100% sure that won't work. My problem is that the WPA password is stored in the gnome-keyring.

---

### Post by peterc26 on 2007-11-04
I have the same problem, and would be equally keen on finding a solution.

The following link details the problem of the WPA password being stored in the keyring, and although I don't fully understand the details, Robert suggests that manual configuration using iwconfig, wpa_supplicant and dhclient may be a better solution than using Network Manager :-

[https://bugs.launchpad.net/network-manager/+bug/34898/comments/25](https://bugs.launchpad.net/network-manager/+bug/34898/comments/25)

I may try and give this a go - if so, I'll let you know how I get on.

---

### Post by peterc26 on 2007-11-04
pug,  I've had some success with my setup here.

I've managed to solve the problem by changing my driver from Gutsy's rt61pci to Ralink's rt61. In doing so, I no longer use Network Manager to enter my WPA key, but instead it is configured in a separate config file for the driver (namely /etc/Wireless/RT61STA/rt61sta.dat).

So now the network successfully starts during bootup. I've also uninstalled network-manager-gnome because it is of no use to me now.

For reference, I followed the How To on:
[https://help.ubuntu.com/community/Wi...ver/RalinkRT61](https://help.ubuntu.com/community/Wi...ver/RalinkRT61)

Obviously this exact solution will only be applicable to you if you have an rt61 network card, but even if not, the same approach may possibly still work depending on what drivers are available to you.

---

### Post by pug on 2007-11-04
I guess I could try to set it up through /etc/network/interfaces.

However I sometimes need to connect to VPN networks and networkmanager has quite a sweet interface for that. I believe mixing network manager and custom /etc/network/interfaces doesn't work very well (it didn't last time I tried it).

Ideally I would love to be able to just enter info manually into networkmanager and bypass the gnome keyring lookup or have networkmanager simply store the password on its own and/or autologin to gnome-keyring. 

If I try to manually setup a wifi connection using network manager (turning off roaming) wifi no longer works....

Networkmanager has no options for not using gnome keyring and you can't setup gnome keyring to allow access to anything without entering a password (e.g. opening your keyring...).

It feels like I'm walking around in circles for something that should "just work".

The default behavior of all other modern operating systems (windows, os x) is that the wifi network is up and working BEFORE you login (e.g. at the login prompt). However this is not the case for Ubuntu.

---

### Post by peterc26 on 2007-11-05
Surely Ubuntu Server Edition must do it properly. I wonder if anyone knows what's different about the way Server Edition gets its network connection - maybe that would hint to the correct solution.:-?

---

### Post by macaronikazoo on 2007-11-11
any progress on this one?  i'm in the same boat.
cheers

---

### Post by pug on 2007-11-24
I have totally given up on Networkmanager. A networkmanager that REQUIRES you to login before connecting is in my opinion FLAWED as hell.

Ubuntu needs to make Networkmanager able to work without having to obtain wifi credentials from a keyring (e.g. from a simple textfile.. that would be wonderful!)

Anyway, I now have a working setup (after fiddling around for some time).

I'm not entirely sure what packages and stuff you need, but if you have your wifi working in networkmanager, chances are this will work for you too (wpasupplicant needs to be installed for sure..)

First do: 
```
wpa_passphrase YOURSSID yourpassphrase
```

with the SSID of your AP and the passphrase you’ve entered in your wifi capable routers WPA-PSK configuration. You’ll receive an output, which looks like this:

```
network={
 ssid="YOURSSID"
 #psk="yourpassphrase"
 psk=edda86468aa67c3f71c0bbaf7828aedccd320f9011d63e699f5381a5b77e0c2a
}

```

Copy this output into a new file called /etc/wpa_supplicant.conf and change the permissions after you’ve finished editing:

```
chmod 640 /etc/wpa_supplicant.conf
```

Now, edit your /etc/network/interfaces file. Mine contains the following:

```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid MYESSID
pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

Most likely most people will want to use -Dwext (I have to use madwifi.. mac mini's.. pfft).

Anyway, the "pre-up" line will most likely be different if you have a different wireless card (mine is an atheros).

After some testing I simply rebooted and started praying.... and lo and behold, it worked!

I hope this helps some of you guys as well! :-)

-pug

---

### Post by pug on 2007-11-24
Oh, one more tip for people using madwifi:

[http://madwifi.org/wiki/UserDocs/PerformanceTuning]("http://madwifi.org/wiki/UserDocs/PerformanceTuning")

```
iwpriv ath0 bgscan 0
```

Should increase performance somewhat (it seems to prevent those pesky dropouts you get from time to time when the wireless card is scanning...)

---

