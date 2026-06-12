---
title: "New User, need help"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by phatlanems@live.com on 2009-06-10
Hi guys

I'm having problems locating packages for my MP3 and video files. Given that my ISP is a bit unreliable, can anyone help me find packages I can download... Thanks

---

### Post by billgoldberg on 2009-06-10
> **phatlanems@live.com said:**
> Hi guys

I'm having problems locating packages for my MP3 and video files. Given that my ISP is a bit unreliable, can anyone help me find packages I can download... Thanks

open a terminal and enter

sudo apt-get install ubuntu-restricted-extras

press enter, give your password (you won't see what you type) and press enter again.

If the java EULA pops up, press tab and enter.

That should install codecs you need.

You can always install the medibuntu repo, and also install the w32codecs and non-free-codecs.

---

### Post by shifty_powers on 2009-06-10
+1

ubuntu-restricted-extras is always one of the first things i install. Well that and VLC. Between the two, never need the medibuntu repo's...

---

