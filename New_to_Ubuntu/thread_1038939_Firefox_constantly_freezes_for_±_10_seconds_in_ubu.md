---
title: "Firefox constantly freezes for ± 10 seconds in ubuntu 8.04. VERY annoying!"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by kramer65 on 2009-01-14
Hello,


Because 8.10 was slowly breaking down I reinstalled 8.04. Although this is going fairly ok again, firefox now became almost unusable.

In normal usage it constantly freezes for 10-20 seconds for no apparent reason. It is not restricted to certain sites but freezes with anything (google, hotmail, any simple text website etc.). It sometimes freezes when opening a new tab but sometimes not. Flash is also a problem since youtube sometimes gives sound, and sometimes not. Since the freezes happen with any website I don't think that should be the problem though.

My pc is fast enough with a Quad core @ 2.66 GHz and 4GB RAM and my internet connection is also quite fast, so that shouldn't be the problem.

Does anybody have any idea how to fix this? I nowadays go that far that I start Win XP in Virtualbox just to surf more easily. And that shouldn't be the solution I think..

---

### Post by stevoo on 2009-01-14
That is definetely not a solution. 

You can install opera until you fix your problems with Firefox.
But if i remember correctly there were issues with Firefox on 8.04.  The same issues you had i was experiencing them as well, until upgrading to 8.10 and all of them went away.

So lets see. 
What version of Firefox are you using ? What version of Flash are you using ?

Try and run firefox from a console and see if any errors occur while doing that.

---

### Post by kramer65 on 2009-01-14
I am running firefox version 3.0.5 and flash version 9.0.152.0.

I just saw by the way, that it does freeze a lot more when I am actually running virtualbox. Since I have to do that a lot these days to work on my thesis as well (I NEED endnote which doesn't work on ubuntu) virtualbox is a lot open anyway.

Coudl it be something in virtualbox as well?

---

### Post by stevoo on 2009-01-14
cant say that it is virrtualbox problem as you do have a lot memory for that to use.

You could use Kile on ubuntu instead of endnote ... i think it is the same

Does it gives any errors when running firefox from terminal ?

---

### Post by kramer65 on 2009-01-15
It doesn't seem to be a virtualbox problem after all..

I ran firefox through the commandline for a while and get many different messages. Many of them are repeated so I will just summarise what I see:

```
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:8020): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8020): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(firefox:8020): Gtk-CRITICAL **: gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

(firefox:8020): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(firefox:8020): Gtk-CRITICAL **: gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(firefox:8020): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

(firefox:27033): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
ALSA lib pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so   (I get many of these)

(firefox:27033): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:27033): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

```

Does that make any sense?

ps. The sounds now also doesn't work in online video's..

---

### Post by delicowa on 2009-01-15
**/usr/lib/alsa-lib/libasound_module_pcm_pulse.so   (I get many of these)

1. for this problem open synaptic and make sure you dont have  broken dependencies

2.you seem to have a lot of GTK_CRITICAL error like i said make sure you dont have broken dependencies and that you gtk librariesare sane, and ok:!

---

### Post by pib712 on 2009-01-15
Flash is definitely a problem in Linux, as are most Adobe products. Try swfdec instead (a Flash alternative designed for Linux).

---

