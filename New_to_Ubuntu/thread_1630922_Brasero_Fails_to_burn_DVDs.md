---
title: "Brasero Fails to burn DVDs"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by Vaxon on 2010-11-25
Hello I am currently running kubuntu 10.10
I attempted to burn a dvd in brasero and here is the output
```
brasero

** (brasero:24124): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory


(brasero:24124): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(brasero:24124): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(brasero:24124): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (brasero:24124): WARNING **: Failed to inhibit the system from suspending: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Segmentation fault

```

---

### Post by bodhi.zazen on 2010-11-25
Not sure about that one.

Personally I advise an alternate tool, k3b comes to mind ...

I would also suggest you file a bug report on launchpad.

---

### Post by Vaxon on 2010-11-25
Thanks for the quick reply
and I am a user of k3b
But it doesn't have a function for burning dvds
and I'm unsure as how to submit a bug report
well a proper one

---

### Post by bodhi.zazen on 2010-11-26
k3b will burn DVD. What problem are you having with that ?

Screenshot:

[img]http://k3b.plainblack.com/uploads/hh/Ia/hhIaQQcwzlzPkOEbV6zSiQ/datadvd.png[/img]

---

### Post by meadhikari on 2010-11-26
After Brasero Failed in my 10.10 I started using Nero(is it just unethical?). and it works fine.

---

### Post by Vaxon on 2010-11-26
I mean burning a video with k3b
like a standard avi mp4 or flv format video
and then being about to play them on a dvd players
or a gaming system

---

### Post by mehturt on 2010-12-30
I have the same problem, is there a bug filed for this?
edit: found one, [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/646902](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/646902)

---

