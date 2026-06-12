---
title: "Weird modem problem..."
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by Liam on 2005-10-17
I've got a hardware problem that isn't actually related to the OS.

I just bought a Diamond SupraExpress 56e external serial modem off of Ebay for dialing in to work.

No worries, right? I've yet to find anything complaining about this particular modem under *any* distro.

So I hook it up, and set up gnome-ppp. Everthything appears to detect fine, and it actually wvdial actually works the first time.

Cool.

*However*, I can't get a dial tone.

After much cursing and a call to the phone company, it turns out that the modem is picking up the line as soon as the RJ11 jack gets plugged in.

As in, it can be powered down with the AC adapter actually *unplugged*, and it'll still hold the phone line open. After a couple of minutes, it starts with the "IF YOU'D LIKE TO MAKE A CALL..." voice and the BEEPBEEPBEEPBEEPBEEP.

Anybody have any idea what gives? Should I be sending it some AT command to hang the hell up when it's not in use?

You'd think that being unplugged and sitting in a drawer overnight would clear whatever it had in memory, but no dice. It "picks up" as soon as I plug in the phone cord, power or no. 

I really don't feel like springing 90 bucks for a US Robotics modem.

Thanks.

---

### Post by m4ng0 on 2005-11-16
I had exactly the same experience with an Aztech external serial modem!
I tried to look for a solution in the AT command set manual but it was unuseful:
it behaved so because it was damaged.
The only thing that worked was to launch the connection with the RJ11 jack
unplugged and to plug it as soon as it started to dial.
For two or three months I went that way, then I decided to buy another modem 
on eBay and that time I was luckier.

---

### Post by mips on 2005-11-17
Sounds broken...

---

