---
title: "Networking tool/Script"
date: 2014-05-22
forum: Networking &amp; Wireless
---

### Post by elliotbeken on 2014-05-22
Hi all,

I am looking for a tool or script that i can import a bunch of IP addresses into so i can send a test ping to check if they are responding.

I work for a managed service provider so the tool is usefull. In this case i would like to use the tool to see when a remote router comes online. The tool/script can run from Ubuntu or Windows 7.

Any help would be great...

Thanks

---

### Post by jonobr on 2014-05-22
i would recommend getting a better tool then a script.
I would recommend using a tool like [nagios]("http://www.nagios.org/") or [cacti]("http://en.wikipedia.org/wiki/Cacti_%28software%29") or something like that which should be used to monitor nodes on a network

---

### Post by elliotbeken on 2014-05-23
Its only a temporary ping test.....

We have a fully licensed PRTG setup and an in house monitoring tool for customers however it takes too long per IP address to add into the system. I am looking for a script that allows me to add in multiple IP addresses and ping test too.

This is not going to be a long term thing......

---

### Post by untrustytahr on 2014-05-23
Why can't you just read in the ip addresses from a flat text file?  While you are reading in the lines execute a quiet ping with a count of one and check the exit status?

---

### Post by elliotbeken on 2014-05-23
> **untrustytahr said:**
> Why can't you just read in the ip addresses from a flat text file?  While you are reading in the lines execute a quiet ping with a count of one and check the exit status?

If you could help with the code i need this sounds perfect:P

---

### Post by jonobr on 2014-05-23
Theres tonnes of resources abnd technotes  ,
heres one way using an email notification when a host fails
[http://stackoverflow.com/questions/18378941/bash-ping-status-script](http://stackoverflow.com/questions/18378941/bash-ping-status-script)

---

### Post by untrustytahr on 2014-05-24
> **elliotbeken said:**
> If you could help with the code i need this sounds perfect:P Help? Yes, I think just about anyone here would help you, but not do it for you.  The whole thing can probably be done in 5 or 10 lines of code.  Try it and post your results and I'm sure people will chime in with suggestions and pointers.

---

