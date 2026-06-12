---
title: "Juniper and Java not working"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by tonyb_uk on 2008-04-23
I upgraded from 6.06 to 7.10 versions of Ubuntu about 2 months ago. On 6.06, I had no problems using Juniper and was able to connect to my work. Since the upgrade, when I attempt to connect I receive the folowing

[COLOR="Red"][COLOR="Red"]Juniper Networks

You are using the secure gateway Java Session Manager, which requires that your browser supports

* Scripting of Java applets
*Microsoft Java 5.0.0.3802 (or above) or Sun Java 2 Runtime Environment 1.4.2 (or above)[/COLOR]

You currently have the following Java Installed on you system: N/A[/COLOR]

Other site that use Java I have no problems with.

I have attempted to follow other threads but no joy.

I have JRE 1.6.0_03 installed

---

### Post by Joseph R on 2008-04-29
I may be having similar problems with connecting, on 8.04, to my corporate citrix. We are using the secure gateway to proxy our ica portal. I have chosen to just use the java client but when it tries to initalize the java applet it fails.

Havent done a ton of digging yet, but its not to happy right now.

Anyone else having any similar problems?

---

### Post by tonyb_uk on 2008-06-06
Just updated to 8.04, and tried to connect. Low nad behold the Firfox browser shipped with 8.04 found the JAVA plug ins, and away we went!

---

