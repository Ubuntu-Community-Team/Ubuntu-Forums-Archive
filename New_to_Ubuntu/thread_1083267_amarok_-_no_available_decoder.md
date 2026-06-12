---
title: "amarok - no available decoder"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by geeare1 on 2009-02-28
hi, i'm new to ubuntu and i'm having trouble with amarok. i'm getting a 'no available decoder' message when i try to play streams.

i did a search and found a repository for w32codecs which i downloaded but i'm still getting the same message.

do i need something in addition to the w32codecs did i never actually need the w32codecs?

thanks,
-gr

liking ubuntu very much so far!

---

### Post by ad_267 on 2009-02-28
Try installing the kubuntu-restricted-extras package. That depends on a few kde specific libraries that aren't included in the ubuntu-restricted-extras package.

---

### Post by geeare1 on 2009-02-28
ad_267, thanks very much for your reply.

as it turns out, installing libxine1-ffmpeg (which may be included in the package you recommended for all i know) did the trick.

thanks,
-gr

---

### Post by ad_267 on 2009-02-28
That's good to hear, and yes that package is included in kubuntu-restricted-extras. 
I think that's the only one you're likely to need out of all of the kubuntu-restricted-extras packages. :)

---

