---
title: "Need help getting ENLWI-G rev 01 PCI card to recognize WPA-PSK"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by linuxn00ber on 2008-03-01
Anyone know how I can get my Encore Wireless ENLWI-G rev 01 card to allow me to use WPA-PSK? I initially had problems installing this card after removing a dlink wireless because it was an 802.11b and only supported WEP.
Once I got this encore card installed and the driver running using ndiswrapper, it only lets me choose WEP as the security. I know the card supports WPA-PSK because I was using this security on a windows machine with the same card. I heard you had to install the wpa supplicat, which I did but still no joy. Anyone know what I might be missing or need to do to get this to work using WPA-PSK before I just break down and get a wireless access point:confused:??

---

### Post by linuxn00ber on 2008-03-02
Ok guess I am learning slowly but surely as I go along. Figgered out how to use the wpa_supplicant... I think. I am having problems doing so however because when I run it, it seems to just hang there in the terminal screen and doesnt return me to my prompt. here is what I am doing:

I browsed to:
usr/share/doc/wpasupplicant

copied the sample wpa-psk-tkip.conf file to my home folder

edited the wpa-psk-tkip.conf file with my own info. It looks kinda like this subbing the passphrase obviously, like this:
# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant

network={
                ssid="davenet"
                key_mgmt=WPA-PSK
                proto=WPA
                pairwise=TKIP
                group=TKIP
                psk="mypassphrase"
}

Now after I did this, I ran the command:
sudo wpa_supplicant -Dndiswrapper -iwlan0 -c/home/david/wpa-psk-tkip.conf

After I do this, the screen just sits there and I have to do ctrl+c to break and afterwards I get the error:

ioctl[SIOCSIWSCAN]: Operation not supported
Failed to initiate AP scan.
CTRL-EVENT-TERMINATING - signal 2 received


Now if someone can help me over this roadblock maybe I can actually get WPA-PSK to work.

---

### Post by apureevil1 on 2008-03-04
Try WICD instead of network manager. 
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
 I have 4 of the ENLWI-SG cards and they all work great using WICD. (SG  uses an atheros chip set and the G uses marvell I believe)

---

