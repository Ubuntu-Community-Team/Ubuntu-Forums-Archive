---
title: "Appointments in terminal"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-03-11
is there any way i can view my evolution appointments through the terminal? 
i am writing a welcome script and want it to show my appointments for the day. any and all help is appreciated. thanks in advance!

---

### Post by ibuclaw on 2009-03-11
I'm not sure how to go about doing this. I am not an evolution user myself.

But I would presume that the data you want is in a file somewhere inside the ~/.evolution directory. All it takes it just a matter of finding it.

[EDIT]

OK, I've just ran a small test, and found that all appointments are stored in here:
```
~/.evolution/calendar/local/system/calendar.ics
```

Now all you need to do is figure out how to parse it. Which won't be pretty using conventional tools...
Infact, I would recommend that you use a high-level text processing language to carry out the job (*hint* Perl *hint*).

But, to make the job simpler, all appointments appear to begin, and end with
```

BEGIN:VEVENT
...

...
END:VEVENT

```

Regards
Iain

---

