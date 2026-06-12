---
title: "WPA Network issue"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by runt on 2008-03-23
Ok,
I can connect to my WiFi network that uses WPA-PSK without a problem.  However I'm at my parent's today and cannot connect to theirs which also uses WPA-PSK.  The only major difference other than the SSID & key is the fact that my parents have a D-Link DI-524 and I have a Linksys WRT54g running DD-WRT firmware.  When I try to connect to my 'rents wireless it looks like it will work, but ends up not working.  The directions (from the Ubuntu WIKI) said to setup a /etc/wpa_supplicant.conf but it doesn't matter if I remove the info for my network or not.  I know that my WiFi card needs to ndiswrapper as Realtek saw fit to give it a different PID than normal for it (RTL8187B).  Also, my key has two spaces and my 'rents key has no spaces.  Does anyone have a clue what could be wrong?

---

### Post by kevdog on 2008-03-23
Can you post your wpa_supplicant.conf file?

---

### Post by runt on 2008-03-23
sure, here it is.

```
network={
        ssid="runt"
        psk=72073e9b17235377a4ce53ac74d0059082b7d3815fa062c1f9f2bc9a0284aaef
}

network={
        ssid="lakeview"
        psk=9432baa6a649fc096294196b0343c7a4a78958b970412d120259e8c83de01970
}
```

---

### Post by kevdog on 2008-03-23
Ok, so your wpa_supplicant.conf file is incorrect.  Here take a look at this other thread I wrote that tells in detail how to compose the wpa_supplicant.conf file:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by runt on 2008-03-23
> **kevdog said:**
> Ok, so your wpa_supplicant.conf file is incorrect. Here take a look at this other thread I wrote that tells in detail how to compose the wpa_supplicant.conf file:
 
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
 
so i would do?  why would my network work fine and my parents wouldn't?
```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="runt"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="blablabla"
        pairwise=TKIP
        group=TKIP
}
 
network={
        ssid="lakeview"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="blablabla"
        pairwise=TKIP
        group=TKIP
}
```

---

### Post by kevdog on 2008-03-23
Yes I think you would do that.  Your setup is for WPA(1).  

One downside to linux is networking.  You cant expect any solution to work 100% of the time.  Meaning be versatile, learn different methods, and employ the different methods in case something doesn't work.

---

### Post by runt on 2008-03-23
> **kevdog said:**
> Yes I think you would do that. Your setup is for WPA(1). 
 
One downside to linux is networking. You cant expect any solution to work 100% of the time. Meaning be versatile, learn different methods, and employ the different methods in case something doesn't work.
 
thats why i'm thinking of dualbooting ubuntu and vista..............

---

### Post by kevdog on 2008-03-23
Sure why not??  Or when you get really good at Ubuntu you will have about 5 different ways to make a connection.

---

### Post by runt on 2008-03-23
> **kevdog said:**
> Sure why not?? Or when you get really good at Ubuntu you will have about 5 different ways to make a connection.
 
well, i used to be able to install gentoo without reading the directions..............

---

### Post by runt on 2008-03-23
ok, working so far.  but i'm at home again.  i would like to know if there is a way i can store the keys in an encrypted format as i don't like the idea of them being unencrypted even though i doubt anyone will use my laptop.

---

### Post by kevdog on 2008-03-23
Yes there is:

Courtesy of Weiman01:

VERY IMPORTANT:
Now convert your WPA ASCII password using the following command:
Quote:
wpa_passphrase <your_essid> <your_ascii_key>
Resulting in an output like...
Quote:
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
}
Copy the "hex_key" (next to "psk=...") and replace <your_hex_key> in the "interfaces" files with it. Then save the file and restart your network:

The hex_key doesn't need to be in quotes in the wpa_supplicant.conf file :)

---

### Post by runt on 2008-03-23
> **kevdog said:**
> Yes there is:

Courtesy of Weiman01:

VERY IMPORTANT:
Now convert your WPA ASCII password using the following command:
Quote:
wpa_passphrase <your_essid> <your_ascii_key>
Resulting in an output like...
Quote:
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
}
Copy the "hex_key" (next to "psk=...") and replace <your_hex_key> in the "interfaces" files with it. Then save the file and restart your network:

The hex_key doesn't need to be in quotes in the wpa_supplicant.conf file :)


i thought that was what i needed to do, i just wanted to make sure.  i am still kinda afraid of breaking my system, that is the reason i have yet to upgrade to 8.04 even though i want to in order to get my webcam working.

<edit>
really helps not to type == instead of = :doh:
</edit>

---

