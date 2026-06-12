---
title: "error trying to connect to internet"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by PLIACHAS PASCHALIS on 2007-02-22
after a lot of tries finally following some instructions found on these forums the two leds on my sagem modem were light green. 
then i use these commands:
modprobe pppoatm
pppd call ueagle-atm
i get 
Plugin pppoatm.so loaded.
pppd: In file /etc/ppp/peers/ueagle-atm: unrecognized option '<VP>.<VC>'

i understand that the problem is that i didn't use the correct vp.vc numbers?
i found on the net that i have to use PPPoA 8.35 for my country's provider.


i hope this will work

---

### Post by chggr on 2007-02-22
Check the file /etc/ppp/peers/ueagle-atm. It should contain the following lines exactly as they are:


# Load the PPPoA plugin with VP.VC pair used by your ISP.
# VP and VC need to be provided in decimal and not in hex as with eagle-usb!
plugin pppoatm.so 8.35


Probably you have forgotten the dot between the VP and VC values or something. These values and the above configurations work fine with me (ConnX)...

Kali tixi patriotaki ;)

---

### Post by PLIACHAS PASCHALIS on 2007-02-23
thanks for reply. but i already bought a adsl2 router and i'm in.
eixa aganakthsei!

exeis kamia idea pos douleyei ayto to edubuntu?
thanks

---

