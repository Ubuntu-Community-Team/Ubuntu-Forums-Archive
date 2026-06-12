---
title: "Conflict with Rythombox and wireless? getting ridiculous"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by dardack on 2010-02-09
I'm starting a new thread because the old one ([http://ubuntuforums.org/showthread.php?t=1395356](http://ubuntuforums.org/showthread.php?t=1395356)) I thought was a wireless issue, but now seems to be a rythombox streaming music over the network issue?

Quick explanation:
If rythombox is not playing, or playing music locally on the hard drive, no issues.

Once Rythombox starts streaming music from my server, websites won't load.  I know the internet is working however, i can ping [www.google.com/yahoo/etc](www.google.com/yahoo/etc).  I can connect/play wow, connect/talk on vent and Can even Gmail IM.

But as soon as I try to refresh a page, or go to a new  page, no webpage will load at all.  I get the error like I'm not connected to the internet anymore

I have been able to consistently produce these results, that once I start streaming music in rythombox it occurs.

Any help/idea's would be greatly appreciated, i need my web and my music.  I really don't want to copy all of my music locally.  Waste needless space.

EDIT: Added a 4min video documenting this:
[http://www.youtube.com/watch?v=YBwE2WURmF4](http://www.youtube.com/watch?v=YBwE2WURmF4)

I know it coulda been cleaner done better, but eh.

EDIT2:
As you can see, gmail as long as the page isnt' refreshed, you can do stuff in gmail.
Also, forgot to show, but this also happens in firefox, not just chrome.  IT takes a reboot to fix it.  Can't just logout back in to fix it.

---

### Post by laurielegit on 2010-02-09
It sounds like your server is streaming music over port 80. When port 80 is taken up with your music, the web browser cannot use it as a gateway to access the internet. Gmail works because it is using https, the secure web protocal, wich uses port 4473 (apox :)). This explanation also applies to pinging servers, using messanging protocals and playing online games. To solve, try changing the port your server is using to somthing that isn't used atm. Hope that helps.

---

### Post by dardack on 2010-02-09
> **laurielegit said:**
> It sounds like your server is streaming music over port 80. When port 80 is taken up with your music, the web browser cannot use it as a gateway to access the internet. Gmail works because it is using https, the secure web protocal, wich uses port 4473 (apox :)). This explanation also applies to pinging servers, using messanging protocals and playing online games. To solve, try changing the port your server is using to somthing that isn't used atm. Hope that helps.

Ok the files are hosted on a windows server.  I just use samba to map this, and point rythombox to the files.  How would i change the port?

---

### Post by dardack on 2010-02-09
I can't figure this out.  I never had issues in previous ubuntu versions.  Maybe i should try amarok.

---

### Post by dardack on 2010-02-09
Nope not amarok, it just played the songs in 1 second.  Bleh.

---

### Post by dardack on 2010-02-09
Copied all my music locally for now, just sux.

---

### Post by dardack on 2010-02-09
Could dansguardian be conflicting, cause rythombox i was listening to local music and it happened again.  Stop dansguardian and started it fixed.  But again this never every happens unless rhythombox is running.

---

### Post by dardack on 2010-02-09
Ok it's tiny proxy doing this.  If i restart tiny proxy it fixes itself.

---

### Post by dardack on 2010-02-09
OK could this be causuing it:

CONNECT   Feb 09 21:22:19 [22433]: Established connection to host "www.discogs.com" using file descriptor 8.
CONNECT   Feb 09 21:22:19 [22426]: Connect (file descriptor 7): localhost [127.0.0.1]
CONNECT   Feb 09 21:22:19 [22426]: Request (file descriptor 7): GET http://www.discogs.com/search?type=all&f=xml&q=Bride+Snakes+In+The+Playground&api_key=45be4$
INFO      Feb 09 21:22:19 [22426]: No proxy for [www.discogs.com](www.discogs.com)


It does this repeatedly.  Anyway to disable this in rhythombox?

---

### Post by dardack on 2010-02-09
Just incase anyone has this issue (looks like some of my music isn't in the discog's library), turn off Cover art in rhythombox, so far this has fixed my problem.

---

