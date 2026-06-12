---
title: "evince problem"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by beew on 2010-10-01
After some upgrading evince wouldn't open any PDF file. I type "evince" in the terminal and get these error messages

> (evince:23821): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(evince:23821): EvinceDocument-CRITICAL **: ev_document_get_n_pages: assertion `EV_IS_DOCUMENT (document)' failed

(evince:23821): EvinceDocument-CRITICAL **: ev_document_get_n_pages: assertion `EV_IS_DOCUMENT (document)' failed

(evince:23821): EvinceDocument-CRITICAL **: ev_document_get_n_pages: assertion `EV_IS_DOCUMENT (document)' failed

(evince:23821): EvinceDocument-CRITICAL **: ev_document_get_n_pages: assertion `EV_IS_DOCUMENT (document)' failed

(evince:23821): EvinceDocument-CRITICAL **: ev_document_get_n_pages: assertion `EV_IS_DOCUMENT (document)' failed
  
I would greatly appreciate it if someone can tell me what is going on and perhaps offers a solution. Thanks.

---

### Post by beew on 2010-10-01
Here is another relevant piece of information I just discovered. I tried to remove evince from the terminal by typing

> sudo apt-get purge evince

While evince did get purged, these warnings showed up
> Removing evince ...
Purging configuration files for evince ...
Processing triggers for gconf2 ...
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Processing triggers for libglib2.0-0 ...
No schema files found: removed existing output file.



I reinstalled evince but the problem persists.

---

### Post by beew on 2010-10-01
Ok, I think the problem is in an upgrade of libglib2.0-0 from 2.25.24 to 2.26.0. Now removing libglib2.0-0 would remove half the installed programs. I am wondering if there is a less painful way to downgrade it. Thanks.

---

### Post by beew on 2010-10-01
I don't know what happened, but I have solved the problem.

First I downgraded libglib2.0-0 to some earlier version using the following procedure:

In the terminal type

```
apt-cache showpkg libglib2.0-0 
```Then it shows the versions that are available in my repositories.

Then I chose the next lower version and type
 ```
sudo aptitude install libglib2.0-0=version (something like 2.24.1-0ubuntu, depends on what is avaliable)
```Then it downgrades ligglib2.0-0 and a bunch of other things and removed a few packages (most of them seem pretty useless)

Then I reinstalled an earlier version  of evince and it didn't work. When trying to open a pdf document it said pdf type not supported. So I took a risk to upgrade evince again  to the latest version (which gave me the troubles to begin with) by activating the source. libglib.2.0-0 also got upgraded and it installed a few additional packages. This time evince worked beautifully, seems  a lot faster due to the upgrade. :)

 icedtea-pluggin was removed during the downgrading and couldn't be reinstalled after the downgrading due to broken dependencies. But after the second upgrade I could reinstall it without problem.

So it all worked out in the end. :)

---

