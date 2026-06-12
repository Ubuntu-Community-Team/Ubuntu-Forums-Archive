---
title: "gksudo nautilus no longer works?"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by mapes12 on 2009-07-22
Hi

I've done something (but don't know what?) which has meant that I can no longer launch nautilus with root privaliges. Here's the Terminal output
> mark@ubuntu-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
(nautilus:6154): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6154): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:6154): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6154): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
mark@ubuntu-desktop:~$ 
Any ideas how I can fix this please?

I have tried reinstalling Nautilus in Synaptic but I still get the same result.

Mark

---

### Post by dk06 on 2009-07-22
[http://ubuntuforums.org/showthread.php?t=691939](http://ubuntuforums.org/showthread.php?t=691939)

[http://ubuntuforums.org/showthread.php?t=927195](http://ubuntuforums.org/showthread.php?t=927195)

After you reinstalled, did you log-out & log back in?


> 
sudo apt-get install nautilus -y


---

### Post by fooman on 2009-07-22
do you by any chance have a cd/blank cd in your drive?  ...if so remove it and try again.

---

### Post by mapes12 on 2009-07-22
> **fooman said:**
> do you by any chance have a cd/blank cd in your drive?  ...if so remove it and try again.
fooman, you are a wizard! Problem solved. Thanks guys:D

---

