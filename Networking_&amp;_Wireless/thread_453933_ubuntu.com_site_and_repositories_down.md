---
title: "ubuntu.com site and repositories down?"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by bmeyer on 2007-05-24
Hello all.  I installed Feisty last night.  After deleting network-manager and working with /etc/network/interfaces to get my nt61 wireless up and running, internet seemed to be working fine.  I'm using it now ;)

However, ubuntu.com appears to be down when I try an access it through Firefox.  Also, I am not able to access any of the ubuntu.com repositories.  Is there any reason I am not able to access anything on the ubuntu.com domain?  All other areas of internet/networking are working perfectly.  Any ideas?

---

### Post by bmeyer on 2007-05-25
Just an update...Obviously everything in the ubuntu.com domain is not down, as I can get to it on other computers.  Any ideas why my Ubuntu box has no problem getting to everything on the internet, but not the ubuntu.com website or ubuntu.com repositories?

---

### Post by dptxp on 2007-05-25
Go to add/remove. Click on preferences at bottom left. In place of default server, choose best server, ubuntu will do it for you. SELECT it.

My default server did not work too.

---

### Post by bmeyer on 2007-05-25
> **dptxp said:**
> Go to add/remove. Click on preferences at bottom left. In place of default server, choose best server, ubuntu will do it for you. SELECT it.

My default server did not work too.

Thanks, I'll try that.  apt-get also wouldn't work since the only repositories setup are ubuntu.com ones.  Will that add/remove server fix that issue as well?  What would be causing me problems getting to [www.ubuntu.com](www.ubuntu.com) from Firefox, but no issues with any other site?

---

### Post by dptxp on 2007-05-25
> **bmeyer said:**
> Thanks, I'll try that.  apt-get also wouldn't work since the only repositories setup are ubuntu.com ones.  Will that add/remove server fix that issue as well?  What would be causing me problems getting to [www.ubuntu.com](www.ubuntu.com) from Firefox, but no issues with any other site?

First please see if you can access the repositories.

Maybe your internet service provider has a temporary problem with some sites. Can not say.
No clue right now.

---

### Post by bmeyer on 2007-05-25
> **dptxp said:**
> First please see if you can access the repositories.

Maybe your internet service provider has a temporary problem with some sites. Can not say.
No clue right now.

Thank you!  That worked wonderfully for packages.  However, I'm still not able to get to any websites under the ubuntu.com domain.  ubuntuforums.org works though.  And all other websites are working.  Has anyone else experienced this?

---

### Post by bmeyer on 2007-05-25
Update: For whatever reason, I configured our router to use openDNS DNS servers, and suddenly the ubuntu website works.  No idea what the hell was going on.

Thanks for the help with the repositories!

---

