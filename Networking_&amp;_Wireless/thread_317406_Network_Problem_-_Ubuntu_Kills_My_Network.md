---
title: "Network Problem - Ubuntu Kills My Network"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by poostick963 on 2006-12-12
I have searched high and low, and this ](*,) happened.
Basically I installed ubuntu yesterday, but i think i had this same problem like 2 years ago. I tried to use the web browser on my Ubuntu Machine and it messes up my router. I have a Mac g4 laptop and another AMD machine on the network and their internet goes out. The router must be reset, as well as my cable modem (comcast). The internet works fine on this machine when I boot up with XP. I tried resetting everything and then checking the network settings in Ubuntu as DHCP. Ubuntu settings were already DHCP. Do i need to do a manual IP and mask perhaps? Please help.

SMC Barricade SMC7004VBR Router
Windows XP SP2
Ubuntu Dapper Drake 6.06
MSI K8N NEO Platinum
AMD 64 - 3700+
Nforce 3 Chipset
eVGA Geforce 6800 Ultra
1Gb Dram
3 SATA drives
2 ATA drives
NEC DVD Burner

---

### Post by poostick963 on 2006-12-12
I had tried bypassing the router and connecting directly to the cable modem with no luck. until I turned *everything off for a few minutes, and was able to get ubuntu online with the direct connection. I am gonna try the "turn everything off" trick with the router....

---

### Post by poostick963 on 2006-12-12
ugg. just what tech support anywhere will always say! unplug EVERYTHING for a minute and then plug it back in... WORKS!! :D  hope this thread helps somebody. I wasted an afternoon searching online before i tried that ;(

---

### Post by poostick963 on 2006-12-13
okay, so the unplug trick isn't working anymore. I rebooted into xp and then back and everything went nuts again. But for like an hour it only killed my mac and ubuntu internet, my 3rd xp pc was fine for a while (my roommate playing WoW.) but I now can not get the internet to work at all on the ubuntu machine through my router. I can connect to my router thru the web browser on all machines, and the computers appear to be networked to eachother, but the internet just does not work. The WAN light on the router is lit and everything. Please help.

---

### Post by poostick963 on 2006-12-13
I have tried manual settings of 
static ip ; 192.168.2.110
mask 255.255.255.0
gateway 192.168.2.1
these are the same settings that the same machine uses when booted thru XP. still no luck ;(

---

### Post by Iowan on 2006-12-13
Dunno if I can help much, but you seem to be the only response to your thread...
I don't see why it would interfere with the other machines, but you might try disabling **ipv6**.

---

### Post by poostick963 on 2006-12-13
thanks for the reply. I think I will try that suggestion. Also I am going to try a renew/release from within the router web browser setup. I also read elsewhere that resetting the router from within the browser setup thru Ubuntu could solve this. I'm gonna try manually entering a DNS first though.

---

### Post by mooter on 2006-12-13
I get the same thing.  I have a D-link DI-524 with a usb wireless adapter.
After maybe 5-10 minutes it will kill the network; all lights on the router stay on, maybe the modem too.

At first it would stay on a lot longer, it's possible it cuts out more when my roommate is surfing the same time.

I set up a static ip that is similar to pootstick.

Gonna keep searchin the forums...

---

