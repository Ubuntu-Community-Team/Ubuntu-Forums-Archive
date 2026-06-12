---
title: "Today's update screwed stuff up!"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by Casey R on 2010-10-20
So, I was alerted to Update Manager upon waking up this morning. There was a new kernel update and some other stuff (I'm on 10.10, for the record).

Upon reboot - there were no title bars for anything! I went into the terminal and typed

[B]metacity --replace
[/B]

which fixed that problem.

Also, Docky was giving me errors. The animation wasn't working and I was getting the error regarding compositing.

So, I went into gconf-editor and turned on compositing from there. It fixed this problem also.

However - when I tried to exit the terminal - both Docky and Metacity screwed up again, and the whole system froze. I had to reboot and now I'm going through the same thing again.

I really don't want to have to leave the terminal open lol.

Any ideas? I'm wondering if it's a Compiz problem....if so what should I do?

---

### Post by sydbat on 2010-10-20
> **Casey R said:**
> So, I was alerted to Update Manager upon waking up this morning. There was a new kernel update and some other stuff (I'm on 10.10, for the record).

Upon reboot - there were no title bars for anything! I went into the terminal and typed

[B]metacity --replace
[/B]

which fixed that problem.

Also, Docky was giving me errors. The animation wasn't working and I was getting the error regarding compositing.

So, I went into gconf-editor and turned on compositing from there. It fixed this problem also.

However - when I tried to exit the terminal - both Docky and Metacity screwed up again, and the whole system froze. I had to reboot and now I'm going through the same thing again.

I really don't want to have to leave the terminal open lol.

Any ideas? **I'm wondering if it's a Compiz problem**....if so what should I do?Remove Compiz via Synaptic (System > Administration) then reboot.

Let us know how it goes.

---

### Post by Casey R on 2010-10-20
That worked.....is there a newer version of Compiz I can reinstall now?

---

