---
title: "Pino Broken"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by 416inversed on 2010-03-26
I updated Pino today & now it no longer works.

Running it in terminal kicks back```

~$ pino

** (pino:4705): CRITICAL **: file default/src/re_tweet.c: line 511: uncaught error: enchant error for language: en_US.UTF-8 (gtkspell-error-quark, 0)

(pino:4705): GLib-GObject-CRITICAL **: g_object_ref_sink: assertion `G_IS_OBJECT (object)' failed

(pino:4705): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pino:4705): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (pino:4705): WARNING **: rest_api_abstract.vala:185: 0
Segmentation fault

```

Is this a bug or is it something on my end?

---

### Post by wojox on 2010-03-26
Pino is still in development stage. You're using the launchpad ppa's? Probably something at their end.

---

### Post by 416inversed on 2010-03-26
On the advice of Troorl @ Pino, I solved this by installing aspell dictionaries.

In terminal:
```
sudo apt-get install aspell
```

---

