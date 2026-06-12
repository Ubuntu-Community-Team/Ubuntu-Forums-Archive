---
title: "Someone please help me solve this router mystery"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by faraz_k86 on 2008-12-02
Im just tired now.... and I give up trying to fix it.

I have a DSL 512 kbps connection. My phone line has been splitted by a adsl splitter which is the required case, and ill stop explaining stuff about the line here cause im sure all of u have DSL and know what a splitter is and what it does :)

K so I have 2 routers, one is my own and the other is the one that came with the connection, i.e the company provided it.

My router is a 108M ADSL 2+ wireless TP-LINK router model number TD-W8920G. It works excellently and has a wicked wireless range and speed.

But the problem is that when a phone call comes on the line and some one is using the phone my speeds drop from 50kbps to 0.3 kbps, like my connection just drops, and when the call is ended the speeds again shootup to 50kbps.

First i thought it was the splitter, i changed that twice. but still get the same problem.

Then i thought it must be the router that is faulty so i sent it in warranty explaining my problem and after 1 month i get it back with their remarks that the router is ok and your mentioned problem does not happen on our end.

My line is also ok.

cause when i connect the router that came with the connetion, its a simple ZTE ADSL router with only one port i get no problem even if a phone call does come.

i know a lot of you guys are tech gurus. Please help me solve this ](*,)](*,)](*,)](*,)

---

### Post by mips on 2008-12-02
> **faraz_k86 said:**
> 
But the problem is that when a phone call comes on the line and some one is using the phone my speeds drop from 50kbps to 0.3 kbps, like my connection just drops, and when the call is ended the speeds again shootup to 50kbps.

This indicates to me that the ADSL filter is not working or not correctly installed.

You mention a splitter but not a filter?

Genrally a splitter will simply split your line in two. A filter is required for the phone instrument though. 

Sometimes you get a combined splitter/filter.

[http://en.wikipedia.org/wiki/ADSL_broadband_filter](http://en.wikipedia.org/wiki/ADSL_broadband_filter)
[http://www.clari.net.au/Customers/SplittersFilters/](http://www.clari.net.au/Customers/SplittersFilters/)

---

### Post by faraz_k86 on 2008-12-02
but how ome the same splitter works with the ZTE modem that came with my connection and give no problems at all

---

### Post by pp. on 2008-12-02
Is your phone a digital or an analog one? 

If digital, one of your routers might be using the wrong channel on the line, i.e. the one being used for the voice transmission.

---

### Post by bapoumba on 2008-12-02
Moved to Networking.

---

### Post by faraz_k86 on 2008-12-02
> **pp. said:**
> Is your phone a digital or an analog one? 

If digital, one of your routers might be using the wrong channel on the line, i.e. the one being used for the voice transmission.

so how do i fix this?

---

### Post by faraz_k86 on 2008-12-02
bump

---

### Post by faraz_k86 on 2008-12-03
no one?

---

### Post by pp. on 2008-12-03
If your phone line is indeed an ISDN (digital) one, you might be able to find more information using the terms I gave you above.

Since I have never used such a line or one of the products you mentioned, I can not give you more information than that, I'm afraid.

---

### Post by mips on 2008-12-03
Post the output of the router log file here when the problem occurs.

I suspect you have faulty hardware though.

Also try updating the router firmware.

---

### Post by jonobr on 2008-12-03
Hello


I know you mentioned the separate phone line, however, just want to check that you are not on a voip line which is actually using the data.
The ZTE may be doing something to priotize voice traffic over the data?

At face value Mips is right on two counts, if you are using a regular phone line this is hardware related and not an ubuntu specific problem, also you should clarify splitter vs filter....

---

