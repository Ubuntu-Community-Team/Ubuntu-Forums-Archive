---
title: "Firefox location bar: must I type in &quot;www.&quot;?"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by watchpocket on 2011-09-06
This may be a slightly ridiculous question because I'm sure the fix is simple, but recently I find that when I type a web address in Firefox's location bar, nothing happens unless I go back and manually put in the "www." to the left of the address.  

The trip-dub prefix should enter automatically, but how/where do I activate that?

---

### Post by axatrikx on 2011-09-06
type about:config on the addressbar
promise that ull be careful n go to the page.
Type fixup on the filter textbox and make 'browser.fixup.alternate.enabled' parameter true.

---

### Post by vasa1 on 2011-09-06
> **axatrikx said:**
> type about:config on the addressbar
promise that ull be careful n go to the page.
Type fixup on the filter textbox and make 'browser.fixup.alternate.enabled' parameter true.

Nice. But it should be that way by default. Perhaps, OP has some add-on that altered the setting?

---

### Post by watchpocket on 2011-09-06
Checking that, I see it's already at "true".  I think it might be my tab utilities addon that's interfering.  I'll have to wade through all its settings.

---

### Post by vasa1 on 2011-09-06
> **watchpocket said:**
> Checking that, I see it's already at "true".  I think it might be my tab utilities addon that's interfering.  I'll have to wade through all its settings.

First, just disable that one add-on and see if the function is restored. That way, you'll know that the add-on was responsible or not. If it's more complicated, you could run in safe mode (under Help in the Fx menu).

---

### Post by necromonger on 2011-09-06
simple type in website name and hold down ctrl and hit enter

---

### Post by watchpocket on 2011-09-06
> **necromonger said:**
> simple type in website name and hold down ctrl and hit enter

Sure, that works, but you shouldn't even have to do that.  I'll disable various addons tonight when I'm at home -- it's definitely going to be one of them and it's just a matter of finding which one it is.

---

### Post by watchpocket on 2011-09-07
It was BarTab, which I've now removed. Tab Utilities accomplishes the same thing (among many others): keeping all your tabs in the tab bar but keeping them unloaded until you load them.

Here's how to do similar, from a comment on the BarTab page:

" using " [https://addons.mozilla.org/en-US/firefox/addon/tab-utilities/](https://addons.mozilla.org/en-US/firefox/addon/tab-utilities/)  " which allows tab unloading after X minutes (working on all versions  of FF to date) as well as reloading the unloaded tab as soon as it is  selected without requiring tab scope or pressing F5. 

about:config -->extensions.tabutils.restartAfter  (change this value with the desired time in minutes).

*Note you can also manually unload/restart the tabs if you desire.*

---

