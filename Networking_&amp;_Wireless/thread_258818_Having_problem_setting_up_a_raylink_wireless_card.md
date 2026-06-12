---
title: "Having problem setting up a raylink wireless card"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by darkchronos on 2006-09-16
My college is still using 802.11 for its wireless infrastructure and is using raylink as the vendor. I have been trying to get the card to work but ot no avail. A friend of mine has it working under mandriva, but when I tried to use the same settings he used it would not work.

In my config.opts I entered this line

#Raylink Config
#Infrastruture network for older cards
module "ray_cs" opts "net_type=1 essid=daytona"


and when I use iwconfig this is displayed
eth1      IEEE 802.11-FH  ESSID:"LINUX"
          Mode:Ad-Hoc  Channel:11  Cell: Not-Associated
          Bit Rate:0 kb/s
          RTS thr: off   Fragment thr: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

for some reason the card wants to stay in ad-hoc when it should be in infrastructure. when i finally was able to get the card's settings right, it would not find an access point. ](*,) 

can anyone help me fix this problem ? :frown:

---

### Post by lupine_nickt on 2006-09-17
config.opts? What on earth is that? 

Use /etc/network/interfaces instead - you can use the wireless-* options within it to set your card up.


xF,

...Nick

---

### Post by bionnaki on 2006-09-17
what card do you have? what driver does it use?

---

### Post by darkchronos on 2006-09-17
i tried using the method you talked about nick but it still wouldnt work. The one thing it did do was set the essid and mode when i plug the card in, but it will still not find an access point

as for the card its a 
raylink pc card wlan adapter by raytheon eletronics 
model number 24020

and the driver it uses is ray_cs

really old .... its only 802.11  :(

---

### Post by MaindotC on 2007-04-17
Hi.  If either of you have provided a solution for this problem I'd love to know it :)  I'm using an IBM Thinkpad T60, Ubuntu Edgy Eft, and I have the Raylink Model 24020.  We're supposed to be upgrading to 802.11n next semester but anything you could help me with now would be appreciated :)

Alan

---

### Post by tturrisi on 2007-04-17
start here:
[http://www.hpl.hp.co.uk/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.html#Raylink](http://www.hpl.hp.co.uk/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.html#Raylink)

---

### Post by MaindotC on 2007-04-25
It will take me a while to dissect the instructions on the website and connected sites, but I think this helps quite a bit.  Thank you so much for being aware :)

Alan

---

### Post by MaindotC on 2008-01-06
I don't imagine this post is visited much more, but 802.11 is out, and now we're straight b/g/n.  Only issue is at this time there is no auto-configuration utility for *nix that inputs the WPA key without the student seeing it.  They have to take their lappers to the helpdesk and the key is manually entered :(  Very 1.0 if you ask me.

Has anyone experimented with N cards for *nix and what type of results did you receive?

---

