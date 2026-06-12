---
title: "install temp and home on same partition"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by ave2 on 2010-05-01
I am going to be installing 10.04, and would like to have a 10 gig partition for system files, and a large one for home.

the problem I had last time i did this was that when I recorded audio tapes, the temp directory was on the system partition, so it would only record for half an hour before the space ran out. 

I see that temp can be on its own partition, but I dont want to do that- how do I share the large home partition with temp

---

### Post by HotShotDJ on 2010-05-01
You could forgo having a separate home partition and just have everything except for swap on a single partition.  However, I don't recommend doing that.  The benefits of having a separate home partition far outweigh any perceived costs.

I've had similar issues when authoring DVD's -- the programs typically default to using /tmp for writing some very large, but temporary, files.  Fortunately, most programs allow the user to change this.  I have created a directory in my home directory for just this purpose (/home/hotshotdj/tmp) and then I set this as the temporary directory for my projects.

---

