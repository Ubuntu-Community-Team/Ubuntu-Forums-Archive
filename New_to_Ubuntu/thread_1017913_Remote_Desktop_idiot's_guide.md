---
title: "Remote Desktop idiot's guide?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by dndrich on 2008-12-21
Ubuntupals:

Can somebody give me an idiot's simple guide to using remote desktop with Ibix?

Here is what I want to do.  My brother is running Ibix at home with a standard router.  I am running Ibix through virtual box on my Mac.  Occasionally he needs help with something.  We don't need a very secure connection, because we would call each other on the phone to start this destop setup.  So, how do I configure the remote desktop software (appears to be Vinagre) so that I can control his desktop without some complicated port forwarding set up?  Is there a simple way to do this?

---

### Post by jimmy the saint on 2008-12-21
You absolutely need the port forwarding setup in order to access his computer behind his router.  Otherwise the communication will hit his router and stop.

---

### Post by handydan918 on 2008-12-21
> **dndrich said:**
> Ubuntupals:

Can somebody give me an idiot's simple guide to using remote desktop with Ibix?

Here is what I want to do.  My brother is running Ibix at home with a standard router.  I am running Ibix through virtual box on my Mac.  Occasionally he needs help with something.  We don't need a very secure connection, because we would call each other on the phone to start this destop setup.  So, how do I configure the remote desktop software (appears to be Vinagre) so that I can control his desktop without some complicated port forwarding set up?  Is there a simple way to do this?

In short, no. 
There is no "simple" way to get port 22 or 5900 or what have you thru a router without port forwarding. The idea of doing this from a VM only adds possibilities for complication.

---

### Post by howefield on 2008-12-21
> **dndrich said:**
> Ubuntupals:

Can somebody give me an idiot's simple guide to using remote desktop with Ibix?

Here is what I want to do.  My brother is running Ibix at home with a standard router.  I am running Ibix through virtual box on my Mac.  Occasionally he needs help with something.  We don't need a very secure connection, because we would call each other on the phone to start this destop setup.  So, how do I configure the remote desktop software (appears to be Vinagre) so that I can control his desktop without some complicated port forwarding set up?  Is there a simple way to do this?

Might be easier to use Team Viewer which has a mac version and can be run under wine in linux. Easier because it just seems to cut through any router configuration without user intervention. You don't even need to install, just run it.

---

### Post by linuxguymarshall on 2008-12-21
Remote desktop always confused me. Use a standard VNC client/ server

---

