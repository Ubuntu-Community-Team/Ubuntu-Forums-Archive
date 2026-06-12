---
title: "Laptop won't connect to campus network"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Mimsy on 2006-11-16
Since about a week, my laptop has started to lose the ability to connect to parts of the wireless net work on campus. It worked just fine earlier this semester, but last week it starte to have difficulties getting annd keeping a connection.

When it happens I go to the GUI NetWork settings, mark the wireless connection and click on Properties. In the field Network name (ESSID) I can usually see at least four networks in the drop down menu (all four of them with the same name!), but no matter which one I chose, I can't get online. Campus tech support seem lost since it'snot a problem with Windows.

Help would be greatly appreciated.

Thanks,
Mimsy

---

### Post by Hmarroqu on 2006-11-16
sounds similar to the problem i had.. check this out

[http://ubuntuforums.org/showthread.php?t=292407](http://ubuntuforums.org/showthread.php?t=292407)

---

### Post by Mimsy on 2006-11-16
That does look a lot like my problem. Thanks! I'll try that as soon as I am back on campus, where I can see if it works or not.

No wireless at home... :)

/Mimsy

---

### Post by Mimsy on 2006-11-16
So I went to that thread and tried to follow the instructions, and things seemed to work fairly well. I noticed though, that I don't have the file etc/network/interfaces . I suppose that's a bad thing?

/Mimsy

---

### Post by Mimsy on 2006-11-16
It's definitely a bad thing. network-manager and network-manager-gnome both refuse to even recognise the built-in wlan, and so now the wireless connection doesn't exist at all. :(

So where do I get hold of that file that I think I am supposed to have, but can't find?

/Mimsy

---

### Post by christhemonkey on 2006-11-16
I would be very suprised if it didnt exist!

/etc/network/interfaces

Mine looks like this:
> 
auto lo
iface lo inet loopback


#iface eth0 inet static
#address 169.254.17.137
#netmask 255.255.255.0

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


auto eth0
iface eth0 inet dhcp

iface ppp0 inet ppp
provider ppp0


though i doubt that is what a typical one looks like!

---

### Post by Mimsy on 2006-11-16
When I go look for it in theNautilus GUI I can find it, open it, and it has a bunch of stuff in it that looks a lot like yours; except nothing is commented out.

So why can't I find it in the command line? I followed that exact path, and gedit opened a new, blank, document. 

Very strange.

/Mimsy

---

### Post by christhemonkey on 2006-11-16
> I noticed though, that I don't have the file etc/network/interfaces . I suppose that's a bad thing?

In that post you didnt put a / at the start of the path, the / at the beginning is very important to the location.
(i realise that it may have just bee:n a mis-type there though)

If you want to edit it try this:
```
gksudo gedit /etc/network/interfaces 
```

---

### Post by Mimsy on 2006-11-16
*copy-pastes*

Hm. Still comes up all blank... but now that I know it's there, I could log in as root and edit it that way though, right?

I think my terminal may be broken. :p

/Mimsy

---

### Post by Mimsy on 2006-11-16
Okay... I logged in as root, I opened the /etc/network/interfaces file, and i commented out allbut the first two lines, and restarted gnome. Now I have a second network manager icon, and it has two wireless networks listed (though as inactive) so everything seems to be working. Next time I am on campus or somewhere else where I know there is a wireless network, I will try it out and see how it connects.

Thanks for the link and help, everyone!

/Mimsy

---

