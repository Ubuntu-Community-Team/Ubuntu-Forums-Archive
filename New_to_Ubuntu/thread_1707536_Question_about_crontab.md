---
title: "Question about crontab"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by sleepy-time-demon on 2011-03-15
I'm just trying to figure one thing about about crontab, I know to enable it it's crontab -e, then it asks for the editor of choice (nano, love my nano)

But at that point do I put the command in? When it opens nano, do I put the command in then? or do I put a link to an .sh script in there?

---

### Post by wojox on 2011-03-15
> **sleepy-time-demon said:**
> I'm just trying to figure one thing about about crontab, I know to enable it it's crontab -e, then it asks for the editor of choice (nano, love my nano)

But at that point do I put the command in? When it opens nano, do I put the command in then? or do I put a link to an .sh script in there?

You set it with something like this:

```
01 04 * * * /somedirectory/somecommand
```

[CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

### Post by sleepy-time-demon on 2011-03-15
Sorry, it doesn't appear like I'm making sense. I do know the syntax I need, but after doing 'sudo crontab -e' I get asked for a text editor and I choose nano. Nano opens, now in that open nano, do I put 
 
```
0 0 * * 0 cp /copy/directory/here -r /paste/directory
```

Or do I have to write the script, and crontab gets the link to the script?

---

### Post by wojox on 2011-03-15
> **sleepy-time-demon said:**
> Sorry, it doesn't appear like I'm making sense. I do know the syntax I need, but after doing 'sudo crontab -e' I get asked for a text editor and I choose nano. Nano opens, now in that open nano, do I put 
 
```
0 0 * * 0 cp /copy/directory/here -r /paste/directory
```

Or do I have to write the script, and crontab gets the link to the script?

Typically I have a /bin directory in /home. I write bash scripts an they reside in there. I then tell crontab to execute that script at a specific time and point it to /home/wojox/bin/. This will back up at 11am and 4pm everyday

```
00 11,16 * * * /home/wojox/bin/backUp
```

---

### Post by sleepy-time-demon on 2011-03-15
Alright, thank you. That helps a lot.

---

