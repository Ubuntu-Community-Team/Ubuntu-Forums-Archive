---
title: "Not at 100% but working on it !!!"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-09
The guy from my isp just came over and some how manually got my internet connection going... for some reason it would not work if i didnt go through my router ???

I clicked applications and add/remove and nearly all apps i selected gave me a msg that i cant install on my pc type (i386)... since the pc is quad core does that mean i need the 64 bit version ???

i cant seem to get better than an 8x6 screen resolution even though video is capable of 2100x1900 (or something similar)...

when i installed ubuntu i did not have an internet connection so perhaps some of the installation is missing ???

do i have to go through a reinstall process or are work around fixes ???

is there a good reason why i need to go through the router for the net ???

does the router create a good firewall ???

[LEFT]please be as non-technical as possible---thanks...
[/LEFT]

NOTAGEEK

---

### Post by jonobr on 2009-07-09
Hello


Your a bit all over the road there:-)

Hope this is not too basic for you.

Ill try to help with what I can

Im not sure of how your set in your home network, however, in most home networks, you need some device to access the isps network (which gains you access to the Internet)

The router used in home offices is not only a traditional router (routing packets to and from your network) but is also a means to transport your packets over a given technology.

So your ubuntu machine, passes IP packets to the router, the router will send them to the internet over a technology.

That technology could be adsl, idsl, cable, dialup, or whatever access technology is there. (For dialup the 'router' would be a modem)

You need to connect your pc to a home router provided by the isp.
Im not sure what your original setup was. and how you were trying to bypass the router, maybe you could explain it some more and I could give some defintiion.

It sounds as if your ISP guy came out and saw your setup, and figured your connections were wrong, moved them around and they worked.

If thats right, then there was no special changes required on ubuntu to get t working,

Typically your router will provide an IP address to your machine,
its like a house number to identify you in your network.
Your router typically gets an ip address to from the ISP,
So when information is destined for you, its sent to your IP address via the router IP address.

The IP address usually assigned the machine your using is usually done using DHCP. THis means when you machine powers up, it says to the router, I need an IP address.
The router says , here you go.
Until you have that ip address you cant do much.,

You can see if you have an ip address by opening a terminal window and typing ipconfig

You  should see something that say, 192.168.1.5 for example.

If you dont see an address like that maybe the ip address was not asked for or given.
In the same terminal window you could type
sudo dhclient

which is almost like doing 
ipconfig /release
ipconfig /renew in windows


On the reinstall, Im not sure why you would need to do that, unless your still having routing problems, which you dont seem to be.

As for using the router as a firewall,

you can do some things with certain routers such as block traffic or redirect traffic, however, ubuntu systems are built with as few services enabled as possible, and in most cases, viruses and worms are more targetted at windows boxes instead of ubuntu machines.
But of course you cant get complacent with security.

Your ubuntu system has an inbuilt firewall which you can add to or take away from

if you go to terminal and type iptables -L

you will see its a bit hard to understand, and you need to know what your doing before tackling that.

---

### Post by LewRockwell on 2009-07-09
> **NOTAGEEK said:**
> The guy from my isp just came over and some how manually got my internet connection going... for some reason it would not work if i didnt go through my router ???

Yes, you should use a router and most will configure themselves to a decent default operating condition upon initial power-up. Routers normally function to restrict/limit/firewall unwanted outside intrusions into your network and/or equipment.

> **NOTAGEEK said:**
> I clicked applications and add/remove and nearly all apps i selected gave me a msg that i cant install on my pc type (i386)... since the pc is quad core does that mean i need the 64 bit version ???

If you are utilizing 64-bit functionality with your equipment then it's probable that you will be using 64-bit compatible applications.

> **NOTAGEEK said:**
> i cant seem to get better than an 8x6 screen resolution even though video is capable of 2100x1900 (or something similar)...

Others have noted similar issues with various video equipment. You'll probably need to identify what you've got and what others have done to successfully correct any deficiencies.

> **NOTAGEEK said:**
> when i installed ubuntu i did not have an internet connection so perhaps some of the installation is missing ???

After initial installation there may be several hundred updates immediately selectable/required and those should be done asap.

> **NOTAGEEK said:**
> do i have to go through a reinstall process or are work around fixes ???

Do the updates first and see what happens.

.

---

### Post by NOTAGEEK on 2009-07-09
> **jonobr said:**
> Hello


Your a bit all over the road there:-)

Hope this is not too basic for you.

Ill try to help with what I can

Im not sure of how your set in your home network, however, in most home networks, you need some device to access the isps network (which gains you access to the Internet)

The router used in home offices is not only a traditional router (routing packets to and from your network) but is also a means to transport your packets over a given technology.

So your ubuntu machine, passes IP packets to the router, the router will send them to the internet over a technology.

That technology could be adsl, idsl, cable, dialup, or whatever access technology is there. (For dialup the 'router' would be a modem)

You need to connect your pc to a home router provided by the isp.
Im not sure what your original setup was. and how you were trying to bypass the router, maybe you could explain it some more and I could give some defintiion.

It sounds as if your ISP guy came out and saw your setup, and figured your connections were wrong, moved them around and they worked.

If thats right, then there was no special changes required on ubuntu to get t working,

Typically your router will provide an IP address to your machine,
its like a house number to identify you in your network.
Your router typically gets an ip address to from the ISP,
So when information is destined for you, its sent to your IP address via the router IP address.




WOW !!! I amazed cuzz i actually understood SOME of that...  lol...

thanks much for the input your time is appreciated... 

my isp is different than most... it is a wireless broadband but there is a send/receive antenna in my yard that talks to a local tower a few miles away... no router is required other than a small box in my house... the ethernet cable runs from the outside antenna into the small unit in the house (router ???) that also has a small transformer that goes from it to a/c current... the ethernet cable then goes from the box to the pc lan... i bought a d-link router when i thought i was going to buy a laptop for the wireless in the house and i ended up with a desktop...

the d-link is not required but had to be put in line between the desktop and the little box router... after that the "isp guy" had to manually tell the broadcast tower the mac address of my gig lan... at that point we had a bingo !!!

i know, i know---i just dont know how to talk tec geek talk yet but thats the only way i can explain it...





> **LewRockwell said:**
> Yes, you should use a router and most will configure themselves to a decent default operating condition upon initial power-up. Routers normally function to restrict/limit/firewall unwanted outside intrusions into your network and/or equipment.

If you are utilizing 64-bit functionality with your equipment then it's probable that you will be using 64-bit compatible applications.

Others have noted similar issues with various video equipment. You'll probably need to identify what you've got and what others have done to successfully correct any deficiencies.

After initial installation there may be several hundred updates immediately selectable/required and those should be done asap.

Do the updates first and see what happens. 


thanks to you also lew... the 9.04 disc that i installed from is 32 bit if that matters ???

my vid card is an msi nvida 9600 gt with 1 gig of ddr3 whatever that means... i have yet to get the hdmi out working either and am working off the vga... i am using a 1080p large lcd tv for a monitor...

i went top center of the screen and clicked help and in the dropdown box ck for updates was gray and not selectable... perhaps i can try later with the install disc inthe opti drive if that might help... is there a better way to check for updates ???

thanks...

NOTAGEEK

---

### Post by Sealbhach on 2009-07-09
To check for updates, go to the update mananger

System>>Administration>>Update Manager

You can also do this using a terminal, it's just another way of doing the same thing. Open a terminal and enter the command

```
sudo apt-get update && sudo apt-get upgrade
```

.

---

### Post by LewRockwell on 2009-07-09
you'll notice on the download page([http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)) near the bottom there is a selection between 32-bit and 64-bit

I don't see a reason why you shouldn't try out the 64-bit LiveCD to see if it works any better for your equipment

one note though, I seem to remember that some 64-bit machines may have a BIOS switch selecting either 32-bit operation or 64-bit operation

.

---

### Post by NOTAGEEK on 2009-07-09
> **Sealbhach said:**
> To check for updates, go to the update mananger

System>>Administration>>Update Manager

You can also do this using a terminal, it's just another way of doing the same thing. Open a terminal and enter the command

```
sudo apt-get update && sudo apt-get upgrade
```.


Thanks sealbhach --- worked perfect and told me my system was up to date... i might learn small but i learn...

Now if i could download stuff without getting the i386 error msg life would be better... lol...




> **LewRockwell said:**
> you'll notice on the download page([http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)) near the bottom there is a selection between 32-bit and 64-bit

I don't see a reason why you shouldn't try out the 64-bit LiveCD to see if it works any better for your equipment

one note though, I seem to remember that some 64-bit machines may have a BIOS switch selecting either 32-bit operation or 64-bit operation

.


thx again lew...  i am not comfortable going into bios yet so i called tech support at the builder...  this guy went into asus mb, and ami bios etc. and i just cought a word here and there... i think he might have even mentioned a flux capacitor and i thought they were for time traveling... i finally asked for a bottom line answer and he said that my bios does not need to be switched... then he went on about compatibility issues with software etc. etc. yikes !! the question i sked of course only needed a 1 word answer...

perhaps when my confidence level increases some i can look into a 64 bit install ???

NOTAGEEK

---

