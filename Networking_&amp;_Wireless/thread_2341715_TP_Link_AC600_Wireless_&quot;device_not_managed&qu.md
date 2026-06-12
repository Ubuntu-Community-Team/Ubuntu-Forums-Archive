---
title: "TP Link AC600 Wireless &quot;device not managed&quot; in Network Manager"
date: 2016-10-30
forum: Networking &amp; Wireless
---

### Post by jeffhoogland on 2016-10-30
I have a TP-LINK AC600 USB wireless device that worked perfectly fine on Ubuntu 14.04 after following the directions for building the kernel module here: [http://askubuntu.com/questions/726569/tp-link-ac600-driver-on-ubuntu-14-04-lts-x64](http://askubuntu.com/questions/726569/tp-link-ac600-driver-on-ubuntu-14-04-lts-x64)

After building this same module on Ubuntu 16.04 the device appears in my network manager, but it is listed as "device not managed". I have edited the file /etc/NetworkManager/NetworkManager.conf to be the contents:

```
[main]plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=true

```

But it did not have any effect. Any suggestions for how to get this wireless card working under 16.04?

---

### Post by jeremy31 on 2016-10-31
See the wireless script link in my signature and post your results

---

### Post by jeffhoogland on 2016-10-31
Results from the requested script attached.

---

### Post by Geoffrey_Arndt on 2016-10-31
Edit . . disregard info & link at bottom . . I reread your post and see you're referring to the wireless adapter (TP Archer . . ?)

So, as FYI in case module won't build (TP Link dropped most linux support) . . another vendor with solid Linux support - Panda Wireless:

[URL="http://www.pandawireless.com/"]http://www.pandawireless.com/

[/URL]
Perhaps the same issue here as yours?   See post 2 for OP's solution:

[https://ubuntuforums.org/showthread.php?t=2293272](https://ubuntuforums.org/showthread.php?t=2293272)

---

### Post by jeffhoogland on 2016-11-01
That second post looks like it is a different issue from mine. Doesn't mention "device not managed" anywhere.

Really kind of frustrating that it worked with Ubuntu 14.04. I've ever tried rolling back kernel versions to what I used there with no luck. Maybe it is a bug in this latest version of network manager with 16.04

---

### Post by Geoffrey_Arndt on 2016-11-01
Maybe this thread from "AskUbuntu" will be closer to your situation:

[http://askubuntu.com/questions/726569/tp-link-ac600-driver-on-ubuntu-14-04-lts-x64](http://askubuntu.com/questions/726569/tp-link-ac600-driver-on-ubuntu-14-04-lts-x64)

EDIT:   here is more info from Launchpad re confirmed bug in building driver - - not sure if your kernel matches the one is this bug.  Last comment appears to have a work-around:

[https://bugs.launchpad.net/ubuntu/+source/rtl8812au/+bug/1613009](https://bugs.launchpad.net/ubuntu/+source/rtl8812au/+bug/1613009)

---

### Post by jeffhoogland on 2016-11-01
> **Geoffrey_Arndt said:**
> Maybe this thread from "AskUbuntu" will be closer to your situation:  

[http://askubuntu.com/questions/726569/tp-link-ac600-driver-on-ubuntu-14-04-lts-x64](http://askubuntu.com/questions/726569/tp-link-ac600-driver-on-ubuntu-14-04-lts-x64)

This is the exact URL I posted in my OP that I said does not work any more with 16.04 Just says device unamanged.

---

### Post by jeremy31 on 2016-11-01
I found some issues in the wireless script results, first lets set the country code
```

sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```
Then we can disable the troublesome power management
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart NetworkManager.service
```
Lets see if
```
sudo iwconfig wlp4s0 txpower 15
```

Reboot and see if your internal wifi will work

---

### Post by jeffhoogland on 2016-11-01
Getting somewhere.

When I run:

```

sudo iw reg set US
systemctl restart NetworkManager.service
```

My USB device sees and connects to networks instead of just showing me the unmanaged message.

---

### Post by jeremy31 on 2016-11-01
Be sure to run all the commands, reboot into a 4.4.0 kernel and then ```
./wireless-info
```

Post the new results

---

### Post by Hadaka on 2016-11-01
Hi , also your network is being managed by NetworkManager so please do..
```
sudo sed -i 's/managed=true/managed=false/g' /etc/NetworkManager/NetworkManager.conf
```
*This gets marked "true" when you manually define...manage... your network with the /etc/network/interfaces file.
thanks.

---

### Post by jeffhoogland on 2016-11-01
Attached is the script after running all commands.

The USB card is working as expected though it seems after iw reg set US and then restarting network manager. Is there a reason I shouldn't just do this at startup and call it a day?

---

