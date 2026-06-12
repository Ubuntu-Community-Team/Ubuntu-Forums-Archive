---
title: "Need some help with Opera and Mplayer"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Speedwagon on 2009-05-02
I have and use Opera, and I have Mplayer installed.  But I see no videos in Opera when browsing pages.  On Opera's site, they have this:

> 
mplayerplug-in is a GTK application, designed for a Gecko browser. To compile it, take the following steps: 
Make sure you have the Gecko SDK installed.
Download the mplayerplug-in source code.
Type ./configure --enable-x [--with-gecko-sdk={path}] where {path} is the path to the Gecko SDK 
Type make 
Locate the files mplayerplug-in*.{so,xpt} and copy them to /usr/lib/opera/plugins or /usr/lib/browser-plugins or /usr/lib/netscape/plugins or /usr/lib/mozilla/plugins, depending on your distribution.
Type ln -s /usr/lib/mozilla/libxpcom.so /usr/lib
Restart Opera.
Verify that the plug-in is working by going to a test page for DivX plug-ins or by watching a trailer on Apple's movie trailer page.

But I really have no idea what they are telling me to do.

---

### Post by zvacet on 2009-05-02
In synaptic find and install mozilla-mplayer package.After that in Opera go t othe preferences>advanced>content>plugin-options and see if mplayer plugin is there.If not click on find new and after that you should see it.

---

