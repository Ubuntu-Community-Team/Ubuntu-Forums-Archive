---
title: "Updates Question"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by jozmoz on 2009-10-18
I do I ignore an update so the update star doesn't keep appearing telling me of this update. is there some sort of ignore update feature?

Thanks for any help.

---

### Post by PorkyPie on 2009-10-18
I'm not sure what you mean, but i've never seen an update star.

---

### Post by kansasnoob on 2009-10-18
> **jozmoz said:**
> I do I ignore an update so the update star doesn't keep appearing telling me of this update. is there some sort of ignore update feature?

Thanks for any help.

What specific update are you wanting to avoid? Need the specific package name(s).

---

### Post by clive littlewood on 2009-10-18
Hi

The update manager gives you the option of leaving until later or if you do not want an update untick the box against the update.

Clive

---

### Post by jozmoz on 2009-10-18
I've unticked the update but even after a restart the update star appears again telling me of this update. There must be a way of telling it I don't want to install this update permantly, especially as its already on my system (google chrome).

---

### Post by kansasnoob on 2009-10-18
> **jozmoz said:**
> I've unticked the update but even after a restart the update star appears again telling me of this update. There must be a way of telling it I don't want to install this update permantly, especially as its already on my system (google chrome).

If you installed using the .deb go to Synaptic and click on Search, type google-chrome (or browser), highlight that package, and go to Package > Lock Version. See screenshot:

[ATTACH]132325[/ATTACH]

Just be careful using the "lock version" feature. Locking the version of some packages can effect security and/or even cause kernel related "breakage"! I hardly trust the security of Google Chrome anyway so IMHO it doesn't matter.

I am curious, since it's still in development, why you'd want to reject updates to it?

---

### Post by sync on 2009-10-18
I would like to know the same thing.  Normally it's a good practice to keep software as updated as possible, as newer versions repair bugs and such that are problematic in previous versions.  I would recommend updating unless you have a real good reason why you wouldn't want to.

---

### Post by ikt on 2009-10-18
> **jozmoz said:**
> I've unticked the update but even after a restart the update star appears again telling me of this update. There must be a way of telling it I don't want to install this update permantly, especially as its already on my system (google chrome).

Is it google chrome or chromium installed from the PPA?

Chromium from the PPA has updates nearly every day.

---

### Post by juancarlospaco on 2009-10-18
*Install updates is recommended, at least once a week, ASAP.*

---

