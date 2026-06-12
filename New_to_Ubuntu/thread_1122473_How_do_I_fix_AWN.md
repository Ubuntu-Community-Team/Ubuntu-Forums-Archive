---
title: "How do I fix AWN?"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by mvalviar on 2009-04-11
I just given AWN another try. But it looks uglier than before. Whenever it animates new icons being inserted or icons moving because one was removed I see white slabs (slabs of the same color as the theme I'm using). Is there a way to fix this? I'm using intrepid, compiz and I have GeForce 7100 gs (cheap, I know =p).

---

### Post by Paqman on 2009-04-11
It could be a number of things, including your graphics drivers or AWN itself. What version of each are you running? Getting more up-to-date versions of both could solve your problem.

---

### Post by ibizatunes on 2009-04-11
If you have the problem i did, which is down to nvidia drivers that create white lines on your awn dock, you need to download the latest drivers from nvidia and install them, that will fix your issue
I did that a few months ago and it worked for me
The other option is install 9.04 and use gnome do dock, personally i think that the gnome do dock is better and quicker that awn!!

Up to you, what you do!! There is a bug already filed for this issue
Personally i think 9.04 is the way forward

---

### Post by Paqman on 2009-04-11
> **ibizatunes said:**
> 
Personally i think 9.04 is the way forward

9.04 is still in Beta for the next couple of weeks, so not quite newbie-ready yet. Although the 9.04 repos do contain updated versions of the nvidia drivers, you can also get them in Intrepid proposed.

**mvalviar**: If you want to try these drivers, go to System > Applications > Software sources and check the "proposed" option. Let the repos reload (they should ask you if they can). After that you should be able to see an updated driver in System Hardware Drivers, or in synaptic (search for nvidia-180). After you've got the new driver, go back and uncheck the "proposed" repo so that you don't get bugged about tons of updates that you don't want.

---

### Post by mvalviar on 2009-04-11
Sorry I forget to mention some details. I have nvidia 180.06 and AWN 0.2.6 (installed through synaptic).

---

### Post by Paqman on 2009-04-11
You might want to try updating AWN to the latest version from the developers' Private Package Archive.

Go to System > Software Sources and add this to the 3rd party repos:
```

deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu intrepid main

```

Then let it reload. You should get a notification telling you that there's an update available for AWN.

---

