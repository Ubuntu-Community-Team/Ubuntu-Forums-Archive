---
title: "x360MediaServe"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by Puggytree on 2010-03-02
Okay, I've been trying to install mediaserve to connect Linux to my 360, but I can't even get past the first stage.. 
I've been using this guide [http://ubuntuforums.org/showthread.php?t=794489 ]("http://ubuntuforums.org/showthread.php?t=794489")

As soon as I paste the first line I get the following:
> wget [http://superb-east.dl.sourceforge.net/sourceforge/x360mediaserve/x360mediaserve-0.0.2.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/x360mediaserve/x360mediaserve-0.0.2.tar.gz)
--2010-03-02 09:41:38--  [http://superb-east.dl.sourceforge.net/sourceforge/x360mediaserve/x360mediaserve-0.0.2.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/x360mediaserve/x360mediaserve-0.0.2.tar.gz)
Resolving superb-east.dl.sourceforge.net... 216.34.181.96
Connecting to superb-east.dl.sourceforge.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-03-02 09:41:38 ERROR 404: Not Found.
My guess is that it means the source no longer exists? If this is right any idea's how I can get the source? Is it a case of changing the wget to a working link? Or do I have to go around it a different way? 

Cheers
Puggy

Okay solved this bit, just the last stage I'm struggling with so I'll go back to that thread

---

### Post by KiLaHuRtZ on 2010-03-02
Try TwonkyMedia Server.  I use that and it works very well.  It does cost $30 for a license but worth it in my opinion.  You do get a 30 day trial to test it out first.

[http://twonkymedia.com/]("http://twonkymedia.com/")
[http://www.twonkymedia.com/downloads/twonkymedia-i386-glibc-2.2.5-full-5.1.2.zip]("http://www.twonkymedia.com/downloads/twonkymedia-i386-glibc-2.2.5-full-5.1.2.zip")

Extract that to a directory somewhere then...

```
chmod 744 /some/directory/twonkymedia.sh
chmod 744 /some/directory/twonkymedia-server-default.ini
```

To start it...

```
/some/directory/twonkymedia.sh start
```

And to configure, in Firefox go to...

[http://localhost:9000](http://localhost:9000)

If you like it, I can show you how to setup RC scripts to start/stop it at boot time and such.

---

