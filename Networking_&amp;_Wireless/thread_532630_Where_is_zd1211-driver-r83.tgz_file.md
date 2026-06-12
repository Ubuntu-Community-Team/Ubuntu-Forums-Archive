---
title: "Where is zd1211-driver-r83.tgz file?"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by tak1150 on 2007-08-23
I would like to follow the following tutorial, but can't find the file "zd1211-driver-r83"

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)")

The link provided does not contain the driver.
```
wget http://zd1211.ath.cx/download/zd1211-driver-r83.tgz
```
The above command will only save a "index.html" (presumably because the driver is not tthere.

Could somebody tell me where this driver tgz file (or any compressed format) can be found? Or anybody has a copy of it, could you post it for me and those who need it? Thank you very much!

---

### Post by tak1150 on 2007-08-23
bump!

---

### Post by Darkhack on 2007-08-23
Your profile says you are a Feisty Fawn user, but you're trying to install an old unsupported driver.  Is this for a friend or some older machine?  If not, then you shouldn't be using it.  The new driver is zd1211rw and is built into the mainline kernel and is in Feisty Fawn.  The device should be recognized when you boot.  What is the output of "iwconfig" in the Terminal?

---

### Post by tak1150 on 2007-08-23
Thanks for replying!
Yes I have tried using zd1211rw, and it works as long as I am not using any security measure (ie ESSID broadcast, No WPA or WEP). After doing some research it seemed like what I should use is zd1211-r83 (or zd1211b).

See: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%287050%29%7C%28f5d%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%287050%29%7C%28f5d%29")

I have an F5D7050 Belkin wireless card version 4000 (705c is what I get from lsusb).

Have you got zd1211rw driver to work with WPA? If so, I'd LOVE to hear about it!
Thanks

---

### Post by Darkhack on 2007-08-23
Yes.  I have full security.  SSID isn't broadcasted and I am using WPA.  I'm not using the same device, but I am using the zd1211b chipset.  NetworkManager caused kernel panics whenever I tried to configure it, so I had to do it manually via the command line.  It's working great though and I have everything so it starts automatically and works with no hassles.  I just followed the tutorial below.  It might take a little bit of tweaking to get working.

[http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")

For my setup I had to modify the wpa_supplicant.conf file a little differently from what is shown in the tutorial.  Try the tutorial's version first because it may work for your device and if not then here is a copy of mine...
[QUOTE=Darkhack's wpa_supplicant.conf]
network={
        ssid="My_Network"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk=0123456789ABCDEF
}[/QUOTE]

---

### Post by tak1150 on 2007-08-23
> Yes. I have full security. SSID isn't broadcasted and I am using WPA. I'm not using the same device, but I am using the zd1211b chipset.

So you are NOT using zd1211rw?
I know that I either need to
[LIST]
[*]get WPA working with zd1211rw, or
[*]zd1211b (zd1211-driver-r83, not r73) working as in the documentation above
[/LIST]

Moreover, situations are very different for different versions of F5D7050 USB sticks.
See: [http://ubuntuforums.org/showpost.php?p=2416740&postcount=43]("http://ubuntuforums.org/showpost.php?p=2416740&postcount=43")

---

### Post by logos34 on 2007-08-23
> **tak1150 said:**
> So you are NOT using zd1211rw?
I know that I either need to
[LIST]
[*]get WPA working with zd1211rw, or
[*]zd1211b (zd1211-driver-r83, not r73) working as in the documentation above
[/LIST]

Moreover, situations are very different for different versions of F5D7050 USB sticks.
See: [http://ubuntuforums.org/showpost.php?p=2416740&postcount=43]("http://ubuntuforums.org/showpost.php?p=2416740&postcount=43")

Try here:

[http://downloads.openwrt.org/sources/](http://downloads.openwrt.org/sources/)

I had to use the zd1211-driver-r85 to get wireless working on an Edgy installation some months back.

---

### Post by Darkhack on 2007-08-24
> **tak1150 said:**
> So you are NOT using zd1211rw?

No, I **am** using the zd1211rw driver.  I was saying that my device is a zd1211b chipset.  The rewrite (zd1211rw) is a single driver that supports both zd1211 and zd1211b chipsets in devices.

---

### Post by tak1150 on 2007-08-24
> Try here:

[http://downloads.openwrt.org/sources/](http://downloads.openwrt.org/sources/)

Good link! thank you.

> No, I am using the zd1211rw driver.
Sorry, darkhack, I misunderstood you. What version of the card do you have? v3000?

```
network={
ssid="My_Network"
scan_ssid=1
proto=WPA
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP
psk=0123456789ABCDEF
}
```
In the above, you have both CCMP and TKIP. Is this necessary? I may try that. I always only had TKIP since that's what my router is set to.

Also did you modify /etc/network/interfaces at all? Or just /etc/wpa_supplicant.conf ?
Thank you!

---

### Post by Darkhack on 2007-08-24
> **tak1150 said:**
> Sorry, darkhack, I misunderstood you. What version of the card do you have? v3000?

I'm not using the same device at all.  The zd1211rw driver is a device driver for any wireless device that happens to use the zd1211 or zd1211b chipsets.  Lots of different devices use this same chipset.  I'm using the Zonet ZEW2501 (0ace:1215).  It's not just that one brand or one model that can use this driver.  There is an entire list here... [http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices]("http://www.linuxwireless.org/en/users/Drivers/zd1211rw/devices")
> **tak1150 said:**
> 
In the above, you have both CCMP and TKIP. Is this necessary? I may try that. I always only had TKIP since that's what my router is set to.
For me, yes.  I gave you a link earlier to a tutorial that shows how to set it up and I mentioned that for my particular setup I had to do it differently.  If I didn't have both CCMP and TKIP, I kept losing a connection and it would drop like crazy all the time.  This fixed it.  Try what it says in the tutorial and use my settings only if that doesn't work.
> **tak1150 said:**
> Also did you modify /etc/network/interfaces at all? Or just /etc/wpa_supplicant.conf ?
Yes.  The tutorial shows how to do all that.  For reference though, here is a copy of my interfaces file as well...
[QUOTE=Darkhack's /etc/network/interfaces]
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
netmask 255.255.255.255
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1
essid My_Network
wireless-essid My_Network
wpa-ssid My_Network
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
wpa-key-mgmt WPA-PSK
[/QUOTE]

---

### Post by tak1150 on 2007-08-25
Thanks for the follow-up.
```

netmask 255.255.255.255
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1
```

How did you figure out the above? I read the how-to, but it was not clear to me.
The web-based administration page for my router status tells
[LIST]
[*]IP Address	 
[*]Subnet Mask
[*]Default Gateway
[*]Primary DNS Server
[*]Secondary DNS Server
[/LIST]
these addresses, but none of them seem local like in your case (ie 192.168....).

Thanks

---

### Post by Darkhack on 2007-08-25
Netmask is the router's subnet mask.
Broadcast is your gateway with 255 as the last octet.  
Network is your gateway with zero as the last octet.
Gateway is the default gateway shown on the router's page.

---

### Post by tak1150 on 2007-08-25
Darkhack,

I must beg for your forgiveness...
As I was browsing through the router pages, I thought I'd make sure that the wireless card is not blocked by MAC filter, which I was sure that it was not because when I took the WPA security off and enabled SSID broadcast, it worked.
But, it WAS blocked by the MAC filtering!

So now I would like to announce to the whole world that I'm silly and that [SIZE="4"]Belking F5D7050 v4000 works with zd1211rw driver OUT-OF-THE-BOX with WPA![/SIZE]

However, I could not get it to work if the SSID broadcast is not on (this is also the case with my laptop which has Atheros AR5212 wireless card using madwifi).

Now I'll have to try to sort out the SSID issue, but even if that's not successful, as long as I have WPA, I'm very happy. Thank you darkhack, for putting up with silly people like myself :)

---

