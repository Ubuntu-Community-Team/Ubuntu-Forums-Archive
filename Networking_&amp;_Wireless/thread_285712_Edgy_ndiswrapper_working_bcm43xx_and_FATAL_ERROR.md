---
title: "Edgy ndiswrapper working bcm43xx and FATAL ERROR"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by squibT on 2006-10-27
Got Edgy working with my Linksys wpc54gs (bcm43xx) and ndiswrapper using:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

BUT the error ](*,) 
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

stopped me until I manually installed ndiswrapper via SPM. Im using the latest Linksys drivers LSBCMNDS.inf and also installed GUI for wpa_supplicant
wpagui as a last step to get it going, also 'blacklist bcm43xx'

BTW IBM T20, bcm43xx 4306 wireless card. 

joy :) :p :)

---

### Post by billtron on 2006-10-28
I followed the instructions at [http://www.ubuntuforums.org/showthread.php?t=25683]("http://www.ubuntuforums.org/showthread.php?t=25683")  and received the same message: 
```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

The problem that I have is I don't know how you solved the problem. What's SPM?  How do I install ndiswrapper using it?  Can you provide instructions for me?

---

### Post by squibT on 2006-10-28
It is recommended that you remove any sign of ndiswrapper from your computer.  To remove, from a Terminal run the following commands:
	 sudo ndiswrapper -e <your_driver/drivers>

         sudo modprobe -r ndiswrapper 

         sudo apt-get --purge remove ndiswrapper-utils 

         sudo rm -r /etc/ndiswrapper/ 

         sudo rm -r /etc/modprobe.d/ndiswrapper

         sudo rm /lib/modules/$(uname -r)/kernel/drivers/net/ndiswrapper/ndiswrapper.kor.ko

System_Admistration_Synaptic Package Manager (SPM)

Search for NDISWrapper or anything...then scroll on the right to find it....select all the packages ...reload...Apply

Hope this helps

---

### Post by wieman01 on 2006-10-30
It's an unusual way to respond to personal message, but you (squibT) have turned personal messaging off so I cannot reply to your note. Here is you answer: 
[QUOTE=squibT]I got my card working (see title) same chipset as Eric but using the latests lsbcmnds.inf driver, ndiswrapper and using wpa_supplicant.conf and network manager no problem.[/QUOTE]
That's good news for us. I just came across that yesterday night myself. Hope Erik will get it done this way. Perhaps you can advise as well if we get stuck.
[QUOTE=squibT]Some posts say that the recommended way is your way...using the network/interfaces file and not wpa file. When I tried it with the interfaces file, my network manager would not recognize any wireless connection  but a query showed the card was working and available.[/QUOTE]
Yes, that's my preferred way. I got WPA-TKIP working with another guy, although I am using WPA2-AES. Check it out (of course you have to replace "ath0" with "wlan0"), read the last page of this: [http://www.ubuntuforums.org/showthread.php?t=225290&page=11&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=225290&page=11&highlight=wpa2+rsn")
[QUOTE=squibT]Are you using network/interfaces file AND network manager also?[/QUOTE]
If you are referring to Gnome-Network-Manager, the answer is NO, I am only using "interfaces". The "networking applet" won't be of much help in that case. It can only cope with WEP.
[QUOTE=squibT]Any ideas how to get switched over to the network/interfaces file? [/QUOTE]
Yes, definitely. Open up a new thread & send me the link. Way more convenient that PM. :-) The corresponding section of your interfaces will look like this:
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid [COLOR="Red"]your_essid[/COLOR]
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk [COLOR="Red"]your_wpa_psk[/COLOR]
[COLOR="Red"]I will delete this post as soon as you have enabled PM...[/COLOR]

---

### Post by squibT on 2006-10-30
Thanx for the reply wieman01,

Gonna use your interfaces file and remove network manager also remove and reinstall ndis.

Here is my file:

auto [COLOR="Red"]eth1[/COLOR]
iface eth1 inet dhcp
        wpa-driver [COLOR="Red"]ndiswrappe[/COLOR]r
        wpa-scan-ssid 1
        wpa-conf managed
        wpa-ssid Digger
        wpa-key-mgmt WPA-PSK
        wpa-proto WPA
        wpa-pairwise TKIP
        wpa-group TKIP
        wpa-psk 64hexdigets not shown

The only diff seems to be the order of the lines, ndiswrapper and my wireless card reports to be eth1. Using wpa_supplicant.conf and network manager it is also eth1 and connects fine.

Dont want to bother you since I can connect, it is just that I wanted to connect the recommended way....network/interfaces file.

I will reinstall and get back to you with my findings.

Thanx again,

squibT

---

### Post by wieman01 on 2006-10-30
You don't need "ndiswrapper" if "eth1" connects fine. You can try "eth1" first of all. Please do a scan & post the results:
> iwlist scan

_**EDIT:**_
Only install "ndiswrapper" if your native Linux driver does not work. If "eth1" has issues, does not find your network, etc. then "ndiswrapper" is the right choice. "ndiswrapper" lets you make use of your Windows driver and deploys them. That's the difference between "wlan0" and "eth1". There is a good guide if "eth1" fails you & if "ndiswrapper" turns out to be the better choice: [http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

---

### Post by Naishy on 2006-11-01
This issue is documented at [Lauchpad]("https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983") 

I tried the suggested [solution]("https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/59983/comments/2") and it worked for me.

Basically, do the following:
```
sudo apt-get install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```

I then had to disable then enable my WiFi adapter using the keyboard function key. This was on a Dell X300 with a built-in Broadcom BCM4309 WiFi card.

Hope this helps....

---

### Post by aztechclan on 2006-11-07
Thanks, this last solution works great!  The problem is that it was using ndiswrapper 1.1 instead of 1.8.  Even a purge of the package (ndiswrapper-utils), and a re-install did not set 1.8 as the default.  I'm installing Edgy off a CDROM (no net link yet).

Again, thanks that's got me rolling.

---

