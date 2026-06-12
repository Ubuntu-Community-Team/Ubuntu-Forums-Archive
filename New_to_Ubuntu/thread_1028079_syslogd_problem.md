---
title: "syslogd problem"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by petekane on 2009-01-02
Running system log, I find that for several days 'syslogd' has been restarting at 08:31:05.

Any ideas what is causing this to happen, as it has not always been this way.

[IMG]http://petekane.myby.co.uk/htdocs/screenshot.png[/IMG]

Regards

Peter J. Kane

---

### Post by hyper_ch on 2009-01-02
could it be because it's rotating the logs?

---

### Post by petekane on 2009-01-02
Yes - that makes sense, but why was it not happening before.  Could it be that an update initially had it setup wrong, then put it right!

And is it possible to define when the rotation happens?

Thanks in advance...

---

### Post by hyper_ch on 2009-01-02
not sure... it's just a guess... every day at the same time... but you're rigth, it won't explain why it didn't do that before... I should check my syslogs to see if it gets restarted also.

---

### Post by petekane on 2009-01-02
Yes - I agree - will check cron.daily logrotate file, see if it provides info on time.

---

### Post by petekane on 2009-01-02
Just waiting for the time when it restarted yesterday, to se what happens.  I did notice that yesterday it terminated cron.daily, when it restrarted - um!!

---

