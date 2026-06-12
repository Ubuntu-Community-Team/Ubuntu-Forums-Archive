---
title: "authenticate window is freezing.anyway to fix?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by human75 on 2010-10-11
hi there.
i just installed final release of ubuntu 10.10 but i am having weird issue.when i try to install any application from ubuntu software center,authenticate windows appears and i am punching my password.After i punched my password authenticate window stops working and i cant install any software.is there anyway to fix this?thanks in advance.

---

### Post by sikander3786 on 2010-10-11
Can you please start Software Center from the terminal and post the output when it freezes. We might see some informative errors.

```
software-center
```

---

### Post by human75 on 2010-10-11
> **sikander3786 said:**
> Can you please start Software Center from the terminal and post the output when it freezes. We might see some informative errors.

```
software-center
```
  i figured that out it does not freezee.when i click x than installation continue without problem.this is weird?! :)..here is the result of terminal
------------------------------
daanyaal@ubuntu:~$ software-center
2010-10-11 09:35:14,241 - softwarecenter.app - INFO - software-center-agent finished with status 1
2010-10-11 09:35:17,084 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.6/dbus/proxies.py', 400, '_introspect_error_handler')'
2010-10-11 09:35:17,084 - dbus.proxies - ERROR - Introspect error on :1.50:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.127" (uid=1000 pid=8692 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.50" (uid=0 pid=1598 comm="/usr/bin/python))
------------------------------

---

### Post by sikander3786 on 2010-10-11
> when i click x than installation continue without problem.this is weird?!

I couldn't actually understand that statement. I am not using Maverick at the moment. What do you mean by 'x'?

---

### Post by human75 on 2010-10-11
> **sikander3786 said:**
> I couldn't actually understand that statement. I am not using Maverick at the moment. What do you mean by 'x'?
i attached screenshot i hope it would help.thanks in advance

---

### Post by alossix on 2010-10-11
Same issue here.  Using the Ubuntu Software Center GUI, the "Authenticate" popup won't close when clicking either "Authenticate" or "Cancel" after entering root password.  Clicking the window-bar X does remove the popup and installation continues.  A minor annoyance, but nothing too bad.

---

### Post by SerafeimG on 2010-10-12
> **alossix said:**
> Same issue here.  Using the Ubuntu Software Center GUI, the "Authenticate" popup won't close when clicking either "Authenticate" or "Cancel" after entering root password.  Clicking the window-bar X does remove the popup and installation continues.  A minor annoyance, but nothing too bad.

Same problem here after upgrading to 10.10.
I don't thing it's a minor annoyance...
I can't install and unistall software through Software Center...
It freezes...

---

### Post by jasontan6 on 2010-10-13
Confirmed... closing the Authenticate window by clicking it's X button makes Software Center to get on to installing.

Using 10.10 maverick btw

---

### Post by jasontan6 on 2010-10-13
this has already been reported: 

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/649939](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/649939)

---

### Post by zahid cheema on 2012-08-10
my problem is still unsolved and it is giving the repair error.

---

### Post by wildmanne39 on 2012-08-11
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

