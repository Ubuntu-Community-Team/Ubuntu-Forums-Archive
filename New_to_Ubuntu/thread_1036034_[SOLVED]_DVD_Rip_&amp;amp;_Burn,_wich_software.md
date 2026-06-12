---
title: "[SOLVED] DVD Rip &amp;amp; Burn, wich software"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2009-01-10
Hi
I'm used to RIP DVD under Windows with DVD Decrypter and burn them with DVD Shrink.
Trying to migrate to Linux, which software should I use ?
I read this : [http://www.linux.ie/newusers/alternatives.php](http://www.linux.ie/newusers/alternatives.php)
But they says DVD rip & burn it's still not very well supported yet (the post was done a year and half ago)

Thanks

PL

---

### Post by JoshuaRL on 2009-01-10
Be careful you've checked out what the laws in your country allow.  I'm in the US and it's illegal to backup DVDs.  The issue is that, unlike CDs that are unencoded audio, DVDs are encoded on the disk.  So decoding them requires a licence, and they don't give out licences for what you're trying to do.

But if its legal, try k9copy or ffmpeg from the medibuntu repo.

---

### Post by cptrohn on 2009-01-10
> **JoshuaRL said:**
> Be careful you've checked out what the laws in your country allow.  I'm in the US and it's illegal to backup DVDs.  The issue is that, unlike CDs that afe unencoded audio, DVDs are encoded on the disk.  So decoding them requires a licence, and they don't give out licences for what you're trying to do.

But if its legal, try k9copy or ffmpeg from the medibuntu repo.

Hopefully REAL wins their lawsuit on this with the fair usage lawsuit they have pending...

---

### Post by nhasian on 2009-01-10
you will want to look into dvdrip and DeVeDe

```
sudo apt-get install dvdrip devede
```

---

### Post by JoshuaRL on 2009-01-10
> **cptrohn said:**
> Hopefully REAL wins their lawsuit on this with the fair usage lawsuit they have pending...

Very much agreed.  Even though it IS in fact decoding, I would like the legal ability to back up the videos I paid for and own.

---

### Post by Pierrot Lafouine on 2009-01-10
Thank you everyone
I have kids and the life expectancy of a DVD is barely a day or 2.
At 20$ per DVD, I make copy of DVD and play the copy, keeping the original is safe place.

So what I understand is DVD is not the same as CD.  We could make any amount of copy of the original CD, but no copy of the copy of the CD were allowed (they called that : SCMS -> Serial Copy Management System).


Thanks

---

### Post by binbash on 2009-01-10
you can still use dvdshrink with wine

---

### Post by JoshuaRL on 2009-01-10
> **binbash said:**
> you can still use dvdshrink with wine

But why?  If there's perfectly good FREE applications that run natively, there's no reason to load a Windows application in Wine.

---

