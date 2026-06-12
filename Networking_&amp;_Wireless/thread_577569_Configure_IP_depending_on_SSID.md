---
title: "Configure IP depending on SSID"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by Hero of Time on 2007-10-16
I'm having  some difficulties with my network. I want to set my IP address information depending to what SSID I'm connected to. At home, I use a static IP and at school they use DHCP. I'm kinda stuck on how to get only the SSID grepped. If I use 'iwconfig eth1 | grep ESSID', I get 'eth1 IEEE 802.11g ESSID: "home"' which is not what I want. I only need the "home" part. Then a variable will be made with the name of the SSID and runs trough a series of if statements. My script looks like this:
```
#!bin/sh
killall -q wpa_supplicant #needed if I brind the i-face down and up again
wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf
sleep 5 #gives wpa_supplicant the time to connect
wifi=$(/sbin/iwconfig eth1 | grep ESSID)

if [ $wifi == "home" ] ; then
   ifup eth1=home;
   cp /etc/resolv.conf.home /etc/resolv.conf; #needed for my dns server, dhclient overrules it and normal config won't set it
fi

if [ $wifi == "school" ]; then
   ifup eth1=school; #interface is set to dhcp in interfaces file
fi
```
Somehow, it doesn't work as it should. One of the reasons is the variable won't get set as it should. Other is that when running the script, I get errors about too many arguments or something in my if statements. I also tried to put the whole string of the iwconfig output to the varible and if statement, but that doesn't work either.

If someone knows what is going wrong, or has an other method that works, please post it. I think others are with the same thing.

---

### Post by spd106 on 2007-10-16
The easiest way would probably be use the Location switcher in the network-admin capplet (System -> Admin -> Network).

This allows you to switch between static and dhcp quite easily, though you still have open network-admin to switch location.

or if you really want to get your script working, have you tried using cut?

I think this might work
```
/sbin/iwconfig eth1 | grep ESSID | cut -d '"' -f 2
```

and don't bother with eth1=*, just have two copies of the interfaces file and swap the one you want in and call ifup.

I would also increase the sleep time to at least 15 secs

---

### Post by patrickfromspain on 2007-10-16
try wicd?

wicd.sourceforge.net

---

### Post by Hero of Time on 2007-10-16
> **patrickfromspain said:**
> try wicd?

wicd.sourceforge.net

Only problem is, I use wpa_supplicant for the autentication encryption used at school.


@spd106:
I prefer a singel interface file with the eth1=* option, as I connect to several wireless networks. I want to be able to change it without much hassle. When having multiple interfaces files I can lose track of the config files. Keeping everything in one file, it's much easier to maintain. Thanks for the cut parameter, I forgot how to use it properly. It does give me what I need, all I hope is that my variable can handle spaces (else I need to put single quotes around it).

---

### Post by Hero of Time on 2007-10-17
Ok, my script seems to work fine for what it looks like. Only problem is when I'm at a location with a space in the SSID. The variable is fine, but when I run it trough if ... I get an unexpected operator with the operator the name of the SSID after the space.

Edit:
Now that I've tested the script on an SSID that doesn't contain a space, The script doesn't what I expect it to do. Right now, this is what I have:
```
#/bin/sh
killall -q wpa_supplicant
wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf
sleep 5
wifi="'$(/sbin/iwconfig eth1 | egrep ESSID | cut -d '"' -f 2)'"
#killall -q wpa_supplicant
echo $wifi
if [ $wifi = "'Home'" ]; then
	ifup eth1=thuis;
	cp /etc/resolv.conf.thuis /etc/resolv.conf;
fi

if [ $wifi = "'hu-euduroam'" ]; then
#	wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf;
#	sleep 3;
	ifup eth1=school1;
#	dhclient eth1;
fi

if [ $wifi = "'Wireless Oud_370_D305'" ]; then
	ifup eth1=school2;
	dhclient eth1;
fi


```
The echo command works just fine, it displays what I want and that is 'ssidname' with the quotes. Only problem is that it doesn't seem to do what is needed after the if statement. In fact, it doesn't seem that it does the if at all. However, if I use the command prompt and type "if [ $wifi = "'hu-eduroam'" ]; then ifup eth1=school1; fi" it works, and also if I paste it in the script. What is going on here, the commands are the same.

---

### Post by Hero of Time on 2007-10-19
This is what I have now, and it seems to work for one small detail.
```
#/bin/sh

wpa_supplicant -Bw -Dwext -iwlan -c/etc/wpa_supplicant/wpa_supplicant.conf
sleep 5

wifi="'$(/sbin/iwconfig wlan | egrep ESSID | cut -d '"' -f 2)'"
#killall -q wpa_supplicant

if [ $wifi = "'home'" ]; then ifup wlan=home; cp /etc/resolv.conf.thuis /etc/resolv.conf;

elif [ $wifi = "'hu-eduroam'" ]; then ifup wlan=school1;

elif [ $wifi = "'Wireless Oud_370_D305'" ]; then ifup wlan=school2;

fi

```
Wpa_supplicant starts, but it doesn't associate with any accesspoint (at least not my home AP). When I put the wpa_supplicant in my interfaces file, it associates.
I also want to know what interface methods are available. All I know is static, dhcp and manual. Are there more than those?

---

### Post by Hero of Time on 2007-10-30
Ok, I've found out why it won't associate at startup using my script. There is one thing I hate and the boot sequence needs to finish first and that is cancel my ipw3945 from associating. Upon boot, after I get the graphical login screen, I see the following line come up after a minute or so:
```
ipw3945: association process canceled
```
Is there a way to force this sooner or not happen at al? After I get this message, I can run my script and it will work. When I associate using the interfaces file, it won't happen. Any ideas?

---

