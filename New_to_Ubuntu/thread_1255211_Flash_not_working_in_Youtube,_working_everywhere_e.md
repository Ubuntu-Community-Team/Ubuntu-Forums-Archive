---
title: "Flash not working in Youtube, working everywhere else"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by Dangger on 2009-09-01
So today I woke up to the fact that suddenly flash is not playing in youtube. I can see the video if it's linked somewhere else but not directly in youtube. 

This is strange and it is only happening with firefox. I have removed and reinstalled everything in firefox and firefox itself. I have upgraded flash as well. 

As you can see in my [screenshot mix]("http://imgur.com/drbQR.png"), I'm actually watching a video in one tab and in the other I get the "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player" message.

Any ideas, thanks in advance :D

---

### Post by Dangger on 2009-09-01
> **Dangger said:**
> So today I woke up to the fact that suddenly flash is not playing in youtube. I can see the video if it's linked somewhere else but not directly in youtube. 

This is strange and it is only happening with firefox. I have removed and reinstalled everything in firefox and firefox itself. I have upgraded flash as well. 

As you can see in my [screenshot mix]("http://imgur.com/drbQR.png"), I'm actually watching a video in one tab and in the other I get the "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player" message.

Any ideas, thanks in advance :D
The problem has been solved. I guess my Firefox profile was corrupted so I removed everything and reinstalled it. This hadn't worked before because I didn't erase my profile and I had Swiftfox as well so it kept the same corrupted profile.

It's working as it should :D

---

### Post by doubleplus on 2009-09-07
This worked for me, too.  Tried all the suggestions in the other thread w/r/t clearing out all the previous flash installs, reinstalling from adobe, getting sun-java, etc, but deleting the user profile ended up working.  You close Firefox and type "firefox -ProfileManager" in terminal.

---

