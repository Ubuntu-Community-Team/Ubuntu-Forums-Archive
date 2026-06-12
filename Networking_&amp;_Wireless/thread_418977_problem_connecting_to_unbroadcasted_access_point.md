---
title: "problem connecting to unbroadcasted access point"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by dtrizzle on 2007-04-22
Dear all,

I have an interesting wireless networking question.  

I got my Broadcom 4306 wireless working using ndiswrapper and it seems to work fine.  I pick up SSIDs.  Here is the problem:  

The wireless network at my school does not broadcast its SSID, therefore it doesn't show up in networkmanager.  Furthermore, lots of people in the school have their computers set up wrong to broadcast the same SSID, except its from their laptops as to set up a ad-hoc network.  My network manager automatically connects to these ad-hoc networks coming from people's laptops instead of my schools unbroadcasted access points which are the same SSID.  

How can I get network manager to connect to the schools access points which is unbroadcasted instead of the ad-hoc networks which are broadcasted and have the same SSID?

In Windows, I simply uncheck the box that says connect to ad-hoc networks and it automatically finds the access point and doesn't connect to the ad-hocs.  Is there a corresponding setting in Feisty?

Thank you all in advance.

Dtrizzle

---

### Post by spd106 on 2007-04-23
I think you're going to have to hack gconf. 

First find the bssid(s) (MAC address(es)) of the AP(s) to which you want to connect. Then open gconf-editor and navigate to system -> networking -> wireless -> networks -> `essid`. There is a key for the bssids, so add the ones you want and delete the ones you don't.

I believe a gui process is being worked on for v0.7.

---

### Post by dtrizzle on 2007-04-23
Thank you for the response.  I'm a little unclear on the instructions.  In the Config Editor, I followed the path.  In the 'SSID' folder, there are three keys.

essid             'SSID'
timestamp    "1177275467"
we_cipher    "1"

I don't see a "BSSID" key anywhere.  Should I just right click and create my own key?  If so, what "type" do I choose?  (I'm guessing "string").  I have the BSSID from doing a "iwlist eth1 scan."

Thanks again for your reply.

Dtrizzle

---

### Post by spd106 on 2007-04-24
Almost, add a "List" of type "String" called "bssids". Then add the 12 digit hex MAC addresses as they appear in iwlist scan, separated by commas. You can add multiple addresses.

e.g.
bssids          [00:11:50:ab:cd:ef,]

I'm not sure if the order matters, but it probably does.

---

