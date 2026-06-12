---
title: "Can't get bonding to work"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by Brandon_MacEachern on 2014-09-27
I am having a problem getting NIC bonding to work.  This is on a computer with dual Intel onboard gigabit ethernet, and while both interfaces work, when I go through the GUI to setup a bond, it doesn't work.  In the networking menu, there's literally no way to check the bond.

Also, when I do it the official ubuntu way, it's with static IP only, when messing with the network interfaces config file.  I need it to use DHCP as the computers IP is managed with my server.

Is there any way to get this to work?

---

### Post by tgalati4 on 2014-09-27
Yes, use static IP addresses for each card.  [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

I'm not aware of a method to use dhcp and bonding.

[http://askubuntu.com/questions/382577/how-can-i-enable-bonded-network-interfaces-in-ubuntu-13-04-13-10-using-networkma](http://askubuntu.com/questions/382577/how-can-i-enable-bonded-network-interfaces-in-ubuntu-13-04-13-10-using-networkma)

The consensus seems to be that NetworkManager does not handle bonding well.  I have always used the old-fashioned way--configuration files.

In reference to bonding throughput, it depends on how it is set up:  [http://askubuntu.com/questions/293349/how-to-check-network-card-bonding-speed-in-ubuntu-10-04](http://askubuntu.com/questions/293349/how-to-check-network-card-bonding-speed-in-ubuntu-10-04)

---

### Post by Brandon_MacEachern on 2014-09-27
> **tgalati4 said:**
> Yes, use static IP addresses for each card.  [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

I'm not aware of a method to use dhcp and bonding.

[http://askubuntu.com/questions/382577/how-can-i-enable-bonded-network-interfaces-in-ubuntu-13-04-13-10-using-networkma](http://askubuntu.com/questions/382577/how-can-i-enable-bonded-network-interfaces-in-ubuntu-13-04-13-10-using-networkma)

The consensus seems to be that NetworkManager does not handle bonding well.  I have always used the old-fashioned way--configuration files.

In reference to bonding throughput, it depends on how it is set up:  [http://askubuntu.com/questions/293349/how-to-check-network-card-bonding-speed-in-ubuntu-10-04](http://askubuntu.com/questions/293349/how-to-check-network-card-bonding-speed-in-ubuntu-10-04)
When I try the method outlined officially in the link you specify, here's what happens.

eth0 shows "Non managed" or something like that in the networking menu, and eth1 shows an IP that is NOT what I specified in the configuration file, in fact the router thinks it's not my computer.  Also, IPv6 fails to work correctly.

Then on top of it, network communications tend to be half broken.  Sometimes data transfer works, sometimes it just can't stop.  and I did verify that each NIC works on it's own just fine.  Connected with CAT6 to a full gigabit switch, using round robin.

---

### Post by Brandon_MacEachern on 2014-09-28
Here's my snag.  While I can browse websites via IPv6 when I try this, any website that's IPv4 only, does not load at all.

[img]https://fbcdn-sphotos-e-a.akamaihd.net/hphotos-ak-xfp1/v/t1.0-9/10678506_10202905320418097_9190918817737134091_n.jpg?oh=3c129f6449de5f46e5641182d6995e9f&oe=54CC4BAD&__gda__=1422973384_e3dbd786ef6c96a58b4e524aa9f25e1b[/img]
[img]https://scontent-a.xx.fbcdn.net/hphotos-xpa1/v/t1.0-9/10641159_10202905320458098_6320359652996556262_n.jpg?oh=de3f542213878e0ee578ac416d4a6635&oe=54B901EA[/img]
[img]https://scontent-a.xx.fbcdn.net/hphotos-xfa1/v/t1.0-9/10712870_10202905320498099_7586155522125741398_n.jpg?oh=4ab20a64303976221db7c69d013c7735&oe=54C59E6D[/img]

You'll notice that it's not even claiming the IP address I told it to do.

---

### Post by Brandon_MacEachern on 2014-09-28
*sigh*  This post has been lost in the forum again, once again no help here that actually gets me anywhere.  I'm about ready to say forget this.

---

### Post by tgalati4 on 2014-09-28
What is the output of:

```
cat /etc/NetworkManager/NetworkManager.conf
```

You need to make sure you allow NetworkManager use your ifup/ifdown settings.

Everything is fixable.  Patience is key.

---

### Post by Brandon_MacEachern on 2014-09-28
The computer is not networkable right now so here's a pic.

[IMG]http://i.imgur.com/H96sryS.jpg[/IMG]

Patience is one thing, but good documentation is another.

---

### Post by Brandon_MacEachern on 2014-10-12
Ok so how patient am I supposed to be again?

---

### Post by coffeecat on 2014-10-12
Well - you certainly don't need to wait a week before bumping your thread. About 24 hours is just fine.

---

### Post by tgalati4 on 2014-10-12
Try **managed=true** and reboot.

Additionally, I think there is a conflict between how your switch handles IPv6 and how your Ubuntu setup handles IPv6.  I would switch off all IPv6 on your computer (search the forums for how to do that) and make sure bonding works in IPv4 mode.  You want to isolate and solve one problem at a time.  And yes, patience implies time.

A forum such as this is not designed for instantaneous problem solving.  It is more for suggestions and guidance.  If any problems get solved on these forums, then that is a bonus.

All linux documentation that you read are suggestions.  They may or may not work in your situation.  If they work, then great.  If they don't, then there is more work to do.

---

