---
title: "Connecting via Ethernet"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by the.dark.lord on 2010-04-30
Can someone provide me with step by step instructions for connecting two Ubuntu computers (both running karmic) with an ethernet cable?

Thanks!

---

### Post by Gone fishing on 2010-04-30
Not a step by step but:

Plugin the cable if you are not using a switch it will need to be a crossover cable.

In the network applet (top panel) right click edit.
Edit the wire connection and edit the IPv4 settings give it an address like 192.168.1.2 subnet mask 255.255.255.0.

On the other machine do the same but give an IP of say 192.168.0.3.

Using a teminal the two PCs should be able to pin each other eg ping 192.168.0.2 or ping 192.168.0.3.

Once you've got this working right click on a directory and select sharing options and then follow the instructions.

With the last bit there are various ways of sharing you could for eg ssh instead which might be better.

---

### Post by Paqman on 2010-04-30
> **Gone fishing said:**
> 
Plugin the cable if you are not using a switch it will need to be a crossover cable.


Used to be so, but modern network adapters can use a normal ethernet cable.

---

### Post by Gone fishing on 2010-04-30
I haven't met a switch for years that didn't crossover detect but I've had issues with network cards recently. Must be all the old crap I deal with!

---

### Post by the.dark.lord on 2010-04-30
> **Paqman said:**
> Used to be so, but modern network adapters can use a normal ethernet cable.

Can confirm this. :) And just setting it to 'Local-link' works.

Thanks, folks!

---

