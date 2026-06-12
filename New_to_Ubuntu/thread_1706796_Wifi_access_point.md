---
title: "Wifi access point"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by abhibr95 on 2011-03-14
Hey guys can you tell me how to make my laptop a wifi access point with the same wireless card i use to connect to the net?? 

Any help is appreciated. I installed Ubuntu just 2 days ago... so dont know anything yet... Thanks anyway

---

### Post by 311005901 on 2011-03-14
I've been looking for this too! I'd love to have my laptop tether to my devices that can receive Wifi, but cannot connect to a secured Wifi signal (e.g. Nook).

I hope somebody has a solution out there.

---

### Post by Hippytaff on 2011-03-14
There are a number of [howtos]("http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html") on this. I searched for 'linux ap' 'linux access point'

---

### Post by 311005901 on 2011-03-14
Thanks for the reply, but that article is almost 8 years old. I feel it is a little outdated using 802.11b as the standard and it also isn't very beginner friendly (you have to compile your own kernel).

---

### Post by Hippytaff on 2011-03-14
> **311005901 said:**
> Thanks for the reply, but that article is almost 8 years old. I feel it is a little outdated using 802.11b as the standard and it also isn't very beginner friendly (you have to compile your own kernel).


I didn't actually read it...should've before I recommended it, but it was just an example (a bad one). I'm sure there are more relevant ones about ;-)

---

### Post by 311005901 on 2011-03-14
:lolflag:
Thanks anyway!

---

### Post by wep940 on 2011-03-15
> **311005901 said:**
> I've been looking for this too! I'd love to have my laptop tether to my devices that can receive Wifi, but cannot connect to a secured Wifi signal (e.g. Nook).
 
I hope somebody has a solution out there.
 
 
Until I totaled my car and had to sell it to get some money, I had a nook wi-fi, and it connected to my WPA2 hidden network just fine.  What kind of problem are you having?

---

### Post by abhibr95 on 2011-03-15
The problem is that when I connect to the internet using a wired connection when I can create a wireless access point with my wifi card. But now what I want is to create a access point in my laptop and to connect to the main router with the same wifi card

---

### Post by inukai on 2011-03-15
> **abhibr95 said:**
> The problem is that when I connect to the internet using a wired connection when I can create a wireless access point with my wifi card. But now what I want is to create a access point in my laptop and to connect to the main router with the same wifi card
So you want your laptop to be connected to two wi-fi networks (Your router and your access point) simultaneously? I'm not sure if that can be done, but I'm not positive. 

To make an access point from your laptop, I would go to the wireless network icon, and click it and then click add new wireless network, then just name it and set security settings (WEP key, etc.) I think this is what you're trying to do when you say you want to make an access point on your laptop.

---

### Post by abhibr95 on 2011-03-15
@inukai: No no. I connect to my home router using Wifi and I get internet connection on my laptop. Now with the same wifi card I would like my laptop to behave like an access point so that other devices like my phone can browse the net through my laptop

---

### Post by wep940 on 2011-03-15
It sounds to me like you either want internet connection sharing, or else you want your laptop to act as a server.  I don't know how to do either one, but may someone else can tell you now that you've clarified things a bit.
 
BTW - when I asked in my previous post I was referring to connecting you Nook to an encrypted network.  I had mine connecting to my hidden wpa2 network with no problem.  Be sure to check the settings page.

---

### Post by 311005901 on 2011-03-16
Thanks for the suggestion wep940, but it simply does not connect to my WEP2 secured with TTLS and MS-CHAPv2. I'm running an original Nook (not color) that is unrooted.

---

### Post by wep940 on 2011-03-16
> **311005901 said:**
> Thanks for the suggestion wep940, but it simply does not connect to my WEP2 secured with TTLS and MS-CHAPv2. I'm running an original Nook (not color) that is unrooted.
 
WEP2?  I guess I haven't kept up on things.  I run WPA2 tkip/aes or aes/tkip, which ever way around it goes with a password with no problem.  However, I don't recognize ttls or ms-chapv2 as any name I remember seeing in the docs for the Nook.  I could do some more searching and see if I find anything.

---

### Post by Tweak42 on 2011-03-16
I was looking to use single wireless nic as an AP as well awhile back but gave up.  I have similar situation, wpa2 mschapv2 network which my wifi enabled phone doesn't support.

In windows I was able to use a 2nd USB nic and route the traffic through.  In linux you can do it at the command line configuration but it's rather complicated and I rather use NetworkManager to handle connections.  

However NetworkManager, which Ubuntu uses is either incomplete or bugged (its up to v0.8.1 atm) and I was only able to get the connection part, but not the routing part working.  It was not a huge priority so I never got around to following up on the NetworkManager project page to see it it's been fixed.

P.S. mschapv2 is used so you can have granular login/password for individual users as part of the wireless authentication connection.

---

### Post by 311005901 on 2011-03-18
> **wep940 said:**
> WEP2?  I guess I haven't kept up on things. ...

Whoops. I was mistaken. Sorry about that. It's not WEP2.
It's a WPA2 Enterprise network with Tunneled TLS authentication and the inner authentication is MSCHAPv2.

I would like to tether my secured/encrypted wifi through my netbook running Ubuntu to my Nook through an unsecured wifi connection.
Can this be done?

---

### Post by wep940 on 2011-03-18
Just for the heck of it I sent an email to Nook tech support about connecting with your network - the response kind of says it all - please call as we need to work with you on this.  Pretty much says beats the heck out of us, eh?
 
I wish I could help more on what you are trying to do, but I don't even know if it's possible to do what you want without your PC acting as a server.
 
Best of luck, and sorry I don't know enough to help.

---

### Post by 311005901 on 2011-03-20
Thanks a lot! Thanks for your help!

---

### Post by wep940 on 2011-03-20
I did find this Wiki page for sharing internet connections in Ubuntu. Right above the "Wireless Ad-hoc connection sharing scenario" is a small section that sounds like it deals with using wireless for this. I've never tried anything like they talk about, so I don't know if you can end up with your wireless acting as a gateway or not. I think what you want to do is normally done by hard-wire connection between the device and the ethernet port on the PC that uses its' wireless connection to see the net. If I understand things, you want to do this:
 
internet cloud
|
|
your wireless modem/router
|
|
wireless connection to your PC ----- wireless connection to other device that wants to share your PC's wireless connection.
 
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
 
That Wiki pretty much says your PC can go wireless to the net, but any devices wanting to share that connection via your PC must be hard-wired to the PC'c ethernet port.  The gateway suggest says you must have 2 adapters in order for it to work.
 
The end result is that you will probably need to hard-wire a connection between your other devices and the ethernet port on your PC and sharing that PC's internet connection.  I know that throws a few kinks in some of the ideas, since some of the devices you wanted to use are either USB connect or wireless connect, but no hard-wire connection.

---

### Post by stevenwscott on 2011-05-02
That is a correct assumption; once your has been defined as an AP and activated it cant be used to connect to another AP. You will need a second nic/path out of you system. 

I have been successful in sharing my wireless connection and routing to a bluetooth tethered cell phone, but it took some hacking to make it work. The Ubuntu guide you mention doesn't tell the whole story, and on my system (Lucid 10.04) there were glaring deficiencies in the "Shared Network" implementation. 

That said, here's the notes from what I did, with some caveats: 
* - Only tested on Lucid 10.04
* - The following actions create a temporary network only. This suited my purposes so if you wish to have a permanent configuration you will have more to do than what is in these notes.
* - I arrived at this solution while on vacation and I didn't feel like spending the time to properly address the issue, but these steps, if taken in exact order, should achieve the desired effect by pre and post configuration of certain network properties. Unfortunately, you have to execute these steps whenever you want to activate sharing again - that's what the "properly address" part is about.
* - NetworkManager is you enemy in this endeavor. If anybody can figure out how to get it to play along nicely, I would be very interested in your solution

1. Create a new shared wireless network with NetworkManager

2. make sure dhcp3-server is installed and not in system startup (unless thats what you really want!)

3. edit /etc/dhcp3/dhcpd.conf with appropriate configuration for your wireless (pick a subnet & iprange, etc. - add the "domain-name-servers" option - *** NOTE *** you will need to verify it matches /etc/resolv.conf after connection to ppp)

4. sudo ifconfig wlandev ip.ip.ip.ip (YOUR WIRELESS) GATEWAY YOU PUT IN DHCP3 CONFIG

5. sudo /etc/init.d/dhcp3-server start

6. "connect" to hidden wireless network in NetworkManager - choose the one you created previously

7 . sudo ifconfig wlandev ip.ip.ip.ip     AGAIN!! - IP IS GATEWAY YOU PUT IN DHCP3 CONFIG

8. connect to ppp/wan network - if DNS server differs, alter dhcp3 config domain-name-servers and restart dhcp3-server

9. echo "1" > /proc/sys/net/ipv4/ip_forward

10. sudo iptables -A FORWARD -i ppp0 -o wlan1 -j ACCEPT

11. sudo iptables -A FORWARD -i wlan1 -o ppp0 -j ACCEPT

12. sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

Should be working at this point. If not, ck IPs, dhcpd.conf, pings, gateway, route, etc..
Good luck!

---

### Post by 311005901 on 2011-05-17
Those are quite difficult instructions, but thanks anyway. :)
I'm looking for a simple tethering program. Do they exist for Linux?

---

### Post by Tweak42 on 2011-05-17
> **311005901 said:**
> Those are quite difficult instructions, but thanks anyway. :)
I'm looking for a simple tethering program. Do they exist for Linux?

You can give Firestarter a shot.  It's in the Ubuntu Software Center.  I tried awhile back, but didn't get it to work.

[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

---

