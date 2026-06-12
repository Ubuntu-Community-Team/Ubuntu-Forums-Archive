---
title: "Persistence Pays off"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by carrarin on 2009-01-21
I was wondering if i can use a live cd, and save changes to my flash drive. Not just documents, but real changes. 

I guess what what im asking is, does Ubuntu live cd allow for persistent write back

---

### Post by Keith_Beef on 2009-01-21
> **carrarin said:**
> I was wondering if i can use a live cd, and save changes to my flash drive. Not just documents, but real changes. 

I guess what what im asking is, does Ubuntu live cd allow for persistent write back

I think that what you're looking for is provided by UnionFS.

Try reading the [Wikipedia article ]("http://en.wikipedia.org/wiki/UnionFS")and then google around for more information.

K.

---

### Post by carrarin on 2009-01-21
i guess this makes this easy then, does ubuntu(live cd) have unionFS, and how does one use it,

---

### Post by snova on 2009-01-21
> **carrarin said:**
> i guess this makes this easy then,

Not really.

> does ubuntu(live cd) have unionFS,

I really don't know... I'd say probably.

> and how does one use it,

With difficulty. :)

UnionFS, in theory, would be something like what would be needed- it's a "filesystem" that internally just looks in two or more physical filesystems for actual files. It's like putting one on top of the other.

Unfortunately, this is probably far from what you'd actually need- not only would it be difficult to actually get it working, but desktop-wide settings wouldn't be applied (kinda). And I'm not even sure it's on the Live CD.

Instead, I suggest you create a bootable USB drive- like a Live CD, but for a flash drive. See:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Installing Ubuntu on USB drive using Windows]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Installing Ubuntu on USB drive using Windows")

---

### Post by Keith_Beef on 2009-01-22
> **carrarin said:**
> i guess this makes this easy then, does ubuntu(live cd) have unionFS, and how does one use it,

Well, this is why I limited my first replay to just the advice to go to Wikipedia and then Google... I've never used UnionFS, I've only read about it in articles.

I don't know if there is a specific Ubuntu Live Disc. I've downloaded installation discs that I've used as a live disc on occasion.

I would venture to say, though, that it should not be too difficult to boot from a live disc and set up UnionFS using a USB memory stick with /var, /etc, /usr and /home on it to overlay those on the disc.

---

