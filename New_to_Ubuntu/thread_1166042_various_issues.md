---
title: "various issues"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by ThePlughead on 2009-05-21
[SIZE=6][SIZE=4]hello,
I am new in ubuntu. I am actually thinking migrating to ubuntu in my main pc, right now I'm testing them in my older computer. Various issues have come up so far.
1. Wine: I am a designer using fully the Adobe Creative Suite (all of it). I installed Photoshop CS2 using wine to see how it works. When I try to open it I get an error msg:"unable to continue because of hardware and system error.Sorry but the error is unrecoverable". Any idea what's going on?? If I am about to migrate completly to linux I must make sure I can run Adobe's Creative Suite,Autodesk's Maya and sound software (reason, virtualDj, abletonLive)

2. Networking: My linux computer is connected with ethernet while my pc (vista) wireless. Any idea how I can make them communicate? (share files etc)

3. (dummy question) why the fonts in firefox for ubuntu are so tiny? 

any help appreciated[/SIZE]
[/SIZE][IMG]file:///home/steve/Desktop/Screenshot.png[/IMG][IMG]file:///home/steve/Desktop/Screenshot.png[/IMG]

---

### Post by spacesamurai on 2009-05-21
I think I can help with number #2.&#12288;How is your wireless and wired network layout? Are they two separate routers? If they are two separate routers, are they on the same network? 

As for how to share files, [samba] is the way to go to share files between Linux and Windows.


As for #3, I never had that problem. What font are you using? You can check this by [Edit] -> [Preferences] -> [Content].  By default, my browser is [serif] [16]. If this is the same, it might have to do with your screen resolution.

Good luck!

---

### Post by kpkeerthi on 2009-05-21
For the fonts issue, do you have msttcorefonts installed?

Enable Universe and Multiverse from System -> Admin -> Software Sources. Then System -> Admin -> Synaptic. Search and install **msttcorefonts**.

If you are using LCD, check your font rendering under System -> Preferences -> Appearance -> Fonts and set sub-pixel hinting to medium (or whichever works best for you).

---

