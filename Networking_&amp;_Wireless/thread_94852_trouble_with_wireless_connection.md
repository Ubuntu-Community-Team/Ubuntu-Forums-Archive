---
title: "trouble with wireless connection"
date: 2005-11-25
forum: Networking &amp; Wireless
---

### Post by Mikeynewbie on 2005-11-25
:???: hey I of course am new to linux but have fallen in love with ubuntu since I installed it recently.  However, I am having one problem, I cannot get connected to a wireless connection.  I installed ubuntu breezy and then installed ndiswrapper set up the windows driver the terminal said that all was well with the card and driver.  I then got wlan0 appearing in the connections applet, downloaded and installed network manager but when I try to connect to any of the wireless signals including my roomates cabel signal running via a linksys router it does not connect.  I also tried several randomly generated WEP encryption keys but they did not fix the problem.  any help would be greatly appreciated.

PS when i run ndiswrappter -l
i get installed ndis drivers:
bcmwl5 driver present, hardware present

(here is the odd thing)
bcmwl5.ing invalid driver!

sincerely mikey

---

### Post by PPower on 2005-11-25
[QUOTE=Mikeynewbie]:???: hey I of course am new to linux but have fallen in love with ubuntu since I installed it recently.  However, I am having one problem, I cannot get connected to a wireless connection.  I installed ubuntu breezy and then installed ndiswrapper set up the windows driver the terminal said that all was well with the card and driver.  I then got wlan0 appearing in the connections applet, downloaded and installed network manager but when I try to connect to any of the wireless signals including my roomates cabel signal running via a linksys router it does not connect.  I also tried several randomly generated WEP encryption keys but they did not fix the problem.  any help would be greatly appreciated.

PS when i run ndiswrappter -l
i get installed ndis drivers:
bcmwl5 driver present, hardware present

(here is the odd thing)
bcmwl5.ing invalid driver!

sincerely mikey[/QUOTE]

Take it from me ( a ndiswrapper user). You are in trouble. Well first you need to remove bcmwl5.ing from the list. Secondly have you renembered to type modprobe ndiswrapper as root. If you are still having problems are you using no protection, WEP or WPA. If you are using WEP you are kind of stuck. As far as I know the only protection that ndiswrapper supports is WPA. If you can change your router to use WPA. Download (from another machine, stick it on a floppy) the wpa_supplicant package from [http://archive.ubuntu.com/ubuntu/pool/universe/w](http://archive.ubuntu.com/ubuntu/pool/universe/w)

Now make your /etc/default/wpasupplicant so it reads this:
 /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>          Wireless drive, typically optional.
#  -i <ifname>          Interface
#  -c <config file>     Configuration file
#  -d                   Debugging (-dd for more)
#  -w                   Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

OPTIONS="-Dndiswrapper -iwlan0 -Bw -c/etc/wpa_supplicant.conf"

Change the config file and the wlan0 to whatever. THERE IS NO SPACE BETWEEN THE OPTION AND THE TEXT (i.e. -Dndiswrapper is correct).

Now edit /etc/wpa_supplicant.conf to look like this:
 Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="The ssid you want to connect to here"
        key_mgmt=WPA-PSK
        psk="Your WPA password here"
        proto=WPA
}


Start wpa_supplicant with wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -Bw

Now configure your network. No information about WEP keys are needed. If it works and your wireless card is the interface you use to connect to the internet see my post somewhere in this networking section. Otherwise you are done.

Hope it helps. If you need more help just post.

---

### Post by Strider420 on 2005-11-28
Does it work when you disable WEP? I ask because I have encountered the same problem. I set up ndiswrapper and the bcmwl5.inf drivers and am able to connect to the wlan but only if encryption is disabled. I tried 64-bit WEP and 128-bit WEP and as soon as I change the settings in my router, the connection stops working. Even after I restart the computer and router. I am beginning to think I need wpa_supplicant but the router (belkin F5D6321-Rev2) doesn't mention anything about WPA, only WEP. I'll post more info when I get home if anyone thinks they can help.

---

### Post by Lambert on 2005-11-28
Post the contents of your /etc/network/interfaces file. Keep the formats but you can xxx out your personal data.

Also what kind of wep settings are you using?

open or sharedkey/restricted
ascii or hexadecimal


As far as ndiswrapper and the setup process a couple questions.
1. Where did you pull the driver from?
2. When you installed the driver did you pull it from a directory on your harddrive and was the .sys file also in that directory?

---

### Post by fog on 2005-11-28
> sudo ifconfig [COLOR="Red"]ath0 [/COLOR]down
sudo iwpriv [COLOR="Red"]ath0[/COLOR] authmode 2
sudo ifconfig [COLOR="Red"]ath0[/COLOR] up

[COLOR="Red"]ath0[/COLOR] is my network, use yours.

---

### Post by Strider420 on 2005-11-28
Here is what my /etc/network/interfaces looks like:

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface

iface wlan0 inet static
address 192.168.2.23
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid WLAN
wireless-key 0b2ba8c717

auto wlan0

My settings are 64-bit hex (as you can see above). I couldn't tell you if I'm using open or shared/restricted as my router doesn't have any setting for that. 

I got my drivers (bcmwl5.inf) from the installation CD that came with my card. Both .inf and .sys files were on the desktop at the time of installation.

Everything works fine as long as I don't use any kind of encryption. If I turn on WEP on the router the connection fails and while I can still see the ESSID, I can't connect to the network.

Thanks for any insight.

---

### Post by cdsboy on 2005-11-28
instead of using a WEP, you could use a mac address filter and just add the mac filters you want to let access your router. That is an easy alternitive and it doesn't require anything special on your computer just the router.

---

### Post by Strider420 on 2005-11-28
That actually sounds like a good idea. Would the MAC address filter be effective for all connections or just wireless ones? (sorry I'm kind of a n00b)

---

### Post by TSJason on 2005-11-28
Hi All,

 I'm using WEP encryption with ndiswrapper and the bcmwl5 driver with no trouble. It's probably your Security Mode that's giving your trouble. Here's my snippet from my interfaces file so you can test it out in yours:

auto wlan0
iface wlan0 inet static
        address 192.168.0.103
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.2
        wireless-essid northshore
        wireless-mode Managed
        wireless-keymode open
        wireless-key1 xxxxxxxxxx
        wireless-defaultkey 1

---

### Post by Strider420 on 2005-11-30
Excellent! I guess I was missing those extra lines in the /etc/network/interfaces file. That network card was the only thing not working right out of the box but thanks to you fine folks I can finally ditch windows completely. :D

---

