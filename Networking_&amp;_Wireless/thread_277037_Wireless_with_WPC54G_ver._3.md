---
title: "Wireless with WPC54G ver. 3"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by Andrew West on 2006-10-13
I know wireless is a common hassle, but apparently this specific card is especically finicky seeing as I've yet to find a working solution after spending most of my day looking. Admittedly, part (or most) of the problem stems from my inexperience with Ubuntu (hence I originally posted in "Absolute Beginner Talk"). Much of my motivation for choosing Ubuntu was the community behind it; I'd much rather be told I don't know what I'm doing than  have to have to figure that out for myself.

A little information on the card:

```
lspci | grep Broadcom\ Corporation
0000:03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

I'm running Dapper 6.06 on a ThinkPad R40. Thanks.

---

### Post by wieman01 on 2006-10-13
It seems that your card has been recognized. That's good news. Please run these commands from command line & show us the output:
> iwconfig
> iwlist scan
> sudo gedit /etc/network/interfaces
> route

Than also let us know what kind of network you have & what the settings are: DHCP, Static IP, ESSID, possibly encryption, router's IP address.

---

### Post by tedrogers on 2006-11-07
I don't know why Andrew hasn't replied yet, but I'm getting massive problems with Dapper and Edgy running the WPC54G card in my IBM T22 laptop. I am running on a fresh install here, I have not installed NDISWRAPPER yet or even gone into the Networking to enable my wireless card. All I have running is my wired eth0 connection, which as ever, works fine. Here's the results that I have - if you can solve my problems I'll be a very happy bunny indeed as this lack of wireless connectivity is the ONLY thing stopping me from switching to Ubuntu full-time on my T22 laptop:

_iwconfig_

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

_iwlist scan_

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

_sudo gedit /etc/network/interfaces_

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

_route_

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

You also wanted to know the the network I have. It's a Linksys WRT54g v5.0. DHCP is automatically assigned. Router's IP is listed above, pretty regular stuff. ESSID is a secret, but if you use 'Your ESSID' or something I will know what you mean. I use WPA2 Encryption if possible, but at the moment it is all turned off (as is Mac Table Filtering etc). I'm trying to use this as bog standard as possible at first...should be easy right!?!?

I notice that my Broadcome card is being labelled as eth1 - shouldn't this be wlan0 - not that it matters I suppose.

Thanks in advance.

---

### Post by wieman01 on 2006-11-07
Ok, a couple of things...

1. "wlan0" is the interface name for "ndiswrapper" which you have not installed yet. "eth1" refers to your Broadcom driver (Linux).
2. Turn encryption off, I'll show you how to enable WPA2 (AES) later on once we get this working.
3. Whatever you do with regard to wireless, make sure you Ethernet cabled it unplugged, otherwise this will create problems.
4. This is the best Broadcom howto I can offer, nice & simple. Forget about the native Linux driver for your card, it's useless: [http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

If this howto does not help, I'll dig out another one. As for WPA2 you can try this later on:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

### Post by tedrogers on 2006-11-07
> **wieman01 said:**
> Ok, a couple of things...

1. "wlan0" is the interface name for "ndiswrapper" which you have not installed yet. "eth1" refers to your Broadcom driver (Linux).
2. Turn encryption off, I'll show you how to enable WPA2 (AES) later on once we get this working.
3. Whatever you do with regard to wireless, make sure you Ethernet cabled it unplugged, otherwise this will create problems.
4. This is the best Broadcom howto I can offer, nice & simple. Forget about the native Linux driver for your card, it's useless: [http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

If this howto does not help, I'll dig out another one. As for WPA2 you can try this later on:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Hi and thanks for your reply.

Looks like I've been stumped at the first hurdle...when I try to run the command

```
sudo gedit /etc/modeprobe.d/blacklist
```

...and I add the line (into an empty document)...

```
blacklist bcm43xx
```

...and I try to save I get an error saying that the file does not exist.

I'm getting some other weird stuff too...like 10 windown opening in Gnome when I want to browse the Computer or Home????

Going to reinstall again and try once more.

Will let you know what happens.

---

### Post by tedrogers on 2006-11-07
Hey it works!

Don't know what was up with my blacklsit the first time round, but I reinstalled and everything went fairly smoothly.

The main thing is I now have wireless connectivity...and I didn't realise that you couldn't have wired and wireless activated at the same time...this may have been part of the problem all along.

Now onto getting encryption etc.

---

### Post by tedrogers on 2006-11-07
Well....been trying for hours to get encryption on both WPA2 and WPA, but sadly I have not been able to do this.

I have a few questions though as per your thread [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

In your personal configuration, using static IP address, you list the following:

auto wlan0
iface wlan0 inet static

    wpa-driver wext
    wpa-conf managed
    wpa-ssid <your_essid>
    wpa-ap-scan 2
    wpa-proto RSN
    wpa-pairwise CCMP
    wpa-group CCMP
    wpa-key-mgmt WPA-PSK
    wpa-psk <your_hex_key>
    address 192.168.168.40
    netmask 255.255.255.0
    network 192.168.168.0
    broadcast 192.168.168.255
    gateway 192.168.168.230
    dns-nameservers 192.168.168.230

My questions are:

1. If I am using DHCP instead of Static IP, do I need the address, netmask, network, broadcast, gateway and dns-nameservers lines? I have tried with and without and I am unable to get it working either way?

2. I am using a 63 character Hex code as my wpa-psk. Is this a problem? I don't see why because it should work for WPA1 and WPA2 in AES encryption mode (as denoted by wpa-pairwise CCMP and wpa-group CCMP entries).

3. In my /etc/network/interfaces file I have an additional entry when compared to yours. Mine looks like this:

```
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-essid <MY ESSID>

auto wlan0
```

I have removed the eth0 lines, just to keep things simple and exactly like your setup....but mine has the additional entry of wireless-essid <MY ESSID> line. If I remove this then it unchecks the Wireless Card in Network ing settings (SYSTEM > ADMINSITRATION menu) and the wireless card has to be manually re-enabled for it to connect to my router.

I'm a bit confused now and will probably give it a rest for the night...but any help you can offer here is greatly appreciated. I've come so far tonight and it seems a waste not to get encryption working...and I just wouldn't feel safe browsing either (and especially for my partner who uses the same machine).

Thanks a lot for your help so far.

I hope someone else reads this and gets the help they need too.

---

### Post by wieman01 on 2006-11-08
> **tedrogers said:**
> 1. If I am using DHCP instead of Static IP, do I need the address, netmask, network, broadcast, gateway and dns-nameservers lines? I have tried with and without and I am unable to get it working either way?
Yes, DHCP will make it simple. See further below.
> **tedrogers said:**
> 2. I am using a 63 character Hex code as my wpa-psk. Is this a problem? I don't see why because it should work for WPA1 and WPA2 in AES encryption mode (as denoted by wpa-pairwise CCMP and wpa-group CCMP entries).
You may have skipped one important point: WPA-PSK passphrase generation. As for WPA-PSK key generation, type the following command in a terminal:

> wpa_passphrase <your_essid> <your_ascii_key>

Resulting in an output like...

> network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab15bbc6c52e7522f709a
}
Copy the "hex_key" (next to "psk=...") and replace <your_hex_key> in the "interfaces" files with it.
> **tedrogers said:**
> 3. In my /etc/network/interfaces file I have an additional entry when compared to yours. 

wireless-essid
This one will only be used if you use no wireless security or WEP. So you don't need it.

So here is your sample file (WPA2, ndiswrapper):
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]<your_essid>[/COLOR]
[COLOR="Red"]wpa-ap-scan 1[/COLOR]
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk [COLOR="Red"]<your_hex_key>[/COLOR]
_**IMPORTANT:**_
1. Pay attention to the mentioned passphrase key generation.
2. "wpa-ap-scan 1" is the right one if ESSID broadcast is enabled. Only if you hide your ESSID, it should read: "wpa-ap-scan 2".

Both points are mentioned in the howto... actually (if you read it carefully). :-)

---

### Post by tedrogers on 2006-11-08
Belting! :cool: :D 

Thanks a lot....you were right about the key generation part...I totally missed that out thinking I could just use my own (and as long as they matched I thought it should work). I now understand some of the other things I've been reading about the key generation stage....it's so that the WPA-PSK is not stored in the OS history and only stored on the router...clever! I think!

The only other thing I wasn't doing was running this command:

```
sudo /etc/init.d/networking restart
```

My network started right up without any problems with WPA2 - excellent!

Thanks so much for all your help and persistence.

---

### Post by wieman01 on 2006-11-08
> **tedrogers said:**
> Belting! :cool: :D 

Thanks a lot....you were right about the key generation part...I totally missed that out thinking I could just use my own (and as long as they matched I thought it should work). I now understand some of the other things I've been reading about the key generation stage....it's so that the WPA-PSK is not stored in the OS history and only stored on the router...clever! I think!

The only other thing I wasn't doing was running this command:

```
sudo /etc/init.d/networking restart
```

My network started right up without any problems with WPA2 - excellent!

Thanks so much for all your help and persistence.
Great!

Last thing you could do is revoke the read right for "interfaces" from "others" so that only root can read it:
> sudo chmod o=-r /etc/network/interfaces
I need to be a bit more persistent. But enough for today. :-)

---

### Post by tedrogers on 2006-11-08
> **wieman01 said:**
> Great!

Last thing you could do is revoke the read right for "interfaces" from "others" so that only root can read it:

I need to be a bit more persistent. But enough for today. :-)

Escuse my ignorance, but if I do this will it stop other users from being able to get access to the wlan/internet? If so, then this would be a problem if I did it.

I've also come across another problem for me...if I shutdown or restart the laptop then the wlan isn't automatically initiated. I've working out that if I run:

sudo /etc/init.d/networking restart

...then this fixes things and my network is up and running. Trouble is while this is fine for me, for my partner it is not good as the terminal would scare the pants off her! ;)

I tried adding the above line into my STARTUP PROGRAMS in System > Preferences....but this didn't do any good. I thought it might pass my login password onto the startup programs if required, but it obviously didn't or something else stopped it.

So, have you any suggestions on how I might get this command to run automatically on login? Perhaps a script or something, but I admit I know very little about these as of this stage. Considering I've only been using Linux in it's various forms for a couple of months I think I'm not doing too bad so far.

Thanks again....you should be a guru!

---

### Post by wieman01 on 2006-11-08
Revoking the read-permission from "others" ensure that no unauthorized user can read the "interfaces" file & hence gets hold of the passphrase. A simlpe security measure, nothing else. Everyone will be able to access the Internet, no problem.

As for the other problem (restart)... See post #2 of my thread. ;-)

Here is a workaround that helps restart the network during boot so that one does not have to do it manually after logging on to the system.

_Create startup script:_
> cd /etc/init.d/
sudo gedit wireless-network.sh
_Add 1 line & save file:_
> /etc/init.d/networking restart
_Change permission (executable):_
> sudo chmod +x wireless-network.sh
_Create symbolic link:_
> cd /etc/rcS.d/
sudo ln -s /etc/init.d/wireless-network.sh **[COLOR="Red"]S40[/COLOR]**wireless-network
[Note: You may have to choose a boot sequence other than **[COLOR="Red"]S40[/COLOR]**.]

Restart...

---

### Post by tedrogers on 2006-11-08
Again...this worked perfectly! :)

I might have to hire you as my personal Ubuntu advisor! :p 

Not entirely sure what the various boot sequences are....I just used S40 and it worked....but I would like to hear an explanation if you feel up to it.

Well...that about wraps it up I think...until something else goes wrong that is.

Once more, thanks for all your help on this....I really couldn't have done it without you. Believe me. You are a 8) dude.

By the way...if you're wondering if I have a moustache (see avatar)...I don't. That is cat hair that I found on the floor in my house and I fashioned it into a moustache and held it on my top lip for the photo. I've been told it suits me! ;)

---

### Post by wieman01 on 2006-11-08
Don't forget: It's amazing how far you get if you use common sense. I am not a guru of any kind, but I do try to understand things in the first place & then apply common sense later on. That works wonders most of the time, you'll see.

See you next time then!

---

### Post by trav5 on 2006-11-17
Weiman thanks for the tip on unplugging the ethernet cable and turning off the wep. I tried this thread [http://www.ubuntuforums.org/showthread.php?t=285809](http://www.ubuntuforums.org/showthread.php?t=285809) numerous times before but to no avail. I am typing this wireless in ubuntu :D

---

### Post by wieman01 on 2006-11-17
> **trav5 said:**
> Weiman thanks for the tip on unplugging the ethernet cable and turning off the wep. I tried this thread [http://www.ubuntuforums.org/showthread.php?t=285809](http://www.ubuntuforums.org/showthread.php?t=285809) numerous times before but to no avail. I am typing this wireless in ubuntu :D
I must have mentioned that in another thread. You're welcome of course.

---

