---
title: "Two APs acting as one?"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by farruinn on 2007-11-14
I need two wireless access points to cover a large room (dining hall at a scout camp) but still be the on the same network segment so that an associated user could walk across the room from the coverage area of AP1 to AP2 without any glitches. How is this achievable?

There are wired connections elsewhere in the building, so this is my guess on the solution:

[FONT="Courier New"]{router}------>wired connections
 |
 v
hub----->AP1
 |
 v
AP2[/FONT]

Where AP1 and AP2 aren't routers (switch instead?) but have the same SSID. I put a hub between the router and the APs so that frames destined for stationA go to both APs and the AP can decide if it needs to be sent. If the hub were a switch then I don't think you'd be able to move seemlessly between APs because it would put stationA's MAC in its table for either AP1 or AP2 and would continue sending data to the wrong AP for a while after the station had reassociated.

Any help on this would be welcome!

---

### Post by Austin_KW on 2007-11-14
The clients will need to reassociate with the second access point so it is not quite seemless. I forget a lot of these layer 2 protocols, but a change of attachment will occur causing  an ARP update broadcast. Meaning it could be a switch rather than a hub because it will see the mac address from the new link?

---

### Post by Austin_KW on 2007-11-14
Forget to mention, use the same SSID on the APs but put them on different channels (1,6,11) so they dont interfere with each other

---

### Post by farruinn on 2007-11-15
I guess I was thinking of "seamless" from the point of view of the transport layer :) If both APs are on the same subnet and acting as switches, I'm guessing the stations would keep their IP address (since that'd be coming from the router) so it wouldn't disrupt TCP connections.

I didn't think about the ARP broadcast. As long as it's being broadcasted across both the wired and wireless interfaces then I'm sure you're right, the hub could be a switch.

Of course, is this all moot? Do laptops with "romaing" do this on their own between APs on separate SSIDs even?

---

### Post by Austin_KW on 2007-11-15
I run something similar with two wireless routers bridged together (one with dhcp switched off). So this is in effect 2 APs connected through 2 switches. I use the same SSID, same WPA keys and run one on channel 1 and the other on channel 11. Seems to work for me.

---

### Post by farruinn on 2007-11-17
Thanks for the excellent suggestion. I did a test with a couple of wireless routers I had available. I only had a 20 foot cable to bridge them, but based on the router's status pages the laptop did in fact reassociate with the second AP when it lost the first one.

---

