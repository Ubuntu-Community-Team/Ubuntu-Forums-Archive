---
title: "Quick Preview of NetworkManager 0.7"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by Darrena on 2008-05-09
I slapped together a quick preview of Network Manager 0.7 at [http://www.darrenalbers.net/blog/?p=9](http://www.darrenalbers.net/blog/?p=9)

I have been playing with it the past couple of hours and it seems like the only options for connectivity that are missing are Analog Modems and Bluetooth DUN.   

A few notes:

It is not 100% stable

It requires WPA_Supplicant > 0.6 so I rebuilt the debian package for Hardy

The GSM/CDMA support works great though it does not display signal strength.  I tested with an AT&T Aircard 860

PPPOE/PPTP support for DSL seems to be in place but I do not have a DSL line to test with.

You can be connected to multiple devices at the same time but there is no routing between them yet.

Let me know if there are any questions.

Thanks!

---

### Post by jlc on 2008-05-12
Did you create new packages for Hardy or just build from src?

---

### Post by Darrena on 2008-05-12
> **jlc said:**
> Did you create new packages for Hardy or just build from src?

Michael Biebl is building the packages for SID, I rebuilt from his sources.   There are a few minor issues that need to be sorted but I can post packages for people to test once they get sorted out as long as they understand that it could likely kill their cat  ;-)

---

### Post by jlc on 2008-05-12
> **Darrena said:**
> Michael Biebl is building the packages for SID, I rebuilt from his sources.   There are a few minor issues that need to be sorted but I can post packages for people to test once they get sorted out as long as they understand that it could likely kill their cat  ;-)

I often run rawhide so my cat has many life's :)

---

### Post by Darrena on 2008-05-16
> **jlc said:**
> I often run rawhide so my cat has many life's :)

We shall see  ;-)   I posted the Howto in the Tutorials and Tips forum, the post is awaiting review by a moderator now.

Thanks!

---

### Post by lembregtse on 2008-05-18
I hope your howto gets online soon, I'm very eager to install your build! I'm currently using a build as from january so it's quite old. Although also quite stable!

So I'm very curious ;) Thanks for the work!

---

### Post by Darrena on 2008-05-18
> **lembregtse said:**
> I hope your howto gets online soon, I'm very eager to install your build! I'm currently using a build as from january so it's quite old. Although also quite stable!

So I'm very curious ;) Thanks for the work!

The post is up here:  [http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)

It took a day or so for it to be approved by the moderators.

---

