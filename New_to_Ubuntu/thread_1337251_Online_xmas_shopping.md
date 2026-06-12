---
title: "Online xmas shopping"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by unknown user on 2009-11-25
I have been doing some online xmas shopping and do not want my wife to see what I am getting her. 

Does Ubuntu store visited websites and images (from the sites) like Windows does in its temp folder? If it does I can delete this history and keep the surprise going. I have firefox set to delete all URL history every timeI close the browser.

---

### Post by Groucho Marxist on 2009-11-25
> **unknown user said:**
> I have been doing some online xmas shopping and do not want my wife to see what I am getting her. 

Does Ubuntu store visited websites and images (from the sites) like Windows does in its temp folder? If it does I can delete this history and keep the surprise going. I have firefox set to delete all URL history every timeI close the browser.

In the case of visited websites, Ubuntu does store them via Firefox cookies. I would highly recommend deleting all cookies every time you exit your session to prevent prematurely ruining the surprise :)

---

### Post by mbzn on 2009-11-25
My guess is that this would be fine unless you wife is a guru, in witch case you might want to hide the computer until after x-mas....
Or wait for someone that could tell you were it is stored...

---

### Post by bodhi.zazen on 2009-11-25
> **mbzn said:**
> My guess is that this would be fine unless you wife is a guru, in witch case you might want to hide the computer until after x-mas....
Or wait for someone that could tell you were it is stored...

Firefox does keep things, but it is easy to stop that behavior.

First you can start firefox in private mode :

Tools -> Start private browsing 

[http://www.firefoxfacts.com/2009/07/01/firefox-private-browsing-mode-help-and-faq/](http://www.firefoxfacts.com/2009/07/01/firefox-private-browsing-mode-help-and-faq/)

If you prefer you can change firefox's behavior.

First in preferences, go to the privacy tab, and clear 

Select "Clear history when Firefox closes" -> clear everything.

Finally, you need an edit in about:config.

Enter "about:config" in your address box -> edit these options :

> #Turn your cache off for off line use
browser.cache.offline.capacity  0
browser.cache.offline.enable  false

---

