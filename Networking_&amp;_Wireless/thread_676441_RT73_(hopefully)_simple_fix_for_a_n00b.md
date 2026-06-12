---
title: "RT73 (hopefully) simple fix for a n00b"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by Davini994 on 2008-01-23
Ubuntu n00b struggling with RT73 wireless here. 

I can get it running ok, the problem is with the startup script - it won't load properly. Root cause is I don't know what I'm doing, but if someone can give me a nudge that would be loverly. The script I have in /etc/network/interfaces is:

```
auto lo
iface lo inet loopback

modprobe rt73
#auto rausb0

pre-up ifconfig rausb0 down
pre-up ifconfig rausb0 192.168.3.88 up

pre-up iwpriv rausb0 set AuthMode=WPAPSK
pre-up iwpriv rausb0 set EncrypType=TKIP
pre-up iwpriv rausb0 set NetworkType=Infra
pre-up iwpriv rausb0 set SSID="SSID_HERE"
pre-up iwpriv rausb0 set WPAPSK="NETWORK_KEY_HERE"


pre-up iwconfig rausb0 mode managed

pre-up route add default gw 192.168.3.1
```

Now... what happens is that everything loads, but it won't connect. ifconfig and route look ok, if I iwgetid it shows the correct SSID sometimes, and blank others. The card flashes like it's trying to handshake WPAPSK ok. If I then re-enter the line 

```
sudo iwpriv rausb0 set WPAPSK="NETWORK_KEY_HERE"
```

Into the terminal, it's all fine. As in, it connects properly and I can ask for help here :)

If I take the hash away to run "auto rausb0" then the script doesn't seem to run at all - lo and rausb0 are not in ifconfig, but show in ifconfig -a. I've tried it above "modprobe rt73" too. I don't know what the mode managed command does.

As you can probably tell I'm at the guessing stage as I've run out of sensible ideas. 

Help please? Thanks if you can.

---

### Post by pytheas22 on 2008-01-26
Two ideas:

1 - I used to have issues that sound similar to yours, where my rt73 card would flash as if it were connecting, but ultimately fail to get an IP address.  If I told it to reconnect, however, it always worked fine on the second try, which it apparently does for you too.  Maybe you could just set a script to run "sudo iwpriv rausb0 set WPAPSK="NETWORK_KEY_HERE" a second time after the card's first try, and it would work, since it works if you do it manually.

2 - I assume that you're using the default rt73 driver that ships with Gutsy, which for me was a huge unstable headache.  You might have better luck using the legacy driver from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads) .

---

### Post by Davini994 on 2008-01-27
pytheas, thanks for the response. I was using a later version of the legacy file mentioned in 2, as I had nothing with the included driver, so we are there with that. There is a manager on the linked page, which I thought would be useful, but it's refusing to install.  Error message is 

> Can't get STA config through special ioctl.

1 Sounds promising; although I do seem to need to drop in the key to make it work, not just dhclient. I've put the "sudo iwpriv rausb0 set WPAPSK="NETWORK_KEY_HERE" into the end of "/etc/network/interfaces" but that's not had any effect; is there another way to run this command on boot? Noob here, I'm ignorant of the basics I'm afraid.

Thanks if you can help.

p.s. is there anywhere that I can learn about the structure of Ubuntu, i.e. what runs where and what's possible? This is a knowledge gap at the mo, and I'm struggling to find what I'm after.

---

### Post by pytheas22 on 2008-01-27
> There is a manager on the linked page, which I thought would be useful, but it's refusing to install.

do you mean Rutilt?  It can be installed from the standard repositories; just open Synaptic and search for it, or get it from [http://packages.ubuntu.com/gutsy/net/rutilt](http://packages.ubuntu.com/gutsy/net/rutilt) .  Network Manager doesn't work with the legacy drivers; only Rutilt does, which might be the explanation for the behavior you were experiencing.

So try installing Rutilt and see if you can get connected that way.  If after twenty or thirty seconds it fails to connect on the first try, click connect again...that's what I always had to do to get it to work.  If you run it from the command-line it will give you useful output, too.  And if Rutilt turns out to work for you, you can make it autoconnect.

Otherwise, I am not at all familiar with how to add commands to boot scripts, although I'm sure if you search on the forum you will find something.  I think that the files in your /etc/init.d directory are what you would need to edit, but I don't know any more than that, and I don't want to tell you something that's wrong because you could easily make your system not boot.

---

### Post by zdude on 2008-01-28
If you are doing static you might tr this:

auto rausb0
	iface rausb0 inet static
	address 192.168.1.10
	netmask 255.255.255.0
	gateway 192.168.1.1
	pre-up ifconfig rausb0 up
	pre-up iwconfig rausb0 essid NetworkName
	pre-up iwconfig rausb0 mode managed
	pre-up iwpriv rausb0 set AuthMode=WPAPSK
	pre-up iwpriv rausb0 set EncrypType=TKIP
	pre-up iwpriv rausb0 set WPAPSK="myPassword"
	pre-up iwpriv rausb0 set SSID=NetworkName

I use this with my RT73 and it works perfectly on bootup and is quite solid. My interface id  is wlan0 instead of rausb0.

Good luck.

---

### Post by Davini994 on 2008-02-17
Thanks zdude, it wasn't working when I tried that, but it has decided it's ok now for some reason! Due to updates I guess. 

Thanks to all for taking the time too!

---

