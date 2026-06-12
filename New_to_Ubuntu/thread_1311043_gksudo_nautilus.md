---
title: "gksudo nautilus"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by batat on 2009-11-02
I got following warnings. Is it normal?

```
gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:8105): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:8105): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:8105): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' vrátil chybu 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (process:8137): WARNING **: Couldn't change nice value of process.

(totem-video-thumbnailer:8137): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(totem-video-thumbnailer:8137): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(totem-video-thumbnailer:8137): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(totem-video-thumbnailer:8137): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(totem-video-thumbnailer:8137): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (process:8148): WARNING **: Couldn't change nice value of process.

** (nautilus:8105): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files

--- Hash table keys for warning below:
--> root
--> inode/directory
--> REMOVED_PRIVACY
--> l2049
Shutting down nautilus-gdu extension

(nautilus:8105): Eel-WARNING **: "unique eel_ref_str" hash table still has 4 elements at quit time (keys above)

(nautilus:8105): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 6 elements at quit time
totem-video-thumbnailer couldn't process file: 'REMOVED_PRIVACY.flv'
Reason: Took too much time to process.
```

---

### Post by winotree on 2009-11-02
To answer your question yes it's normal if or when you use the wrong code -- unless I'm mistaken you really need to use ```
gksu nautilus
``` or *gksu* for any gui application.  Why not try that and see how it works.  :)

---

### Post by alphaniner on 2009-11-02
**gksudo** *is* **gksu**:

```
$ file /usr/bin/gksudo 
/usr/bin/gksudo: symbolic link to `gksu'
$ man gksudo

GKSU(1)                          User Commands                         GKSU(1)

NAME
       gksu - GTK+ frontend for su and sudo

$
```

Though technically, **gksudo** is the command you are supposed to use in this case.

And it's not uncommon to see error messages when launching GUI apps from the terminal.  Unless the app misbehaves, you can usually ignore them.

---

### Post by Xomm on 2009-11-02
As stated above, you usually get error messages like that when starting some GUI apps with terminal.

Just keep an eye out for serious looking errors, to be safe.

---

### Post by winotree on 2009-11-02
I only know that when I switched from gksudo to gksu any issues I'd been having stopped  -- and because they'd stopped I hadn't reverted to double-check that behavior.  :|  ;)

EDIT - this is what I'd read previously

   
    [I]....gksu is a frontend to su and gksudo is a frontend to sudo. Their  primary purpose is to run graphical commands that need root without the  need to run an X terminal emulator and using su directly.... 
[/I]


More here [http://linux.die.net/man/1/gksudo](http://linux.die.net/man/1/gksudo) 

As I'd stopped using sudo in favor of su quite some time ago I can now see how I made the statement I did.

---

### Post by batat on 2009-11-03
gksudo is softlink to gksu.
 I did not found yet why SOMETIMES I get CRITICAL error, despite doing same think (at least hope so).
 Is there way how I can help to remove those?

P.S.: This forum sucks. I am getting "The message you have entered is too short. Please lengthen your message to at least 1 characters." Why is it using yahooapis.com javascripts?

---

### Post by MrWES on 2009-11-03
> **batat said:**
> gksudo is softlink to gksu.
 I did not found yet why SOMETIMES I get CRITICAL error, despite doing same think (at least hope so).
 Is there way how I can help to remove those?

P.S.: This forum sucks. I am getting "The message you have entered is too short. Please lengthen your message to at least 1 characters." Why is it using yahooapis.com javascripts?

You will get that error when you are typing your response in the >  area, so techincally you have responsed with any text. Just make sure your response starts AFTER THE  tag.

~Bill

P.S. Also, since you received several responses very quickly to your problem; I don't understand how you can, after two posts, say this forum sucks.

---

### Post by batat on 2009-11-03
To clarify things: I did not wanted to offend anybody. When I said forum, I ment software, NOT community. Community is great. &#9829; Accept my humbly apologies.

---

### Post by sisco311 on 2009-11-03
You may find the nautilus-gksu extension handy. It provides a "Open as administrator" right click menu option. 

After installing the package you have to restart nautilus (*killall nautilus*) or log out and log back in.

---

### Post by afrodeity on 2010-04-01
gksudo nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-image-converter extension
Initializing nautilus-dropbox 0.6.2
Initializing nautilus-gdu extension

Then when I try to open a folder, it freezes.

oh dear.

---

