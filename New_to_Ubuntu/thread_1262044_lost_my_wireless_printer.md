---
title: "lost my wireless printer"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by LNDSS on 2009-09-09
Hi guys:

I have an HP printer which connected wirelessly to my Ubuntu desktop properly before.  Last week my son reset my network and now I CAN'T print from this desktop to the HP printer.  All I get is the message that 'printer...may not be connected'.  I tried the troubleshooting tool but it couldn't fix it.  Any ideas?  Your help is much appreciated as I use this for work also.  thx.


Louis

---

### Post by smokindans on 2009-09-09
This seems to be very common issue based on the number of posts.  Unfortunately, I am unable to offer any assistance because I am experiencing the same situation.  My HP printer worked before and then stopped. I reinstalled it and worked again for a few weeks and then stopped. Now no matter how many reinstalls, reboots, etc I do I can not get this perfectly functional printer to come back on-line. It works fine on my Windows computers so it is not a function of my network.  I am hoping that this thread produces some useful information to assist us both.

---

### Post by halitech on 2009-09-09
if the printer was set up using an IP address, when the system or router was reset, it may have been assigned a different IP address. Check the router and see if it has the same IP or not and then, can you ping it.

---

### Post by LNDSS on 2009-09-09
Hi Halitech,

Thanks for your tip.  I tried to ping my HP printer's IP address via the System/Administration/Network Tools  and it did return with 100 % successful packets upon sending 5 requests.  What do I do next?  Thanks again.  

Louis

---

### Post by LNDSS on 2009-09-09
hey Smokingdans, 

I just did this:


[LIST=1]
[*]find the IP Address for your printer from your WINDOWS machine
[*]then in ubuntu, go to System/Administration/Printing,
[*]click on your printer, and check the Device URI
[*]change it to be the same as 1. above
[/LIST]
and it should work for you.  It worked for me!

Thanks everybody.


Louis

---

