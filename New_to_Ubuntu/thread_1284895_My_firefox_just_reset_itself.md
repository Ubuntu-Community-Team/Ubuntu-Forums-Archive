---
title: "My firefox just reset itself?"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by suitedaces on 2009-10-07
I've just turned on my computer and firefox seems to have reset itelf, asides from cookies (it still automatically logged me in here so I assume cookies are still stored?). But homepage has been reset, and there's no sign of bookmarks etc. Have I unwittingly done something wrong, and is there a possible fix?

---

### Post by suitedaces on 2009-10-07
And I've just noticed status bar missing in spite of it being selected in View, and my location bar stays with the original address I typed in, regardless of where I navigate to.

---

### Post by suitedaces on 2009-10-07
The plot thickens, I've just noticed my back, forward, refresh and home buttons are still there, but are greyed out and no longer work?

---

### Post by suitedaces on 2009-10-07
Thread half solved. I seen this as an opportunity to upgrade to shiretoko (in synaptic), expecting to start from scratch again. But somehow shiretoko has automatically found the bookmarks et al that firefox was oblivious to?

I'd consider this fixed now, but if someone wants to answer just to have it here for the next person doing a search, that's grand. I'd just like to point out that I've no idea what happened firefox. I closed it as normal last night and shut down etc, hadn't been doing anything more than simple browsing. Turn it on this morning, and all gone. Even more bizarre was shiretoko automatically finding the stuff I had in firefox up until last night, stored passwords etc. I'm confused. I hadn't even looked at shiretoko until 5 mins ago, so it couldn't have been installation issues.

---

### Post by baikinman on 2009-10-07
Hi,

I had a similar problem. Try it like this:
First you locate your Firefox profile directory, it's probably something like /home/username/.mozilla/gibberish.default. 
Copy that folder and rename it to something else, then open a terminal and start firefox with the ProfileManager attribute.

```
firefox -ProfileManager
```

Make a new profile, chose the newly copied folder and start firefox. Then select "Manage Bookmarks" and try to restore a backuped bookmark-file.

Good luck.

---

