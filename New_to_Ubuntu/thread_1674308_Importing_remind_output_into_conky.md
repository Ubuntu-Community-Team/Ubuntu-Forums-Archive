---
title: "Importing remind output into conky"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-01-23
Hi All,

I see that the conkyrc thread is locked so I'll post this here.

I use remind to keep track of reminders.  It works great in the terminal and pipes into gmessage to send popup reminders of important things.

Without being too verbose, does anyone know how I can take one reminder and get it into conky?  I have a calendar and I want to put how many days until an event below the calendar.

I've tried several scripts but each seems to begin counting down faster and faster as time goes on so I want to use the output from remind, as that seems to be the most stable.

---

### Post by cariboo on 2011-01-24
Just to let you know, the Cafe will be opened back up after the new hardware arrives and is setup up.

---

### Post by GrouchyGaijin on 2011-01-24
Solved

```
${font ubuntu}${execpi 60 remind /path/to/the/.file-with-the-reminder-you-want-to-display | sed -e '1d'}${font}
```

---

