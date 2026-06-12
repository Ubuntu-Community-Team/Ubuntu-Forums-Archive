---
title: "Ethernet connection not closing on shutdown 10.04"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by ruger01 on 2010-07-29
Hi There,
 
Just wanted to know if someone could help with this issue i am having - I have Ubuntu 10.04 (love it) installed on a brand new HTPC that i built, the issue is when i shutdown the computer it does not shutdown the connection to the modem i.e. the network adapter is still connected and the light on the modem is on?
 
Anyone have a solution as to how i make this shutdown as per normal so it will turn of the connection to the modem?
 
Thankyou in advance,
 
Cheers,
 
Ruger01.

---

### Post by pricetech on 2010-07-29
If I understand what you're saying, it's not abnormal, but Ubuntu isn't doing it.  Modern NICs, onboard or addon, will have a certain amount of power on them at all times.  That's how services like Wake On LAN work, the NIC is listening for a Magic Packet with its MAC address.

Check your BIOS to see if you can turn off the NIC when the computer is powered down.

---

### Post by ruger01 on 2010-07-29
Will have a dig around the bios, thanks for the speedy reply pricetech appreciated.

---

### Post by ruger01 on 2010-07-30
Just did a system update and fiddled around in the bios and problem seems to have vanished.

---

### Post by ruger01 on 2010-07-30
Strike that - the problem still persists.

---

### Post by jerenept on 2010-07-30
Is this problem really that serious?

You can, of course just leave it be. It doesn't use that much power.

---

### Post by cjv8888 on 2010-07-30
All my NICs in my computers are on even when the computers are shut down.  Just turn the power off at the powerpoint if it worries you.  I do it with one of my computers.

---

### Post by ruger01 on 2010-07-30
It's not really a big deal and i always turn the home theatre system off at the mains anyway to save power. 

The issue i have is both my htpc and the Sony PS3 have ethernet cable going to them from an RJ45 double adapter from the one socket in the wall, which then runs through the walls to one port of the modem - sooooo when i turn the Sony PS3 on it won't connect to the internet/online etc as the lan controller is on at the htpc (signal scrabble etc as both signals trying to go to one port on the modem) At present i have to disconnect the cable of the htpc from the double adapter so i can play online if you get my drift is a little annoying.

Cheers Ruger01.

---

### Post by ruger01 on 2010-07-31
Found a setting on the motherboard Bios (Gigabyte GA-880GM-USB3) EURP under power management settings i disabled this and now turns off the light on the modem when shutdown.

---

### Post by pricetech on 2010-08-03
> **ruger01 said:**
> 
The issue i have is both my htpc and the Sony PS3 have ethernet cable going to them from an RJ45 double adapter from the one socket in the wall, which then runs through the walls to one port of the modem

Yeah, that's not the way it works.  It's not like a phone line that you can split.

The do make adapters that allow you to use the "other 4 wires" in the network cable.  I couldn't tell you what they cost because I just make my own when I need to double up on a network drop.

If you can terminate a network cable you can make one yourself.  If not, find someone who can and ask them to make you one for each end.  They probably won't charge much.

---

### Post by ruger01 on 2010-08-03
Thanks for that Pricetech, i have sorted the issue now as i said i changed a setting called "EURP" on my motherboard BIOS so that when the PC shuts down the light on the modem goes out, i can then turn on the PS3 and it works as per normal i.e i am not send two signals down the one set of wires as per what you are saying.
 
That is a great idea though about using the unused 4 wires with adapters each end,
 
Thanks for the reply,
 
Cheers,
 
Ruger01.

---

