---
title: "&quot;bug in some application using the D-Bus library&quot;"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-11-27
I've just updated to 9.10. I chose to watch the procedure in the terminal.

Something odd was that I got a particular error message come up numerous times. It didn't stall the upgrade, but there seemed to be no logic behind what types of package threw up the error and which didn't.

The error message read:
```
process 18451: arguments to dbus-move-error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 278.
This is normally a bug in some application using the D-Bus library.
```

Does anyone know what this means in plain English?

What is the D-Bus library?

Which applications use the D-Bus library?

Do I need to do anything to rectify whatever errors there were?

---

### Post by Roger Allott on 2009-11-30
bump

This query is still outstanding, and it's still confusing me. All I can get from google searches etc. is that D-Bus is some sort of internet messaging protocol, or something.

If anyone can shed any more light, I'd be very grateful.

---

### Post by winstonkirk on 2009-12-13
I don't know what it means yet but I have the same exact problem, but with process 17473. I'll try to figure it out but it's highly unlikely I'll be able to on my own (my first upgrade, learning the systems, etc).

The error stopped my upgrade and I didn't want to screw around with it so I grabbed my old comp and jumped on here. Can I just force through somehow and get back on?

---

