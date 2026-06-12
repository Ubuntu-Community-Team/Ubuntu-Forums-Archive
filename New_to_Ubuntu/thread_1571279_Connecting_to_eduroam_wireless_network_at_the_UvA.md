---
title: "Connecting to eduroam wireless network at the UvA"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by cantillon on 2010-09-09
I thought this might be useful for other University of Amsterdam students that use ubuntu (it might also work for other distros).

I wanted to connect to eduroam wireless network at one of the university facilities and they gave me this really complicated instruction manual, but I couldn't make it work. Then I found this [post]("http://www.annehelmond.nl/2010/01/27/connecting-to-eduroam-via-android-with-uva-credentials/") with instructions for Android, and they worked like a charm for Ubuntu, too. You just have to do this:
1. Select "eduroam" from the list of available wireless networks.
2. In the settings, enter the following:
[INDENT]EAP method: TTLS
anonymous identity: [email]anonymous@uva.nl[/email]
Phase 2 authentication: PAP
Identity: **yourlogin**@uva.nl
Password: **yourpassword**[/INDENT]

Replace the text in **bold letters** with your information.

You don't need a CA certificate, or at least I didn't use any and it still worked.

You can find more information on how to use the UvA services on your linux laptop on this blog:
[http://linuxatuva.wordpress.com/]("http://linuxatuva.wordpress.com/")

---

### Post by AutoStatic on 2010-12-15
[http://home.medewerker.uva.nl/j.jongepier/bestanden/Handleiding_NetworkManager.pdf](http://home.medewerker.uva.nl/j.jongepier/bestanden/Handleiding_NetworkManager.pdf)

Best,

Jeremy

---

