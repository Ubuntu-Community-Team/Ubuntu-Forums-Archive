---
title: "Update Manager"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by jnmjr on 2010-05-19
Hey guys, just a question about UDManager, since upgrading to Lucid I haven't gotten any auto notification of up dates, I've done it manually about once a week or so, with Karmic I always got notifications quite often, has this changed with Lucid? THX.

---

### Post by Ozymandias_117 on 2010-05-19
Are you saying that it's not popping up that you need updates, but if you try to manually update, it finds some?

---

### Post by jnmjr on 2010-05-19
> **Ozymandias_117 said:**
> Are you saying that it's not popping up that you need updates, but if you try to manually update, it finds some?

Yes, but the thing is that I've been finding tons of them and it should be popping up to let me know???

---

### Post by Ozymandias_117 on 2010-05-19
Open up gconf-editor and navigate to apps/update-notifier. Make sure auto_launch is checked, then you might want to change the "regular_auto_launch_interval" to something lower. It defaults at 7 (7 days). 0 means as soon as they're available you'll be notified, 1 is 1 day etc.

---

### Post by jnmjr on 2010-05-19
> **Ozymandias_117 said:**
> Open up gconf-editor and navigate to apps/update-notifier. Make sure auto_launch is checked, then you might want to change the "regular_auto_launch_interval" to something lower. It defaults at 7 (7 days). 0 means as soon as they're available you'll be notified, 1 is 1 day etc.

Just what the Doctor ordered, THX

---

### Post by pizza-is-good on 2010-05-19
> **Ozymandias_117 said:**
> Open up gconf-editor and navigate to apps/update-notifier. Make sure auto_launch is checked, then you might want to change the "regular_auto_launch_interval" to something lower. It defaults at 7 (7 days). 0 means as soon as they're available you'll be notified, 1 is 1 day etc.

Thanks, that was worrying me too, and that fixed it. Thanks!

~pizza

---

