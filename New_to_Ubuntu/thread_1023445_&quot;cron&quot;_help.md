---
title: "&quot;cron&quot; help"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by marcusesses on 2008-12-27
I'm having some trouble scheduling something using crontab.

Here's what I've tried so far:

```
crontab -e
```

(then scheduling)

```
* * * * * firefox
```

(it gives me some messages)

```
crontab: installing new crontab
```

(and when I run it again):
```

No modification made

```

I've run this for all users and for me specifically, via 

```
 crontab -u username -e 
```

It shows up when I do crontab -l, but my changes don't show up in /etc/crontab (though these may be two separate entities, I'm not sure...)

Any help would be appreciated. And if you need more information, let me know. Thanks.

UPDATE: So I ran a little test program like thus

```
 crontab -e
 * * * * * test >> file

```

where test just spits "hello" into a file. 

But the real job I want is to start firefox at those specified times...is this possible? It doesn't seem to work...

---

### Post by hyper_ch on 2008-12-28
I don't like to edit the crontab directly. Instead I prefer editing a text file and edit that to cron.
And then I don't think you can run gui programs on cron.

---

### Post by easybake on 2008-12-28
You should try using the full path to where firefox is located. 

/usr/bin/firefox

just curious but why would you want to launch firefox every minute?

---

### Post by marcusesses on 2008-12-28
> just curious but why would you want to launch firefox every minute?

I was just making sure it worked...my end goal is to launch the a streaming radio station in the browser at a certain time in the dat (say 07:00)...which would then serve as an alarm clock for me. I just launched it every minute here b/c it was easy to test.

I solved my problem though...I did call directly from the path (/usr/bin/firefox), but it didn't matter either way...what solved my problem was this

```
export DISPLAY=:0

```

I'm not really sure what's going on there (I'll look it up tomorrow). 

And I did directly edit the crontab...Any thoughts?

---

