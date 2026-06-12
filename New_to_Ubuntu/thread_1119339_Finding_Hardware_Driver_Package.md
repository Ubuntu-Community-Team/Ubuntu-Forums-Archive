---
title: "Finding Hardware Driver Package"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Gyroscope352 on 2009-04-07
So I updated the kernel from 2.6.27-7 to 2.6.27-11 and my wireless stopped working (something that also happened when I first installed Ubuntu). If I boot up in the old kernel everything works fine. Apparently I'm going to have to reinstall these damn wireless drivers every time I breathe, but that's fine as long as I know how. Here's why I'm pretty sure the drivers are the problem:

In System>Administration>Hardware Drivers (on the old kernel), I have support for Atheros 802.11 wireless LAN cards. In Hardware Drivers on the new kernel, I do not.

So my question is, knowing that the drivers are installed and working on the old kernel, how do I go ahead and install the same drivers when I boot up in the new kernel? Is there a package on my hard drive somewhere, or what?

---

### Post by Michael.Godawski on 2009-04-08
hey Gyroscope352,

perhaps something like this happened to you:

[LIST]
[*][http://blog.rtg.in.ua/2008/11/madwifi-hal-dkms-mini-how-to.html](http://blog.rtg.in.ua/2008/11/madwifi-hal-dkms-mini-how-to.html)
[/LIST]
First let us know what your wlan card model is:
```
lspci -nn | grep -i net
```Post the output here.

A possible workaround:

[LIST=1]
[*]make sure the file /etc/network/interfaces looks as follows: 
```
auto lo
iface lo inet loopback
```
[*]Deactivate the madwifi driver in System > Administration > Hardware Drivers >*** Support for Atheros 802.11 wireless LAN cards***
[*]Install the backports ```
sudo apt-get install linux-backports-modules-intrepid
```
[*]Restart
[*]The new ath5k driver should be activated for your card.
[/LIST]

---

### Post by Gyroscope352 on 2009-04-08
> **Michael.Godawski said:**
> hey Gyroscope352,

perhaps something like this happened to you:

[LIST]
[*][http://blog.rtg.in.ua/2008/11/madwifi-hal-dkms-mini-how-to.html](http://blog.rtg.in.ua/2008/11/madwifi-hal-dkms-mini-how-to.html)
[/LIST]
First let us know what your wlan card model is:
```
lspci -nn | grep -i net
```Post the output here.

A possible workaround:

[LIST=1]
[*]make sure the file /etc/network/interfaces looks as follows: 
```
auto lo
iface lo inet loopback
```
[*]Deactivate the madwifi driver in System > Administration > Hardware Drivers >*** Support for Atheros 802.11 wireless LAN cards***
[*]Install the backports ```
sudo apt-get install linux-backports-modules-intrepid
```
[*]Restart
[*]The new ath5k driver should be activated for your card.
[/LIST]

I am pretty sure that is exactly what is happening to me. I have the 242x as well. See my output:

whitsongordon@Whitson-Gordons-Macbook:~$ lspci -nn | grep -i net
01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 22)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

I tried the workaround you posted but it did not work - BUT the driver said it was for Atheros 5xxx series, which is not what I have (I think?). It activated the drivers in the new kernel and everything, though. It just still wouldn't detect networks.

Another problem I had - I could not deactivate my old driver before installing the new one (because I needed the internet to download them). But I don't think that's the problem, because the newly downloaded drivers showed up on the new kernel, like I said (they said Atheros 5xxx instead of just Atheros 802.11).

So what next?

---

### Post by Gyroscope352 on 2009-04-08
I hate bumping, but I've learned more about this problem and am posting an update. After some more googling and such, I'm seeing a lot more people who had this problem when they updated to kernel 2.6.27-11 (I don't know why my Ubuntu just updated to this kernel, but it did). What happened with them was that they would get two drivers - the old one and the 5xxx one. Generally some combination of this worked for them.

I am only getting the 5xxx driver and not the old one. With the 5xxx enabled, I am not detecting any wireless networks. If I boot into 2.6.27-7, I have the old driver activated and I am getting wireless. So what's wrong? Anyone have an issue like this/know how to get the right drivers up?

---

