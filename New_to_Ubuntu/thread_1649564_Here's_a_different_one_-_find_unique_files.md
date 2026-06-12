---
title: "Here's a different one - find unique files?"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by ScottinSoCal on 2010-12-20
I can - and realize I probably will - wind up doing this manually, but figured I'd give this a shot.

Given two directory structures is there a utility to scan through the files and give me a list of those files which are unique? I'm constructing a data packet for a product. Call it a computer, for the purposes of the example. Many of the files, like drawings with dimensions, will stay the same for all shipped units. A few of the files, like specific thermal characteristics of the CPU under a given load, will be unique to each shipped unit. Is there a utility which would compare the data packet folders for serial number 1 and serial number 2 and give me a list of only those files which are different?

I've got a dupe finder, but it's exactly the reverse of what I need. And I know this is a pretty bizarre request, so there may not be anything out there that does what I need done.

---

### Post by TeoBigusGeekus on 2010-12-20
Look at uniq
```
man uniq
```

---

