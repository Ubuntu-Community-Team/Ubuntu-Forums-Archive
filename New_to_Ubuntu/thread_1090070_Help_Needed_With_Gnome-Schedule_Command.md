---
title: "Help Needed With Gnome-Schedule Command"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Viverrid on 2009-03-07
Hi,

I am trying to get gnome-schedule to run the following command every hour:

```
/home/mike/rss2email/r2e run
```

The following error is returned when I click the "Run Task" button to test it:

```
python: can't open file 'rss2email.py': [Errno 2] No such file or directory
Press ENTER to continue and close this window.
```

The script works as expected when run from the terminal. Any help would be most appreciated. Thanks in advance.

---

### Post by sdennie on 2009-03-08
What happens if you instead have it run:

```

cd /home/mike/rss2email ; ./r2e run

```

---

### Post by Viverrid on 2009-03-08
> **sdennie said:**
> What happens if you instead have it run:

```

cd /home/mike/rss2email ; ./r2e run

```

That worked! Thank you so much. Is there a tutorial you would recommend to read that covers this?

---

