---
title: "How to delay ASSP until after ClamAV starts?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by cleanden on 2008-12-10
Having installed ASSP, I am now working on running File::Scan::ClamAV.

I seem to have things setup correctly, but after a reboot ASSP warns:
Cannot connect to 'localhost:3310': IO::Socket::INET: connect: Connection refused

but if I restart ASSP with:
sudo /etc/init.d/assp restart
the error goes away.

Is there a way I can force ASSP to wait some period of time to make sure clamav/clamd is running before it starts on boot?

Thanks,
Alex

---

### Post by nhasian on 2008-12-10
yes you can use the *sleep* command like

```
sleep 10 && sudo /etc/init.d/assp restart
```

that will have it wait ten seconds before proceeding

---

### Post by cleanden on 2008-12-10
That sounds perfect.
Is there a file I should add that command to that will execute on startup?

---

### Post by cleanden on 2008-12-10
/etc/rc.local did the trick.
Thanks!

---

### Post by Dr Small on 2008-12-10
Basically, all you should have to do is change the startup order.

---

### Post by cleanden on 2008-12-10
This would be good to know how to do.
Can you point me at where to look at that?
I searched and found mention of System, Preferences, Sessions, Startup Programs but my ASSP service isn't listed there

---

