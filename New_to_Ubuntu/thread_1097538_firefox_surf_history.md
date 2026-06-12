---
title: "firefox surf history"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by serros88 on 2009-03-16
Hi, 

When I hit Clear Private Data with Firefox 3.0.7, my history is not cleared at all, still can see the last surfs!?

How to properly clear surfing history with Firefox, but also on the HD (cookies, etc).

Any tool for cleaning PC under Linux?

Txs
serros

---

### Post by nelskurian on 2009-03-16
Someway late...

In firefox,the proper way to clear history is to clear private data by checking all the options.

You have 2 options.

You can either use [Hide Unvisited Add-on]("https://addons.mozilla.org/en-US/firefox/addon/7429") for Firefox or perform the following steps to reconfigure the Navigation bar:

Type: About:config in the Navigation Bar
Click: I'll be careful I promise when the warning prompts you from Firefox
Scroll down to: browser.urlbar.maxRichResults
Double Click and Change Default from 12 to 0

---

### Post by orethrius on 2009-03-16
I've gone rounds with people on this one.  Are all the "history" results you're seeing marked with gold stars?  Those are bookmarks, and yes - until you remove them, they will continue to show up in address bar searches.  This behaviour is handy if you easily misplace technical articles, manuals, forum posts and the like; not so much if you have a jealous lover and certain *cough* interests *cough* that might set them off.

Now, that being said, you can *mask* bookmarks from appearing in the address bar by doing this:

[quote=Hippos]
1) Type &#8220;about:config&#8221; (without the quotation marks) into the location bar
2) Click the &#8220;I&#8217;ll be careful, I promise!&#8221; button
3) Filter &#8220;browser.urlbar.maxRichResults&#8221;
4) Double click the row and reset the value to &#8220;0&#8243;

Written by Hippos on 06.18.08
[/quote]

Additionally, the site list itself can be flushed by using [this extension](https://addons.mozilla.org/en-US/firefox/addon/7429) (addons.mozilla.org), though I'm unclear on whether it's a real flush or a simple reimplementation of Hippos' masking method, above.

As for your cookies, those can be removed by checking "Cookies" on the "Clear Private Data" dialog, or by heading to Edit > Preferences > "Privacy" tab > "Private Data" section, "Settings..." button, checking "Cookies" and hitting "OK".

None of this changes the simplest, best advice I've ever heard: if you don't want people to know about it, don't keep bookmarks about it. ;)

---

### Post by billgoldberg on 2009-03-16
> **serros88 said:**
> Hi, 

When I hit Clear Private Data with Firefox 3.0.7, my history is not cleared at all, still can see the last surfs!?

How to properly clear surfing history with Firefox, but also on the HD (cookies, etc).

Any tool for cleaning PC under Linux?

Txs
serros

If you really don't wont people to know what website you visit, download the new firefox beta.

It has an "anonymous" mode.

---

### Post by skymera on 2009-03-16
Yes.

I run Firefox 3.1b3 in XP, everytime i use the private browsing, it freezes.

---

