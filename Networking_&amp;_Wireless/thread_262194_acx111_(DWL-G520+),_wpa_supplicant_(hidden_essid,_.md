---
title: "acx111 (DWL-G520+), wpa_supplicant (hidden essid, TKIP) and dhcp"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by MadeR on 2006-09-21
Greetings, I'd like to share my experience with a D-Link DWL-G520+ wireless card, based on Texas Instruments ACX111 chip.
My native language is Italian, so there surely are many errors in this text!

I'm a linux newbie (though I could say quite the opposite with FreeBSD) and this is my first guide, so if there are more correct or smart ways to modify the system files, tell me!

The whole process of making it work was very tricky, manly due to HW/SW and SW/SW problems.

I did not success to use acx.
I used both the standard Dapper acx modules and cvs ones.
I used all kind of firmwares, the standard (buggy) 2.3.1.31 and the supposedly working 1.2.1.34 and also the firmware packaged in the windows drivers.
Nothing at all.

The only solutions was ndiswrapper
```
sudo apt-get install ndiswrapper-utils
```then you have to find the WindowsXP drivers of your wireless card; it's a bunch of .bin, .sys., .cat, .inf or .ntf files.
put them all in a directory, then in that same directory run:
```
sudo ndiswrapper -i *driver_inf_file*
```then you have to associate the driver to the PCIID. To obtain the device ID run:
```
lspci -n | grep `lspci -vv|grep "ACX 111"|cut -d\  -f1` | cut -d\  -f3
```*note on -d\  -f*: there are 2 spaces between \ and -

To know the driver's name: 
```
sudo ndiswrapper -l
```then ```
sudo ndiswrapper -d *PCIID driver_name*
```let's unload the acx driver and replace it with ndiswrapper:
```
sudo modprobe -r acx
sudo modprobe ndiswrapper
```Sometimes ndiswrapper causes a kernel panic; in this case reboot and try again loading the ndiswrapper module: the crash does not happen always.

Now we have to make sure that:
1) acx won't be loaded automatically when /etc/network/interfaces is read;
2) ndiswrapper module will be loaded instead.

#1: add the following line to /etc/modprobe.d/blacklist
```
sudo vim /etc/modprobe.d/blacklist
``````
*blacklist acx*
```#2
```
sudo ndiswrapper -m
```then
```
sudo depmod -a
```now we can try wpa_supplicant.
if your ESSID is hidden, wpa_supplicant won't connect unless (strangely) you set ESSID also via iwconfig.

create your /etc/wpa_supplicant/wpa_supplicant.conf
```
sudo wpa_passphrase *ESSID*
```copy and paste the output to /etc/wpa_supplicant/wpa_supplicant.conf

then add:
```
network={
        bssid=[COLOR=Purple]MAC_ADDRESS[/COLOR]
        ssid="[COLOR=Purple]SSID[/COLOR]"
        scan_ssid=1
        auth_alg=OPEN
        key_mgmt=WPA-PSK
        proto=WPA
#       psk=[COLOR=Purple]"ASCII Password"[/COLOR]
        psk=[COLOR=Purple]*hex password*[/COLOR]
        pairwise=TKIP
        group=TKIP
}
```then the trick, before running wpa_supplicant, issue the following command:
```
sudo iwconfig wlan0 essid [COLOR=Purple]SSID[/COLOR]
``````
sudo wpa_supplicant -c /etc/wpa_supplicant/wpa_supplicant -Dwext -iwlan0 -d
```if it connects, keep reading this guide :)
note: I only said «connects», is it "normal" that packages do not flow through the connection!

modify /etc/network/interfaces:
```
auto wlan0
iface wlan0 inet dhcp
pre-up iwconfig wlan0 essid avalon && wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```let's talk about dhclient: i did not manage to make it work with my wlan0 connection.
no way.
I had to replace it with "pump" another dhcp client of ubuntu:
```
sudo apt-get remove dhclient
sudo apt-get install pump
```Now everything will hopefully work.
I have only one small question: pump does not send the pc name, so my AP tells me "/Object Not Found"?!?!?


DHCP Active IP Table for LAN
DHCP Server IP Address:  
[FONT=Courier New]192.168.158.1   
# Client Host Name    IP Address       MAC Address    
1 traktor           192.168.158.203 00:13:02:07:3e:b9    
2 aurin             192.168.158.202 00:c0:49:55:90:1b    
3 /Object Not Found 192.168.158.201 00:11:95:47:07:6b[/FONT]

I think the solution is the --win-client-ident option for pump: does anybody tell me how to write the /etc/pump.conf file to solve this problem? the man page is horribly written... thank you!

---

### Post by compwiz18 on 2006-12-01
hello,

Great guide, thanks.  I'm not trying to setup this card, but I was trying to figure out how to use WPA and a hidden ESSID, and your guide is great for this purpose too.  As for your question, dhclient doesn't send the name of the computer either, so...I can't help you there, sorry.

---

### Post by manic007 on 2007-05-01
I'd like to point out that this is the only solution that worked for me under Feisty Fawn using this exact card. I upgraded from Edgy (wireless worked flawlessly under Edgy using this same solution).

However, I couldn't get network manager to work under Feisty despite various modifications to the above code (i.e. commenting out everything in interfaces script; modifying using this guide:

[http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA+G520%2B](http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA+G520%2B)  ).

Fortunately Wifi-radar works "reasonably well" with this solution.

There is just one cavet - the ndiswrapper (version 1.9) that I downloaded using apt-get did *not* work for me. When issusing the command

```
sudo ndiswrapper -d PCIID driver_name
```

I recieved error messages saying that the symbollic link already exists (I made sure I uninstalled v1.8 of ndiswrapper since this is known to have problems in Feisty and the old ndis kernel modules from edgy were removed, but to no avail). Instead I had to download the latest tar ball from the [ndiswrapper homepage]("http://ndiswrapper.sourceforge.net/joomla/") and everything worked peachy :)  (except I couldn't use checkinstall with the ndis tar ball :( but I'll just have to remember that I have it installed from source when I next dist upgrade :-? )

But in general this is by far the best solution!

---

### Post by compwiz18 on 2007-05-01
> **manic007 said:**
> I'd like to point out that this is the only solution that worked for me under Feisty Fawn using this exact card. I upgraded from Edgy (wireless worked flawlessly under Edgy using this same solution).

However, I couldn't get network manager to work under Feisty despite various modifications to the above code (i.e. commenting out everything in interfaces script; modifying using this guide:

[http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA+G520%2B](http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA+G520%2B)  ).

Fortunately Wifi-radar works "reasonably well" with this solution.

There is just one cavet - the ndiswrapper (version 1.9) that I downloaded using apt-get did *not* work for me. When issusing the command

```
sudo ndiswrapper -d PCIID driver_name
```

I recieved error messages saying that the symbollic link already exists (I made sure I uninstalled v1.8 of ndiswrapper since this is known to have problems in Feisty and the old ndis kernel modules from edgy were removed, but to no avail). Instead I had to download the latest tar ball from the [ndiswrapper homepage]("http://ndiswrapper.sourceforge.net/joomla/") and everything worked peachy :)  (except I couldn't use checkinstall with the ndis tar ball :( but I'll just have to remember that I have it installed from source when I next dist upgrade :-? )

But in general this is by far the best solution!
I might be wrong, but I think that you can just distupgrade right over the ndiswrapper source, and that should take care of it.

---

### Post by manic007 on 2007-05-13
That would be SOO cool! Its always been my personal grip about certain "older" distros (no names mentioned) . Well, I look forward to testing this theory in 6months time :)

---

