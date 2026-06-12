---
title: "Changing focus in FF and TB"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by dunbrokin on 2010-01-12
When I click on a link in TB, it is opened in FF in a new tab - this is good....however focus is switched to this new tab....I want focus to remain on the originating page (the same thing happens when I click on a link in a tab in FF)....how do I keep the focus on the original page in both FF and TB.

Thanks

---

### Post by KIAaze on 2010-01-12
In Firefox:
Edit->Preferences->Tabs->"When I open a link in a new tab, switch to it immediately"

Uncheck it.

---

### Post by dunbrokin on 2010-01-12
> **KIAaze said:**
> In Firefox:
Edit->Preferences->Tabs->"When I open a link in a new tab, switch to it immediately"

Uncheck it.

That was my first idea.....but it was unchecked already!!!

---

### Post by KIAaze on 2010-01-12
Sorry, you're right, it doesn't help. :oops:

Maybe one of these links can help you:
[http://kb.mozillazine.org/About:config_entries]('http://kb.mozillazine.org/About:config_entries') (interesting, link only works if copy/pasted, not when clicked...)
[http://kb.mozillazine.org/Command_line_arguments](http://kb.mozillazine.org/Command_line_arguments)

---

### Post by whitethorn on 2010-01-12
Try middle clicking on the link instead of left click.

---

### Post by aktiwers on 2010-01-12
Middle-click or CTRL+mouse-click

or type about:config in the addressbar and search for [B]browser.tabs.loadInBackground

[/B]and set it to "true".

Look here for more configurations
[http://www.mvps.org/dmcritchie/firefox/tabs_config.htm](http://www.mvps.org/dmcritchie/firefox/tabs_config.htm)

---

### Post by dunbrokin on 2010-01-12
Sorry, middle click or CTRL +click do not give the expected result....they cause the same effect as the normal click i.e. focus transferred to the new tab.

---

### Post by dunbrokin on 2010-01-12
bump!

---

### Post by aktiwers on 2010-01-13
Did you look at the link I posted above?

---

### Post by dunbrokin on 2010-01-13
Ooops sorry....missed that.

---

### Post by dunbrokin on 2010-01-13
> **aktiwers said:**
> Middle-click or CTRL+mouse-click

or type about:config in the addressbar and search for [B]browser.tabs.loadInBackground

[/B]and set it to "true".

Look here for more configurations
[http://www.mvps.org/dmcritchie/firefox/tabs_config.htm](http://www.mvps.org/dmcritchie/firefox/tabs_config.htm)

Browser.tabs.loadInBackgroun = true did not work.

I will browse through your link to see if I can find anything there.

---

### Post by dunbrokin on 2010-01-13
I think it must be a bug...I am using Swiftfox 3.5.7 and have tried the following to no avail.

browser.tabs.loadDivertedInBackground;true
browser.tabs.loadInBackground;true

So while these may work on FF, the do not seem to work on SF.

---

### Post by KIAaze on 2010-01-13
I can confirm that "browser.tabs.loadDivertedInBackground;true" works in Mozilla Firefox 3.5.3. (installed from 9.10 repositories).

---

### Post by dunbrokin on 2010-01-13
Thanks.

---

