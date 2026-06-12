---
title: "Ubuntu nuking my router."
date: 2010-03-25
forum: New to Ubuntu
---

### Post by imperius69 on 2010-03-25
As the title says

When ever i go to my ubuntu installation, after a while my router gets nuked, forcing me to reset it.

Even if i reboot the PC and enter Ruindows, i still got no internet. Im forced to reset the router.

This only happens with ubuntu, on Ruindows works fine. And im not using any p2p application. Just normal web browsing and then internet goes down. Network manager continues to say im plugged in, but i cant access the router page or access the internet.

And this not only happens on this PC (main PC) as also happens on my very old PC. At the time i thought it was the network card, i changed it, and had the same problem, because i dont use that pc very much i dismissed the problem and put the PC aside, now i installed on my main PC and still have the problem with a totally different network card, so, 3 cards and same problem, not the card's problem. 

My router is a SMC Barriczade 54G  (smcwbr14-g2), im using cable (wired connection)
My network card is a Realtek PCIe GBE Family Controller (on-board).
I use static IP (No DHCP from the router)

Another fact, if i use ubuntu as guest OS on virtual-box, the network works fine. (Ruindows 7 as main OS)

Im linux newb. Prefer point and click, but im not afraid of the cmd line.

Can someone help me plz. :(

Thank you

Imp.L

edit: forgot to say its ubuntu 9.10

---

### Post by undecim on 2010-03-25
Interesting. Do you have the same static IP set up for Windows and Ubuntu?

---

### Post by imperius69 on 2010-03-25
> **undecim said:**
> Interesting. Do you have the same static IP set up for Windows and Ubuntu?

no, they are different addresses.

ps - just got time to enter my ubuntu, write the above reply before loosing connection :S

---

### Post by undecim on 2010-03-25
> **imperius69 said:**
> no, they are different addresses.

Can you try changing the Windows IP to Ubuntus IP? (or the other way around)

---

### Post by imperius69 on 2010-03-25
> **undecim said:**
> Can you try changing the Windows IP to Ubuntus IP? (or the other way around)

i can.

btw, this time when i rebooted to windows i had internet without rebooting the router.
And im already using the ubuntu IP on my Ruindows.

---

### Post by tgalati4 on 2010-03-25
Sounds like your router has bad firmware.  It should automatically detect the new IP on the port and change it.  If it doesn't, then it's either a bug in the firmware or possibly the firmware got corrupted.  Try updating the firmware from the manufacturer's website.

---

### Post by undecim on 2010-03-25
> **tgalati4 said:**
> Sounds like your router has bad firmware.  It should automatically detect the new IP on the port and change it.  If it doesn't, then it's either a bug in the firmware or possibly the firmware got corrupted.  Try updating the firmware from the manufacturer's website.

My thoughts exactly.

And if that doesn't fix it, just stick with the same IP address between the two OSs.

---

### Post by imperius69 on 2010-03-25
ok i will try that later and tel here the result.

thanks all for your reply's.

:popcorn:

---

### Post by imperius69 on 2010-03-25
upadted my router firmware

same thing.
Ubuntu nukes my router out, no matter what IP is using.
Even if i change to windows, i still have to reboot the router because i dont have connectivity.

:(

---

### Post by tgalati4 on 2010-03-25
Post the output of:

route -n

---

### Post by oldsoundguy on 2010-03-25
Really don't understand why two different IP addresses on the same physical computer.  
I don't go through the foolishness of having a dual boot .. instead I have multiple computers running different platforms working through my router .. the router IP address is the same for all .. only the LOCAL NET addys are different.

It is much more efficient as I can utilize a KVM switch and move from one working computer to another without having to re-boot.  Hence I can and do run multiple operations on multiple computers .. and all are on line at the same time.

---

### Post by Calash on 2010-03-25
Does anything show up in the Router security log?  It should be in the status area of the left menu, according to the Manual.

I am wondering if the built-in firewall is triggering on some of the Ubuntu traffic.  If it is there should be something noted in the log area.

---

### Post by imperius69 on 2010-03-25
> **tgalati4 said:**
> Post the output of:

route -n

I'll do this as soon i reboot again.

> **oldsoundguy said:**
> Really don't understand why two different IP addresses on the same physical computer.

The 2 different IP's was just for testing, i would have used the same IP if all was working.
I also don't understand because this happens to me in 2 different boxes, old and new, so for me is a ubuntu problem somewhere, since in the old boxe the ubuntu also nukes the router out, and i cant figure out why :(

Also to note is if i connect directly to the internet modem, all works fine in both PC's.


> **Calash said:**
> Does anything show up in the Router security log?  It should be in the status area of the left menu, according to the Manual.

I am wondering if the built-in firewall is triggering on some of the Ubuntu traffic.  If it is there should be something noted in the log area.


Sorry mate, cant give you this simply because, my firewall is off :p

---

### Post by imperius69 on 2010-03-25
> **tgalati4 said:**
> Post the output of:

route -n

here it is

> 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0




---

### Post by The Cog on 2010-03-25
I wonder it it's a problem with the ARP tables in the router. Using different IP addresses from the same adapter is a bad idea. Try cofiguring both OSs to use the same IP address and see how that goes.

---

### Post by imperius69 on 2010-03-25
> **The Cog said:**
> I wonder it it's a problem with the ARP tables in the router. Using different IP addresses from the same adapter is a bad idea. Try configuring both OSs to use the same IP address and see how that goes.

ill do that, right now actually they both using different IP's and funny thing, has passed almost 2 hours and i have not lost the connection!!

I really don't get this ....

Anyway, gtg for now, ill see how it goes tomorrow.

---

### Post by tgalati4 on 2010-03-25
Your route table looks OK.  Sometimes routers get hot and act strange.  The processor chip inside doesn't have a heat sink and depending on usage, they can overheat.  Try a small fan to blow some air on it and see how long it lasts.  How old is the router?

---

