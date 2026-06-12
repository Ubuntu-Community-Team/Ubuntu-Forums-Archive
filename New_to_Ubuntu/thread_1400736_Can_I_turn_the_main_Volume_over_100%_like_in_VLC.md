---
title: "Can I turn the main Volume over 100% like in VLC"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Caramin on 2010-02-07
Hy! Bought a new notebook yesterday and started Ubuntu (by chance - xp didn't provide the drivers...ubuntu worked fine / I have overnight become fan of the system, I'll kepp it). Unfortunately the notebooks speakers a kind of silent, so I asked myself if there was a way to turn the main (system-) volume over 100% like its possible with VLC-player? Didn't find a hint by googeling.  Does anyone have an idea?  THX

---

### Post by jward3010 on 2010-02-07
Actually, you may be having a problem with the PCM channel being lower than usual, at the same time you may just have quiet laptop speakers. There are a couple of volume controls in Linux that you can alter in sound preferences - Master, PCM, Headphones (sometimes has an actual effect), one simply called Volume. Often one or the other of these is turned down to about 65% and it needs to be at 100% to let the Master control work at 100%.

Right click on the volume icon and click either mixer or Preferences, you should be brought to a window with sliders make sure that Master is set to 100%. The important ones to look out for are PCM, Volume, Speaker or any at around 60 to 70%, increase them while playing music and see what happens.

---

### Post by Caramin on 2010-02-07
Ah, thanks! That one was simple!!

---

### Post by jward3010 on 2010-02-07
> **Caramin said:**
> Ah, thanks! That one was simple!!
No problemo, in 9.10 it was fixed I think, in other words the default level of the PCM / Speaker channel was left at 100% and the master was left at around 60% which makes most sense. As to why they drop the level of this spurious control I have no idea.

If you like mark this one as SOLVED by going to thread tools option at the top of this page ,helps people know the finished threads from the incomplete.

---

