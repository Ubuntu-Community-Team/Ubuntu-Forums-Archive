---
title: "openconnect through network-manager not selecting right group"
date: 2014-03-18
forum: Networking &amp; Wireless
---

### Post by dfr3sh1 on 2014-03-18
Greetings,

Having an issue with openconnect when connecting to a cisco asa anyconnect setup.  Everything works fine except that when prompted I'm given a drop down list and a choice between two groups.  I select the appropriate group (technically I'm in both but I want a specific group as it has a specific external nat ip address)  however when I select it in the listing and sign in, it signs me into the other group and not the one I selected.  I've confirm this on the asa as it shows me connected to the other group.  I'm not sure if this is a known issue or not.  It has worked before but its pretty hit and miss.  most of the time I connect using the wrong group.  Is there a way instead of selecting from the drop down list to force it in the config file(s)?  

Also not sure what debug information you want me to include. I don't see reference in the logs for either group.  No errors that I can see.  It all appears pretty normal. 

Doug

---

