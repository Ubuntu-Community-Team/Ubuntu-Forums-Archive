---
title: "Nautilus crashed"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by nemodot on 2009-11-06
Hi, thank you all for answering last time.

I have a new problem. This happens everytime I start the computer.
My desktop looks like one from Win98:
[http://i.imgur.com/eFfgw.png](http://i.imgur.com/eFfgw.png)

And i get this when I type "nautilus" in the Terminal:

```
esteban@esteban-desktop:~$ sudo nautilus
[sudo] password for esteban:

(nautilus:2535): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:2535): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2535): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2535): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** Message: Initializing gksu extension...
Nautilus-Share-Message: Called "net usershare info" but it failed: La «red compartida» devolvió el error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No existe el fichero ó directorio
Please ask your system administrator to enable user sharing. 
```

What can I do to fix this?

---

### Post by spyrosebastos on 2010-03-05
Old, but bump.

Same error here:


[B]spyrosebastos@spyrosebastos-linux:~$ sudo nautilus
[sudo] password for spyrosebastos: 

(nautilus:2535): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
** Message: Initializing gksu extension...
Initializing nautilus-gdu extension

** (nautilus:2535): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2535): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2535): WARNING **: No marshaller for signature of signal 'ShareCreateError'[/B]


(Except the last error msg you get).  When I Google this Ubuntu error, the only two responses from Google are the two threads you've started regarding this subject; [one in English, one in Español].  In my position Nautilus still opens, however I've had these errors come up every time it starts since I upgraded to Karmic.

---

### Post by marshmallow1304 on 2010-03-06
Those are all just warnings.  Does anything not work?

---

