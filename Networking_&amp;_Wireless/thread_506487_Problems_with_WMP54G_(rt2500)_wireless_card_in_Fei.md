---
title: "Problems with WMP54G (rt2500) wireless card in Feisty"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by Commodore Guff on 2007-07-21
Okay, I've been using Ubuntu for a while now, and my card works fine in Edgy.  However, I cannot connect to my wireless access point in Feisty.

I am not using WPA, just WEP with open authentication.  This should not be presenting any problems.  However, what might be is the fact that the access point is set to not broadcast its name (this is not my choice, and yes, I know it adds little security if any, but I have no say in this matter).  For some reason, I have no problems with Edgy, but Feisty will not connect at all.

Can anyone help?
Thanks.

---

### Post by Sipswitch_Peter on 2007-07-21
I seem to recall having a similar problem when using it on a laptop a while ago.
Ubuntu has issues with WEP.  You have to put an entry in the file manually.  The graphical interface is no use.

Sorry I cant remember how I did it or i'd post it - but I'm sure you can search for the infor easily enough.

---

### Post by Commodore Guff on 2007-07-21
> **Sipswitch_Peter said:**
> I seem to recall having a similar problem when using it on a laptop a while ago.
Ubuntu has issues with WEP.  You have to put an entry in the file manually.  The graphical interface is no use.

Sorry I cant remember how I did it or i'd post it - but I'm sure you can search for the infor easily enough.
The thing is that I'm using the exact same configuration that I had with Edgy.

And a while back, I did test WEP with an access point that actually broadcasts its name, and there wasn't a problem.  Thus why I think it's not a matter of WEP.

---

### Post by kevdog on 2007-07-21
There is a problem with network manager and rt cards in Feisty. In order to use WEP its my understanding that the setup has to be done manually either at the command line or through modifications in the /etc/network/interfaces file such as:

```

auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid YOUR_ESSID
	pre-up iwconfig wlan0 key WEP_KEY

```

Again the above is only an example.  wlan0 may not be your interface name, so you will have to modify it appropriately.

---

### Post by Commodore Guff on 2007-07-21
> **kevdog said:**
> There is a problem with network manager and rt cards in Feisty. In order to use WEP its my understanding that the setup has to be done manually either at the command line or through modifications in the /etc/network/interfaces file such as:

```

auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid YOUR_ESSID
	pre-up iwconfig wlan0 key WEP_KEY

```

Again the above is only an example.  wlan0 may not be your interface name, so you will have to modify it appropriately.

I set it up as you described, but it still fails to connect.  No dhcpoffers.

---

### Post by kevdog on 2007-07-21
Can you post our /etc/network/interfaces file?

Im no expert in the area, but the only other thing I would recommend is to update your drivers to the latest serial monkey rt2500 drivers.  Instructions are here:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Notice however that the instructions are for the rt73 card, however if you put 2500 in place of 73 it will work.  Also do not blacklist the rt2500 module as this is the module you are trying to update.

The serialmonkey site where the source driver files are located is here:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

Ive taken a few people through the process and to my knowledge everything has worked well in the end.

---

### Post by Commodore Guff on 2007-07-21
> **kevdog said:**
> Can you post our /etc/network/interfaces file?

Im no expert in the area, but the only other thing I would recommend is to update your drivers to the latest serial monkey rt2500 drivers.  Instructions are here:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

Notice however that the instructions are for the rt73 card, however if you put 2500 in place of 73 it will work.  Also do not blacklist the rt2500 module as this is the module you are trying to update.

The serialmonkey site where the source driver files are located is here:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

Ive taken a few people through the process and to my knowledge everything has worked well in the end.```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto ra0
iface ra0 inet dhcp
	pre-up ifconfig ra0 up
	pre-up iwconfig ra0 essid "[name of the network]"
	pre-up iwconfig ra0 key [wep key]

```
Also, the actual SSID has spaces in it.  Could this be a problem?

Yes, I just installed the updated driver.  Once I get some other things done, I'll restart and see how it works.

---

### Post by kevdog on 2007-07-21
I wouldnt put spaces in the ESSID name.  Also I dont really know if when you specifiy the ESSID name it needs quotes or no quotes.  I know there is a difference, and some people have reported it works with quotes, and other without quotes. Maybe its a driver/router interaction.  Who knows???

---

### Post by Commodore Guff on 2007-07-21
> **kevdog said:**
> I wouldnt put spaces in the ESSID name.  Also I dont really know if when you specifiy the ESSID name it needs quotes or no quotes.  I know there is a difference, and some people have reported it works with quotes, and other without quotes. Maybe its a driver/router interaction.  Who knows???
As I've said before, it's not my decision.  I'm not in charge of the wireless router.
It didn't seem to want to work at all without quotes (because the spaces confused it).

---

### Post by kevdog on 2007-07-21
Try with both single (' ') and double (" ") quotes.

---

### Post by Commodore Guff on 2007-07-21
> **kevdog said:**
> Try with both single (' ') and double (" ") quotes.

Doesn't work either way.

I might be able to get the SSID changed to something without spaces, but I think what's killing me is that the access point doesn't broadcast the name, and my father seems to think that adds a level of security (a laughable amount at best, but he doesn't believe me).

---

### Post by kevdog on 2007-07-22
Can you post some error messages when you say it doesnt work.  That would help me greatly.

Did you uninstall network manager
sudo aptitude purge network-manager

And just to debug can you post
lshw -C network
sudo iwlist ra0 scan

Can you add this to the interfaces file before the essid line:
pre-up iwconfig rausb0 mode managed

Have you tried issuing these commands on the command line in sequence one by one to see which one gives you problems???

---

### Post by Commodore Guff on 2007-07-22
Eh, never mind, I guess.  The network's SSID is now set to broadcast, and I can connect fine.  It would just be nice to know why it couldn't connect when the name wasn't broadcast, especially when Edgy could.

---

### Post by kevdog on 2007-07-22
Well glad you got it working.  I cant explain your dilemma.  Hopefully the next upgrade, Gusty, will take care of a lot of the problems that used to work in Edgy but no longer in Feisty.

---

### Post by Gruelius on 2007-07-23
try using iwpriv. I made a script for my mums pc, ill grab it for ya if you want.

---

