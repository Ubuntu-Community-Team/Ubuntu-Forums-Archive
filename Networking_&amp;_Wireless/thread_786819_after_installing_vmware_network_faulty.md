---
title: "after installing vmware network faulty"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by spinanicky on 2008-05-08
Hi, 

My desktop is connected to a router and it is getting the right ip address from the router 192.168.1.101 however nothing can connect to the internet. I am guessing that this has something to do with my installation of vmware server... the computer i am writing from is connected to the same network and is fine... 

Could someone either help me troubleshoot it or simply reset my network settings to what they were when ubuntu was freshly installed (like 5 days agp :( )

If you need any info just tell me... and ill try and get it for you (you might want to tell me what to input in the terminal :P)

Thank you!!!
Nicky

Edit: solved by using [this]("http://www.vmware.com/support/ws55/doc/ws_net_configurations_changing_hostadapter.html")

sudo vmware-config.pl

then when it asks you whether you want networking say no... restart your computer, and it should work. If you then want to enable networking again simply use the command above but say yes and make sure you create new settings... don't use the old ones when it asks you!!

---

