---
title: "wireless using ndiswrapper on WPCI810G"
date: 2005-06-07
forum: Networking &amp; Wireless
---

### Post by aubreyisland on 2005-06-07
okay, here's the deal. i installed ubuntu on my machine yesterday. me and some friends in my apartment complex share an open unsecured wireless connection. 

i got my wpci810 card added.
ndiswrapper -l shows it's there

i have tried EVERYTHING to detect the network (with essid travbill). heck i even tried forcing the AP- nothing.

so, i don't really know what to do now. its like my card isnt doing anything linux is telling me it's doing. 

i have it configured as so:

iwconfig wlan0 essid travbill
iwconfig wlan0 channel 11

i even went as far as setting every single other thing.... such as rate, the ap, frag limit, all that stuff. but the above should work.

any clue on what is happening?
i get nothing from iwlist wlan0 scan.
i ifconfig wlan0 up and down multipl times and still nothing.
i tried wifi-radar to get anything - nothing.

just seems it might be an ndiswrapper problem.... because on the list of
working cards it said (on my card) that you had to put essid and country settings
in /etc/ndiswrapper/(driver)/14E.conf - did that and still nothing. im pretty much
a noobe so i might just be doing something stupid. i really need to get ubuntu on
the web to actually use it - so any help would... haha help.

---

### Post by Dhar on 2005-10-03
I'm facing the same problem you report here...card is detected, but no AP is ever seen through it.  Did you every resolve you problem?  Care to share some hints? :)
-g.

---

### Post by Suparious on 2008-03-16
Well I am about to find out what this is about as I just plugged in my WPCI810G.

---

