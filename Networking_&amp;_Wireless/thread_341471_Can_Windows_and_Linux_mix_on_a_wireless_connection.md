---
title: "Can Windows and Linux mix on a wireless connection?"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by aresgoddess on 2007-01-18
Today is the first day of my household having Roadrunner. Which is great and all, but there are three computers and only one connection. The solution is a wireless connection. Yay! But how? This is my question: [COLOR="DarkOrchid"]How do I set up a wireless router that will allow both my Linux comp and my family's Windows comps on the same connection? And how do I make it a secure wireless connection?[/COLOR] 

I already have a wireless card for my laptop from the Belkin company, and my dad also has one for his own laptop (same exact one actually). I intend to buy from the same company for the wireless cards for the other computers in the house. 

I use my laptop at school, which requires a login to the school's network, so i have it set up to do that when I connect over there. But I want to know if this will interfere with the connection at my house, if it is also a secure connection and uses a login or whatever else to make it secure. I tried searching the forum for any relevent information, but I couldn't find anything pertaining to this. All i found was setting up a network between a Windows comp and a Linux comp and sharing files between them, but not about a wireless internet connection. Any information or a point to the right thread would be greatly appreciated.

My school's network allows Windows, Mac, and Linux on it (though I don't think they realize that Linux even exists), so i know it's possible, I just can't find out how to do it at my house. =/

---

### Post by spd106 on 2007-01-18
Yes, there's no problem co-existing on a wireless link. You will probably want to use WEP at first to get used to setting up the wifi connection. This can be done in System -> Admin -> Networking, just enter then network name (ssid), then the WEP key. These settings will match those on the router. You can save the settings as a location, to make switching easier. 

You could also install network manager for a nice simple way of roaming wifi networks. It also supports WPA, so you have greater protection. See [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

The most important part is using the right SSID, this will allow you to grab an IP address in the same way as a windows PC.

---

### Post by tturrisi on 2007-01-18
Gateways-Routers-Access points operate independant of ANY computer's operating system, they work withh all operating systems because the protocols used for networking are standardized & all op systems use these standard protocols.  This is WHy the Internet can exist.  There's no basic difference between a router you buy for home networking and a router used by the isp or Internet backbone provider except features and price, their basic funcionality is identical.

Get the idea of being able to use a Toshiba television OR a RCA television with the cable box, they both work because televisions & cable boxes use standardized protocols.

---

### Post by aresgoddess on 2007-01-19
> **spd106 said:**
> The most important part is using the right SSID, this will allow you to grab an IP address in the same way as a windows PC.

ok, i've got a signal, which i didn't have before even though i was right next to it, but the network icon has that little X mark on it, so i'm still not connected. i can't figure out what i need to do to correct that. would it be the wpa_supplicant.conf file, or the network interfaces file? or something else? i've been referring to [this thread]("http://www.ubuntuforums.org/showthread.php?t=263136"), but i'm still stuck. I don't know the IP address or the Gatway address or the subnet mask thingie, or what the difference between an ASCII and Hexidecimal password type is (in the configuration settings window when you click on the network icon). this is starting to get frustrating. *sighs*

---

### Post by alinuxfan on 2007-01-19
are the other computers on the network connecting?
Set the computers side by side and see if you can figure out the difference.
Has the wireless router already been set up?
Make sure you have the right ESSID in the field (SSID in windows)
Hex vs ASCII...Both router and computer changes my ASCII WEP key to hex so you can just input your ASCII code in and make in the correct field that it is Plain (ASCII)

Where are you at in the configuration?  Has the router been set up? have any computers been set up?

Man this is why I don't work tech support.  I know exactly how to do it and could trouble shoot it if I was there but I suck and describing what I am thinking.  I hope some of this made sense :p

---

### Post by spd106 on 2007-01-19
I'll give you mine as an example
/etc/network/nterfaces```
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

/etc/wpa_supplicant/wpa_supplicant.conf
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
network={
        ssid="linksys"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        #psk="Thi5 pa55phra5e is n*t u5ed in Real life"
        psk=db4bf51f7b1b215b15c8906f495f54225248806184c8df4f463a7f639cbbf228

```
I'm not sure that the first six lines actually do anything, but since it worked I'm too afraid/lazy to mess with it too much.

If your passphrase is not as long as the psk bit, then you can be quite certain that it is an ascii passphrase. Yes the spaces do count so you need to use single quotes around them with the wpa_passphrase command. E.g.```
:~$ wpa_passphrase linksys 'Thi5 pa55phra5e is n*t u5ed in Real life'
network={
        ssid="linksys"
        #psk="Thi5 pa55phra5e is n*t u5ed in Real life"
        psk=db4bf51f7b1b215b15c8906f495f54225248806184c8df4f463a7f639cbbf228
}

```

---

### Post by Floppyjoe on 2007-01-19
> Can Windows and Linux mix on a wireless connection?

If your not careful you might get some Lindows and Winux! :biggrin:

---

