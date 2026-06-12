---
title: "Not able to connect to t'internet"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by ShaqArif on 2007-05-26
Hi,

I seem to be having a problem with my PC not being able to connect to the internet, despite things like thunderbird and Frostwire being able to connect and retrieve/transmit data fine.

I have tried various browsers: Firefox, Swiftfox, Opera, Ekiga...

I think this problem occured when I recently installed dansguardian.  I have since removed it, but since then, the browser always gives me an 'unable to connect to remote server' error. I have Firefox configured 'Direct connection to the Internet'

I am currently Ubuntu Fiesty Fawn and am connecting to the Internet using a SKY Broadband router, using an ethernet cable.  If anyone can help and would require any further info then please let me know...

Thanks,

Shaq

---

### Post by hasimir44 on 2007-05-26
i'm not familiar with dan's guardian (but it sounds like it works too good :)

a couple of things that I would try.. 

install wget (grabs web pages from command line)

```
sudo apt-get install wget
```

then try to grab a page.. 

```
wget www.google.com
```

I'm guessing that it won't work, but the error should give you some more info.. 

you can dump iptables rules to a file like this (again - not sure if dan's uses them..)

```
sudo iptables-save > firewall
```

then read the file

```
cat firewall
```

these suggestions won't change or fix anything, but they hopefully will lead you in the right direction..

---

