---
title: "Flash is Rubbish!"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by NikoNZ on 2010-08-29
Hi there,
I can't really watch flash videos or play any games based in flash in Ubuntu, because the video is so choppy and slow.


How may others here are in the same boat?


Is the adobe plugin for Ubuntu to blame? 
In windows7 (I'm duel booting) everything is fine.


Until flash runs smoothly in Ubuntu, my PC is basically just a glorified typewriter - Please tell me there is a magic line of code that fixes everything...

---

### Post by MrWES on 2010-08-29
Try turning off visual effects and see if that doesn't improve performance.

Bill

---

### Post by NikoNZ on 2010-08-29
> **MrWES said:**
> Try turning off visual effects and see if that doesn't improve performance.

Bill

Unfortunately, Visual effects are already off.

Thanks for the quick reply though :)

---

### Post by NikoNZ on 2010-08-29
-I should clarify: some video on youtube is ok - it's more movies and so forth that are (I guess) higher quality that are buggered.

---

### Post by Vaphell on 2010-08-29
netbook = hardware underpowered for energy efficiency and portability
flash = no hardware acceleration under linux (thanks, Adobe)

without GPU help all the work has to be done by the CPU and on netbooks it's quite easy to hit the performance ceiling, especially with higher res clips.

You can try to copy video clips from /tmp folder after their download in the browser is finished (don't close the tab) and then watch it in mplayer or vlc - these players do a much better job than the horribly inefficient flash and you should get somewhat better experience.

---

### Post by NikoNZ on 2010-08-30
Aha, so the difference is under my windows partition it will stream fine because of hardware accelleration, whereas linux is only able to use CPU. That would explain it then.

I'll try the temp file VLC workaround. Thanks.

p.s. Why would Adobe do that???

---

### Post by Perfect Storm on 2010-08-30
> **NikoNZ said:**
> 

p.s. Why would Adobe do that???

Properly because Linux users ~1.5% on the Desktop market. So they don't use many resources there.
If you only use flash for youtube and alike I can recommending using html5 instead as flash is buggy and resource hungry (despite which OS you use).

---

### Post by varunendra on 2010-08-30
> **NikoNZ said:**
> I'll try the temp file VLC workaround.

You may try websites like keepvid.com or a native application like acetoneiso to download videos from youtube or similar websites. These would also give you options to download the video's quality-based variables (high quality mp4 or lower quality flv) if they exist.

However, it'd be really cool if we could ever get a natively supported flash plugin that is both better & lighter than that of adobe's.

---

### Post by jmore9 on 2010-08-30
I use flash for youtube and the like and don't have any problems with the viewing.  From a 2gig overclocked athlon xp to a P4 running at 3 gig.  I personally like flash better than html5.  Been using it for years on windows and Debian, Fedora, and Ubuntu systems. Plus you can play flash videos on windows media player. I have no luck whats so ever getting windows media player or mplayer for that matter, to play html5 videos, probably just me and my setup!

---

