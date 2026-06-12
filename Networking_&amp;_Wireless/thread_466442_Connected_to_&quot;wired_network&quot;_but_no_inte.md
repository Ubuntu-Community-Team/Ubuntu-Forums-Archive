---
title: "Connected to &quot;wired network&quot; but no internet"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by davidvandebunte on 2007-06-06
Network Manager in Ubuntu connects to a wired network when I connect it to my family's ms wireless base station (through wired port) but I get no internet.  Firefox sits for a long time trying to go to any site and then it says the server can't be found.

I've got an Inspiron 1501, 64-bit, wired internet connects fine in vista. I've seen a similar problem on other sites but it always comes to a dead end.  I'm awfully new to this, so thanks for any help you can give.

---

### Post by carolinason on 2007-06-07
are using dhcp?

sounds like the name servers.

check network manager or /etc/resolv.conf for name server entries.

check them against the ns's in the router.

---

### Post by Leopold_Butters_Stoch on 2007-06-07
So...
I am fairly new to Ubuntu, but I managed to have my internet working for quite some time, through wireless and when plugged into a wired connection.  On several different networks (my home network and my college campus network) but just the other night my internet stopped working and I have no idea what the problem is.

I discussed it with a friend who is familiar with Ubuntu and he thinks it is due to something that messed up when I installed some Ubuntu autoupdates...and I did install some updates just the other night shortly before the internet stopped working so that would seem to make sense.

The network manager still recognizes the connection and still shows a strong signal to the wireless, but when I open firefox it just sits there and sits there and sits there until it times out.

Any ideas or suggestions?  Would uninstalling and reinstalling network manager help?  Would I then have to screw around with the pain in the *** of getting the broadcomm wireless stuff working again?

I really like Ubuntu, but I need my internet back!!  Please help!

---

### Post by carolinason on 2007-06-07
Not sure who I am talking to here, since there are different names with different problems in this thread.

assuming you are using a router:
If wireless doesn't work, try reconnecting to the desired wireless router. You might need proper credentials here.

If wired doesn't work, try resetting your network by unchecking and checking your ethernet adapter in the network manager. This will request IP information from the router.

---

### Post by monsterror on 2007-06-07
> **davidvandebunte said:**
> Network Manager in Ubuntu connects to a wired network when I connect it to my family's ms wireless base station (through wired port) but I get no internet.  Firefox sits for a long time trying to go to any site and then it says the server can't be found.

I've got an Inspiron 1501, 64-bit, wired internet connects fine in vista. I've seen a similar problem on other sites but it always comes to a dead end.  I'm awfully new to this, so thanks for any help you can give.

I've got this same problem on my Inspiron 6000, running Hoary. I'm extremely new to Linux in general, so any help at all, with as much walkthrough as possible would be much appreciated.

Also, I just cecked the name servers, and the only one there is "nameserver 192.168.1.1"

---

### Post by carolinason on 2007-06-07
Have you tried reconnecting to the router?

---

### Post by pardesi on 2007-06-07
when i wrote the code 
```
sudo gedit /etc/network/interfaces
```
i get a blank page in Gedit .i have DHCP
though my dektop icon says i am connected no page display.alos each time after i boot ubuntu and reboot with XP my XP shows low or limited connectivity but if i reboot again with windows everything is fine

---

### Post by monsterror on 2007-06-07
Yeah. At least, I think I did.

There are 3 networks with the name Linksys. I would change the router name to avoid confusion, but its not mine to do so.

---

### Post by hillbilly on 2007-06-07
Have you tried resetting the router. It could be because the router provided an IP which has expired :? !

---

### Post by hillbilly on 2007-06-07
Ok, there could be another cleaner way to do this. but I'm not sure how! Will be watching this thread though.

---

### Post by monsterror on 2007-06-07
Personally, I don't care how I have to do it; I just want it fixed.

Any help at all is much appreciated.

---

### Post by pardesi on 2007-06-07
> **monsterror said:**
> Personally, I don't care how I have to do it; I just want it fixed.

Any help at all is much appreciated.

same here;)

---

### Post by carolinason on 2007-06-07
If the router is a public router, then it could be full as someone said before. Just try resetting/requesting an IP address.

If the router is a private router, you'll need to ask the owner/administrator of the router to add you as client.

---

### Post by hillbilly on 2007-06-07
Try
> $/> sudo ifdown eth0
$/> sudo ifup eth0
$/> sudo dhclient eth0

replace eth0 with your network interface name.

Does this work ?

---

### Post by pardesi on 2007-06-07
how do i know whether my router si public or private.also if i write the code
```
network-admin
```
i am being denied acess despite being the only one to use my PC.
further is that just any thing i need to check that could help u helping me.
also i ahave mentioned before after booting ubuntu i boot XP it shows low connecticity otherwise everything is fine

---

### Post by hillbilly on 2007-06-07
are you on fiesty ? if so don't you have network manager running ?Type 
> sudo nm-applet
and see if you can get neworkmanager to run

---

### Post by carolinason on 2007-06-07
Connecting to your pc and the router are going to use two different credentials. They are not related.

If you are able to connect to the router and the internet in xp, then you should be able to connect in ubuntu. **Can you connect in XP?**

When you say you are *denied* access, I think this is a credential issue. 

Just trying to figure what the issue is. I could have you try and reset your ip address all day long, but if you don't have access to the router, then that would do you no good.

---

### Post by pardesi on 2007-06-07
yes i am able to do so in XP.i have been using internet in ubuntu for almost a week now.but the problem started yesterday..

---

### Post by hillbilly on 2007-06-07
whoa !! there seems to be three different questions in this thread. One wired internet, one wireless and one intranet :O !! I think splitting into different threads would help each of the concerned people more.

---

### Post by pardesi on 2007-06-07
> **hillbilly said:**
> whoa !! there seems to be three different questions in this thread. One wired internet, one wireless and one intranet :O !! I think splitting into different threads would help each of the concerned people more.

i had already done.[http://ubuntuforums.org/showthread.php?t=467123](http://ubuntuforums.org/showthread.php?t=467123)
 so since no one was replying i had to get into an active thread

---

### Post by carolinason on 2007-06-07
Hoary is about 2 years old, I haven't ran that in about a year and half, so... 

Can you find the router in the network manager?

---

### Post by pardesi on 2007-06-07
since i am in my XP also i can't reply to you in ubuntu is there anything more you want me to look at ,also how to know presence/absence of router.

---

### Post by pardesi on 2007-06-07
no i couldn't get anything rather couldn't search.

what i could od was see the result after the code
```
cat /etc/network/interfaces
```as

```
auto lo
iface loinet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by hkahwaji on 2007-06-07
I agree that there are too many questions here. I recommend that you first tackle connceting via the wire and then worry about wireless later. 

Login to the Router via the XP machine. Usually when you try to access the web-interface of the router, you will be prompted for username and password. I hope that you have that. 

If all looks good then switch to Ubuntu and open a terminal 

Type the following

ifconfig -a

look to see what the eth0 configuration is: Do you have an IP address?

If not you need to look at the interfaces file to see what the rules are set for the eth0 logical port. If you fo not have an interfaces file in the /etc/network directory, then you need to create one. Also, look in the iftab file in /etc, you should have the eth0 entry there with the MAC address of the wired NIC card.

run the following commands and post the output

sudo cat /etc/network/interfaces
sudo cat /etc/iftab

Hope this helps

---

### Post by pardesi on 2007-06-07
my interface file exists but it' blank.
also see above to see the result of the code
```
cat /etc/network/interfaces
``` 
i don't thonk i have a router because never in my life have i entered any password or login name to acess the net

---

### Post by SpudNik on 2007-06-07
I doubt very seriously that it is your router. Those updates took it out. After installing v. 5.0.1 for the first time, my wireless card worked automatically. Using my wireless card, I downloaded automatic updates and rebooted my machine.  After doing so I was unable to open a web page in my browser. So I checked my network connection from the network utility and it displayed a bar reporting 96% signal strength. I am now connected directly to my router and attempting to reinstall my drivers. I'm working towards a solution and I will keep you posted. It would appear we are dealing with the same issue.

-Nick

---

### Post by pardesi on 2007-06-07
but i didn't have any updates i just appended the word 'noapic' to my grub boot menu

---

### Post by davidvandebunte on 2007-06-07
I'm the guy who originally started the post, recently got back from work...

I tried

sudo cat /etc/network/interfaces
and got...

```

auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp




iface eth0 inet dhcp

```

and when I tried...
sudo cat /etc/iftab
I got...

```

# this file blah blah blah

eth0 mac 00:19:b9:55:62:e1 arp 1
eth1 mac 00:1a:92:7f:83:75 arp 1

```

Note that I have to copy this stuff from one screen to another cause I can't copy and paste onto the internet (can't get it on ubuntu).  That's where the blah blah blah comes from hehe

I tried to follow carolinason's advice to get name servers but didn't really know how to do that for my router.  In result.comf I have:

```

search calvin.edu
nameserver 153.106.64.10
nameserver 153.106.4.99

```

(I go to calvin college during the school year, three weeks ago.  Don't remember even trying to get onto the internet there with ubuntu but I may have.  Very unlikely I got on though)

Also, when I went into etc/resultconf the folder I found something about Avahi not detecting my currently configured local DNS server serves a domain .local.  This is inherently incompatible with Avahi and thus Avahi disabled itself.  For what thats worth.  Please keep trying to help even though this thread is pretty scattered on subjects...

---

### Post by carolinason on 2007-06-07
Sorry davidvandebunte, your thread was hijacked. I just started to answer threads and probably should have waited for your reply.

You'd have to log into the router to check the name servers, they'd be in the dhcp settings "somewhere".

I was just wondering if you have the wrong DNS servers and this is why you can't resolve web pages.

Try going to [http://82.211.81.158/](http://82.211.81.158/), it's ubuntu's web site.

It's a bit late for me right now, but I might have a bit more oil in my head.

---

