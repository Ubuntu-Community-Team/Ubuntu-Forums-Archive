---
title: "pandora will not play"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by cykotiktek on 2009-06-29
When i try to listen to music on pandora.com i get this error
we're sorry but unless you agree to share registration with %s, you will be unable to listen to %s

anyone know how to fix it?

---

### Post by Revolutionary101 on 2009-06-29
That's odd, did you log onto your account?

---

### Post by nhasian on 2009-06-30
Pandora is playing for me right now.  I'm also using Karmic 64bit alpha2 with firefox 3.0.11 (firefox 3.5 should be out tomorrow).  rather than using the 32bit adobe flash via nswrapper, i grabbed the 64bit alpha flash plugin directly from adobe's website.

---

### Post by cykotiktek on 2009-06-30
It won't let me even get to the sign in screen for pandora

---

### Post by Crunchy the Headcrab on 2009-06-30
> **nhasian said:**
> Pandora is playing for me right now.  I'm also using Karmic 64bit alpha2 with firefox 3.0.11 (firefox 3.5 should be out tomorrow).  rather than using the 32bit adobe flash via nswrapper, i grabbed the 64bit alpha flash plugin directly from adobe's website.

Just a quick question regarding the 64bit flash alpha:
Is unzipping it to /home/user/.mozilla the proper way to uh...install it?

Also how does one go about uninstalling it when an official version hits? Just delete the file in .mozilla?

---

### Post by nhasian on 2009-06-30
actually you want to copy the libflashplayer.so file to /usr/lib/mozilla/plugins/

when you want to uninstall it, simply delete /usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by Crunchy the Headcrab on 2009-06-30
Oh.  I was told on another page that you just install it in the user/.mozilla/plugins.  It seems to be working for me.

---

### Post by nhasian on 2009-07-01
yeah that works too, but then it will only be installed for that particular user.  if you want it to be installed for all users, then you put it in /usr/lib/mozilla/plugins/

> **Crunchy the Headcrab said:**
> Oh.  I was told on another page that you just install it in the user/.mozilla/plugins.  It seems to be working for me.

---

### Post by ghostofmybrain on 2009-08-26
> **cykotiktek said:**
> When i try to listen to music on pandora.com i get this error
we're sorry but unless you agree to share registration with %s, you will be unable to listen to %s

anyone know how to fix it?
I'm getting this error, too.  I have tried the fixes for the other pandora problems that people have been posting, but these don't seem to work.  But, then again, I could be doing it all wrong anyway. Has anybody found a way to fix this particular problem?

EDIT:  I posted prematurely.  I was in the middle of trying [this solution](http://impnerd.com/ubuntu-is-firefox-crashing-with-flash), and once I finished it, it worked.

---

