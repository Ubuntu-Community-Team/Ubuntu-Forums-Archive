---
title: "avahi ??"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by Mgiacchetti on 2008-06-22
is this a problem??

Your application **cpusd** makes use of the [Apple Bonjour/libdns_sd]("http://www.apple.com/macosx/features/bonjour/") compatibility layer of [Avahi]("http://www.freedesktop.org/Software/Avahi").

Please fix your application to use the native api of avahi!

---

### Post by LeoSolaris on 2008-06-22
You do realize that the devs (the people who put Ubuntu together) do not read the forums. This place is for us, the users, to help each other.

---

### Post by sydbat on 2008-06-23
I found this same "warning" message in my logs. What does it mean? What is Avahi? Is there a "native api of avahi" in the repositories? I have not found anything, but I may not be looking in the right place...

---

### Post by lswb on 2008-06-23
Is that application possibly cupsd rather than cpusd? 

Is there a problem with the application not working as expected? To me the message seems to be simply stating that the app is using a "compatibility layer" rather than the native (linux) api. This appears to be just an information message, not an error or even a warning to worry about. Where did this message appear?

---

### Post by chubbtech on 2008-06-23
Well, on my part my HP LaserJet P1006 stopped working after an update so I looked around my logs and thought maybe that was the problem
...

...and so... after a bit of fiddling around, I "unshared" my printer and got rid of that message in my user.log...but the printer still won't work

---

