---
title: "WEP or WAP not working. SSH socks proxy instead? Adaptor is WUSB300N linksys wireless"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by sunksullen on 2007-12-11
My WEP or WAP isn't working with my wireless adaptor (linksys WUSB300N).  Has anyone had encryption work with this or similar cards?  

  I'm restricting computers by only allowing known MAC address for the local network by configuring through the router settings. 

Out of paranoia,  I also wrote a bash script that is in a constant loop which alerts me if any IP addresses log on or off the network..(It's sortof an intrusion detection program, I guess)

 I'm also routing most of my network applications  through my friends SSH server by using the socks 5 proxy option. ( ssh -d 8080 [email]user@remotenetwork.com[/email]) .  It's slow connecting through my friend though...is there anyway I could encrypt my data through a local area proxy, or an open ssl proxy or something like that?  If I installed a proxy locally would it still encrypt my data from packet sniifers?  Is it less secure to connect through an encrypted proxy on the local network, than it would be to connect to my friends network, which is 10 min away?  

My only concern is having unathorized users access the network, and be able to eat up bandwidth.  I'm also very concerned with user's being able to sniff my packets and be able to spy on me.   

Any ideas?  THANKS so much!!!!

-sunksullen

---

