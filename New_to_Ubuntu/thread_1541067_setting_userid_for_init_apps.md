---
title: "setting userid for init apps"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by _Dan on 2010-07-28
Hello,

I see apache is run as user "www-data".

Now I have some other server software (a video streaming software) that creates media files, and I want these files deletable from PHP scripts.

So what I think I need to do is to get this media server software to run as the same user as apache (www-data), then apache/PHP will be able to hopefully access/delete any files created by the media software.

So how do I get this media server application to run as www-data user? At the moment it's started from /etc/init on boot and runs as root.

---

