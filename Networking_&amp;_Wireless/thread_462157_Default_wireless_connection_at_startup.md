---
title: "Default wireless connection at startup?"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by msubullyfan on 2007-06-02
Hi, everyone!

First post here... just installed Ubuntu 7.04 this morning.  I was thrilled to get my Linksys WMP54GS working quickly using the .deb package someone posted here.  However, my computer can see multiple  wireless networks at startup (mine and my neighbor's), and it connects to my neighbor's unsecured broadcast connection at startup.  Of course, I want it to automatically connect to my WPA-secured network w/o SSID broadcast.

Anyone know how to do that?  I've searched around, but couldn't find anything.

Thanks in advance.  I'm glad to be back in Linux after a 10-year absence.

---

### Post by Griffiss on 2007-06-02
Hi msubullyfan, welcome

have you seen this thread? it's pretty helpful for a lot of wpa stuff

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

griff

---

### Post by msubullyfan on 2007-06-02
Thanks for the response.  Yes, I've seen that thread.  Being a newbie, it doesn't make a ton of sense.  I came across it while searching on how to get my wireless NIC working.  After I got it to work, I was afraid that following that could cause problems, and I don't like typing commands and changing config files unless I understand what they're doing.

I guess I should give it a whirl.  I've been away from Linux for a decade now -- I guess I better find some tutorials and books to read up on on Debian and Ubuntu.

---

### Post by msubullyfan on 2007-06-03
Well, I tried the instructions in that thread, and it didn't solve my problem.  It connects to one or the other (seemingly at random) on startup.  So, I still haven't figured out how to make it connect to my home connection instead of my neighbor's connection.

Also, I installed the deb package as outlined in this thread...
[http://ubuntuforums.org/showthread.php?t=428099&highlight=wmp54gs+install+this+reboot+enjoy](http://ubuntuforums.org/showthread.php?t=428099&highlight=wmp54gs+install+this+reboot+enjoy)

That got my Linksys WMP54GS to work.  However, when the connection starts, it asks me to input a password for a "keyring", which I did.  Now, I have to input  this password every time when my WLAN connection starts.  Exactly what is this, and is there anyway I can get it to not require me to input a password every time???

I apologize for the stupidity.  I'm trying to learn as I go, and I would just like to get this annoyance out of the way so I can enjoy my life without Windows.

And, thanks again for the help!

---

### Post by msubullyfan on 2007-06-03
Ignore the last post.  I figured out the keyring issue (I don't know how I missed it when I searched the first time), but I still can't figure out how to make my wireless connection default to my network instead of another one.  Anyone have any ideas?

I did find this info in the NetworkManager FAQ:


[INDENT][I]How does NetworkManager select which wireless network to connect to?

NetworkManager only attempts to automatically connect to networks you have previously told it to connect to. If it finds multiple wireless networks that you have connected to in the past, NetworkManager selects the network one you connected to. If NetworkManager isn't connecting to the network you want, try to force it to connect to the network you wish to be connected, and NetworkManager will remember that setting next time.[/I][/INDENT]

However, I don't know what "try to force it" means.  I swap over to the right connection each time I log on... but that doesn't seem to be a firm solution.

Any ideas??????????????

---

### Post by Griffiss on 2007-06-04
I'm a noob myself so can't help directly. perhaps try ```
man iwconfig
```in a terminal. this will bring up the manual for the wireless configuration command iwconfig. you may be able to use this to specify which network to connect to.

---

### Post by hkahwaji on 2007-06-05
Hi,

I installed Ubuntu Desktop 7.04 and connected to my wireless network at home using WPA-PSK. Here is the instruction. I hope it helps:

Make the necessary changes in your AP to set the wireless security settings to WPA-PSK / TKIP or AES. Open a terminal and download the wpa_supplicant support. To install wpa_supplicant, run the following command from the terminal

	sudo apt-get install wpasupplicant 

On your computer, edit the interfaces file in the /etc/network directory to add the following:

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_wireless_network_ssid>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <your-hex-key>

Note: Here is the description of the values that are passed:
Wlan0: is the logical interface for your wireless card
Dhcp: setting the DHCP protocol
wpa-driver: that is Linux wireless extensions (generic)
wpa-ssid: Your wireless network SSID
wpa-ap-scan: Values can be either 1 or 2. Set to 1 if you are broadcasting the SSID or 2 if you are not broadcasting the SSID
wpa-proto: WPA if you have WPA(1) set up at your AP or RSN if you have WPA(2) set up at AP
wpa-pairwise: TKIP if wpa-proto is WPA and CCMP if you have wpa-proto set to RSN
wpa-group: TKIP if wpa-proto is WPA and CCMP if you have wpa-proto set to RSN
wpa-key-mgmt: WPA-PSK  (Authentication via pre-shared key)
or 
"WPA-EAP" = Authentication via enterprise authentication server.

Note: You will need to pass the a hex key for wpa-psk, to obtain the hex equivalent to the passphrase that you set up at the AP. Open a terminal and run the following command:

	wpa_passphrase <your-wireless-essid> <your-passphrase>

You should get an output equivalent to this:

network={
        ssid="linksys-n"
        #psk="test1234"
        psk=7270ebe2783ca7af537cc1a618e6306169a8aa1f142c1877f766d1a4a6da6cbd

The psk value is your hex key. Copy and paste that to the wpa-psk key value.

Save the file and restart your networking services using the following command:

	sudo /etc/init.d/networking restart

You now should be able to obtain an IP address

---

