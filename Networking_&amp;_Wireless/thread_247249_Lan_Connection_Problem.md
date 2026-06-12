---
title: "Lan Connection Problem"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by pjmcswee on 2006-08-30
My university recently cleared their database of MAC addresses.  I am running  Ubuntu on a laptop and lost connectivity (wired) once this happened.  When I use ifup eth0 it says SIOCADDRT: Network Unreachable, but binds my IP address to a private 172.203.60.3 address.  I have a DNS entry, but any attempt to ping a host says: connect: network unreachable.  I am receiving packets from the connection.  On a windows laptop it would redirect to a registration page and then once registered it would give it a real public IP address (something like  192.168.20.3).  Has anyone encountered this problem before?

---

### Post by dannyboy79 on 2006-08-30
Why don't you just note the what the url of the registration page that your windows box was taken to and enter it in a browser on your ubuntu box and then you should hopefully get an ip since it sounds like what you are saying is that once your computer reaches this "registration" page, it records the mac address after you enter some info and then allows that mac address to recieve an ip. I am totally guessing based on what you have told us. Sorry I couldn't be more help.

---

### Post by pjmcswee on 2006-08-30
I appreciate the quick reply! :) I've already tried that unfortunatley, it says cannot find the web page.  I even tried to use the IP address of the registration page, but then it says connection refused. I cannot even ping the address of the host registration page... :(

---

