---
title: "The 2 router problem"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Detailedghost on 2008-05-26
Ok here's my problem, and u may want to sit down to solve this dooze. ok i have a 2wire 1000SW Homeportal (which is also a terrible router) and a Linksys WRT55AG A+G wireless router. The @wire is connected to the phoneline, the Linksys is connected to that and My desktop (which has ubuntu) is directly connected to the Linksys. I too have laptops connected to the Linksys wirelessly and a slingbox directly connected to it. Here is what it looks like:

Phone line
     |
     |
     |
2wire 1000SW Homeportal
     |
     |
     |
Linksys WRT55AG A+G
     |
     |
[------------------------------------------]
   |           |          |        |
   |           |          |        |
Desktop   |  Slingbox  |Laptop | Laptop




Nows here's my problem, the wireless network that use to be on the Linksys g use to be called "linksys g", but now its gone. Not to mention that ubuntu cannot recogonize the router's internet. So this is what I want to do:
[LIST=1]
[*]Create a new wireless network using Ubuntu
[*]Connect my desktop to the internet
[/LIST]
So what I need help on figuring out is how do I create a home network off of the linksys g and connect all my stuuf to the internet? Thanks or the help.

---

### Post by mapes12 on 2008-05-26
Here are some resources that should help you out. If you can't find the answer here then it's unlikely you will find the answer anywhere:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Also, take a look at this excellent HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If the above doesn't work then consider abandoning your current wifi card and get one that Linux fully supports. I got mine (Comtrend RT2500 - just plug in and it works!) from these guys:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

ndiswrapper is an option for cards not fully supported but in my experience the configurataion breaks down over time. I ended up having to go back to windoze for a while until I got the new card. Natively supported cards work much better.

:guitar:

---

### Post by Detailedghost on 2008-05-26
Ok after experimenting a little, i found out that when i directly connected my 2 wire to my desktop the internet works. So i concluded that the problem isn't the 2wire but rather the linksys itself. When I plugged the 2wire into the linksys and the computer into the linksys, it didn't work. So now how to I make a new network off the linksys so ubuntu can recognize the internet and work?

---

### Post by fwre01 on 2008-05-26
Do both the boxes have a web based GUI you can log into?

what are the subnets being used?

---

### Post by Detailedghost on 2008-05-26
yes they have web-based guis however i cannot access them through firefox. How would I access them? And i don't no the subnets.

---

### Post by fwre01 on 2008-05-26
you need to set your wired interface to be on the same subnet as the boxes.

Firstly we need to establish what both of the routers are doing. Lets cut the linksys out of the equation for a moment and plug straight into the 2wire, what address and default gateway do you get from the router?

---

### Post by Detailedghost on 2008-05-26
i got an ip address that is 65.69..., etc. but how do I find the gateway #?

---

### Post by fwre01 on 2008-05-26
you got an address starting 65.69? you shouldnt be getting that unless you have NIC assigned addresses on your internal LAN. you should be getting an address more like...

192.168.x.x
172.16.x.x
10.0.0.x

could you paste the output from "route" in a terminal?

---

### Post by Detailedghost on 2008-05-26
im sorry if im driving ur patience, im kinda new to the whole linux and terminal thing. Do u mind me asking how I do that? I'm just clueless that's all.

---

### Post by fwre01 on 2008-05-26
sure...what linux are you using? im assuming Ubuntu Hardy? (but as we know, assumption is the mother of all f*** ups! lol)

Click, Applications > Accessories > Terminal

in there type "route" (without the "") and hit return (it might take a few seconds to show all the results)

then just copy and paste the results in here

---

### Post by Detailedghost on 2008-05-26
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
65.69.XXX.XX    *               255.255.255.224 U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         adsl-65-69-141- 0.0.0.0         UG    0      0        0 eth0



here u are.

---

### Post by fwre01 on 2008-05-26
errrm...im a little bit surprised by the results

You appear to have Internet assigned (i.e, routable) addresses on your INTERNAL LAN. (which is uncommon)

I need to know the IP address your box is getting instead of it being X'd out. Who did u say ur providor was? When you purchased ur ADSL did u purchase a block of public address space at the same time?

---

### Post by Detailedghost on 2008-05-26
The IP is 65.69.141.XX and the service provider is AT&T. And i don't think i purchased a block of public access.

---

### Post by fwre01 on 2008-05-26
my appologies, i need the ip address you are getting in full along with the subnet mask. i think whats happening is you are being assigned a block of public IP addresses internally and your other router is probably using private address space, this is why it isnt working.

Convention (i use the term loseley) says that ADSL users get one public address on the outside of their router and use private address space inside their network. i.e 192.168.x.x

i realise this probably isnt helping you very much, but you will probably be paying for those extra addresses and unless u need them i wud advise talking to ur providor about it (if not, we can prob work around it)

Perhaps not untill the morning....iv spent far too long avoiding my revision on this forum, lol, and its now half past midnight, i shud prob get some sleep. i will take alook 2moro if it hasnt already been solved

---

### Post by fwre01 on 2008-05-27
So, public address space...

Basically there are two ways of getting this working, using public address space (which is EXTREMELY dangerous and insecure) or by using private address space, which is the standard way for an ADSL setup.

---

### Post by Detailedghost on 2008-05-29
Oh sorry i could reply back earlier, i had exams to study for :(. Anyways how do I fix this problem? Apparently it could be my internet provider? Dang. Well I appreciate the help and this problem is a tough one to tackle.

---

### Post by fwre01 on 2008-05-30
Well it seems asthough you are using public address space on your internal LAN, it might be best to confirm with your provider what you are paying for. It seems rather unnecessary...

It would be easier to use an internal range inside your LAN and then when clients access the internet they are represented by one public IP address using a technique called Port Address Translation.

---

### Post by Detailedghost on 2008-05-30
Ok, I'm gonna talk to my internet provider about that but anyways back to the main issue. I had a friend come over and check it out. He's a big time Ubuntu guy and networking guy and he explained to me is not the 2wire but the linksys. The linksys apparently has a gui built into it which you access from the browser, but the problem Ubuntu is having is it cannot read the router correctly. 

What do I mean by that? Well Ubuntu for some reason thinks the Linksys is 2 router not 1. It prompts me to use "eth0: avahi" but that makes no sense, because when I use it, it doesn't even work. What my friend told me was that it was a most likely a "port forwarding" issue and he's going to consult his "sensi" before helping me further. So I'll keep posting just for the sake of some other poor sap that's having the same problem I'm having. Also if there are any suggestion on how to edit "port forwarding" that would be much appreciated.

:guitar:

---

### Post by fwre01 on 2008-05-30
OK cool,

it does seem strange, my understanding of avahi is that it allows you to access services on the same broadcast domain without the need for an IP address. you normally see this when you arent being allocated a DHCP address (thats why im guessing you cant access the linksys from the eth0:avahi interface)

Good luck!!

---

### Post by Detailedghost on 2008-06-05
ok my friend was in a bit of a hurry but he traded my Linksys A+G router out with a Linksys G. Why? Well it turns out the other one was broken, so he switched it. He told me the only thing I need to figure out is how to configure this new router.

So does anyone know how I can configure a Linkgsys G WRT54G Router? I was able to configure it on Windows with Internet explorer but how do I do it with Ubuntu? Thanks for the help.
:confused:

---

### Post by Detailedghost on 2008-11-05
Sorry. I managed to fix it. It was not my router rather my provider. I'm good now thanks.

---

