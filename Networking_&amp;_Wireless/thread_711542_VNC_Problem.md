---
title: "VNC Problem"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by Pvpede on 2008-02-29
Hello!

I have this problem with the **Terminal Server Client** with VNC.

The graphix SUCKS very hard.


Look:
[[img]http://pvpede.be/imuu/images/238380testingVNC.png[/img]](http://pvpede.be)


Anyone knows how to get better quality?

---

### Post by Mr. C. on 2008-02-29
What speed do you have the connection set to ?  I'm guessing you left it at auto, and VNC is choosing a low resolution mode.  You can force a higher resolution, but your speed may be compromised

---

### Post by HermanAB on 2008-02-29
Uhmmm, you are using VNC to connect to Windows???

WinXP has RDP built in. Simply enable remote desktop and connect to it using rdesktop from Linux:
$ rdesktop -g 90% windowsipaddress

Cheers,

Herman

---

### Post by Mr. C. on 2008-02-29
Having the desktop blanked and logging the user out is not very useful for many.  RDP is fine, but this is a very limiting *feature*.

---

### Post by HermanAB on 2008-02-29
OK, yes VNC is good for co-sessions, but with XP you are still limited to having only one user logged in at any one time.  Win2003 allows 3 user sessions by default and you can have more if you buy terminal server licenses.

---

### Post by Mr. C. on 2008-02-29
Yup, an XP limitation for any remote client.  Good to know Vista has bumped that limit.  Not that I'll ever purchase / use it! :-)

---

### Post by Pvpede on 2008-03-01
Listen up, I didn't ask you to give me another kind of connection ideas (RDP), I'm using VNC and I just want to get the graphics better.

> 
What speed do you have the connection set to ? I'm guessing you left it at auto, and VNC is choosing a low resolution mode. You can force a higher resolution, but your speed may be compromised - 
How do I do this ?

---

### Post by Mr. C. on 2008-03-01
> **Pvpede said:**
> Listen up, I didn't ask you to give me another kind of connection ideas (RDP), I'm using VNC and I just want to get the graphics better.

 - 
How do I do this ?

Easy there.

When you open Terminal Server Client, there is a Display tab.  Select "Use specified color depth" and chose your bit depth, setting it as large as possible.  See if that helps.

---

### Post by Pvpede on 2008-03-01
Using this:
[[img]http://pvpede.be/imuu/images/226069TSC1.png[/img]](http://pvpede.be)

Result:
[[img]http://pvpede.be/imuu/images/588678TSC2.png[/img]](http://pvpede.be)

- didn't work :(

Is there another VNC Connector for Ubuntu? =)

---

### Post by Mr. C. on 2008-03-01
I see you are using RealVNC.  I've been using UltraVNC for a long time now, and left RealVNC behind.  I find the options and features richer. Give it a shot.

Is 1400 x 1050 a valid resolution ?
Any luck changing this?

With UltraVNC:
One thing I alway set on the server, is Remove Wallpaper for Viewers.
I do not use the Mirroring driver - it is too buggy in my environment.

---

### Post by Pvpede on 2008-03-01
Will try later, thanks for the tip.

---

### Post by Pvpede on 2008-03-02
Problem solved.  
It was some problem with my client. I just updated it to 0.150 :)

---

