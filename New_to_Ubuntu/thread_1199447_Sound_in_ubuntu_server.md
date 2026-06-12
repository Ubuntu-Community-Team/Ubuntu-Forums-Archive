---
title: "Sound in ubuntu server"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by jdarias on 2009-06-28
How do i enable sound in ubuntu server?
Currently, all applications (mocp, aumix, orpheus) that use sound have to be run as sudo to work.
I´ve tried installing alsa-base, alsa-utils with no luck.

---

### Post by RedSquirrel on 2009-06-29
Is your user in the **audio** group?

You can run the command (in a terminal):

```
groups
```and it will list the groups to which your user belongs.

If you are not in the **audio** group, you can run

```
sudo adduser username audio
```and then logout and log back in again. You should now be in the audio group.

---

### Post by jdarias on 2009-06-29
Whoa! thanks! Had a bit of trouble but i relogged in, and it works now! :)

---

