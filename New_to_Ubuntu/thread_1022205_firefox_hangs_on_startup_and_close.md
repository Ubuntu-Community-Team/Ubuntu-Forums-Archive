---
title: "firefox hangs on startup and close"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-26
I have been using firefox on 8.10 and 8.04(two different computers)
for a while with no problem. Recently though, firefox on both computers has been seemingly much slower. 
It takes longer than usual to start. 
When I try to close it takes long enough for my force quit option to come up.

Now to be honost I don't really pay attention to updates I just click on install. So I am not sure where my problem is.

thanks for any help

---

### Post by Coder543 on 2008-12-26
Hmm, perhaps you should open firefox. Goto Edit -> Preferences. Then Go to privacy then in the Private Data section click settings. Check all the boxes (except perhaps the clearing of the saved form and data) then click ok. Then click clear now.

---

### Post by Archmage on 2008-12-26
Is it possible that an extensions is slowing Firefox down?

Try to start firefox with the -P parameter ("firefox -P") and use a new profile to see if it is than running better.

But you should use the updates, because there are some bugs that might slow down firefox...

---

### Post by mmcastig on 2009-01-08
I'm also having the same problem. Unless something changed recently it's not a plugin issue. I'm using the same ones I've always had (sans the ones that are not Firefox 3 compatable). I've also noticed that Firefox will pretty frequently arrest control of all of my system resources. I understood that the memory leak problem was fixed as of version 3, apparently not. I also make sure to apply both FF and system updates as they become available. I'll give running under another profile a shot, but I'm guessing it's not plugins? Does anyone else have this problem or a possible solution?

---

### Post by Crafty Kisses on 2009-01-08
While Firefox is running, run the following:
```
top
```
Post the results back here at the forums and I might be able to help you.

---

### Post by chandra on 2009-01-21
Same problem as reported by mmcastig.

Chandra

---

