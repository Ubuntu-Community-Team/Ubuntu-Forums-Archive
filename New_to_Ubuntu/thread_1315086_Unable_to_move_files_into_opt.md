---
title: "Unable to move files into /opt"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Cruvenium on 2009-11-05
Hi guys,

I'm trying to install Songbird.

I followed this guide: [http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html](http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html)

When I reach the part where I have to enter: 

```
tar xzvf Songbird_0_2_1_linux-i686.tar.gz
```

It comes up with alot of errors like this.

[IMG]http://a.imagehost.org/0969/Screenshot_18.png[/IMG]

I tried extracting it on my desktop and move it into the /opt folder, but this error comes out:

[IMG]http://a.imagehost.org/0642/Screenshot-1.png[/IMG]

Is there a solution for this? Or another method to install Songbird?

---

### Post by movieman on 2009-11-05
I suspect they meant:

sudo tar xzvf Songbird_0_2_1_linux-i686.tar.gz

---

### Post by Cruvenium on 2009-11-05
Oh.

Let me try and I'll report back again.

**EDIT:**

Alright, it's working now.
Thanks a lot movieman!

---

