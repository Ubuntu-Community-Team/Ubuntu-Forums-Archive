---
title: "Yet another wireless networking problem"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by colin winters on 2006-11-19
Hello, I've been running ubuntu for some time with wireless networking.  I never really understood how I set up the wireless, but it worked fine for some time.  However, last week I found that the wireless network stopped working, and I have been unable to figure out what has happened.  The router itself is working fine right now, as I am typing on a laptop connected to it.  I'm having two main problems:  Not getting iwconfig to consistently register the essid, and dhclient is failing to get a dhcpoffer 100% of the time.

Pertinent info:
I have a belkin usb wireless router, and it's set up with the rt73usb module with ndiswrapper.  
Ndiswrapper -l returns:
Installed drivers:
rt73         driver installed, hardware present 

iwlist wlan0 scan    shows the router I wish to connect to, so I'm pretty sure my hardware is fine.
However, the iwconfig settings I previously used seem to not work now.
I've tried just this:
iwconfig wlan0 essid "My AP" key the26charsfor128bit
When I do that, iwconfig returns ESSID:off/any-clearly this isn't going through.  Even if I add in ap theapstring to the end of that line, it doesn't register.  
However, if I change the mode to ad-hoc, it goes through fine.  But iwlist reports the router's mode as managed-I'm not sure what this means.

Sometimes, through repeated iwconfig commands (i've done this for hours and can't even remember what I've done anymore), I'm able to get the ESSID to register properly.  I have no idea what this means, as I'm pretty sure that it's incorrect to set that. If I then set the mode to managed it seems to stick.  However, at no time does iwconfig list anything about encryption.

Furthermore, I turned off WEP momentarily, and tried configuring the device that way, but it still didn't work.

I'm able to get link quality to be 100/100 when iwconfig correctly registers what I tell it, but dhclient absolutely fails to connect, and I don't understand why iwconfig refuses to output anything about encryption (which iwlist shows as enabled on the router).

Also, I've tried using /etc/network/interfaces, and here's the info there:
iface wlan0 inet dhcp
wireless-essid "My AP"
wireless-key 26digits
wireless-mode managed   (i've tried it without this too)
auto wlan0

Doing a /etc/init.d/networking restart still fails to get any dhcpoffers.

Sorry that this is so rambling, and thanks for any advice that anyone can provide.

---

### Post by dmizer on 2006-11-20
some cards like to have the commands hit them more quickly.  i know my linksys card did.  you can string the whole set together like so:
```
sudo ifdown wlan0&& sudo iwlist wlan0 scan&& sudo iwconfig wlan0 essid "Your AP" mode Managed key the26charsfor128bit&& sudo ifup wlan0
```

see if that gets more consistent results for you

---

### Post by colin winters on 2006-11-20
Stringing the commands doesn't seem to work-for some reason, I'm back to getting 0/100 link quality (a problem I've had before) too.    Furthermore, isn't ifup essentially replicating what I'm typing in iwconfig, except it's using /etc/network/interfaces?

---

### Post by FrodoB on 2006-11-20
Colin;

You said

 Pertinent info:
I have a belkin usb wireless router, and it's set up with the rt73usb module with ndiswrapper.

There is part of the problem. If you use ndiswrapper you cannot use the rt73usb module, the two conflict with each other.

The rt73usb module include in Edgy is broken, to use it remove ndiswrapper completely and install according to:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview)


If you want to remain with ndiswrapper you need to blacklist the rt73usb module in /etc/modprobe.d/blacklist:

$ sudo gedit /etc/modprobe.d/blacklist

Add there lines to the bottom of the file:

# Blacklist these just in case we add the rt73 or use ndiswrapper
blacklist rt73usb
blacklist rt2570

Just trying blacklisting first may fix your ndiswrapper if it is installed correctly.

---

### Post by colin winters on 2006-11-20
Thank you very much Frodo.  I simply put in the two blacklist lines, removed rt73usb, unloaded and reloaded ndiswrapper, and did the minimal wireless config I used to use (iwconfig wlan0 essid "my ap" key keystring && dhclient wlan0) and it worked :)

I'm very curious as to how they were conflicting but I was still able to scan.

---

### Post by FrodoB on 2006-11-20
Well, I can't answer that, but the symptom you describe is often indicative of driver contention. I have experienced it myself between rt73usb and the rt73 native driver and it worked like that as well.

---

### Post by colin winters on 2006-11-20
One other thing-it appears I have my /etc/network/interfaces set up wrong, as ifup won't activate the card right.  I'm thinking it's syntax problems.  the essid has spaces in it, is it correct to do it as "My AP" or do I use My_AP?  Also, do I use a dash or an underscore for the wireless-essid and wireless-key settings?

---

### Post by FrodoB on 2006-11-20
I don't know that it will hurt. I am using the rt73 native driver and it dones not require quotes around my ESSID which contains spaces.

You are using the ndiswrapper thought, correct?

---

### Post by colin winters on 2006-11-20
Yes, I'm just using ndiswrapper-it's working fine.  The reason I'm wondering about syntax is that iwconfig seems to be very picky about it, and I wasn't sure if /etc/network/interfaces used the same syntax rules :)

---

### Post by FrodoB on 2006-11-20
The scripts that read the interfaces file try to do the quoting for us I believe. On the other hand I do not think that using them will hurt, you could try it and see if it makes any difference.

---

