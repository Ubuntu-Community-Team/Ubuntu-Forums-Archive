---
title: "remove last update"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by andyubu on 2008-12-25
I am developing a very simple web site  (Apache2, mysql 5, php 5, javascript, Xdebug on Eclipse PDT, firebug) testing on localhost. Everything has been OK. Last night, before turning off the computer, I just let update manager install the latest updates. This morning, when I turn on the computer, the browser  (firefox 3.0.5) just randomly shutdowns without any error message, even the usual question about the current open tabs [...[Quit] [Cancel] [Quit & save]..] is no more shown.
Since this never happens before, the first thing coming to my mind is to remove these updates that were installed last night to see if the problem is related to that. 
My question: 
How to get the list of recent updates together with a timestamps so that I can uninstall them?  
Thank you very much

---

### Post by Moop on 2008-12-25
Try creating a new profile in firefox and see if it starts ok. In the terminal type...

```
firefox -ProfileManager
```

---

### Post by zvacet on 2008-12-25
To see what you installed go to the** synaptic>files>history**.

---

