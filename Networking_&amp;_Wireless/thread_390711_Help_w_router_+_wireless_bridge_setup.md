---
title: "Help w/ router + wireless bridge setup"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by tj.milligan on 2007-03-22
This is not a distro-specific question, but I'm asking for help setting up a wireless bridge so that I can avoid wireless network card driver hell w/ Ubuntu. I have a dsl modem connected to a Linksys WRT54GL right now. I'm introducing a Buffalo  WLI-TX4-G54HP Wireless Ethernet Converter. Problem is, my Linksys is at 192.168.1.1 (by default my devices would be at 192.168.1.101, 192.168.1.102, etc) and my Buffalo is at 1.1.1.1.

My question is two-fold. (1) In order to set the Buffalo up, what do I plug into what, and (2) how do I set my computer to 1.1.1.2?

(The Buffalo's instructions say to do #2, but I have no idea how to set this up in the router and still have connectivity)

[I]For reference, this is my previous thread:
[http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871)

and this is the Buffalo converter:
[http://www.newegg.com/Product/Product.asp?Item=N82E16833162168](http://www.newegg.com/Product/Product.asp?Item=N82E16833162168)[/I]

Thanks in advance

---

### Post by chili555 on 2007-03-22
In order for your bridge to connect to your router, the bridge has to be in the IP address range of the router. I would suggest re-assigning the bridge with a 192.168.1.x address.

This brings up DHCP. You really only want one DHCP server on your network, presumably the router. If you set up the router to hand out ten IP addresses, from x.101 to x.110, then set up the bridge with an IP address outside this range, to avoid those pesky fatal collisions, such as 192.168.1.115. Then turn off the DHCP server in the bridge. 

Set up the computer attached to the bridge with a static IP, also outside the range of the router, say 192.168.1.118. Try connecting, pings, etc, unencrypted first, just to be sure everything is done right so far.

Now, encryption. Figure out the most secure form of WPA both devices support and set up in the admin pages of each device. Write down the password you generate, check it twice and run to the other device and repeat.

Post back if you need more help.

---

### Post by SactoBob on 2007-03-22
Hi, I see that you bought that bridge on my recommendation, so I guess I should help you with setup.  (Plus, my family is from Ventura, so I might run into you.)  You are going to love that bridge once you get it set up.  Admittedly, the directions are not that great and assume some knowledge that you might not have.  I am not home with the router right now, but will give it a shot.  Drop me a p.m. if you like, and I will even help you over the phone if you want.

First task is to communicate with your bridge.
Pull out your old wireless pci card to avoid any confusion.
You plug in the power supply and power up the bridge.  It has four ethernet outlets.  Plug one of the supplied cables into any one of the ports, and the other end into the ethernet port of your computer.

Now go to your Network Menu in Ubuntu, which is a submenu under "System" -"Administration".
Click on "Wired Connection" and set its properties.  You want to temporarily set the ip address of the computer (configuration) to Static rather than DHCP(auto), and specify the address of 1.1.1.2
The reason you work with the "wired" menu is because your computer will see the connection as "wired" since all the wireless stuff is handled by the bridge itself.

The reason you select "static" at "1.1.1.2" is because the bridge has its address set at 1.1.1.1
To communicate with it, you must set your computer's wired connection address to something on the same subnet - that is 1.1.1.2 through 1.1.1.255.  Since the manual recommends 1.1.1.2 and that is fine, just use it.

Now your router has the default address of 1.1.1.1 and your computer has the address of 1.1.1.2  so your computer can talk to the bridge.

The way to do this is to start your web browser, presumably Firefox.
Up at the top, where you usually type in the address that you want to go to, such as google.com, instead type 1.1.1.1

Don't precede the numbers with "http://" etc.  Just type 1.1.1.1 and nothing more, and then enter.  Since the bridge ("ethernet converter") is at 1.1.1.1 you will see its menu.  If you don't, you probably failed to set the computer's address to static at 1.1.1.2

If you know absolutely nothing about networking, it would be good to have the help of a friend who does, but you could also use this as an opportunity to learn.

There is a main menu which handles connection.  Click the "Refresh" item, and your router should appear.  Connect with your router.
You will also see an item marked "Advanced".  From there you can do such things as change the address of your bridge and change many settings that you should not have to.

Once the bridge has connected to your wireless router, you are nearly done.  But there is a Catch-22.  Remember, you set your computer's ip address to 1.1.1.1 to talk to the bridge's menu.  But your router is at 192.168.1.1.  So go back to System, Network, and now set your wired connection back to DHCP (auto), assuming that your router is using DHCP, which is almost for sure its default setting.  At that point, you should be in business.

If you are a network newbie (or even if you are not), it may take a couple tries if, for instance, you mistyped the encryption key, or set the wrong type of encryption or something.  That can be a PIA.  Every time you have to go back and talk to the router, you must repeat the same cycle.  Set the computer network ip to 1.1.1.2, then make the changes, and then reset the computer network ip to DCHP.  In fact, you might also do a reset first as shown below.  Once the bridge gets a DHCP address from the router, it is no longer on the 1.1.1.x subnet.  You can be sure it is there with a reset.  The sooner you configure the address of the bridge on your existing network subnet (below), the better.

Eventually, you may want to change the ip of the bridge so that you don't have to repeat this cycle.  One of the menus on the bridge has a way to change the address of the bridge.  Since your router is at 192.168.1.1, you could change the default address of the bridge to 192.168.1.50.  If you do that, write it down on a piece of tape to the bridge so that you don't forget the new number of the device.  Since it is now on the same subnet as your router, you don't have to change anything to get at the menu.  Just go to your browser and now type 192.168.1.50 and your menu will pop up.  At this point, 1.1.1.1 will no longer work, since you changed that address.

If things go horribly wrong or you ever forget, there is a reset button on the bridge.  Hold it down for several seconds and the bridge reverts back to its default state of 1.1.1.1 and you can start over.

These instructions sound long, and if it is your first time setting up, will seem a bit complex.  but once you do the setup you will see that the actual work itself is pretty easy.  I think you will be pleased with the performance of the Buffalo.  You can run 4 ethernet cables off of the bridge.  You can unplug the bridge and move it somewhere else.

If you ever take it somewhere else where you have to connect to a different wireless network, you will have to go through the setup again.

As I said, I will be home this evening.  Drop me a pm and I will even run  you through it over the phone if you don't rub it in on how beautiful the weather is in Ventura.

Bob

---

### Post by tj.milligan on 2007-03-23
chili555, SactoBob,

Thanks for the input. =D> I'll attempt this tonight when I get home (yesterday I attended [USC-LUG]("http://linux.usc.edu/") immediately after work, which coincidentally centered around alternative Linux-based firmware solutions for Linksys WRT54GL router:)). I'm a database programmer who took networking as part of my ComSci BS curriculum, but sadly all I remember from that class is the OSI model and the difference between TCP and UDP :rolleyes: I'm excited to get this bridge to work not only to avoid Linux-wireless-network-driver-hell, but also to get hands on experience with the "advanced" side of networking. All the while using my fav all-around distro!

---

### Post by tj.milligan on 2007-03-26
Works like a charm! Got everything set up in ten minutes *and* it's super fast (the access point is directly above on the second floor). Thanks for a push in the right direction! Wireless Bridge + Linux is the only way to roll.

---

### Post by willl on 2007-06-12
> **SactoBob said:**
> Eventually, you may want to change the ip of the bridge so that you don't have to repeat this cycle.  One of the menus on the bridge has a way to change the address of the bridge.  Since your router is at 192.168.1.1, you could change the default address of the bridge to 192.168.1.50.  If you do that, write it down on a piece of tape to the bridge so that you don't forget the new number of the device.  Since it is now on the same subnet as your router, you don't have to change anything to get at the menu.  Just go to your browser and now type 192.168.1.50 and your menu will pop up.  At this point, 1.1.1.1 will no longer work, since you changed that address.

Does the converter's IP have to be within the range assigned by DHCP? My router/cable modem provided by the cable company is set to distribute a range of only 5 IPs (not sure whether this is adjustable or fixed by the ISP, probably the latter), so I'm wondering about the potential for conflicts. 

Phrased as a general networking question. If DHCP distributes, for example, a range of 192.168.1.10 to 192.168.1.14, can you set a PC to a static IP of, let's say, 192.168.1.50 and have it still reach/be recognized by the router?

This is a fantastic unit, btw, which I highly recommend.

---

### Post by chili555 on 2007-06-12
> range of only 5 IPs (not sure whether this is adjustable or fixed by the ISP,Probably adjustable, but if you have only 2-3 computers on the network, there is no need to do so.> If DHCP distributes, for example, a range of 192.168.1.10 to 192.168.1.14, can you set a PC to a static IP of, let's say, 192.168.1.50 and have it still reach/be recognized by the router?Yessir. My router is set to allow addresses from 192.168.1.101 to 192.168.1.150, yet I have a wireless access point configured as a repeater that uses 192.168.1.245.

---

