---
title: "Conky weather."
date: 2009-02-26
forum: New to Ubuntu
---

### Post by omni504 on 2009-02-26
I've googled this, read through alot of posts on this same forum, but it seems like it looks more and more complicated and confusing. I've been messing around with conky (took someone else's script and just changing the colors and font sizes and what not)... It's got all the stuff i want on there, except the weather. 

I tried following along with alot of posts, but they mostly leave me even more confused than i was before (with all the "different" ways of setting up...so i dont know if the next step is for me or just an alternative).

So please if anyone can give me a link or show me a clear cut ONE way to do it. Steps to follow, anything, it would be greatly appreciated (please keep it as simple as possible). And i'll keep googling and looking for understandable instruction.

---

### Post by glotz on 2009-02-26
I don't have a step-by-step to point you to but the basics are simple.

First, you obviously need a data provider that actually tells you how the sky is gonna look. There are many such web sites.

Then you need to scrape the data and parse the stream for the things you're interested in. Like temperature tomorrow and humidity yesterday.

And finally you need to present the data in a visually pleasing format. For this purpose people have made special font sets that can be used with conky. For example, the letter r could look like a rain cloud in such a font set.

Just go ahead and try a few tutorials you find, or if you're unsure, post the links here and people will tell you their opinion. Note that not all advice is good though.

---

### Post by chamber on 2009-02-26
I used [this]("http://ubuntuforums.org/showthread.php?t=869328") one, mine works great.  All of kaivalagi's scripts are great.

---

