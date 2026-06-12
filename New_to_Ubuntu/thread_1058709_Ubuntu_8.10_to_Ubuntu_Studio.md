---
title: "Ubuntu 8.10 to Ubuntu Studio"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by AkiraBergman on 2009-02-03
I have Ubuntu 8.10 and can not start Rosegarden properly. It complains about the kernel and suggests Ubuntu Studio. I tried to choose 8.10-rt from the boot menu but would not load and hangs. I have no other sound or video problems. 

Can the rt option in the boot menu be fixed? Would that help Rosegarden?

Would you recommend the installation of Studio? Would it install over 8.10 with no problems? Can I use the packages in Synaptic or should I use the DVD image downloadable from the web?

---

### Post by ajcham on 2009-02-03
In the past I have experimented with Ubuntu Studio.  I decided to install the ubuntu-studio-desktop package and all of the application packages.  These were installed on top of my standard Ubuntu system.

In my experience this caused a small, but noticeable, increase in resource use, and doubled my boot time from 45 seconds to a minute and a half.  Ultimately it was not worthwhile for me to keep it and I've since performed a clean install of Intrepid.

For you, things may not be so bad - I assume you would only require the audio packages, and not the video and graphics ones, so you wouldn't take quite the performance hit I did.  Whether or not using the Ubuntu Studio DVD results in a leaner system, I cannot say as I've not tested this option.

---

### Post by vandorjw on 2009-02-06
I also want to play around with Rosegarden

I have installed it, along with JACK and Qsynth.
I start JACK, then I start Qsynth and then Rosegarden

I have gotten rid of many warning messages, telling me that I am missing files, and now I am finally down to my last one.

This is what Rosegarden tells me.

> 
System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
You may be able to solve this problem by loading the RTC timer kernel module. To do this, try running sudo modprobe snd-rtctimer in a terminal window and then restarting Rosegarden.
Alternatively, check whether your Linux distributor provides a multimedia-optimized kernel. See [http://rosegarden.wiki.sourceforge.net/Low+latency+kernels](http://rosegarden.wiki.sourceforge.net/Low+latency+kernels) for notes about this.


Is this command safe?
 sudo modprobe snd-rtctimer

What does it do?

Thanks for the explanation in advance.

PS: uname -r returns the following.
2.6.27-11-generic

---

