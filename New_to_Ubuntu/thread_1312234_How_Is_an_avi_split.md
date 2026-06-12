---
title: "How Is an avi split?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by nakama85 on 2009-11-03
I recently came across a video that was split into many rar files.
When I extracted the first in the series the rest automatically extracted and joined into 1 large avi file.

I was wondering if someone could tell me how this is done.

Thanks

---

### Post by travmanx on 2009-11-03
> **nakama85 said:**
> I recently came across a video that was split into many rar files.
When I extracted the first in the series the rest automatically extracted and joined into 1 large avi file.

I was wondering if someone could tell me how this is done.

Thanks

If you are asking for how-to do it:
I know on Windows machines (Suppose you are using Winrar)you right-click on it and click compress. In the settings you can specify it to be split into multiple files and specify the size of each parts.

[img]http://getit.rutgers.edu/tutorials/winrar/images/11_-_advanced_options.gif[/img]


On Unix:

Right click the item -> Compress

Check "Split in volumes of:" and specify how large of chunks of the files you want.

---

### Post by nakama85 on 2009-11-03
> **travmanx said:**
> If you are asking for how-to do it:
On Unix:
Right click the item -> Compress
Check "Split in volumes of:" and specify how large of chunks of the files you want.

Thanks so much. This solved it. you do however need to install rar or 7zip as they are the only two formats that seem to support splitting.

---

