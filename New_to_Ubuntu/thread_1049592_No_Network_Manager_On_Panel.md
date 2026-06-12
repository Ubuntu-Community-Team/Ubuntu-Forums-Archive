---
title: "No Network Manager On Panel"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by rednano12 on 2009-01-24
I accidentally deleted the NM applet from my panel and cannot find how to get it back. I am running 8.10. If I go into terminal and type nm-applet (with --sm-disable or not) I get this error:

WARNING **: <WARN> applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.
Return: 3

(nm-applet:6659): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

Help?

---

### Post by Periswell on 2009-01-24
try in the terminal

> nm-applet

-joshua

---

### Post by theinnercityhippy on 2009-01-24
does this still happen after a restart?

if not try finding out the process id of the nm-applet by typing the following into a terminal

```
ps -aef | grep nm-applet
```

The first of the two numbers will be the PID of nm-applet. next we need to stop that process by typing 

```
kill [number you got from the last command]
```

Then finally restart the serveive with the command you tried before

```
nm-applet
```

probably bes you do this by pressing alt+F2 as it won't leave an open terminal window.

Hope this helps :-)

(ps to find the full listing of what ps can do, type ps --help)

-JimDog*-

---

### Post by rednano12 on 2009-01-24
@Joshua: Please read the first post!

@Hippy: Thank you for the in-depth suggestion. Here are the results:
I did exactly as you said (in the terminal). At the end I got a empty terminal and nothing else. I just need that icon back in my panel! Any other ideas?

EDIT: *facedesk* I should have googled first. NM is built into Notification manager.

---

### Post by freelook on 2009-01-24
> **rednano12 said:**
> EDIT: *facedesk* I should have googled first. NM is built into Notification manager.

I'm having the same problem and I don't understand your statement.  Any steps I can take to get the applet to show up?

---

### Post by james.gardner0 on 2009-01-25
I would also love an answer to this question.

Thanks

-EDIT-

this worked for me:
right click on panel
click add to panel
add the "Notification Area" option

---

### Post by killerdogg77 on 2009-01-25
try right clicking on panel,add to panel then  add notifiction area

---

### Post by Cannaregio on 2009-01-27
Here is what I did solving my problem on a netbook:

1) make sure to [COLOR="#0000ff"]have a notification area[/COLOR] on the panel 
(rightclick on panel ==> add to panel ==> notification area)
2) go to services (system ==> administration ==> services)
3) [COLOR="Blue"]enable _and start_ Network manager[/COLOR]
4) reboot to check

That's it (I hope for you :-)

Cheers!

---

