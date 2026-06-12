---
title: "Ieee80211/0 is chrewing up clock cycles"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by disabled_20220313 on 2008-03-06
Evening,

I was hoping for some help.

My computer has begun to stutter since installing Gutsy, and I think it is the "Ieee80211/0" program that is doing it.

According to "top" it is consuming about 14% of the CPU continually! 

I'm guessing it has something to do with networking, specifically wireless applications. My computer does have a wireless card, which has been detected but it is unsupported. I still use the wired ethernet connection though. I don't know if Ieee80211/0 is needed for both.

As networking is controlled by network manager. I have forced NM to ignore it by putting in manual "dummy" settings into the wireless configuration box. 

Is there a way I can kill "Ieee80211/0"? Seeing as I don't need wireless. Or is it crucial to networking? I cannot kill it using ```
sudo kill PID
``` it just keeps going.

Thanks,

Ciarán

---

