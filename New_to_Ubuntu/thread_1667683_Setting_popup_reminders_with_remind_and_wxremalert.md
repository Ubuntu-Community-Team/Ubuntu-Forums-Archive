---
title: "Setting popup reminders with remind and wxremalert"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-01-15
Hi All,

Maybe someone can clarify this for me. ( I hope anyway)
I've read many web pages on how to write reminders using remind and the addon wxremalert but don't find an answer to my question.

I need to do something on Monday, but I want a popup to remind me every so often (say once an hour) for a few days before Monday and then not remind me after Monday.

The problem I'm having is getting the once an hour popup to work. Both popups work if I type rem into the terminal.  I've checked and remind is running in daemon mode.

I've tried

```
REM 15 Jan 2011 UNTIL Jan 18 2011 *1 RUN wxremalert -d1 % TEST% %
```

and

```
REM 15 January 2011 *1 UNTIL 18 January 2011 AT 12:00 +4320 *1 RUN wxremalert -d1 % TEST2 %
```

The +4320 is supposed to be the number of minutes 3 days before noon on Jan 18 and the *1 is supposed to trigger a popup once a minute.

Does anyone have experience with this?  I'd really appreciate any help.

I got an answer from the guys at [www.roaringpenguin.com:](www.roaringpenguin.com:)

[I]Remind won't let a reminder cross a day boundary, so +4320 won't work.

You have to do it in two steps (the THROUGH keyword is new in 3.1.10;
you can use "UNTIL ... *1" instead if you are running an older version
of Remind):
[/I]
```
# Run once a minute, all day, 15-17 Jan
REM 15 Jan 2011 THROUGH 17 Jan 2011 AT 23:59 +1439 *1 RUN ...

# Run once a minute until noon, 18 Jan
REM 18 Jan 2011 AT 12:00 + 720 *1 RUN ...
```

---

