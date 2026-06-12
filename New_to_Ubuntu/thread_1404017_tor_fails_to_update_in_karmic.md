---
title: "tor fails to update in karmic"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Enuffalready on 2010-02-10
I have tried to install Tor for 9.10 using the community documentation at. 

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

and by visiting [https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian)

as reccomended by the community Doc.  However after copying both sets of commands into "software sources" to update the tor repositories this as consistantly failed to do so although new packages appear to be available. 

Realy new to Ubuntu so greatly appreciate any help, Cheers E.

---

### Post by Temposs on 2010-02-11
OK, so, can you run this command for me and paste the output here:

```
sudo apt-get install tor tor-geoipdb
```

---

### Post by Enuffalready on 2010-02-15
Hi sorry for the delay in getting back, ive been away for awhile, did as you suggested and got this response

Reading state information... Done
tor is already the newest version.
tor-geoipdb is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nice@nice-laptop:~$ 

so it would seem that either there is no need to apply the changes to the software sources as suggested in both the community page and the tor page as previously mentioned or the this is not in fact the latest version.   Furthermore the addition of those new addresses for tor to software sources as prevented me from being able to update any of the latest synaptic packages/software, which i fixed by un-checking the new address boxs.  

this seems to me be something that is unlikely to happen without a greater response from the community, therefore it seem that i have fundamentally miss-understood part of the process.

further to this Tor does still not appear to be installed? greatly appreciate any further help on this E,

---

