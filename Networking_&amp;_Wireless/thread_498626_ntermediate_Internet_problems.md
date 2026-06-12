---
title: "ntermediate Internet problems"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by jba6511 on 2007-07-11
I have been having issues with firefox and opera detailed in this thread here that no one can answer [http://ubuntuforums.org/search.php?searchid=23557958](http://ubuntuforums.org/search.php?searchid=23557958) Here is the situation: Sometimes I load up firefox or opera, get a few (like 1 to 2 second delay) and then the homepage loads and everything works fine. Sometimes I open the program and firefox can not connect to my homepage, or any other site, including google, or it takes an long time (45 -60 seconds) before connecting. Once it connects everything is fine. Other times nothing will connect and a quick restart fixes the problem. No other computer experiences this problem on my network. I have replaced the router, and am currently using opendns (Same problem occurs using the ISP's DNS - Time Warner Cable RoadRunner). I have also disabled IPv6 as well, but it has not helped. I am not running any desktop effects anymore either and Ubuntu version is fiesty with all updates. I get access through a cable modem that is conected to the router, and all computers are connected to the Ethernet ports on the router. This particular computer is using a wired connection that has the problem. Trying to ping a site during the load times does nothing. Any ideas on what can be done?

forgot to add all computers haver static ip addresses.

---

### Post by jba6511 on 2007-07-12
help please????

---

### Post by jba6511 on 2007-07-21
well I found the solution. I replaced my Ethernet card as it was an old card I was using since Ubuntu does not support the Ethernet controller on my Gigabyte 965p s3 board. I also cleared out all my cache and temporary files. Now the problem no longer occurs. Not sure which step took care of it, but I am leaning towards replacing the card.

---

