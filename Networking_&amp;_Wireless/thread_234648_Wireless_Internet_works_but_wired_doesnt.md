---
title: "Wireless Internet works but wired doesnt"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by jbodell on 2006-08-11
Hello all, I am stuck with a wierd networking problem. I have a wireless router also with 4 eth ports. I can connect to the router (and Internet) wirelessly with no problems. I have been forced to move this computer into a different room which cannot receive any of this wireless signal due to the walls being too thick. I bought a couple of 'homePlugs' to send the internet from the router into this room. ([http://www.justhomeplug.co.uk](http://www.justhomeplug.co.uk)) 

I can obtain an IP via dhcp no problems, I can also Ping my router, google, and all other domains I have tried. I CANNOT view any pages whatsoever through my browser, (that includes the router- 192.168.2.1), I also cannot wget anything from command line. I can however, view pages hosted by the box (apache2) using [http://127.0.0.1](http://127.0.0.1) and 192.168.2.5- the internal network IP. From an XP box on the same network, I can also view these webpages hosted on the Ubuntu box. I have ipv6 DISABLED in Firefox- this did not correct the problem. 

There appears to be no problem with the homePlugs, as the box I am writing this on (XP) is connected to the internet through the exact homePlugs I have tried to use with Dapper. 

Hopefully this is a straightforward problem, as removing Ubuntu is not an option.

Thankyou all in advance!

---

### Post by coffeecat on 2006-08-12
Baffling. I've got just one suggestion. You say, 'as the box I am writing this on (XP)..' which suggests that you have different physical computers for Windows and Ubuntu rather than a dual-boot. If so, could the ethernet port on your Ubuntu box be faulty? See if Ubuntu is detecting and configuring the ethernet port. Also, again if you have two computers there, suggest you try running the Dapper live CD from the Windows box to see if it can connect through that box's ethernet port.

By the way, I have the Devolo microlinks. Similar to your Homeplugs - just a different make. Excellent aren't they? I was showing them to someone and commented that they were expensive. He replied, 'much cheaper than getting in an electrician and then having to replaster and redecorate.' True enough. :)

---

### Post by jbodell on 2006-08-12
Hi thanks for the reply. 

I've tested the homePlugs on Dapper Live on the XP box and they work. I will test the plugs with Dapper Live on my problem box now. If that doesnt work I guess its gotta be my ethernet adapter that is broken. I'll let you know how it goes. 

Cheers!

---

### Post by jbodell on 2006-08-12
OK problem solved for anyone interested. The problem was actually to do with the homePlugs. I ran an extension cable into the room I need internet in, plugged the homeplugs into the extension and it works on the Ubuntu Box. This must mean that the room I am in and the room the router is in use different powerlines? Highly irritating! The whole idea for the homePlugs was so I didnt have cables lying around the place- and this room also receives no wifi signal! I will not give up!

---

### Post by coffeecat on 2006-08-12
Have a look in your junction box where the trip switches are. You've probably got two (or more) rings for the wall sockets. If I'm right that means that the signal won't pass from one ring to another.

Irritating but reassuring because the reason the Devolo devices encrypt the data stream with a password is to ensure your neighbour can't tap into your signal - apparently that's theoretically possible.

I'm glad you've posted. The electrician who wired my house must have been inhaling something because I've got two mains rings with a weird layout. In three rooms, sockets at different ends of the room are on different rings - and there's no vertical logic to it either. That might have thrown me if I'd decided to move any of my equipment.

**Edit:** No, I've just checked. The two microlinks are plugged into sockets on different rings but I'm getting good data transfer - about 75-77 Mbps, against a maximum possible 80. Strange. Must be whatever the electrician was inhaling. :)

---

