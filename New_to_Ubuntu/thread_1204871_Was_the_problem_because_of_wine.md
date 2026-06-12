---
title: "Was the problem because of wine?"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by kewl_123 on 2009-07-05
I faced following problems:
1) Was unable to login to sites like this one
2) Was unable to search any site except using google
3) The forward and back button on firefox were grayed out
4) Download them all add-on was acting strange
5) When I clicked on manage add-ons, firefox disappeared.

I tried to uninstall firefox using synaptic manager, but firefox and all above stated problems were still there.

Then I uninstalled wine, and with it went all the problems and thats how I am able to post here. Did anyone have any such experience before?

Thank you.

---

### Post by ivanvajar on 2009-07-05
Never.

---

### Post by xavierp94 on 2009-07-05
> **kewl_123 said:**
> I faced following problems:
1) Was unable to login to sites like this one
2) Was unable to search any site except using google
3) The forward and back button on firefox were grayed out
4) Download them all add-on was acting strange
5) When I clicked on manage add-ons, firefox disappeared.

I tried to uninstall firefox using synaptic manager, but firefox and all above stated problems were still there.

Then I uninstalled wine, and with it went all the problems and thats how I am able to post here. Did anyone have any such experience before?

Thank you.
I can't imagine WINE being the culprit of the problem. It must of been some sort of dependency that may have caused this?

---

### Post by napalm brain on 2009-07-05
I'm assuming that you're not using Wine to run Firefox since you spoke of having uninstalled Firefox from Synaptic. 

But no, the chances of it being associated with Wine are extremely small. 

Try and reinstall Firefox from the repos and see what happens. As stated earlier, it could be a bad dependency or two. The installation of Wine was probably just a coincidental event.

---

### Post by kewl_123 on 2009-07-05
> **napalm brain said:**
> I'm assuming that you're not using Wine to run Firefox since you spoke of having uninstalled Firefox from Synaptic. 

No, I am not using firefox from wine.
And even after uninstalling from synaptic, its still there and works. 
And may be it was a co-incidence that uninstalling wine solved the problem.

---

### Post by shae on 2009-07-06
The best option might be to try something like this.

Rename your ~/.mozilla folder to ~/.mozilla-bak.  Start firefox and see if it still has problems.

---

