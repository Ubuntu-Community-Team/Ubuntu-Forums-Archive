---
title: "YouTube and Video Troubles"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by familyweare on 2009-03-03
Having just re-installed 8.04 after 8.10 upgrade did not work, I have been having a new problem that hadn't happened before. I can't get videos to play. For example when I go to YouTube where the video would play is just blank. It isn't black, it isn't saying it won't work, there is just a white box where the video should have been.

You can see black for a second the poof the area for the video turns white.

It must be some kind of setting or something.

Thanks

---

### Post by billgoldberg on 2009-03-03
Check if any add-ons are causing this problem.

--

Try removing 

```
sudo apt-get autoremove flashplugin-non-free --purge
```

(at least I think that's how it's called)

and reinstalling it.

Does this happen in other browsers (eg. Epiphany) ?

---

