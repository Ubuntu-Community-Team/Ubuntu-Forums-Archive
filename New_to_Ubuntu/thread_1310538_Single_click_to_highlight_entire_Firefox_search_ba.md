---
title: "Single click to highlight entire Firefox search bar?"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by sayeo87 on 2009-11-01
Is there a way to select the entire FIrefox search bar on a single click? (Like the way it behaves in Windows)? I can't seem to find anything relevant in about:config. Thanks!

---

### Post by kaibob on 2009-11-01
This is the about:config entry:

```
browser.urlbar.clickSelectsAll
```

---

### Post by danielgrosvenor on 2010-06-06
To expand on that slightly for those who don't know:

In your Firefox URL bar, type [B]about:config
[/B]You will see a warning sign urging you to be cautious ('Here Be Dragons').

After the warning page, scroll down until you find the line:

browser.urlbar.clickSelectsAll

You will see the value is set as 'false', meaning this function is disabled.  Right click on it and select 'toggle' to change it to 'true'.  The text will become bold and you are now able to select all with a single click.

---

### Post by Ron Carson on 2010-06-06
Thank you so VERY much for this question and answer!!!!!!

---

### Post by danielgrosvenor on 2010-06-06
> **Ron Carson said:**
> Thank you so VERY much for this question and answer!!!!!!

Pleasure. :)  I'm new to Linux myself, so understand the value of taking time to explain things in detail for those who need that extra guidance.

Frankly I don't see any advantage to the double-click approach. It was one of the first things I changed.

---

### Post by formaldehyde_spoon on 2010-06-06
> **danielgrosvenor said:**
> ... 
Frankly I don't see any advantage to the double-click approach. It was one of the first things I changed.

One of my pet hates about IE is the single click select! ;)

When double clicking to place the cursor in the current address it's much easier to move the mouse slightly and miss your target location than it is with a single click.

---

### Post by zorglub76 on 2010-10-19
Is there a way to do the same thing for the search field? This only helps with url bar (at least on Ubuntu 10.10 with firefox 4b08)...

---

### Post by bilbs84 on 2012-10-11
This was annoying me too, i changed the address bar issue, but was still  annoyed with the search bar behavior, however, i found an acceptable  solution.
[https://addons.mozilla.org/en-us/fir...lear-search-2/]("https://addons.mozilla.org/en-us/firefox/addon/clear-search-2/")
this addon will clear the search bar with every search, so its always  empty when you click into it, hope this help you as much as it did me :smile:

---

### Post by Pletched on 2012-10-11
> **bilbs84 said:**
> This was annoying me too, i changed the address bar issue, but was still  annoyed with the search bar behavior, however, i found an acceptable  solution.
[https://addons.mozilla.org/en-us/fir...lear-search-2/]("https://addons.mozilla.org/en-us/firefox/addon/clear-search-2/")
this addon will clear the search bar with every search, so its always  empty when you click into it, hope this help you as much as it did me :smile:

There is an option in the configuration (i.e. about:config) named browser.search.cleanOnSubmit. It's descriptive.

---

### Post by Bucky Ball on 2012-10-11
[B][I]Thread Closed
[/I][/B]
***Reason:*** Necromancy

From Code of Conduct:

> **Thread Closing: **... This is a non-exhaustive list of reasons a thread may be  closed, but will give the general idea:
  
[LIST=1]
[*]The thread has run it's course and posts have begun repeating themes
[*]The thread has degraded into an argument
[*]The thread topic is a duplicate of another current and active thread
[*]***The thread is very old.***
[/LIST]
Please post a new thread with any current issues. ;)

---

