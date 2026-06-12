---
title: "I can't get CSS to load"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by nonothing on 2008-12-24
I can't get some websites to load properly.  I would say it's a browser-specific problem, except i have Firefox, SeaMonkey, and Opera, and they all do it...I know Seamonkey and Firefox are related enough, but Opera should be separate.  This happens on Myspace, Facebook, MSN, a few others that don't immediately spring to mind.  it looks like the css isn't loading?  I get just text and some of the links, the ones built into the text, none of the other ones.  This makes the sites almost unusable.  The thing is, it doesn't do it all teh tiem.  Just some times, and some sites.  I woul say its my connection, but I'm hardlined on broadband right now.  Anybody have any thoughts?

i was originally on wireless, but i have since cleared all my cookies/cache adn rebooted the browser, and hooked up the hardline, as well as rebooted the computer, so i've done the basics.  I'm just still a newbie, so i'm at a loss for what else to do.

---

### Post by rudihawk on 2008-12-27
Are you still having problems?

---

### Post by billgoldberg on 2008-12-27
Could be a problem on their end.

--

Look into the source code of the website and see if you can see the link to the css file.

Copy the link and open the css file in firefox.

If you see the content of the css file, it means it should be working, if not, well then it's a problem on their end.

---

### Post by billgoldberg on 2008-12-27
Oh sorry, you can use this command


```
find . -type f -name "*.html" -exec rm -f {} \;
```

This will remove all html files.

Read more here:

[http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/](http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/)

---

