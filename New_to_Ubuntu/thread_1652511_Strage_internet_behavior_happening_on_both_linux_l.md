---
title: "Strage internet behavior happening on both linux laptop and windows desktop"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by XRaptor on 2010-12-25
Hey everyone,

So I'm having a really strange issue using the internet.  It happens on both my laptop running the newest desktop version of Ubuntu and on my desktop running Windows 7 Home Premium, fully updated.  First, I'll give you a little background info.

Just last night I formatted my laptop (which originally ran Windows 7 Home Premium) and installed the newest desktop version of Ubuntu, using a live cd.  The only other installations I did in Ubuntu once I got it up and running was a program to enable the rotating cube desktop effect.  I followed this guide to do it:

[http://www.ehow.com/how_2257535_get-rotating-cube-ubuntu.html](http://www.ehow.com/how_2257535_get-rotating-cube-ubuntu.html)

Anyway, on to my problem.  I was using firefox on Ubuntu just fine, until I navigated to google.com.  The normal google page that we're all familiar with did not load up; instead, it gave me an access denied error.  I didn't think much of it; I then went to my windows 7-running desktop to try to load google in firefox.  It also loaded that same "access denied" page!  I even tried loading it in google chrome on my desktop, but it still gave that same error page.  I talked to my brother about it, and he tried loading google on his windows 7 laptop.  It was loading google just fine.  Okay, now things are getting a little weird.

I cleared the history, cookies, cache, everything, in firefox on both my windows desktop and ubuntu laptop, and restarted both.  I reloaded firefox in both computers upon rebooting, and google loaded just fine.  But here's where it gets weirder...

After some more browsing on my ubuntu laptop, I went to google again.  This time, the page was completely white, and only displayed two words in the upper left: "It works!".  I wondered if it would happen in my windows desktop too.  What do you know, it displayed the same "It works!" page in firefox and google chrome.  I went to my brother's laptop again, and it loaded google like normal.

I cleared the history, cookies, cache, everything yet again on both computers and restarted them both again.  Upon rebooting, google was loading just fine on both computers. Until a few minutes later, I went to google again in the ubuntu laptop, and instead of loading google, it loaded the canonical Ubuntu store:

[http://shop.canonical.com/](http://shop.canonical.com/)

This happened also on my windows desktop.

At this point, I was getting a little freaked out.  I repeated the same clearing/rebooting steps as before, and this time, shut down my laptop.  I'm using my windows desktop right now, and google is loading (and has been loading) just fine.  

What on earth is happening?  I'm very nervous right now because I'm not sure if something (or someone) is messing with my network, or if it was the "cube desktop" thing I installed, or if it is a simple ubuntu issue when using my home network.  And why is this not happening to my brother's windows 7 laptop, even though he is using the same home network?  Can anyone help me understand what is happening?

Thanks for your input!

---

### Post by Gone fishing on 2010-12-25
Is there anything else? For example your in a school or university campus? How do you connect to the net?

For example I set up our school system (a proxy server) to deny access from all but certain IP ranges then you then may need to logon using usernames etc.

---

### Post by XRaptor on 2010-12-25
> **Gone fishing said:**
> Is there anything else? For example your in a school or university campus? How do you connect to the net?

For example I set up our school system (a proxy server) to deny access from all but certain IP ranges then you then may need to logon using usernames etc.

I'm not at my university right now, this is happening at my house.  Over my home network.

I connect to the net wirelessly.  I have built-in wifi in my HP laptop running Ubuntu.  On my Windows 7 desktop that I custom-built, I have a USB Wireless adapter.  Both computers are connected to my DSL modem wirelessly, and the modem has an antenna (aka a wireless gateway).

The only other strange thing that happened was after I restarted my windows desktop the third time.  At the windows login screen, the resolution changed to what looked like 1024 X 768.  It should have been 1680 X 1050 (my monitor is a 21.6" widescreen). A restarted again and the resolution went back to normal.  But this resolution change doesn't seem to be related to my internet issue.

---

### Post by theozzlives on 2010-12-25
What happens when you typr your search terms in the box in the upper right and is your brother's machine using FF or MSIE?

---

### Post by XRaptor on 2010-12-25
Thanks Gone fishing and theozzlives for your assistance, I decided to try google chromium on ubuntu and everything seems fully functional.  I'll let you know if weird stuff starts happening again.

---

### Post by Golem XIV on 2010-12-25
If this happens both in Ubuntu and Windows it's obviously not a problem of the operating systems.

I'd check carefully your wireless access point (router).  Have you reconfigured it after purchase?  These things have a factory default password and it should be the first thing one changes after installing it, otherwise it can get hacked.

These routers usually have a reset switch on the back.  Check the manual and reset it back to factory defaults, then log into it (connect to it by network cable and use the browser to access the configuration screen of the router - the information should be in the manual), change the password and then configure wireless and the rest.

If it's a router leased to you by your ISP call their tech support to have them do it for you.

---

