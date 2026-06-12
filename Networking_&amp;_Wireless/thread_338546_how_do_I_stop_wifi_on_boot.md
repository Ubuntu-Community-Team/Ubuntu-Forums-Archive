---
title: "how do I stop wifi on boot?"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by Pollywoggy on 2007-01-14
I installed kubuntu Edgy a few days ago and I have three network profiles, but something is wrong because when the machine boots, wifi is active (not connected but interface enabled) and I have to go to the network settings to disable it.

Is there a way to prevent it from being enabled on boot?

---

### Post by spd106 on 2007-01-14
Go to the /etc/network/interfaces file and comment out the line "auto eth1", assuming eth1 is the wifi card name e.g.
```
auto eth0
iface eth0 inet dhcp

#auto eth1
iface eth1 inet dhcp
wireless-essid linksys
wireless-key 012345678910
```

This will keep your settings, but stop the card being configured automatically. When you wnat the card to start you will have to remove the # and run **sudo ifup eth1**. It should be possible to do this through network-admin by unchecking "enable this connect", but it isn't always that simple.

---

### Post by Pollywoggy on 2007-01-15
> **spd106 said:**
> Go to the /etc/network/interfaces file and comment out the line "auto eth1", assuming eth1 is the wifi card name e.g.
```
auto eth0
iface eth0 inet dhcp

#auto eth1
iface eth1 inet dhcp
wireless-essid linksys
wireless-key 012345678910
```

This will keep your settings, but stop the card being configured automatically. When you wnat the card to start you will have to remove the # and run **sudo ifup eth1**. It should be possible to do this through network-admin by unchecking "enable this connect", but it isn't always that simple.

I should have mentioned that the wifi interface is not set to auto, only eth0's stanza has 'auto eth0'.

I am going to find out how best to install Gnome so I can try the Gnome wifi tools.

---

### Post by dmizer on 2007-01-16
don't bother installing gnome, it's not going to make a difference in this issue.

well, let me start with this ... is there something wrong which is making you want to turn your wifi adapter off?

there is nothing wrong, ubuntu is behaving as expected.  you've told it to not connect, but since the driver is loading, the card is ready to go when needed.  if you want to completely disable the card like it doesn't even exist on the system you would have to unload the driver module.

this is the same behavior that occurs in windows by the way.  you can kill the card, but not until after the system is loaded.

i guess what i'm getting at here, is i'm not too sure exactly why your problem is a problem.

---

### Post by Pollywoggy on 2007-01-16
> **dmizer said:**
> don't bother installing gnome, it's not going to make a difference in this issue.

well, let me start with this ... is there something wrong which is making you want to turn your wifi adapter off?

there is nothing wrong, ubuntu is behaving as expected.  you've told it to not connect, but since the driver is loading, the card is ready to go when needed.  if you want to completely disable the card like it doesn't even exist on the system you would have to unload the driver module.


It is possible that I only think it is a problem because I had not see this behavior before, when I used the card in Linspire and Freespire.  The wifi lock indicator on the laptop (it is on the hardware) would only light when I actually made a wifi connection.  The behavior I see now is different.  The lamp lights only because the interface is up, even though I have no connection to anything.

---

### Post by dmizer on 2007-01-16
i see.  yes, it could very well be that ubuntu is driving the card slightly different than freespire and that the light is not functioning as expected.  for example, the "link" light on my linksys wireless adapter functions more like an "activity" light instead.  but the card's physical functioning is no different.

you can try a couple of things.  first of all, if you know which identifier (eth0, wlan0, ra1) is your wireless adapter, you can try this command:
```
sudo ifdown wlan0
```
where "wlan0" should be replaced with the identifier for your card.  if this turns the light off, perhaps we can come up with an alternative.  but i'm still not convinced that this is a real problem.  i mean, if you're not automatically connecting to a wireless network, it's not like there's a possibility of someone else connecting to your computer wirelessly without your knowledge.

or in other words, ubuntu will not be actively seeking wireless access points as long as the "noauto" option is _not_ listed in /etc/network/interfaces

i suppose there's some validity in talking about battery drain, but i also don't suspect that battery drain is going to be much (if any) higher.

---

### Post by Pollywoggy on 2007-01-16
> **dmizer said:**
> 
you can try a couple of things.  first of all, if you know which identifier (eth0, wlan0, ra1) is your wireless adapter, you can try this command:
```
sudo ifdown wlan0
```
where "wlan0" should be replaced with the identifier for your card.  if this turns the light off, perhaps we can come up with an alternative.  but i'm still not convinced that this is a real problem.  i mean, if you're not automatically connecting to a wireless network, it's not like there's a possibility of someone else connecting to your computer wirelessly without your knowledge.


That was one of the first things I tried and though I don't recall the exact output, it told me that the interface was not configured, though 'ifconfig' showed the interface, ra0, in my case.

---

### Post by dmizer on 2007-01-16
if "sudo ifdown ra0" indicates that your wireless device is not configured, then it is off, and the light can be considered erroneous.

---

