---
title: "Wireless works with Windows but not with Ubuntu"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by randell6564 on 2007-04-01
Hey folks.

I am dual booting Windows XP and Ubuntu Dapper Drake on my desktop pc.  I am living in an apartment complex that provides free wireless internet connection (T1)

I use a Linksys Wusb11 ver 2.6 wireless antenna.  I CAN connect to the network here, and get internet access, but ONLY when I boot to Windows XP.  Ubuntu does not seem to see any network.

I went to 'networking' and then 'properties' for Wlano, entered the essid, chose DHCP and got no results.

Can anyone give me some assistance?  I've been a long time Ubuntu user.  Finally was able to stop using Windows until I moved here.  

Thanks!

---

### Post by randell6564 on 2007-04-01
'Bump'

---

### Post by Porta-Chaves on 2007-04-01
try this in command:

```

sudo iwlist scan <adapter_name_here_(ex: ath0 or eth0)>

```

try that like three times in a row by pressing up and then enter... It happens often that you won't get scan results at your first try...

let me know what u got...

---

### Post by randell6564 on 2007-04-01
> **Porta-Chaves said:**
> try this in command:

```

sudo iwlist scan <adapter_name_here_(ex: ath0 or eth0)>

```

try that like three times in a row by pressing up and then enter... It happens often that you won't get scan results at your first try...

let me know what u got...

Will do.  Gotta reboot to ubuntu.  Thanks!

---

### Post by MaLk0 on 2007-04-01
Have u installed gnome network manager? 

If not try "sudo apt-get install nework-manager-gnome" and reboot the computer. Works perfect for me.

---

### Post by randell6564 on 2007-04-01
> **Porta-Chaves said:**
> try this in command:

```

sudo iwlist scan <adapter_name_here_(ex: ath0 or eth0)>

```

try that like three times in a row by pressing up and then enter... It happens often that you won't get scan results at your first try...

let me know what u got...

Well, heres what I got:

> bigboss@room224:~$ sudo iwlist scan wlan0

> iwlist: unknown command 'wlan0'

Wlan0 is how Ubuntu identified my antenna at my preveous home.  Everytime that I go to 'Networking' now, I have to enter wlan0 under 'Default Gateway Device'.

Its almost as if I need to install a driver, but This was not required at my other home, so I don't know why it would be different here.

I hope its not a driver issue!  I have never manually installed a driver using Ubuntu, (never had to).

---

### Post by mrund on 2007-04-01
I have the exact same problem on a Dell Inspiron 6000 with a Intel 2200 BG wireless card, dual-booting Win XP and Edgy.

But there's a twist to it for me. Before installing Edgy, I test-ran it from a CD -- and wifi worked! Now, with Edgy installed, it works neither if I boot it from the hard disk nor from the CD. Win XP still has wireless, though.

---

### Post by randell6564 on 2007-04-01
> **MaLk0 said:**
> Have u installed gnome network manager? 

If not try "sudo apt-get install nework-manager-gnome" and reboot the computer. Works perfect for me.

Hi Malko.  
I can't connect to the internet using Ubuntu, and I would have NO idea how to download and install the network manager application into the proper directory while using Windows XP, since Windows does not recognize Ubuntu's File system.

---

### Post by mrund on 2007-04-01
Porta-Chaves, I'd like to try the iwlist trick too. How do I find out the eth/ath name of my wireless adapter?

---

### Post by Porta-Chaves on 2007-04-01
I'm really sorry, I switched things XD, try this:

```

sudo iwlist <adapter_name_here_(ex: ath0 or eth0)> scan 

```

in your case:

```

sudo iwlist wlan0 scan 

```

@mrund

To find out the adaptar name of your wireless adaptar open up network settings, I can't tell you exactly how to get there since I'm on XP now, I guess it's systems --> administration --> network settings. If you can't find it try tell me so I login in Ubuntu to explain it better...

---

### Post by Porta-Chaves on 2007-04-01
> **randell6564 said:**
> Hi Malko.  
I can't connect to the internet using Ubuntu, and I would have NO idea how to download and install the network manager application into the proper directory while using Windows XP, since Windows does not recognize Ubuntu's File system.

If the package is already on your PC you don't need to connect to the Internet... Just go to command and enter:

```

sudo apt-get install network-manager-gnome

```

and it will install it

---

### Post by Drate on 2007-04-01
For Broadcom 43xx chipsets, as in standard issue Wal-mart Linksys with speedbooster and some other cards...

THIS is what you have to do:

[http://www.ubuntuforums.org/showthread.php?t=381770](http://www.ubuntuforums.org/showthread.php?t=381770)

If in fact your Linksys, or whatever card you have, has a Broadcom 4318, 4306, or whatever... 43xx chipset... the above WILL work for you.. I c an translate into Noobie friendly instructions if you like. :-D

---

### Post by mrund on 2007-04-01
I ran "iwlist scan" and got a nice big list of the wireless access points in my apartment house, including my own. So the adapter is working fine and seeing my accesspoint. The wireless adapter is named eth1. But when I right-click the network connection icon top right I find only "lo", the loopback interface.

---

### Post by Porta-Chaves on 2007-04-01
> **mrund said:**
> I ran "iwlist scan" and got a nice big list of the wireless access points in my apartment house, including my own. So the adapter is working fine and seeing my accesspoint. The wireless adapter is named eth1. But when I right-click the network connection icon top right I find only "lo", the loopback interface.

ok, now lets try to connect:

```

sudo iwconfig eth1 essid "<ESSID_HERE>"
sudo iwconfig eth1 ap <MAC_ADRESS_HERE>

```

the essid and mac of your accesspoint can be found ising the iwlist command

in case your accesspoint has an encryption key

```

sudo iwconfig eth1 key <key>

```

and now lets see if we get some results:
```

sudo dhclient eth1

```

post results here

ow and by the way if you want to eth1 show up at your network connections click where it says lo, so you get the posibility to write, and write eth1, worked with me.

---

### Post by mrund on 2007-04-01
OK, I tried:

[I]No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/I]

I also tried connecting to a neighbour's unprotected access point, which worked fine to the extent that I got a nice orange connection-quality bar. But my web browser still couldn't find any sites. That may be due to the crappy signal quality from the neighbours, the are at about -80 dBm and my own access point is at -40.

---

### Post by randell6564 on 2007-04-01
> **Porta-Chaves said:**
> I'm really sorry, I switched things XD, try this:

```

sudo iwlist <adapter_name_here_(ex: ath0 or eth0)> scan 

```

in your case:

```

sudo iwlist wlan0 scan 

```


No problem my friend!  I do the same thing all the time!  Thanks.  I'll let ya know what happens.

---

### Post by Porta-Chaves on 2007-04-01
your connection doesnt require specific settings? like static ip? dhcp? and if you are using an wep encryption what type is it? wep? wpa? Note that ASCII keys need a "s:" prefix.

---

### Post by mrund on 2007-04-01
I'll have to re-familiarise myself with the wireless router, it's just been sitting under my desk for two years and I haven't thought much about it.

It's getting late in Stockholm, Sweden, so I'll be back in 18 hours when I've fiddles around some more. Thanks everyone!

---

### Post by randell6564 on 2007-04-01
> **Porta-Chaves said:**
> your connection doesnt require specific settings? like static ip? dhcp? and if you are using an wep encryption what type is it? wep? wpa? Note that ASCII keys need a "s:" prefix.

Sorry, but i wish people would not hijack threads. (not really sure just WHO you are directing your question to.)

When we moved here, I had ONLY Ubuntu on my box.  Once I learned that Ubuntu would not connect to the network, I installed Windows XP so that I could get online.
This network is open; no Wep/Wpa key is needed.  (but I DO have to go to the manager and get a username and password once a week in order to access the internet.  Dont know if this matters any because its not a requirement to access this network.  Its just to access the internet THROUGH this network)

Anyway, heres what I got so far after scanning:
```
bigboss@room224:~$ sudo iwlist wlan0 scan
```

```
wlan0  Failed to read scan data: Resource Temporarily Unavailabe
```

I did the above four to five times in a row like you suggested, but nothing.

I'm baffled!

---

### Post by randell6564 on 2007-04-01
I just checked the [wiki for supported cards ]("http://linux-wless.passys.nl/query_part.php?brandname=Linksys")and my adapter is all green! (wusb11 Version 2.6)  So I must not need any drivers.  

It's GOT to be something on the network admin side.  Maybe a hardware issue.  They do not use Linksys hardware, but then again, I dont have any problem connecting when using Windows.

---

### Post by mrund on 2007-04-02
Porta-Chaves asked:

*your connection doesnt require specific settings? like static ip? dhcp? and if you are using an wep encryption what type is it? wep? wpa? Note that ASCII keys need a "s:" prefix.*

No static IP. Logging on with WinXP or my handheld, all I need to provide is the network key (which I think of as its password).

My access point uses WPA-PSK authentication and TKIP encryption.

I've tried prefixing the key with "s:", to no avail. Can somebody explain to me why that wouldn't be a completely arbitrary demand, BTW?

[IMG]http://scienceblogs.com/aardvarchaeology/upload/2007/04/screendump.jpg[/IMG]

---

### Post by mrund on 2007-04-02
Oh man, this is just completely erratic. Now I somehow have an 86% signal strength indicated for my wireless connection (nice green indicator column in the applet top right), but I'm still "Status: Disconnected". And no matter if I tell the program my password is hex or ascii, and no matter if I prefix it with "s:" or not, I can't get on-line.

---

### Post by Porta-Chaves on 2007-04-02
Try installing wi-fi radar, wich, in my opinion, is much easier connection to the Internet, go to your synaptics and search for radar, it should appear there, mark it for installation.

And btw, you can copy-paste you know, lol.

EDIT: just for curiosity (happend to me) try searching something in the browser using the google searcher in the top right corner...

---

### Post by chili555 on 2007-04-02
mrund-
I believe iwconfig key is for WEP and not WPA. I suggest you check here: [http://www.ubuntuforums.org/showthread.php?t=318539](http://www.ubuntuforums.org/showthread.php?t=318539)

---

### Post by mrund on 2007-04-03
WEP or WPA may be a later consideration. But I just disabled wireless security entirely, and Edgy still can't connect to the access point.

---

### Post by sabi on 2007-04-03
> **mrund said:**
> WEP or WPA may be a later consideration. But I just disabled wireless security entirely, and Edgy still can't connect to the access point.

Sounds like your frustration level is high. Sorry about your difficulties.

From looking at the previous posts, your network card driver seems to be recognized under Ubuntu. Is that correct? Are you using your Windows install to post to this forum?

When you use the command:

```
sudo iwconfig
```

Is your wireless card listed (eg ath0, eth1 ...)?

If so, when you issue the command:

```
sudo iwlist ath0/eth1 scan
```

Do you see the access point you are trying to connect to?

Are you using the command:

```
sudo dhclient ath0/eth1
```

to obtain a dynamic ip address?

Sorry, did not look closely at your screen shot. It appears you already have a dynamic address process running. Do you have an ethernet cable attached to an access point? If so, you will need to disconnect the ethernet cable when testing your wireless, so the results are not confusing.

Hope this helps....


Sabi

---

