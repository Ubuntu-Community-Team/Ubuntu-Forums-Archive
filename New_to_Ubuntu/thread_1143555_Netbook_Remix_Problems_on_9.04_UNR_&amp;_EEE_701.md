---
title: "Netbook Remix Problems on 9.04 UNR &amp; EEE 701"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by kneedalz on 2009-04-30
Hello, I have just installed 9.04 UNR on my Asus EEE 710.  From the get go it was real choppy and sluggish, but only while on Netbook home page.  When in other apps, it was responsive.  Figured I didn't need Netbook so I went through Synaptic & removed it.  Now my windows don't have the bar @ the top where the minimize, maximize, & close buttons go.  Any sugggestions on how I go about getting it back? Thanks in advance!!!!

---

### Post by sede on 2009-04-30
Hi,

I don't know the netbook remix very much, but maybe I can help.
To remove the netbook remix, you have to remove more applications not just the netbook-launcher one. So:
sudo apt-get remove go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet

If you don't have the window decoration you can switch on for that session any time (although it is not permanent) with alt+F2, then type:
metacity --replace

---

### Post by bennachie on 2009-04-30
The best way to solve the 9.04 UNR problems on an eeePC 701 is to replace UNR with a fresh installation of the vanilla 9.04 Gnome version, which runs like a charm without any of the annoying delays in the launcher. 

The only caveats are that you will have to put up with one or two of the installation windows extending beyond the screen (just accept the default settings, and fix them afterwards) and remember, once you have the system running, to set desktop effects to "none" so you can use the CTRL-ALT-drag workaround on preference and other windows that extend beyond the screen.

---

### Post by Herroth on 2009-05-17
I actually had the exact same problem with my eee 900.  It would run slugish and miss a few frames whenever the netbook launch page would do an animation for an icon.  What I did to fix it is, under settings, I clicked "switch desktop mode."  I switched gnome to the classic desktop and solved the problem.
Though, since you removed the netbook style desktop, you might have a little trouble without a fresh install.
Hope this helped.

---

