---
title: "Autsch...can't install anymore"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by longtom on 2009-02-03
Have the following error message once I installed all updates.  Anybody seen that before?:

"An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Opening /etc/apt/sources.list - ifstream::ifstream (13 Permission denied), E:The list of sources could not be read.'"

Error message from update manager.

Greetings

longtom

---

### Post by albinootje on 2009-02-03
> **longtom said:**
>  'E:Opening /etc/apt/sources.list - ifstream::ifstream (13 Permission denied), E:The list of sources could not be read.'"


Please do the following :
```

sudo chmod 644 /etc/apt/sources.list
sudo chown 0:0 /etc/apt/sources.list

```
and try again. Let us know if that doesn't fix the problem.

---

### Post by longtom on 2009-02-03
worked like a charme...  Thank you very much.

Any chance you can try to explain, what I did?;)

Greetings

longtom

---

### Post by albinootje on 2009-02-03
> **longtom said:**
> worked like a charme...  Thank you very much.

Good! :)
> 
Any chance you can try to explain, what I did?;)

The two commands changed the file into a read/writable state for user root (sysadmin), and made the owner and group of that file root (sysadmin).

In case you're asking what went wrong before that, I have no idea, perhaps you've changed some permissions yourself ?

Here's some more to read, in case you haven't read this already :
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by longtom on 2009-02-03
> **albinootje said:**
> Good! :)

In case you're asking what went wrong before that, I have no idea, perhaps you've changed some permissions yourself ?


Well - who knows....if I just would know how to do that.  Could I have done that by accident? *headscratch

Just scaned those links you gave.  I have done nothing of that sort - well - not knowingly anyway.

Thanks again

longtom

---

