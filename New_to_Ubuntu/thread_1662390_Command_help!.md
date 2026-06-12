---
title: "Command help!"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by alexwang32 on 2011-01-08
Hi!

I'm new to ubuntu and I need some help with a perhaps simple situation.

There this show that I enjoy listening, so I download the podcast everyday. I use the command "wget" for downloading, and it's pretty good. Since the only part of the link that changes is the date part, I want to change the date part into a variable so that I don't have to change it myself daily.

Example : wget [http://www.example2011/01/08.mp3](http://www.example2011/01/08.mp3) (what I want to change is the '08')

Thanks!!!

---

### Post by TiBaal89 on 2011-01-08
Check out the 'date' command - you can specify the format and have it return only the day, month, or year individually.  For example:

```
$ date +"%d"
08
```

This could be used to construct your wget command.

---

### Post by DavidG24 on 2011-01-08
Not that it solves your problem, but in case you didn't know about it gPodder is a great application for managing podcasts.

---

### Post by alexwang32 on 2011-01-08
Thanks for the info, but how do I 'construct it'.

Like this? 

wget http://smart2011/01/"date =%d".com/

Didn't work!

---

### Post by thameera on 2011-01-08
Use this:
wget http://example2011/01/$(date +"%d").com/

---

