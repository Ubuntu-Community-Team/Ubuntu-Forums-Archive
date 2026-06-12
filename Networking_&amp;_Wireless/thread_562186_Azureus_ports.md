---
title: "Azureus ports"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by Metaphor on 2007-09-28
Hi.

I've configured my router correctly as it was when i used to have Windows, but in Ubundu azureus doesn't recognise the open ports, it keeps saying "NAT error".

Does Ubundu have any kind of firewall or something like that?

any ideas?

thx in advance

---

### Post by Biggus on 2007-09-28
Yeah dude, there's an inbuilt one called 'iptables' or something like that.

You can probably do most of what you want to do with the 'Firestarter' program, which I believe to be a simple GUI for the 'iptables' program.

---

### Post by Metaphor on 2007-09-28
i don't have any of those installed so how is it possible that something is blocking my ports??

because i have a router with buit-in firewall, i don't want any other installed...

i can't understand the problem...

---

### Post by Seisen on 2007-09-28
Do you have the same ip for Ubuntu that you had for Windows?

---

### Post by Metaphor on 2007-09-28
I don't know that...in Windows the IP was automatically configured, i never worried about that... :/

In Ubuntu isn't the same way?

---

### Post by nickpaton on 2007-10-01
iptables is installed by default and you will need to open ports within it to allow torrents to down and upload load properly.

The easiest way to set it up is to use GUI Firestarter, which you can install via Synaptic.

Once installed, open Firestarter via System >Administration.

To open the ports (port forward for torrent downloading):

Policy Tab > Click within  "Allow Service | Port | For" box. 

Click on now highlighted "+Add Rule" icon.

In Add New Inbound Rule box complete the following:

Name: leave blank

Port:  Whatever port you have configured within the router to open (port forward), eg 65000.  
If you specified a range of ports (eg 65000 to 65010), type 65000-65010.

Select "When source is anyone".

Click "Add" button.

Finally in main window click "Apply Policy".

Moving to Azureus, check you have the same port specified, as in Firestarter above:

Azureus > Tools > Options > Connections > 

Both "Incoming TCP...." and "....UDP Port" boxes: insert the port (or first number of the port range) number you specified above in Firestarter (and for the router), eg 65000.

Click "Save" button, and restart Azureus by closing and restarting again.

---

### Post by Metaphor on 2007-10-01
Thx a lot!

I'll try that and then i'll tell you if it worked!

---

