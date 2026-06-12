---
title: "How to make a Dialer in Edgy for Eth card??"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by rksenthilkumaar on 2006-11-15
During the Edgy Installation, it detected my Lan Card correctly & I'm able to configure it.
My problem is: _My Modem is set in such a way that it will jst establish a link & whenever I need, I should dial & log on!_ (This is how I have ben using my PPPOE connection in XP! I use to create a dialer thro Control Panel-->Network Connections-->Setup New-->Type of connection:pppoe-->Usename & Passwd-->ok, Should I do something similar to that?? How to do??)
So do you know how to create a dialer for Ubuntu 6.10??
I'm new to Linux & if some one could help me figure this out, I would be really grateful.
If it starts connecting to net, the remaining things about it will be so simple to learn!

---

### Post by towsonu2003 on 2006-11-16
I believe you are supposed to use the "sudo pppoeconf" command from the terminal (alt+f2 and type gnome-terminal)

I found this info after a quick search. A better search on the forums should reveal a better guide for this
[quote=http://balajoe27.wordpress.com/2006/10/31/100-ubuntu-linux/]
to setup new <bla> account just type the pppoeconf on the terminal and click yes all the way from there.Must provide <bla> username and password only

pon-dslprovider to on connection
poff-dslprovider to turn off connection
[/quote]

note that you can use dhcp (much much much easier to use) if your modem is also a router. 

also note that if your modem is connected to your machine via a usb cable, it's really hard to set that up. 

this has a little bit of info as well: [http://www.ubuntuforums.org/showthread.php?t=288645&highlight=pppoeconf](http://www.ubuntuforums.org/showthread.php?t=288645&highlight=pppoeconf)

---

### Post by rksenthilkumaar on 2006-11-16
I also face a problem in connecting to internet!
Now I'm using Ubuntu 6.10
During Installation it properly detected my Eth card & I'm able to configure IP & also could "sudo pppoeconf" as well!!
When I type "pon dsl-provider" it says the connection is on.
But I'm unable to view any sites!!
Even I'm unable to view: 192.168.1.1 let alone type username & password as admin & admin!!

But I could see my modem blickering, when some data's are  transferred during the time of connection!!

I'm using Huawei SmartAX MT 882 Modem.
The Connection is dataone [BSNL]

Could some body help me out??

---

