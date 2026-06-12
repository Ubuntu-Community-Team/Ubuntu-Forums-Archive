---
title: "Two network cards"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by Bill007 on 2006-11-19
Kia Ora All from Wet New Zealand:rolleyes: 

I Have decided I would like to set up a server using ubuntu 5.10
I have installed just the base system

wanting to run my own production server

Loaded 
Apache2
A MYSQL SERVER
PHP5
PERL
RUBY
FASTCGI
WEBMIN ETC all has gone well

I have two network cards 

eth0 is set to dhcp 

(Which is finding my router and the internet fine as i have downloaded all the neccesary packages thru it so far)

eth1 is set to static settings below

auto eth1
iface eth1 inet static
address 192.168.1.100
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1  

but I cant seem to make it find the lan network 

I have gone to a remote machine on the network (running xp windows) but cant pull up the webmin interface  

Its almost like the network card eth1 is not being recognised by the server machine and its not configuring with the static settings 

I have made the changes with sudo nano /etc/network/interfaces

everything is saved

going nuts](*,) 

REGARDS

[URL="http://newplymouthmotel.co.nz"]
New Plymouth accommodation[/URL]

If you see me getting smaller Im leaving

---

### Post by Peter76 on 2006-11-19
What is the ip you get on eth0 ( ifconfig eth0 )? If it is something like 192.168.1.whatever, note the 1 here as third number, change your settings for eth1 so the third number is a 2 ( or something else, but NOT a 1 ). Good luck

---

### Post by Bill007 on 2006-11-19
Hey thanks for that

I made the changes but then my key board stopped functioning out of the blue never happened before 
I then crashed the server and now have no monitor @#$#$#^#!! OR IT CANT SYNCHRONIZE AT LEAST 
I  will be back by the looks after a complete rienstall ugg good practise  
i should be quiet adept at ubantu intallation some time soon

over and out time for sleep

Regards Bill007

[newplymouth accommodation]("http://newplymouthmotel.co.nz")

---

### Post by lloyd_b on 2006-11-19
What is probably happening is that eth0 is configured as your default, so that all packets (including packets to the 192.168.1.x network) are being sent via it.

First question:  What network range is eth0 using?  This can be determined by going into the router configuration.  Alternately, you could just type "ifconfig" and see what IP eth0 has been given.
 
Second question:  What routes are being defined?  Just type the "route" command in a terminal window, and you'll see a list of all defined routes.
Look for a default route (the word "default" or a "destination" of 0.0.0.0), and see which interface it's associated with.

Lloyd B.

---

### Post by Bill007 on 2006-11-19
Thanks lloyd_b

sounds like you could be touching on something there 
that default situation sounds like the real cause

how can I either reset the default or even get rid of that default setting what are your suggestions 

but unfortunatly Im stuffed as I may have cooked my on board graphics card god knows how

must have been tied in with machine crashing

SO ill be outa action untill i resolve this new problem 

Regards Bill

---

