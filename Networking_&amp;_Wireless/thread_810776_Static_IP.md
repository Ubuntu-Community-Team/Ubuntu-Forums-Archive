---
title: "Static IP"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by kshane on 2008-05-28
I decided to play around with KDE4 and have been having problems with the network.  For some reason DHCP doesn't work for *any* Linux distro I've tried on my network.  So I'm trying to set it up as a static IP, but I can't find any place to set it.  This is a wired network (cable) in an extended-stay hotel.

Isn't there a file which holds this info?

Thanks in advance...

Kevin

---

### Post by pytheas22 on 2008-05-28
In Gnome you can use Network Tools to set static IPs in a GUI; I'm not sure what you use in KDE but there must be a similar utility.  Alternatively, you can use the command line and ifconfig to set IP addresses, e.g.:

```
sudo ifconfig eth0 192.168.0.2
```

Netmask and so on can also be specified if necessary; take a look at the ifconfig man page for the syntax.

DNS server addresses should be put in /etc/resolv.conf.

---

### Post by bwhite82 on 2008-05-28
To make the static IP persistent, edit:

/etc/network/interfaces

[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by kshane on 2008-05-28
> **pytheas22 said:**
> In Gnome you can use Network Tools to set static IPs in a GUI; I'm not sure what you use in KDE but there must be a similar utility.  Alternatively, you can use the command line and ifconfig to set IP addresses, e.g.:


Yes.  I finally ran into the spot, but i couldn't tell you where it was.  KDE is pretty foreign to me.  That's why I wanted to give it a shot...

```
sudo ifconfig eth0 192.168.0.2
```

> **pytheas22 said:**
> 
Netmask and so on can also be specified if necessary; take a look at the ifconfig man page for the syntax.

DNS server addresses should be put in /etc/resolv.conf.

Thanks, pytheas22....

Kevin

---

### Post by hacker_at_linux on 2009-03-07
Its okay man to do it with terminal but can sm one tell me how to set the gateway n subnetmask.

And isnt there sm graphical way to do this while KDE is all about graphics

---

### Post by pytheas22 on 2009-03-07
> Its okay man to do it with terminal but can sm one tell me how to set the gateway n subnetmask.

And isnt there sm graphical way to do this while KDE is all about graphics

You can set netmask and gateway using the 'ifconfig' and 'route' commands, respectively.  For more information read their man pages or consult Google.

In Gnome, you can specify these things graphically by going to System>Preferences>Network.  I'm not sure where the equivalent is in KDE, but I'm sure it exists and can be found if you look around.

---

### Post by hacker_at_linux on 2009-03-07
Man well I looked around bt dint found any thing 

there is only one network manager , in which there is no option fr static configuration 

So can any one tell me the graphical way to do this.

---

### Post by pytheas22 on 2009-03-07
I'd be surprised if there's really no GUI in KDE for configuring the network.  But I haven't used KDE in several years so I don't remember.

There are instructions [here]("http://ubuntuforums.org/showpost.php?p=207243&postcount=5") for setting netmask and gateway in your /etc/network/interfaces file.  Open the file for editing by typing:
```

sudo kate /etc/network/interfaces
```

Then make the changes as instructed.  It's really not that hard.

---

### Post by hacker_at_linux on 2009-03-07
That is okay man but KDe without an interface 
isn't that strange cuz kde is all about graphics n leaving behind Terminal
so there has to b a way 

if there is not I have a sftware in ubuntu named xnetcardconfig fr gnome
It only works with gnome not with KDE 

cant we tell kde developers to modify it fr KDE 4.1

it would b good

---

