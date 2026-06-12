---
title: "Checking Bandwidth Usage for Verizon Mobile Broadband?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-14
I have Mobile Broadband internet through Verizon. I followed the excellent tutorial on setting up EVDO Cards, and it worked flawlessly. Not only was it faster to setup than VZAccessManager in Windows, but the internet speeds are significantly faster as well.

However, a small issue is that I need to monitor my bandwidth usage, otherwise Verizon hits me with some serious charges. I have 5GB of data use a month, and I usually end up hovering around 4.5GB usage by the time it resets. 

Is there a way I can check my data usage in Ubuntu?

---

### Post by aleks.rudzitis on 2009-04-14
If you are comforatable with the command-line, I would try bmon.

```
sudo apt-get install bmon
bmon
```


Once you've launched it, press d to view detailed statistics.

---

### Post by LowSky on 2009-04-14
Wow I just check the prices and your paying like 60 a month before taxes...  that seems expensive!
OK never mind It seems most US carriers are charging the same price for the smae plan.. talk about price fixing.

how about this, sounds like what you need
[http://usageagent.sourceforge.net/index.htm](http://usageagent.sourceforge.net/index.htm)

here is a screen shot

---

### Post by Noise... on 2009-04-14
> **LowSky said:**
> Wow I just check the prices and your paying like 60 a month before taxes...  that seems expensive!
OK never mind It seems most US carriers are charging the same price for the smae plan.. talk about price fixing.

how about this, sounds like what you need
[http://usageagent.sourceforge.net/index.htm](http://usageagent.sourceforge.net/index.htm)

here is a screen shot

I know. It's insane, but it's LITERALLY my only option. I live completely off-grid - about 15 miles from the nearest phone line. Satellite is expensive as well, and isn't nearly as reliable. It's pricey, but better than not having internet. The 5GB monthly bandwidth is what really sucks.

Thanks for the recommendations. :D

---

### Post by LowSky on 2009-04-14
Well if the FCC's plan to offer free wifi to the masses ever happens you will have free 768KB/sec sometime after 2010
[http://wistechnology.com/articles/5910/](http://wistechnology.com/articles/5910/)

---

