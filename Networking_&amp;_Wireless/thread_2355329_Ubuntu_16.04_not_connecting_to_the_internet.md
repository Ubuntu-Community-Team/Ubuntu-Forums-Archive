---
title: "Ubuntu 16.04 not connecting to the internet"
date: 2017-03-11
forum: Networking &amp; Wireless
---

### Post by cobradabest on 2017-03-11
I have built a PC recently, and have installed Ubuntu 16.04 alongside Windows 7 on it, but I'm having problems getting Ubuntu to connect to the internet. (Wireless)


The "available" networks show, but when I try to connect to one, it connect after a minute or so, and then after one or two seconds, it just disconnects again. On Windows 7, the internet works just fine.


I have set the IPv6 method to "ignore" and the password stored itself, (Those were the most common solutions I found online) and the problem persists.


What do I do?


If it helps, here are my specs:
8-core 4.0GHz AMD CPU
8GB RAM
AMD R9 Fury GPU
4TB Hybrid Drive (1.8TB used for Ubuntu Partition)

Here are photos I took of outputs of certain commands: (Sorry for the camera-on-screen thing, my Ubuntu currently refuses to accept all but 2 of my PC's USB ports, both are taken up by my keyboard and mouse, so I had no way of getting copying and pasting the text.)
[http://prnt.sc/eirq91](http://prnt.sc/eirq91)
[http://prnt.sc/eirzsz](http://prnt.sc/eirzsz)
[http://prnt.sc/eis10s](http://prnt.sc/eis10s)
[http://prnt.sc/eis1k3](http://prnt.sc/eis1k3)
[http://prnt.sc/eis30l](http://prnt.sc/eis30l)

---

### Post by cobradabest on 2017-03-13
Bump... I really need this to be solved... (Are bumps allowed on here? I can't remember... if not, delete this.)

---

### Post by jeremy31 on 2017-03-13
Can you change the size of those images to maybe 30% of their current size as they locked up my browser.

If anything else look at ```
lspci -nnk | grep -iA3
```
Post what it says for kernel driver in use:
Then look at ```
iwlist scan | egrep -i 'ssid|cipher'
```
If TKIP is listed as a cipher below your SSID you should change the access point to WPA2-AES, WPA2-PSK, some WPA2 option without WEP or TKIP

It might just be the wifi power management being enabled by default
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
And after a reboot it will stay disabled

---

### Post by QIII on 2017-03-13
Bumps are allowed if you have no response for 12 hours.  The single word "bump" is all you need in a new post.

We all recognize that everyone who asks a question needs a solution.  But as this is an all-volunteer forum, it is possible that the person with the very best answer is preoccupied with real life and just has not seen your post yet.

Cheers!

---

### Post by cobradabest on 2017-03-13
> **jeremy31 said:**
> Can you change the size of those images to maybe 30% of their current size as they locked up my browser.

If anything else look at ```
lspci -nnk | grep -iA3
```
Post what it says for kernel driver in use:
Then look at ```
iwlist scan | egrep -i 'ssid|cipher'
```
If TKIP is listed as a cipher below your SSID you should change the access point to WPA2-AES, WPA2-PSK, some WPA2 option without WEP or TKIP

It looks like the problem is worse than I first thought... [http://prnt.sc/ejloc4](http://prnt.sc/ejloc4)

> **jeremy31 said:**
> It might just be the wifi power management being enabled by default
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
And after a reboot it will stay disabled
I tried that and then reboot the system, but no joy... :-?

---

### Post by jeremy31 on 2017-03-13
I missed a parameter for the command ```
lspci -nnk | grep -iA3 net
```

---

### Post by cobradabest on 2017-03-14
Okay, I tried that command and this is what came up: [http://prnt.sc/ejvsa9](http://prnt.sc/ejvsa9)

I finally got an ethernet cable and tried to connect through that... that didn't work either... ](*,)

---

### Post by jeremy31 on 2017-03-14
If you click on the Networking icon in the notification area, is the enable networking and enable wireless checked
[img]https://i.stack.imgur.com/54xeq.png[/img]
Ignore the delete connection arrow

Does ```
systemctl restart network-manager.service
```
Change anyhting?
Also do ```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Then ```
sudo modprobe -r ath9k
```
```
sudo modprobe ath9k
```

---

### Post by cobradabest on 2017-03-15
> **jeremy31 said:**
> If you click on the Networking icon in the notification area, is the enable networking and enable wireless checked
[IMG]https://i.stack.imgur.com/54xeq.png[/IMG]
Ignore the delete connection arrow

Does ```
systemctl restart network-manager.service
```
Change anyhting?

Nope, I'm getting the message
```
Failed to restart .service.service: Unit .service.service not found.
```

> **jeremy31 said:**
> Also do ```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Then ```
sudo modprobe -r ath9k
```
```
sudo modprobe ath9k
```
[s]Okay, I can connect via the ethernet port now, so that's one problem down.[/s]

EDIT: I spoke too soon, I got cut off, and I can't connect again...

---

### Post by jeremy31 on 2017-03-15
Since you can connect using ethernet, see the wireless script link in my signature and post results

---

### Post by cobradabest on 2017-03-15
Okay, I tried it, and then looked into the resulting TXT file, and all I got was this:

```

########## wireless info START ##########



```

That's it...

I had a similar problem with Windows 7 recently (I know I said in the first post that it worked fine, but then it suddenly didn't...) and it turns out that installing the drivers for the motherboard fixed the problem, or at least I could then connect through Ethernet. Maybe I need to do the same for Ubuntu. I couldn't find any drivers for that OS... (It's a GA-990X-Gaming SLI, by the way)

---

### Post by jeremy31 on 2017-03-15
Try running the command again as it should make this go much quicker

---

### Post by cobradabest on 2017-03-17
What command?

---

### Post by mus1cfreak on 2017-03-17
The wireless Script command, i belief.

---

### Post by cobradabest on 2017-03-19
There was no command, it just told me to run the script, and the output overwrote that file...

---

### Post by jeremy31 on 2017-03-19
You can just run ```
./wireless-info
```
Does it give any errors?

---

### Post by cobradabest on 2017-03-21
Okay, I got something this time.

[ATTACH]274254[/ATTACH]

---

### Post by jeremy31 on 2017-03-21
Check the BIOS to see if there is an IOMMU setting and change it

---

### Post by cobradabest on 2017-03-21
Okay, I found the option for "IOMMU Controller", which was disabled, so I enabled it and rebooted Ubuntu and... no joy, it still won't connect...

---

### Post by jeremy31 on 2017-03-21
Does it find any access points with ```
iwlist scan
```
Try ```
sudo iwconfig wlp5s0 txpower 17
```
Then see if you can connect

---

