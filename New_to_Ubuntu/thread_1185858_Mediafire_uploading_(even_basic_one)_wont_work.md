---
title: "Mediafire uploading (even basic one) wont work"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by Ryuki_NdranC on 2009-06-12
I already searched for a while about this but it seems most post are eather old, not solved or not many ppl face this problem.

Im trying to upload 14 files to mediafire using the advance update tool, first thing i notice everything works just fine untill the actual upload when it greys out, then send me back to mediafire home screen (conky net speed counter seems to tell there is a sudden spike in the upload speed for about 30 secs then it drops).

Then i tried to use the basic uploader and it wont work with more than 4 files at a time. When i try with 5 or more it says upload speed is 1 kbps and it will never upload (i have to cancel the upload myself). But with 4 files or less it works just fine.

Im using ubuntu jaunty with last firefox from the repos, and the java/flash installed from the medibuntu repos. My machine has a dualboot with vista and everything works just fine in vista. So i guess is not my network.

Any ideas? :/ Really appreciated if you could clue me up a little :)

Thx in advance

---

### Post by MontelEdwards on 2009-07-14
if i remember correctly, Mediafire uses Java for the advanced uploader. I haven't used it in a while so i cannot be  100% sure. You probably have the open source Java, which IMHO sucks ***. So, I would download the real java, and Firefox plugin and try it again. uninstall whatever version you already have installed and then

```
 sudo aptitude install sun-java6-plugin 
```

---

### Post by Sepero on 2010-06-15
This problem is fixed in the latest flash player for linux

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

