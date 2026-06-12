---
title: "Official Ubuntu Documentation wiki pages Inaccessible from Android"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by brucewagner on 2010-04-17
I have a Droid phone running Android Linux.

This has been bugging me for quite some time now.

I don't know the proper place to post such a "bug", but the "Official Ubuntu Documentation" wiki pages are completely inaccessible from Android browsers.

Pages such as  [https://help.ubuntu.com/](https://help.ubuntu.com/) 

Results in:   "Warning: This certificate is not from a trusted authority."

Then:  "The server failed to communicate.  Try again later."

This has happened consistently for the past 4 or 5 months.  Same whether I am on Wi-Fi or 3G connection.

Is there a proper / official channel to report such an issue?

---

### Post by brucewagner on 2010-04-18
There is a serious problem with ALL the web pages beginning [https://wiki.ubuntu.com](https://wiki.ubuntu.com) AND [https://help.ubuntu.com](https://help.ubuntu.com)

NO pages beginning with these subdomains are accessible from any Droid web browser running Android. 

After an invalid certificate warning, you get "Server failed to load".

This has not worked since November, at least. 

What can be done?

What is the proper place to report such a bug with the Ubuntu Community Documentation,  Help, and Wikis --- ALL of them.  ...?

---

### Post by Jon Monreal on 2010-04-18
You can report a bug [here]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs"). You'll need to log in to Launchpad to do so. Don't be deceived by the "ubuntu-docs" name, it applies to online documentation (including the wiki) as well.

If you wouldn't mind, please post a link to the bug report here so that people searching the forum in the future can find it.

Thanks.

---

### Post by louieb on 2010-04-18
It may be that your having problems because it is a secure site - information is sent encrypted.  Do you have the same problem with other secure sites such as your pay-pal account page?

---

### Post by Iowan on 2010-04-18
Threads merged.

---

### Post by Jon Monreal on 2010-04-18
From [this page]("http://groups.googlea.com/group/android-developers/msg/176b2ba199ba9245") it appears that Android supports HTTPS and encrypted pages (although I can't find many details). It also indicates that the problems could be server-side.

---

### Post by brucewagner on 2010-04-19
Yes, the Android browser fully supports HTTPS pages.   ...but these "Official Ubuntu Documentation" URLs do not work.  The problem appears to definitely be server side.

---

### Post by e4uforums on 2010-04-19
I did some testing myself on my Nexus One.  

Using Opera 5 beta, I was able to connect to both the help site and the wiki.

Using the latest Dolphin browser, I had the same problem you described above.

Using the built in Browser app, I had the same problem you described above.

I looked through the security settings on the phone, but I didn't see anything about certificate management or anything other setting that might be causing this.

---

### Post by brucewagner on 2010-04-19
Here is the official Bug Report I have just now filed...  Please be sure to add your comments, findings, etc. to it.  Thanks!

Bug #566728 

"Official Ubuntu Documentation wiki pages Inaccessible from Android" 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/566728](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/566728)

---

### Post by aysiu on 2010-04-19
> **e4uforums said:**
> I did some testing myself on my Nexus One.  

Using Opera 5 beta, I was able to connect to both the help site and the wiki.

Using the latest Dolphin browser, I had the same problem you described above.

Using the built in Browser app, I had the same problem you described above.

I looked through the security settings on the phone, but I didn't see anything about certificate management or anything other setting that might be causing this. That makes sense, actually, since Opera renders the pages on its servers and then sends the compressed rendered pages to your phone instead of rendering them on your phone directly.

What happens if you change the user agent on your browser? I can't remember which browsers let you do this (Steel? Dolphin?). I know xScope can change the user agent. Maybe I'll test this out myself later today.

---

### Post by e4uforums on 2010-04-19
I should have mentioned.  I did switch the user agent over to "Desktop" and I got the same error.

I did not try iPhone though out of principle.  :)

---

### Post by aysiu on 2010-04-19
Tested on xScope with Cupcake (Android 1.6). Used user agent switcher to be Android, iPhone, Desktop, and iPad. All did not work.

---

### Post by brucewagner on 2010-04-19
Oddly...  This is all somewhat reassuring...   That it's NOT just me.  :)

---

