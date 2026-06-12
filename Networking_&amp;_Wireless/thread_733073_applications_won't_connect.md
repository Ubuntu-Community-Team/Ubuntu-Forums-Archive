---
title: "applications won't connect"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by hellomoto on 2008-03-23
It apears I am having a problems with applications connecting to the internet. 

Problem #1: Evolution mail wont send/recieve emails.
- as far as i am aware all settings are correct, im quite familiar with M$ outlook so i am fairly sure all the settings are corect.

Problem #2: Pidgin won't connect to any protcols at all. 
 - days spent playing with the settings with no sucsess.

Problem #3 synaptic package manager is unable to connect to download updates or applications.
-looked and tryed all the settings here.

It would be very suprising if all these had poor setting configerations which brings me to the conclusion that my problem is network based.

Strangley: 
Firefox is working with no problems 100% of the time. However to get firefox to connect I had to disable IPv6 because it would keep timing out.

-- could my applications be having problems with a similar time out problem?

My connection:
D-link DSLG624T router (which hands out IP addresses)

I connect on a laptop using a netgear WG511v2 wifi card using ndiswrapper.

Hope someone can help as im stumped now! I have a connection which only one application connects to! :(

---

### Post by prshah on 2008-03-23
> **hellomoto said:**
> 
Strangley: 
Firefox is working with no problems 100% of the time. However to get firefox to connect I had to disable IPv6 because it would keep timing out.


You can disable ipv6 across the system by adding it to the modules blacklist:```
sudo echo blacklist ipv6 >> /etc/modprobe.d/blacklist
```

Or you can open up the /etc/modprobe.d/blacklist in gedit/kate/mousepad/pico/vi and add the line "blacklist ipv6"

---

