---
title: "Unable to connect , loose  wifi signal quality"
date: 2016-05-10
forum: Networking &amp; Wireless
---

### Post by phifgo on 2016-05-10
Hi all !  

I've been using Ubuntu for  10 yrs, But I've never seen such a STRANGE issue
I've brought my 4yrs old laptop to  technical service to replace the keyboard due to an accident with waters, I also ask them  to clean........... 
after that my laptop's wifi  "suddenly" loose quality of wifi signal
Places where I used to work with full signal strength  , now have only a very low signal quality and some "networks are  unable to be connected:

this is a dmesg command's output: 
authenticate with 00:23:69:ad:e1:60
[ 2181.200914] wlan0: direct probe to 00:23:69:ad:e1:60 (try 1/3)
[ 2181.403892] wlan0: direct probe to 00:23:69:ad:e1:60 (try 2/3)
[ 2181.607749] wlan0: direct probe to 00:23:69:ad:e1:60 (try 3/3)
[ 2181.811604] wlan0: authentication with 00:23:69:ad:e1:60 timed out
[ 2183.103401] wlan0: authenticate with 00:23:69:ad:e1:60
[ 2183.123220] wlan0: direct probe to 00:23:69:ad:e1:60 (try 1/3)
[ 2183.326433] wlan0: direct probe to 00:23:69:ad:e1:60 (try 2/3)
[ 2183.530233] wlan0: direct probe to 00:23:69:ad:e1:60 (try 3/3)
[ 2183.734084] wlan0: authentication with 00:23:69:ad:e1:60 timed out
[ 2185.425580] wlan0: authenticate with 00:23:69:ad:e1:60
[ 2185.445659] wlan0: direct probe to 00:23:69:ad:e1:60 (try 1/3)
[ 2185.648669] wlan0: direct probe to 00:23:69:ad:e1:60 (try 2/3)
[ 2185.852489] wlan0: direct probe to 00:23:69:ad:e1:60 (try 3/3)
[ 2186.056293] wlan0: authentication with 00:23:69:ad:e1:60 timed out
[ 2188.247498] wlan0: authenticate with 00:23:69:ad:e1:60
[ 2188.267159] wlan0: direct probe to 00:23:69:ad:e1:60 (try 1/3)
[ 2188.470448] wlan0: direct probe to 00:23:69:ad:e1:60 (try 2/3)
[ 2188.674266] wlan0: direct probe to 00:23:69:ad:e1:60 (try 3/3)
[ 2188.878131] wlan0: authentication with 00:23:69:ad:e1:60 timed out
[ 2201.233541] wlan0: authenticate with 00:23:69:ad:e1:60

any suggestions ??

---

### Post by kc1di on 2016-05-10
It sounds to me like they may have forgotten to reconnect the antenna wire to your wireless card.  I would take it back to them.

---

