---
title: "Telnet HTTP .... !!!!!!"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by tornado89 on 2008-06-18
Hi All...
I'm Creating A Server Using C++ Sockets Programming
And I Wonder If Is It Possible To Send A Search Request
To Any Search Engines Like Google And Then DUMP The Results
Back To Me Using GET or Any Other Method ???!!

IS IT POSSIBLE THROUGH CLIENTS LIKE Telnet ??!!!

---

### Post by decoherence on 2008-06-18
Well, I don't know about C++ or that evil thing known as telnet (at least, I disavow knowledge)

But to extract stuff out of Google I would use wget to dump the search to a file, then write whatever pasring stuff I needed.

Getting started is as simple as

wget [http://www.google.ca/search?hl=en&q=how+do+I+search+google](http://www.google.ca/search?hl=en&q=how+do+I+search+google)

hope that's what you need...

---

### Post by tornado89 on 2008-06-18
Thanks decoherence,
It was not exactly what i am looking for ... but u helped..

---

### Post by decoherence on 2008-06-19
Are you trying to do the GET from within C++? Sorry, I can't help you there. It was the question about doing it through a client that threw me...

good luck with whatever it is you're doing ;)

---

