---
title: "TL-WN321G doesn't work - driver installed"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by th3.w1z4rd on 2008-03-13
Hello,
i followed the guide found [here ]("http://ubuntuforums.org/showthread.php?t=694726&highlight=wn321g") and installed the drivers for my TL-WN321G under Ubuntu 7.10.
They seems to work properly but, if i try to connect using **sudo /etc/init.d/networking restart**, it gives me this output:

There is already a pid file /var/run/dhclient.wlan0.pid with pid 5733
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:e0:89:1c:b8
Sending on   LPF/wlan0/00:19:e0:89:1c:b8
Sending on   Socket/fallback
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:e0:89:1c:b8
Sending on   LPF/wlan0/00:19:e0:89:1c:b8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directory



I have a wireless network with WPA2 protocol, DHCP for automatic IPs, a password long about 22 characters and my **/etc/network/interfaces** file is that

auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wpa-psk 0a15f68fd29d2b4eedc5107658b81c5f939b3d6d004d86f293b2493b87a75289
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid TWIZ

auto wlan0


I didn't edit it, just used the managing visual tool given with ubuntu...
how can I solve this problem? I haven't a cable to the router and this device is the only way I can use to connect...thank you :)

---

### Post by {BzF}~JOKesTER on 2008-03-13
Easiest Way Is To Go To The "Add/Remove" Tab Under Applications Menu And Install "Windows Wireless Drivers"

Run The Program And Browse To Your Drivers .inf File And Install It - Now Restart Your Computer And All Should Work!

Hope This Helps!:)

---

### Post by th3.w1z4rd on 2008-03-13
I can't find Install Windows Wireless Driver in Add/Remove GUI :( have I to load the windows drivers downloaded frome the TP-Link site? if yes, how can I do? :( sorry, I'm a really new new newbie :(

---

### Post by {BzF}~JOKesTER on 2008-03-13
Open A Terminal And Type:

sudo apt-get update

Now Hit Enter

Now Type:

sudo apt-get install ndisgtk

And Hit Enter

And Now Follow My Other Instructions!!

Hope This Helps Ya A Bunch!:)

---

### Post by th3.w1z4rd on 2008-03-13
I haven't an active internet connection on Ubuntu, I'm using my nb, right now, on my desktop (where Ubuntu is) I have no network connections...I can use apt-get insering the Ubuntu installation CD and then do as you told me to?

---

### Post by {BzF}~JOKesTER on 2008-03-13
Unfortunately Probably Not...

You Can Try - But I Don't Think It Will Work.

I Would Temporally Hardwire Its Connection If You Can...

---

### Post by th3.w1z4rd on 2008-03-13
there's no other way? :(

---

### Post by th3.w1z4rd on 2008-03-14
I did apt-get update (placing my case near the router) and all goes well... but when I try to type
apt-get install ndisgtk
it says me
Impossible to found ndisgtk...
why?!

---

### Post by th3.w1z4rd on 2008-03-14
I've installed also the ndisgtk...but it doesn't work!!!
I downloaded the windows driver for my TL-WN321G, but it doesn't install at all :(
Help!!!

---

### Post by {BzF}~JOKesTER on 2008-03-14
Ok Dude.

I'll Try And Make This As Easy As Possible.:)

First Under The "Applications" Menu On The Toolbar.

Click "Add/Remove" 

Now In The "Filter" Bar At The Top Left Corner Type:

windows wireless

Now It Will Search....

In The Right-Hand Pane You Will Se A Check Box Next To The "Windows Wireless Drivers" Install - Check That Box.

Now Hit "Apply"

And It Will Download And Install For You!!!

Ok,

Next Go to "Control Center" And Find The "Windows Wireless Drivers" Entry Inside There.

Click It.

Now Click The "Add New Driver" Button - This Will Open A Dialog Box.

Download The Attached Drivers - To Your Desktop.

Now In That Box - Extract The Downloaded Drivers To Your Desktop- {By Right Clicking It And Clicking "Extract Here"}

Now In That "Add New Driver" Window - Browse To Your Desktop
And The Extracted Folder - And Double-Click On "rt73.inf" {You May Have To Click "Add"}

And Thats It!!!

Now Restart Your Computer.:)

Hope This Helps - IF I Does Please Hit "Thanks" As Much As You Can!!!:)

---

