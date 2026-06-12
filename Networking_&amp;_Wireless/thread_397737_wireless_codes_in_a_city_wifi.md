---
title: "wireless codes in a city wifi"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2007-03-31
I am on a trip: in the area where I am now there's a city wifi. You buy a card with two codes and you can access there for one day, or week, etc.
The problem is that they tell you: *You start your sistem* (windows, of course), *you open Explorer, and it will appear a site where you have to login and write the password from the card you previously bought*. 
And yes, it works, with windows.
But when I go back to my Ubuntu, I open Firefox and nothing happens, so I can not login in the city wifi and must go back to windows.
When I check the essid, it appears to be non encrypted. I understand this is an open network that only gives you IP after loging with the password.

I am feeling desperate browsing from windows 
:cry:

Many thanks!

PS: I guess it is the same system many hotels are using, isn't it?

---

### Post by zvezdogled on 2007-03-31
hy. 
try connecting to this network.

First setup your essid:
sudo iwconfig eth2 essid "your ssid"

and then connect to it:
sudo dhclient3 eth2

And now open firefox and proceed registration.

Note:
you must change eth2 with address your card uses. U can chack that by writting command:
iwconfig

---

