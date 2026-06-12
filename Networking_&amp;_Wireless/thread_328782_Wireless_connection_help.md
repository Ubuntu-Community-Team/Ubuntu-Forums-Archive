---
title: "Wireless connection help"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by potosynthesis on 2006-12-31
Hi! I am complety new and I have Xubuntu 6.10. I wish to have wireless connection. My card is

Linksys Wireless-G
Model No WPC54GS ver. 2

If anyone could help me getting connected with above card it would be greatly appreciated. Please, since I am new, give me step-by-step instructions.

Thanks.

---

### Post by SugarDaddy on 2006-12-31
Hi potosynthesis, there are lots of ways to configure a wireless router: unsecure, WEP, WPA, WPA2. Each of these requires slightly different steps to configure properly. What I can tell you is that the most secure, latest and greatest, encryption technology is WPA2 with AES (you might want to update the firmware of your router if WPA2 is not available, check the documentation of your router on how to choose the encryption and update the firmware).

So assuming you know how to setup the wireless router for this encryption including SSID and password, the next step is to setup your WiFi card to connect to the router. There are numerous threads that help with setting up the WiFi card. The first is the HowTo at the top of this forum. The second and third are additional helps that are useful for troubleshooting, etc.

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
[http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)
[URL="http://ubuntuforums.org/showthread.php?t=324545"]http://ubuntuforums.org/showthread.php?t=324545
[/URL]
Hope this helps!

---

### Post by potosynthesis on 2007-01-01
I am having some trouble with aptitude.

```
danielle@dubuntu:~$ aptitude search wpa
i   wpasupplicant                   - Client support for WPA and WPA2 (IEEE 802.
danielle@dubuntu:~$ sudo aptitude install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
danielle@dubuntu:~$ 
```

I don't know what to do if I can't install wpasupplicant.

---

### Post by SugarDaddy on 2007-01-01
If your computer isn't connect to the net through a wired connection then you will need to download the wpa_supplicant .deb package from a computer that does have internet access, transfer the file to your ubuntu machine using a flash drive or CD-RW, then install the .deb. However, this method requires you to resolve dependencies on your own if there are any (these are other .deb packages that wpa_supplicant may require to be installed before it will install, and sometimes these dependecies can be quite long). You will instantly know if and which dependencies are needed when you first try to install the wpa_supplicant deb. Just go get the missing debs, eventually you will resolve them all and get wpa_supplicant installed. Here are some quick steps to get you started:

Go to the following site and find the wpa_supplicant .deb package:

[http://packages.ubuntu.com/edgy/](http://packages.ubuntu.com/edgy/)

Download it and transfer it to a location. I prefer /home/user/debs

Then type the following command in a terminal:
```
dpkg -i package_name.deb
```

---

### Post by Pobega on 2007-01-28
<Edit> Nevermind.

---

