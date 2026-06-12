---
title: "Mass internet chaos - wireless and wired"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by Heide264 on 2008-05-13
Bear with me here please - not the most experienced.

When I came home from school and went to take advantage of our wireless (static IP's but no real protection yet) - I found that network manager didn't like static IP's very much. So after reading a bit on the tutorial here, I went through it and followed the tutorial but got a couple errors and figured it was network manager interfering and disabling my wireless card. Soooo, got rid of network manager and found out I was dumb and my drivers were apparently not correct (thank you restricted driver management). Problem being I can't connect to download any drivers via ubuntu.

So I rebooted into my windows partition and am begging you for help =P. I can connect through hardwire if somebody could help me out with a simple way to fix my ethernet cards settings to connect at a static IP via terminal or config files. I believe the main problem I am having is setting the gateway actually.

For reference I'm running Gutsy still - Hardy didn't like my video card so sticking with this for a while.

Thanks for any help =)

---

### Post by solar george on 2008-05-13
Ok,

Run
```
iwlist
```
and look for an entry other than lo which has "no wireless extensions" i.e. your wired card - make a note of the name e.g. eth0 - wherever i say eth0 replace it with this
Then
```
sudo gedit /etc/network/interfaces 
```
and type
```

iface eth0 inet static # replace eth0 with the name from previously
        address 192.168.1.5 #make sure that this address is not used for another computer and is similar to the other addresses on the network
        netmask 255.255.255.0 # get this from another machine already setup
        gateway 192.168.1.1 # ditto

```
Removing any other lines starting iface eth0
Then run
```
sudo ifdown eth0
sudo ifup eth0
```

This should allow your wired connection to connect with a static ip (and will still be there when you reboot.

Then install either network-manager or wifi-radar or similar.

---

