---
title: "Weather Indicator. Problems with forecast."
date: 2010-11-13
forum: New to Ubuntu
---

### Post by Arazu on 2010-11-13
When I click on the weather indicator in the panel then click the forecast tab it always lists the current day and then the weekly forecast starts on Tuesday. For example it currently shows "Today, Tonight, Tuesday,..." It doesn't matter which day of the week it is the next day shown is always Tuesday.

This didn't happen with 9.10. Any thoughts?

---

### Post by I'mGeorge on 2010-11-13
well I've never used forecast as I can see the weather in xbmc, but there's a saying around here, coffee it's always better on tuesdays. :-)

You should try reinstalling the application after you've removed all it's config files 

```

sudo apt-get --purge remove forecast
sudo apt-get install forecast

```  

and see how it goes

---

