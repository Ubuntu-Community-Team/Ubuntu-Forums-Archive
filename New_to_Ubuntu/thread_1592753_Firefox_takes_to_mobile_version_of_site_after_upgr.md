---
title: "Firefox takes to mobile version of site after upgrading to Maverick"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by mmasroorali on 2010-10-10
This is the weirdest problem I have ever seen.

After I upgraded to Maverick, Firefox is taking me to the mobile version of a site rather than taking me to the regular site.

This started happening when I upgraded my office machine to 10.10 beta about two weeks back. I did not find a clue and thought that things will be alright ones the stable version is released. Now, yesterday I upgraded my home machine to the stable version and the same thing started to happen. 

The site is [http://www.somewhereinblog.net/](http://www.somewhereinblog.net/), but FF takes me to [http://m.somewhereinblog.net/](http://m.somewhereinblog.net/). (Do not worry about the fonts, they are Bangla characters.)

Opera and Chrome works fine by the way.

Thanks in advance for your help.

---

### Post by t.h.w. on 2011-12-04
Hi!
Same problem here.... Very annoying and makes it impossible to visit the right site...
(Ubuntu 11.04, Firefox 8 )

Anyone a suggestion?

---

### Post by jawilljr on 2011-12-05
I was having the same problem. The problem sites for me were [Denny's](http://www.dennys.com) and [BigCharts](http://bigcharts.marketwatch.com)

My fix/workaround is below:

1. Typue "about:config" in the address bar and hit enter.

2. in the filter line put "user"

3. look for the name "general.useragent.compatMode.firefox" and double click on it ot make it "True"

Restart firefox and it should work.

Jerry

---

