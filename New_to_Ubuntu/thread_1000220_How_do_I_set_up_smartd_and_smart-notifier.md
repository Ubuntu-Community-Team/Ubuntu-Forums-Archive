---
title: "How do I set up smartd and smart-notifier"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by occams_beard on 2008-12-02
I would like to have smartd (from smartmontools) run at startup. I've installed the package but can't get the daemon to run.

Also, I installed smart-notifier, but it will not run either. When I try to start it from the command line, it just sits there and I have to do a ctrl+c to kill it. After which it reports:
```

Traceback (most recent call last):
  File "/usr/bin/smart-notifier", line 17, in <module>
    smart_notifier.gui.service()
  File "/usr/share/smart-notifier/smart_notifier/gui.py", line 52, in service
    gtk.main()
KeyboardInterrupt

```

Can someone please help?

---

### Post by optim on 2009-01-10
Uncomment the &#8220;#start_smartd=yes&#8221; line by removing the &#8220;#&#8221; in /etc/default/smartmontools.

---

