---
title: "Ralink RT73 USB stalls system"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by wilbertnl on 2007-06-29
Hello All,

Last night I installed and updated Ubuntu 7.04/Feisty Fawn on my ancient HP Omnibook XE3-gf and I found out that when I boot with wired network, Ubuntu performs well.
But when I plug in a Ralink RT73 usb wireless network, the mouse and the system respond very slow, When I disconnect the wireless usb, the system freezes.

I haven't modifiied the Ubuntu setup yet, neither the RT73 driver setup.
Is there any way that I can make this wireless USB work with Ubuntu?

Thank you.

---

### Post by odiseo77 on 2007-06-29
Hi, I have a rt2500 based card and it works like a charm on Feisty. I searched on the serialmonkey forums for your card and I found [this thread]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3660&") that can be usefull; for what they say, it seems you must blacklist the rt73usb, rt2570, rt2x00lib modules and install the [rt73 cvs driver]("http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz").

Greetings, and good luck.

Oh, and for other thread I saw, you have to install the kernel sources for your kernel in order to compile the driver.

---

### Post by wilbertnl on 2007-06-29
Thank you very much, odiseo77,

I'm considering the purchase of a different wireless adapter. I have much better results with a Altheros chip.
Maybe I give the suggested solution a try before I order something else.

---

### Post by odiseo77 on 2007-06-29
Hi, I don't know about Atheros cards, but rt2500 based cards work like a charm on ubuntu (you can find the list of supported cards [here]("http://rt2x00.serialmonkey.com/wiki/index.php/Hardware#rt2500")).

Greetings, and good luck!!

---

### Post by wilbertnl on 2007-06-30
Well, I'm now online through the RT73 wireless.
The suggestions worked well.

Thank you very much for encouraging me,  odiseo77.

Now I need to find the document that explains how to make this WPA enabled network connection permanent. (for now I typed the commands from the README).

Again, thank you very much!

---

### Post by odiseo77 on 2007-06-30
Hi, glad you got it working! :)  As for WPA, I'm not sure (I'm using WEP, though I think I'm gonna switch to WPA in the next days), but maybe [this]("http://doc.gwos.org/index.php/WirelessSec") could work?

Greetings, and good luck!

---

### Post by wilbertnl on 2007-07-02
> **odiseo77 said:**
> (I'm using WEP, though I think I'm gonna switch to WPA in the next days)
It seems that the fastest way to get WAP working with the Ralink adapter is by installing [RutilT]("http://cbbk.free.fr/bonrom/").
It offers a GUI front end to WAP setup.
And it is working allright on my system.

---

### Post by twistie on 2007-07-02
I had the exact same problem. But whenever I enabled the driver it would stop and keyboard and mouse communications with the computer. The computer wouldn't freeze it would just rather be useless!

---

### Post by odiseo77 on 2007-07-02
> **wilbertnl said:**
> It seems that the fastest way to get WAP working with the Ralink adapter is by installing [RutilT]("http://cbbk.free.fr/bonrom/").
It offers a GUI front end to WAP setup.
And it is working allright on my system.

Hi, precisely a few hours ago I changed to WPA, tried with the guide I posted above, but it didn't work at all. Then I saw your post and installed RutilT. It's a very usefull tool; detected my AP and connected using the WPA key, but the only problem is I'm using a PC (not a laptop), so I need my machine to automatically connect to my router upon boot (something RutilT doesn't seem to do; I had to manually start it and connect to my router every time I rebooted my PC; anyway, it's an excellent tool for laptops which connect to different AP's). So I searched on google and found an article (in spanish) explaining how to setup a WPAPSK connection with the rt2500 driver. If anyone's interested, basically what I did was to edit the /etc/network/interfaces file and put the following info in it:

```
auto ra0
iface ra0 inet dhcp
pre-up iwconfig ra0 essid MYESSID
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set Channel=11
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK=MYPASSWORD
pre-up iwpriv ra0 set TxRate=0
```

Then ran ***sudo ifdown ra0*** and ***sudo ifup ra0***; rebooted to test it, et voilà :)


> **twistie said:**
> I had the exact same problem. But whenever I enabled the driver it would stop and keyboard and mouse communications with the computer. The computer wouldn't freeze it would just rather be useless!

Hi, I'm not using the same adapter you have, so I can't be very useful here, but did you try the above? (see my first post).

Greetings.

---

### Post by kevdog on 2007-07-03
Im assuming to use WPA that the wpasupplicant package needs to be installed.

Additionally can you clarify the Password Parameter?

> 
pre-up iwpriv ra0 set WPAPSK=MYPASSWORD


Is the the password hex or ASCII?

If hex, is this how you convert to hex?

> 
wpa_passphrase 'your_essid' 'your_ascii_key'


Resulting in an output like...
> 
network={
ssid="test"
#psk="12345678"
psk=fe727aa8b64ac9b3f54c72432da14faed933ea511ecab1 5bbc6c52e7522f709a
}


In the above the hex-key would be the value of psk=.

---

### Post by odiseo77 on 2007-07-03
Hi kevdog, as for the password, I put it in ASCII format, but according to the [source]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500") of the document I took this info from, it should be in hexadecimal (look for item 3.2: WPA info), so, I think I'll changed to a hex key tomorrow for security reasons.

As for the wpasupplicant package, you don't have to worry about it if you're on feisty, since I guess it comes installed by default (I don't remember having installed it, and it was already installed when I was about to configure my connection) :)

Greetings.

EDIT: yes, either the hex key or the ASCII key will work, but I guess the hex key is more secure.

---

### Post by wilbertnl on 2007-07-03
> **kevdog said:**
> Additionally can you clarify the Password Parameter?
Is the the password hex or ASCII?
If hex, is this how you convert to hex?

To generate your password, do this:
```
wpa_passphrase <SSID of your router> <your password>
```
Discard the < and > here.
The command will generate the password for your that you can copy and paste.
The output would would look like this:
```
network={
        ssid="MyHomeWireless"
        #psk="SuperSecretPassphrase"
        psk=e42ac2538ef03f906d37332a0df4446150e04cdcdd392e309486075065a70a1f
}
```

---

### Post by kevdog on 2007-07-03
wilbertnl

How did the gui compilation, installation go? Was this the ruitl package that comes in the downloaded tarball with the drivers??  Could you post any screen shots??

Thanks

---

### Post by wilbertnl on 2007-07-03
Compilation and installation are quite simple.
```
sudo su
./Configure
make
make install
```
It installs the application in /usr/local/bin and I found "RutilT WLAN manager" automatically added to my XFCE menu.
See attachment for the screenshot.

---

### Post by kevdog on 2007-07-03
Last question and I'll stop bugging you.  I saw the changes on the previous page that needed to be done to the interfaces file.  Did you uninstall network manager anywhere along the way???  Also at startup or boot, does anything need to be added to the rc file, or do you any any way have to bring the network up manually or start rutilT manually?

---

### Post by wilbertnl on 2007-07-03
> **kevdog said:**
> Did you uninstall network manager anywhere along the way???  Also at startup or boot, does anything need to be added to the rc file, or do you any any way have to bring the network up manually or start rutilT manually?
All I needed to do is edit the /etc/networks/interfaces file to get WPA enabled wireless at boot time.
No other actions required (assuming that you installed a functioning driver)
I did not uninstall anything.

I had to modify the interfaces file as follows to make it work on my system:
```
auto wlan0
iface wlan0 inet dhcp
*pre-up ifconfig wlan0 up*
pre-up iwconfig wlan0 essid backdoor
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set WPAPSK=***
pre-up iwpriv wlan0 set EncrypType=TKIP
```

For static IP setup replace *iface wlan0 inet dhcp* with:
```
iface wlan0 inet static
address 192.168.x.x
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers x.x.x x.x.x.x
```

Thank you very much, odiseo77, for your excellent contribution.

---

