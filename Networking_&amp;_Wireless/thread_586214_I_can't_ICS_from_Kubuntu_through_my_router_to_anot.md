---
title: "I can't ICS from Kubuntu through my router to another computer. plz help!"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by GrantShoe on 2007-10-22
I have my kubuntu computer connecting to the University's network and then I'm wirelessly connected to my router which has a NAS drive on it.  I have no problem connecting to the internet through DHCP and mounting the ntfs NAS drive but my issue is with sharing the internet through the router to another computer.

I've been trying to research this and I tried to install firestarter but I'm not really getting anywhere with that.  I also tried searching on here and I haven't really found this issue too much.

How can I ICS(or NAT... whatever it's called) from Kubuntu through my router and to another computer.  When I did this with XP-XP in the past, it was fairly simple and I just checked the ICS button on the wireless card's properties and on the other computer specified a gateway and the DNS servers.  It's definitely more complicated on linux.

One last thing... I know this is a pain in the *** but is there a way to graphically do this rather than terminal?  I can work with the terminal but I prefer to use an interface.

---

### Post by dmizer on 2007-10-22
you shouldn't have to do anything other than plug your second computer into the router, grab an ip from the router, and browse.

a router does nat (ics) for you so you don't have to.  are you sure you have a router and not a hub?

if you have a hub, you will need to restructure your network like so:

university network > kubuntu network card 1 |NAT| kubuntu card 2 > wireless hub > second computer

---

### Post by GrantShoe on 2007-10-22
> **dmizer said:**
> you shouldn't have to do anything other than plug your second computer into the router, grab an ip from the router, and browse.

a router does nat (ics) for you so you don't have to.  are you sure you have a router and not a hub?

if you have a hub, you will need to restructure your network like so:

university network > kubuntu network card 1 |NAT| kubuntu card 2 > wireless hub > second computer

Ahhhh yes.  It's a router but I'm using it as a hub.  The problem is that the University has a strong authentication system so I need to use a computer rather than a router to log in and from there I can share my internet connection so I really need to configure the |NAT| part of that.

sorry for the bad explanation

---

### Post by dmizer on 2007-10-22
no problem.

most routers can also handle authentication.  what kind of authentication are you needing to pass (ex: ppoe pppoa)?  also, what brand/model of router are you using?

---

### Post by GrantShoe on 2007-10-22
> **dmizer said:**
> no problem.

most routers can also handle authentication.  what kind of authentication are you needing to pass (ex: ppoe pppoa)?  also, what brand/model of router are you using?

I actually work for the school's computer systems so I know that there's limitations on the routers.  Routers can't authenticate to the wired 802.1x system here.  When you plug a router into the port, it automatically shuts off your port and you have to call and get it enabled.  I had to install some kind of modified version of WPA supplicant to get my linux box working.  Really all I need is some kind of guidance on how I can set up kubuntu to share the internet with my hub/other computers on the LAN :confused:

---

### Post by dmizer on 2007-10-22
for internet connection sharing to work, you will need two internet adapters.

one to plug into the school's port, and one to plug into the router ... which means you'll forfeit wireless on one computer.

here's your howto: [https://help.ubuntu.com/community/InternetConnectionSharing?](https://help.ubuntu.com/community/InternetConnectionSharing?)
text way is best (no overhead) firestarter is easiest (gui config)

---

