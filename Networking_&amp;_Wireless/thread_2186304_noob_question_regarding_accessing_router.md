---
title: "noob question regarding accessing router"
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by macakcira on 2013-11-06
[HR][/HR]OK, this is not a question directly related to Linux or Ubuntu, but since I am Ubuntu user and since I know many smart people visit this forum I will post it here.

When I was at my neighbor's house (2 persons live there, so 2 computers) I have set up a wireless connection with one person's computer and my router and typed in a wpa2-psk passphrase (so only I know the password), so that computer is connected to my network. I forgot to set it up for the second person's computer, but after few days I looked in connections and saw that the other computer was connected too. So i am wondering how did she manage to connect without knowing my password? The only plausible explanation I can think of (and I hope this is the case) is that she typed [http://192.168.1.1/](http://192.168.1.1/) and since I didn't change username/password for my router (admin/admin) she saw it there. So basically the question is can one login to the router from the computer that is not the access point, but is in the network? because if not (if they used keylogger or dictionary attack or something), than this means war!

EDIT: I don't know because my 2nd computer is broken so I can't check!

---

### Post by drmrgd on 2013-11-06
Any computer that can see your local network can access the router at that address.  If you left the default username and password, then yes it would be easy for her to access the router settings and get the password.  Likewise, if your neighbors are close enough to get your wireless signal, they could conceivably access your router settings and do what they like as well

The other possibility is that the guest network is turned on in your router settings and she can access the network that way.

---

### Post by macakcira on 2013-11-06
Alrighty, thank you very much!

---

