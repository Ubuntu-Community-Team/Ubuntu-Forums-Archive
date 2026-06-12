---
title: "No login and only generic desktop on reboot?"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by jjoyce2011 on 2011-08-13
I've been running Ubuntu 10.10 for netbooks on my lenovo thinkpad x100e for months now and it's generally fine, except for the daily crash. This morning I updated the system and was using Chrome when it crashed, which seemed pretty normal.

But when I booted it up, the normal Ubuntu purple desktop appeared with a white box in the middle displaying only the ubuntu logo and my computer name. Typically, it allows me to login at this point, but no dice. In the lower right, there's a power button that gives me a choice between restart and shut down. Neither work.

There's also a button for universal access control, which is meaningless. I can't do anything else.

I can get to the command line, but have no idea what to do from there. Advice?

---

### Post by LowSky on 2011-08-14
Welcome to the forums.

You shouldn't be crashing at all. If you are it can cause hard drive failures and may be the cause of the current issue.

More than likely you need to resume the install of the latest updates.

From the command line

```
sudo apt-get upgrade
```

hopefully that works

---

### Post by jjoyce2011 on 2011-08-20
Thanks a million. That's apparently what it was.

Generally, the machine crashes while using Chrome, often in conjunction with Flash or something. That seems to be a consistent issue and you're probably right about hard drive issues.

Any easy ways to remedy that?

---

