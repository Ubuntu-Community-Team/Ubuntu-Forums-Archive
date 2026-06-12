---
title: "script to re-start a dropped mplayer stream"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by anandamide on 2009-05-08
Hey folks
I've set up my netbook to act as a radio-alarm using cron; only problem is that the wifi signal in my bedroom isn't too strong and it sometimes drops the stream. I was thinking today of maybe writing a script to check if mplayer was running, and if not, initiate it. This would be my first ever script and my implementation is probably a little crazy.

Basically I thought a ps - A | grep mplayer command could be used, with the output being put into  variable that is then checked by a subsequent if-then loop. But I can't see how to pump command output into a variable, as opposed to a file.

Is this even a sane way of going about things? Is there a much simpler fix?

Thanks for any help :-)

---

### Post by andrew.46 on 2009-05-08
Hi anandamide,

I am not sure about restarting such a stream but definitely you could add a big cache to MPlayer:

```
mplayer -cache 8192 etc etc
```

and perhaps to be ultra cautious you could use the '-cache-min 100' setting. But I am afraid that I have nothing to offer about acually checking and restarting the stream :confused:.

All the best,

Andrew

**Edit:** Oops my apologies I thought you were *recording* a stream not using it as an alarm :-).

---

### Post by durand on 2009-05-08
VARIABLE=`pgrep -c mplayer`

That will return the number of mplayer programs currently running.

---

### Post by anandamide on 2009-05-09
> **durand said:**
> VARIABLE=`pgrep -c mplayer`

That will return the number of mplayer programs currently running.

Brilliant - thanks. I was (in true clueless beginner style) using

ps -A |grep mplayer > VAR

In the light of morning I now see how hopelessly daft this was :-p

Ta muchly :)

---

### Post by durand on 2009-05-09
No problem, I was like that when I was a beginner! If you need any more help, just post here.

---

