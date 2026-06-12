---
title: "Need Bluefish 1.0.7 help... Please"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by sillyboy on 2011-07-09
When using Bluefish 1.0.7 , I can't get my html page to open in my browser (Firefox). I click on the button and nothing happens.  I have looked for tutorials...covers everything but what I need.  I have used a variety of editors in windows XP, and had no problems.

Anyone know what I should do?   :(

Thanks

---

### Post by lisati on 2011-07-09
I haven't used Bluefish, but notice that there's a newer version available at [http://bluefish.openoffice.nl/download.html](http://bluefish.openoffice.nl/download.html)

---

### Post by andrew.46 on 2011-07-10
> **sillyboy said:**
> When using Bluefish 1.0.7 , I can't get my html page to open in my browser (Firefox). I click on the button and nothing happens.  

I suspect you need to adjust the syntax that calls Firefox as well as its position in the list of external browsers. The new default Firefox line is:

```
firefox -remote 'openURL(%p)' || firefox '%p'&
```

and I attach a screenshot showing the details.

---

