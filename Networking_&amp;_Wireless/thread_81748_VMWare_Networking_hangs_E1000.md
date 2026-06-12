---
title: "VMWare Networking hangs E1000"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by lorenco on 2005-10-25
I am having difficulty in getting VMWare to configure on Breezy,  the vmware-config.pl runs through but fails to start vmnet0 (Bridged Networking)

In running vmware-config.pl again it freezes the session.  The Ethernet adaptor also then fails.  Shutdown then hangs trying to shutdown the network ...:mad: 

I then have to "hard reset" *OUCH*:( 

Running VMware fine on older kernel on Hoary...

Hardware : T41 IBM Thinkpad, E1000 , Athereos WiFi. VMWare 
VMWare : 5.0.0 Bld: 13124

---

### Post by Murena on 2005-10-25
I'm having the same problem, but with completely different hardware. I'll post tomorrow the details.

---

### Post by lorenco on 2005-10-25
:D Got it Working! 
See : [ VMware Forum]("http://www.vmware.com/community/message.jspa?messageID=291692")

Update VMWare using the latest [patch]("http://platan.vc.cvut.cz/ftp/pub/vmware/vmware-any-any-update94.tar.gz")

I used 94. Just make sure you have gcc AND g++ installed (gcc does not compile this patch... :rolleyes: 

Have Fun!

---

