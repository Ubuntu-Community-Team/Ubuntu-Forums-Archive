---
title: "Slow Internet"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Hank926 on 2009-04-18
I have Ubuntu as my only OS, and just recently the internet has been running really slow, it was really fast for awhile but now it won't even load videos or anything. what could be the problem? it is a brand new dell inspiron 13 with a wireless N card using mozilla firefox.

---

### Post by Bölvaður on 2009-04-18
you probably have the same problem as I have..... a bad internet service provider.
you could try check for data loss by pinging your local google server.
try to see if you get more speed with ethernet instead of wireless
and if you can access the internet faster with live cd (which would let you see if it is ubuntu's fault... which it probably isn't)

---

### Post by ssdt on 2009-04-18
I'm having the same type of problem. Can you configure the internet just like you can configure the sound by double clicking on the icon?

---

### Post by Bölvaður on 2009-04-19
my point was that if there is a problem with internet in ubuntu you wouldnt be able to access it at all.
slow internet would be because of your isp or bad wiring in your house.

---

### Post by ulfj on 2009-04-19
I have the same problem off and on today it's on,my laptop won't connect at all but the desktop I'm working on is fine.It seems to me it's my ISP,I'm going to wait till tommorrow to see if it changes.

---

### Post by ELD on 2009-04-19
I have a lot of internet problems but that lies with only having a 2mb connection shared between 5 and we don't have a great router either.

---

### Post by Big Luke on 2009-04-19
I think I might know how to help.  I have installed different OS's multiple times and everytime I install a new one the internet (FF and IE) are slower.  So what I do in Firefox is go to the url "about:config" and search for "pipelining" with this it should only show 4 options, double click on "network.http.pipelining" and it should change from false to true.  after that double click on "network.http.pipelining.maxrequests" and increase the number(not too much because if I understand it right its like a naggy little kid asking the same question over and over until its answered, increasing it just make it work faster and if its set too high, your ISP and others will get a little frustrated with you :P ) i suggest between 35 - 65.  Someone please correct me if I am wrong, but I think this makes a very big difference and it will for you too.

good luck ;)

---

### Post by superprash2003 on 2009-04-19
few things you could try
1)use opendns servers
2)ensure that you have a decent MTU
3)disable ipv6

---

### Post by joey-elijah on 2009-04-20
> **ELD said:**
> I have a lot of internet problems but that lies with only having a 2mb connection shared between 5 and we don't have a great router either.

Wow! I struggle with 10mb between 2!

---

### Post by cycle_mycle on 2009-04-20
The suggestion by Big Luke is a great suggestion. i just did it and it sure got quicker. I set the maxrequest to 35 just to keep it down like he said and I'm a lot happier with it. 

I would take great care in doing this though - Heed the warning you get when you are directed to about:config

thanks again!:D

---

### Post by ELD on 2009-04-21
> **joey-elijah said:**
> Wow! I struggle with 10mb between 2!

Yeah tell me about it, really annoying, we are supposed to have 10mb...but it is virgin media...

---

