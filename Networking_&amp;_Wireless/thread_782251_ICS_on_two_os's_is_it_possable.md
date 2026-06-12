---
title: "ICS on two os's is it possable"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by tazmannusa on 2008-05-04
Hello All
  I am running Vista ultimate 32bit as my home server, ICS setup for the sierra 875 wireless card and its shared through hard wired network + have wireless access point hooked to hub Its all setup DHCP from Vista and it works slick. I allso Have Kubuntu 8.04 i386 with Ubuntu desktop added installed on second drive. What I would like to do if possable is have Kubuntu-Ubuntu do the same when I boot into it. Would this work or would it be to conflicting for the other PC's on the network? If it would work whats the simplist way to go about setting it up?
  The sierra 875 card is in a PCMCIA to PCI adapter and in Kppp its dev/ttyUSB0 , works as dial up modem.
 Thanks for any input on the subject
  Tom

---

### Post by superprash2003 on 2008-05-04
ICS on ubuntu [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by tazmannusa on 2008-05-06
Thankyou for the links
  I have been trying your instructions but ran into a snag, when I try to start the dhcp server I get an error in dhcpd.conf line 1; semicolon expected. The ddns-updates-style
 Any Idea where the semicolon is supposed to be?
 I am using the root shell in kubuntu
 Tom

---

### Post by superprash2003 on 2008-05-06
that line has to end with a semi colon 
ddns-update-style ad-hoc;

it could be that you have missed a colon , make sure the contents of the dhcpd.conf file is similar to that in the tutorial

---

### Post by tazmannusa on 2008-05-07
Ok figured out what I did, there was no # in the begening of line one, put it in and then she worked. the dhcp server started and worked, checked from other pc's. Then went through the rest of the steps to share intranet and no luck there, might be because of using ppp0 instead of eth0 or eth1 as the intranet connection.
 I will keep playing with it when I get time 
 Thanks
 Tom

---

### Post by tazmannusa on 2008-05-09
DHCP and ICS are working good now. I ended up reinstalling system and starting over, Used Superprsh2003 instructions for the DHCP server then use firestarter to share internet, works aweet even assigned ip for wireless access point.
 Now for the big question If I wanted to share printer and files from kubuntu 
can I use the samba server and the DHCP server at the same time? I havnt installed samba yet wasnt sure if I would have a conflict between the two.
 Thanks for any help
 Tom

---

