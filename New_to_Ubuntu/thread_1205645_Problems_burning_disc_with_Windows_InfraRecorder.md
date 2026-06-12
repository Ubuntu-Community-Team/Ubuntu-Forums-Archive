---
title: "Problems burning disc with Windows InfraRecorder"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by MisterLambda on 2009-07-06
I actually managed to install Ubuntu on a relative's laptop. He actually requested it for it.

Now my neighbours wants a slice of the action. I tried burning a disc in InfraRecorder (my Linux PC has no burner), but sites recommend 4x instead of max, but InfraRecorder is preventing me from sleecting a low speed because it's greyed out. I noticed the advanced tab has an option to force speeds. Is this safe?

---

### Post by Mark Phelps on 2009-07-06
Don't know about InfraRecorder, per se, use Nero for burning in MS Windows, but generally, the issue is one of CPU performance and underrunning.  What this means is that the CPU gets busy and is unable to keep up with the data migration demands needed by the optical burner, so the burner doesn't get the data packet in the timeframe needed to do the burning.

Generally, any decent optical media burning app will include an option to buffer against this problem.  If it does, the speed doesn't really matter because the buffering will handle it.  If it does not include this option, the lower speed is often needed to stop the burner from asking for data packets faster than the CPU can supply them.

Would suggest that you grab a copy of ImgBurn (Image burn).  It's free and has this feature built in.

---

### Post by Sef on 2009-07-06
Get [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

---

### Post by Jerry N on 2009-07-06
I haven't used Infrarecorder but I have burned about 100 ISOs to CD with Nero in Windows at 40X and have never had a failure.  I have also burned a few in Ubuntu using NeroLinux at 40X.  

Ignore the 4x crap and go ahead and burn the CD and see how it comes out.

Jerry

---

