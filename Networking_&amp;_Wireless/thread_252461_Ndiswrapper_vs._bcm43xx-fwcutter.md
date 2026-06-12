---
title: "Ndiswrapper vs. bcm43xx-fwcutter"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by JackTheKnife on 2006-09-06
How I can use 'ndiswrapper' instead of 'bcm43xx-fwcutter'which I already using. I want to check if I will get those same problems with ndiswrapper. I have Linksys WPC54G v1.2

---

### Post by haiku99 on 2006-09-06
see [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
worked well for me once I got the latest version....IIRC you will need to blacklist fwcutter

---

### Post by JackTheKnife on 2006-09-07
How I can blacklist? Thanks

---

### Post by garrye on 2006-09-07
> **JackTheKnife said:**
> How I can blacklist? Thanks

 echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

followed by...

sudo rmmod bcm43xx  
## remove module bcm43xx

sudo rmmod ndiswrapper  
## remove module ndiswrapper

sudo modprobe ndiswrapper  
## add module ndiswrapper to kernel

The last three lines of code are overkill to ensure that all things run smoothly I think.  If ya likes tinkering & reading yer in d right place!!!

Enjoy and good luck!!

---

### Post by JackTheKnife on 2006-09-07
Thanks GarryE!

After ndiswrapper installation I trying do this:

```

sudo ifdown eth1
sudo ifup eth1

```

And I got message:

```

No DHCPOFFERS received.

```

Looks like this same problem what I had with bcm43xx-fwcutter - can't get infos from DHCP (Windowze wifi works well) :evil:

PS.1
Finally for ndiswrapper:
- DHCP not working
- static IP not working
- no signal

Ndiswrapper vs. bcm43xx-fwcutter - 0:3

PS.2
And right now WiFi card is not recognized at Network Settings ](*,) 

Ndiswrapper vs. bcm43xx-fwcutter - 0:4

PS.3
I got back WiFi card, and also I run

```
dmesg
```

and got informations about wlan0 

```
wlan0: ndiswrapper ethernet device 00:0f:aa:bb:cc:dd:ee using driver lsbcmds
```

but I didn't have at Networking Settings (WiFi card is as eth1).

---

### Post by JackTheKnife on 2006-09-07
Started from scratch and went through [http://www.ubuntuforums.org/showthread.php?t=201902&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=ndiswrapper)

and got wireless finally working \\:D/ , but

- I need to do modporobe ndiswrapper each time after system reboot/start
- use pswd to unlock default keyring (how to remove it?)

[COLOR="Red"]
Ndiswrapper vs. bcm43xx 4:4[/COLOR]

---

### Post by JackTheKnife on 2006-09-07
Answering my own questions:

> **JackTheKnife said:**
> 
- I need to do modporobe ndiswrapper each time after system reboot/start

```
sudo echo ndiswrapper >> /etc/modules
```

or add ndiswrapper

```
sudo gedit /etc/modules
```

How to remove PAM Key:

[http://ubuntuforums.org/showthread.php?t=192281](http://ubuntuforums.org/showthread.php?t=192281)
[COLOR="Red"][SIZE="2"]
And finally winner is... [SIZE="5"]ndiswrapper[/SIZE] 6:4 bcm43xx[/SIZE][/COLOR]

---

