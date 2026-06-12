---
title: "WG111v2 Wireless issues in 6.10 edgy"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by zephyrcat on 2007-01-10
Hi! I am currently booting off a CD on a PC with a Netgear WG111v2 wireless adapter connecting to a wireless network with a **128-bit WEP** encryption (in bold, because this seems to be an issue). A "wireless connection" shows up, but I am not able to type in my full password. Since it is 128-bit it is quite long and the password field has a max length of less then the 128-bit length. I have also tried the terminal equivalent of that (iwconfig wlan0 key blahblahblah), but I get an error message:
```
Error for wireless request "Set Encode" (8B2A):
SET failed on device wlan0 ; Operation not permitted.
```
I do not have a wired internet connection and and I cannot easily get one due to the the way my network is setup. Does anyone know what I should do? I could also do this on an intel-based iMac, would that be easier?

---

### Post by phossal on 2007-01-10
What is the error message?

---

### Post by zephyrcat on 2007-01-10
The error was:
Error for wireless request "Set Encode" (8B2A):
SET failed on device wlan0 ; Operation not permitted.

---

### Post by phossal on 2007-01-10
Will you post the command you're using?

---

### Post by zephyrcat on 2007-01-10
I did (see first post). Here it is again:
iwconfig wlan0 key blahblahblahthekeygoeshere

---

### Post by phossal on 2007-01-10
No sudo? And, that's not the command you're using. That's "blahblahblahthekeygoeshere". Are you actually using a 26-digit hex key, or are you supplying a password? For the sake of addressing the problem, you could *change* your key/password. I trust you're not guilty of it, but it would be helpful to see the actual commands to rule out syntax problems. The smartest guys can make the dumbest mistakes.

---

### Post by zephyrcat on 2007-01-10
Nope, I was just trying to give it the full WEP.

---

### Post by phossal on 2007-01-10
```
bash 3.1:iwconfig wlan0 key 578
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not permitted.
```

I generate this error when I don't enter the 26-digit hex key. As you can see, I used 3 digits. I also generate this error when I don't use sudo.

When I enter the 26-digit key *and use sudo*, it connects without error.  Example:
```
bash 3.1:sudo iwconfig wlan0 key 57835756472222222222222222
bash 3.1:
```

---

### Post by zephyrcat on 2007-01-10
I just tried that. I do not get an error when I do that, but nothing happens and I still don't have internet. Any other ideas?

---

### Post by phossal on 2007-01-10
If you didn't get an error, it set the key. Now try*: 
[SIZE="1"][COLOR="DimGray"]*taking for granted you set the other parameters: *essid*, etc.[/COLOR][/SIZE]
```
sudo dhclient wlan0
```

iwconfig allows you to set the parameters for the interface. You still need to "bring the network up", by using a command like *dhclient*, which essentially asks the network for an IP address. If you find you're still not connecting, post the output.

---

### Post by zephyrcat on 2007-01-10
I tried that and here is what I got:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:14:6c:6c:b1:59
Sending on  LPF/wlan0/00:14:6c:6c:b1:59
Sending on  Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.

I hope I got that all right, I have to hand type this, because I have no internet from Ubuntu .

---

### Post by phossal on 2007-01-10
Have you successfully connected without wep/wpa enabled?

---

### Post by zephyrcat on 2007-01-10
Ahh... stupid me, missed setting the essid (removed it before since not working anyway). This is what I typed:
> sudo iwconfig wlan0 essid networkname
sudo iwconfig wlan0 key networkkey
sudo dhclient wlan0

At this point I got a very similar message. It was identical except for at the beginning it said:

There is already a pid file /var/run/dhclient.pid with pd 14876
killed old client process, removed PID file

And then continued on to the rest of the message. Also, the intervals were 4, 11, 21, 18, and 7, but I doubt that matters.

---

### Post by zephyrcat on 2007-01-10
Sadly, I cannot try that. :-( Multiple computers use this network.

---

### Post by phossal on 2007-01-10
How did you install it? Did you use a tutorial, or just plug it in?

---

### Post by zephyrcat on 2007-01-10
I am currently running off a CD that I just burnt today. I don't know if it matters, but the Networking application in System > Administration is not showing any of these changes.

---

### Post by phossal on 2007-01-10
Okay, many people have trouble with this adapter.  There are two choices for installation. I almost always recommend the 2nd, using ndiswrapper, but I know you're not connected.


[B]
Method 1:[/B] The device is plug and play, but you have to blacklist a couple drivers. Example:

Blacklist existing drivers.*
```

sudo gedit /etc/modprobe.d/blacklist

```

Copy and paste the following to the bottom of the file. Save it. Close it.
```

#wg111v2 conflicting drivers
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b

```

Insert the wg111, and then reboot. 


**Method 2:** The device requires ndiswrapper, and requires set up as shown in [this tutorial]("http://ubuntuforums.org/showthread.php?t=329299")

---

### Post by zephyrcat on 2007-01-10
Will I be able to do this without an internet connection?

---

### Post by phossal on 2007-01-10
Not method 1.

---

### Post by zephyrcat on 2007-01-10
Ok. So I should just use method 2? BTW Thank you so much.

---

### Post by zephyrcat on 2007-01-10
Method 2 seems to need an internet connection, I just tried method one and it did not work. :-(

---

### Post by phossal on 2007-01-10
Method 2? You can download everything you need on another computer, but you will have to compile your own ndiswrapper. I wouldn't want to do it that way. :(

---

### Post by zephyrcat on 2007-01-10
Would you mind telling me where to get it and what to do and such or point me to another tutorial?
Again, thank you so much.

---

### Post by phossal on 2007-01-10
type: 
```
lsusb | grep NetGear
```
 
post the output

---

### Post by zephyrcat on 2007-01-10
Bus 004 Device 003: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

---

### Post by phossal on 2007-01-10
[Download this wg111v2 driver]("ftp://downloads.netgear.com/files/wg111v2_1_3_0.zip")

You're connected to the internet, so you can get everything you need. I don't know what way of installing ndiswrapper is easiest. You can build an rpm or something on another system, and then install it on the target, or you can download the source files and compile it on your own. Whatever method you use, you need it. You might ask in another thread for some advice. Once ndiswrapper is installed, getting the hardware working is a snap.

---

### Post by zephyrcat on 2007-01-10
Ok. Should I extract it or move it to Ubuntu first?

---

### Post by phossal on 2007-01-10
Move it. And then hold short. lol I have a thread open to see how we get you ndiswrapper. Do you know how to compile it on your own or build an rpm? If not, we'll have to wait until we get answers.

---

### Post by phossal on 2007-01-10
Check this out... [ndiswrapper]("http://ubuntuforums.org/showthread.php?t=335853"). 

With the live cd, the driver, and ndiswrapper, follow the tutorial for method 2 below. Good luck. ;)

---

