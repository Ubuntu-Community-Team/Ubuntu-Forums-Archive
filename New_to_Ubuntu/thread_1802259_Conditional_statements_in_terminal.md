---
title: "Conditional statements in terminal?"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2011-07-11
Hi, I'm not sure if anything like this is possible, but I'd like to make some sort of reminder for myself. I would like a command that at a certain time (10PM-est), a dialogue box or something of that sort will pop up and remind me to do what I have to do. Basically in English, "At 10pm, display 'text here'"  In windows, I think it was the "echo" command that did something along these lines, so how would I do this in Ubuntu?

It would be really helpful if I could get the webpage to automatically open up at that time too. Is that possible?

---

### Post by GWBouge on 2011-07-11
Check out cron, or for a gui solution, the package gnome-schedule.

For the pop-up dialog, you could set a cron task to use zenity:
```
DISPLAY=:0.0 zenity --info --text="Do something"
```

... or could use the notification bubbles:
```
DISPLAY=:0.0 notify-send "Do something"
```

... and you could use it to open up a web page:
```
DISPLAY=:0.0 firefox http://www.thewebpage.com
```

If you use Evolution, it can also manage tasks and reminders, but I don't use it for that, so I can't describe how or how well it works, lol.

---

