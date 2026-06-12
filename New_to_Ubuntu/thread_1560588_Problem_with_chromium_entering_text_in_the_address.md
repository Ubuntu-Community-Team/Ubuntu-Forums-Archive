---
title: "Problem with chromium: entering text in the address bar does not start a search"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by legolas_w on 2010-08-25
Hi,

I am using latest version of Chromium daily builds and it is almost a week that the address bar which start a Google search after we enter a text into it malefuntion and does not initiate a Google search despite pressing enter several times.

Any clue what is wrong?

Thanks.

---

### Post by rburkartjo on 2010-08-25
lego i also use the daily builds but have not experienced you problems. i have set my default search engine for google. lot of times i just use ctrl-k for searches

---

### Post by Fluffums on 2010-10-06
I found this thread because I've been dealing with this problem for awhile myself. I just figured it out for myself and thought I'd share.

Somehow, it seems that Google got removed from the list of search engines in Chromium. I never added any other search engines and none were listed in Chromium when I found this, so I don't know if it is just a matter of losing the default engine, losing Google, or losing all search engines.

Anyway, after uninstalling and re-installing Chromium and finding all my setting the same, including the lack of searching, I found the missing search engine problem.

What you need to do, if you are experiencing the same thing I was, is add a default search engine. I just added > http://www.google.com/search?q=%s for basic Google searching. The %s is replaced with what you type in the search bar. You have to give the search engine a keyword, like "google.com", but that doesn't matter once you make the engine your default.

To get to the search engine dialog, right-click on the url/search-bar and click on "Edit Search Engines...".

---

### Post by Fluffums on 2010-10-08
Okay . . . I was a little premature. That fix I mentioned fixes it, until you reboot.

So, does anyone know where Chromium is trying to save the Search Engine configuration? I'm thinking there's something wrong with where it's saving the config file. Sound plausible to anyone?

---

