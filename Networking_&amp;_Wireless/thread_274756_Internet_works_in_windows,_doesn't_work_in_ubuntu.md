---
title: "Internet works in windows, doesn't work in ubuntu"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by blackcoatman on 2006-10-10
Hello all

I have an ADSL internet connection running through a D-Link DSL-502T modem/router, connected through ethernet. While everything works fine in Windows, in Ubuntu I cannot see any web pages (it sticks to "connecting to blah blah blah" forever, it pings sites normally) and Synaptic won't connect at all. I played with the disableIPv6 in about:config (as I read in similar posts), I changed the DNS server from 192.168.1.1 to the one that was in the modem's configuration, changed the DNS server to the ones provided by the... provider and still I get nothing. It didn't work in Xubuntu either... BUT the internet worked fine in Gentoo! ](*,) Now what is going on? :-? Any ideas?? No, I don't want to use gentoo :mrgreen: I really wish to make Linux my most usable operating system and without internet, well, capabilities are collapsing to nothingness (ok I exaggerate, but still it's more than useful!)

---

### Post by srt4play on 2006-10-10
So you can ping internet sites but can't browse to them? In firefox connection settings is it set for direct connection to internet? Can you ping your DNS server?

---

### Post by blackcoatman on 2006-10-10
I can ping my DNS server allright. I'll chech the firefox option you mention. But even if the problem was that firefox is not configured like that, shouldn't Synaptic work?

---

### Post by grendelkhan on 2006-10-10
Does /etc/resolv.conf list your DNS server?

---

### Post by mips on 2006-10-10
What firmware version are you using on the D-Link ?

---

### Post by blackcoatman on 2006-10-10
It worked! I just added the DNS adresses in th resolv.conf file... Funny, because I did that before and it didn't work, but maybe because I used a different DNS adress which was automatically fetched by the modem interface. Duh. Thank you all! *gives you cookies*

---

### Post by mips on 2006-10-10
> **blackcoatman said:**
> It worked! I just added the DNS adresses in th resolv.conf file... Funny, because I did that before and it didn't work, but maybe because I used a different DNS adress which was automatically fetched by the modem interface. Duh. Thank you all! *gives you cookies*

Not so fast. I suspect when you reboot it will no longer work. Just check.

---

### Post by blackcoatman on 2006-10-10
It still works... It wasn't the firmware, as it seems. I think i have the latest version too. Oh, and finally nvidia-xconfig worked fine with nvidia drivers without destroying the Xorg, for the first time on my pc (irrelevant, but good nevertheless)! So far so good... so what? :P

---

### Post by blackcoatman on 2006-10-10
...but on the other hand, you may be right :P After some time of usage the net stopped funcioning. I checked the DNS and it was changed back to the default. Why did this happen?

---

### Post by dannyboy79 on 2006-10-10
i believe it happens due to dhcp lease time. instead of adding it by using gedit and editing resolv.conf, what if you add it by going into system, admin, networking, and adding it to one of those tabs. if that doesn't work, just gogle soemthing about resolv.conf changes on me and i know you'll find the solution, i have read it before.

---

### Post by blackcoatman on 2006-10-10
I've done it both ways :/ I'll google around...

---

### Post by blackcoatman on 2006-10-10
I changed the Lease time of my router DHCP settings from 3600 seconds to 0 hoping this would negate things... I'll see how it goes.

---

### Post by mips on 2006-10-10
There is a fix for this if you need it

---

### Post by dannyboy79 on 2006-10-10
> **blackcoatman said:**
> I changed the Lease time of my router DHCP settings from 3600 seconds to 0 hoping this would negate things... I'll see how it goes.

the solution is here!

---

### Post by blackcoatman on 2006-10-10
I think i got it right, indeed... :) 3 hours running and all is good. Thanks again :)

---

### Post by dannyboy79 on 2006-10-10
> **blackcoatman said:**
> I think i got it right, indeed... :) 3 hours running and all is good. Thanks again :)


just so you are aware, if you stayed with your fix where you changed the lease time on your router it's still gonna mess up your file if you ever get a power outage or you unplug your router to reset itself just so you know. another solution would be to go the static ip route which is what i have for my 2 xbox's, my xubuntu laptop, my winxp desktop, and my ubuntu desktop. Static ip's are important cause i stream stuff from my xp and ubuntu box to my xbox's.

---

### Post by blackcoatman on 2006-10-10
I think my connection doesn't support static IP :/

---

### Post by jineesh on 2006-10-11
i downloaded init-tools and tried to install. but when i tried to generate modprobe.conf using the command ./generate-modprobe.conf, it takes more than 1hr and in between , proxy connection also disappear!!!! this is second time i m facing the same problem!!!! plz help me.
                        jin

---

### Post by nocturn on 2006-10-11
> **mips said:**
> There is a fix for this if you need it


I would like that Mips.  A friend of mine is stuck with a similar problem on a DLinks router (don't remember the exact model)

---

### Post by blackcoatman on 2006-10-11
Duh again, cause I just added the new DNS address in the DHCP configuration of the router (different from the independent DNS configuration tab that was there and I initially edited) and I think that's the one Linux used to connect, as it put it in the resolv list on its own. The lease time solution gave me sme problems with windows. Now it works smoothly in both OSs. But now I have to face deterioration of the xorg.conf file again :( I will never be able to install new nvidia drivers properly :P

---

### Post by mips on 2006-10-12
[http://www.ubuntuforums.org/showthread.php?t=128254](http://www.ubuntuforums.org/showthread.php?t=128254)  post#13
[http://www.ubuntuforums.org/showthread.php?t=126533](http://www.ubuntuforums.org/showthread.php?t=126533)  post#17

[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) General D-Link issues

---

