---
title: "Firefox &quot;Problem loading page&quot;"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by mith2k7 on 2007-09-02
Hello,
I have a more general question about loading a webpage in firefox

sfa.osu.edu

that page just will not open here in ubuntu (feisty fawn) but if I boot into XP the page comes right up..
I had a friend in Germany (he runs Gentoo) try it and it's the same thing, page won't load.

Now my question would be how is that possible? Is that page blocking some sort of Linux ID??

thx

---

### Post by noob12 on 2007-09-02
The page loaded for me running Feisty with Firefox 2.0.0.6 installed from the Feisty repository.
It took a long time to load though.  Maybe the site is just underpowered and fails sometimes.

I have seen sites using User-Agent string filtering that exclude legitimate Firefox builds by mistake.  But this doesn't appear to be such a case.

---

### Post by mith2k7 on 2007-09-02
> **noob12 said:**
> The page loaded for me running Feisty with Firefox 2.0.0.6 installed from the Feisty repository.
It took a long time to load though.  Maybe the site is just underpowered and fails sometimes.

I have seen sites using User-Agent string filtering that exclude legitimate Firefox builds by mistake.  But this doesn't appear to be such a case.

Usually I would agree 100% with what you said. The only thing that makes me disagree is the fact that it loads perfectly in WindowsXP. 
I doubt the site is underpowered for two reasons
a) it's a big university site.. I'd hope they have the firepower for their servers
b) I can try it in Feisty -> won't load, 1minute later in XP -> loads, 1 min later in Feisty -> won't load

I tried "faking" the User-Agent in Firefox (in Feisty) to make it show the same ID it has in XP but that didn't change anything.. so you're right it doesn't seem to be a User-Agent-String Filter problem..

I just had a friend try to load the page from a Windows System and it loads without problems.. the same time I try to load it and it looks like the server is dead :>

---

### Post by banewman on 2007-09-02
Firefox will time out if the site is busy. Same with IE. When I get that problem I use the back button then the forward button and that mostly gets me in. Don't know if that helps but it worth a shot.

---

### Post by keeto7 on 2008-01-15
mith2k7, did you ever find a solution for this? Both my roommate and I are experiencing the exact same problems.

---

