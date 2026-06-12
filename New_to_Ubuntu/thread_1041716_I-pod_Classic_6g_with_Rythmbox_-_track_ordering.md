---
title: "I-pod Classic 6g with Rythmbox - track ordering"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Jon_shaw on 2009-01-16
Hello!
Just got a new system with Ubuntu 8.10. I can use Rythmbox to put music on to my i-pod but the tracks are playing alphabetically rather than in the order on the album.
Also, I imported an unknown cd and then can't seem to enter details, either in rythmbox or via the music folder.
All suggestions greatly appreciated.
Thanks for reading.
Jon

---

### Post by JoshuaRL on 2009-01-16
Make sure your ID3 tags are correct.  If I'm right, iTunes reads only the ID3 V2 info (well, when you rip them thats all it writes).  So I would suggest you install Kid3 from the repos and check the ID3 tags.  Tedious, yes.  But that's always fixed any problems like that for me.

---

### Post by Jon_shaw on 2009-01-18
Thanks, Joshua, in case you didn't get the message.
To all reading this, Joshua was dead right about the tagging.
I tried kid3, but if you are as novice as me you may find that easyTAG is a lot more intuitive, even though cleverer folk can no doubt tag more quickly using other things.
So if anyone can tell me how to get rhythmbox to tag with the track numbers when importing cds in the first place, I'll (briefly) be the happiest man alive!
Jon

---

### Post by evilkastel on 2009-01-18
Well, i do not know how to make rhytmbox do that because the ipod support in rhytmbox is very... poor. 
I'll suggest you give a try to gtkpod,or banshee (updated version, not the one in the repos) or even amarok 2.0. If the problem is general, then it might be like in my shuffle, the track order can't be alterated. or else, ¿have you tried setting the ID3 "track number" tag?

---

