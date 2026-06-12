---
title: "Package to get Broadcom wireless working (user posted it before)"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by linfan on 2008-04-09
When I tried 7.04 (I think) I remember seeing a post on here where a user posted a file which would install ndiswrapper and fwcutter (I think), I had great success with this, does anyone know what the post was called?

---

### Post by Foster Grant on 2008-04-09
Are you using 7.10? If so, have you looked at the restricted drivers manager yet?

---

### Post by linfan on 2008-04-09
I have tried that but I get the following error message:

"The software source for the package

bcm43xx-fwcutter

is not enabled"

I heard I needed to be connected to the Internet (which I am) for it to download the firmware needed, I have my Broadcom drivers on my USB stick ready to go.

---

### Post by Foster Grant on 2008-04-09
Enable the Universe and Restricted software repositories in Synaptic Package Manager (Setting menu->Repositories/"Ubuntu" tab). For best future results, enable all 4 repositories on that tab. Now try the Restricted Drivers Manager again.

Should do it.

---

### Post by linfan on 2008-04-09
Ok thanks, all done!

---

