---
title: "Facebook not sharing facebook cookies with Java applet?"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by DrSpirograph on 2007-07-22
Hi,
I've just upgraded to Fiesty,and I'm finding I can't upload photos to [www.facebook.com](www.facebook.com) using the Java applet.

In Firefox at first I was getting "unable to update files in cache" when the Java applet first loaded. After searching google it seemed this problem was due to facebook being incompatible with the caching in Java 6. So I downgraded to Java 5, but although the error no longer shows when the applet loads, it doesn't upload photos.
After uploading the photos to the server, the applet says "Upload failed."

If I use tcpflow to watch what the server returns, I notice it sends back a 302 redirect to the facebook login page - I've already logged in, and browsing other pages with Firefox continues to work - could it be that firefox is not passing the cookie onto the Java applet?

This wasn't a problem when I was Edgy.

I've also tried using Konqueror to upload the photos, but in that case the applet doesn't even load.

Any ideas?

I've got a lot of photos I want to upload, so using their manual upload option (5 at a time using plain old HTML file upload forms) is very unattractive.

Cheers,
Chris

---

### Post by PhinnFort on 2007-07-23
To get the applet to load in Konqueror, go to the Tools menu, choose Change identification, Other, Safari (I use 2.0, but the other ones might work as well), and reload.
DISCLAIMER: I have a norwegian locale, so it might not be exactly right.

It Worked For Me (tm)

-PhinnFort

---

### Post by DrSpirograph on 2007-07-24
Well, now the applet loads in Konqueror, but it hangs a lot, not permanently,  but just enough to be annoying, like when I click on a new directory to browse it'll pause for 30 seconds, or when I click on upload photos.
Any ideas how to deal with that?
Getting it working in Firefox would be nice too.

---

### Post by PhinnFort on 2007-07-24
I have no idea how to deal with the lagginess, it worked fine here though.
Which Java version are you using? I'm using the "official" sun version.

Output from "java -version":
> java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)

Also, I don't really like Firefox, so sorry about that too;)

-PhinnFort

---

