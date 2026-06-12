---
title: "sync/access iPhone Cal &amp; Contacts?"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by smcrossman on 2011-07-20
I wasn't sure which forum to go to for this.  I did search and saw a lot of older things, but it didn't look like any dealt with Natty.

I have an iPhone 3GS, which I would like to sync up my calendar to Korganizer, and my contacts into claws.  Originally using evolution I broke down and used Google Calendar which would sync into evolution.Still cleaning up minor headaches from that one, but evolution just didn't meet my needs for filtering and such.  I've been using claws for several weeks and it seems to fit pretty well....except no calendar.  So I'm looking at trying Korganizer for that.  Only until I can get my info in.

I found the iPod/iPhone sync software in synaptic, but its showing broken due to ipod-convenience. Checked Ubuntu Software, and it had the same issue. Searched on ipon-convenience....didn't find a package anywhere.  Googled and found the Ubuntu page with the downloads for Karmic Koala.

Is that package what I need for the software to install & work?Is there another program that I haven't found?

I can access app files, documents, pictures, and music/video etc in general fashion, but haven't figured out the needed calendar and contacts.

Suggestions, tips, tricks, experiences welcome & appreciated.  I'm currently limited to mobile access and tyrin gto pack for moving in about 3.5 weeks so my time to do the in depth searching is limited.

Thanks!

---

### Post by Bodsda on 2011-07-20
The ipod-convenience package only seems available on hardy. Have a look at some of the other ipod packages thogh
 
[http://packages.ubuntu.com/search?keywords=ipod&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=ipod&searchon=names&suite=all&section=all)
 
I had a quick google, but nothing really stood out in terms of being able to sync the ipod to a calander app, usually it was the other way around. 
 
Bodsda

---

### Post by smcrossman on 2011-07-20
Thanks!  I suspected the app was outdated.  I don't understand why syncing doesn't automatically go both ways, but then again....I don't program! 

I might be able to get around this issue by using my old phone I'm aobut to re-activate (a Samsung Strive) which isn't even classified as a smart-phoone.  I know Samsung has software that syncs it up with MS Outlook.. And I seem to recall it will sync with Google.  Maybe one of the other sync up applications will work with it if they don't with the iPhone.

Wow! That is an impressive search page!  I obviously don't know how to search the documentation so well.  How do you specify something like "package name" when you do a documentation search? I'm thinking I'm as blind as the vision checks keep saying I am!

---

### Post by Bodsda on 2011-07-20
> **smcrossman said:**
> Thanks! I suspected the app was outdated. I don't understand why syncing doesn't automatically go both ways, but then again....I don't program! 
 
I might be able to get around this issue by using my old phone I'm aobut to re-activate (a Samsung Strive) which isn't even classified as a smart-phoone. I know Samsung has software that syncs it up with MS Outlook.. And I seem to recall it will sync with Google. Maybe one of the other sync up applications will work with it if they don't with the iPhone.
 
Wow! That is an impressive search page! I obviously don't know how to search the documentation so well. How do you specify something like "package name" when you do a documentation search? I'm thinking I'm as blind as the vision checks keep saying I am!
 
If you want info on any package in the repo from the command line, try this
```

apt-cache show <packagename>

```
 
if the app is installed, you can run
```

man <application>

```
 
HTH,
Bodsda

---

