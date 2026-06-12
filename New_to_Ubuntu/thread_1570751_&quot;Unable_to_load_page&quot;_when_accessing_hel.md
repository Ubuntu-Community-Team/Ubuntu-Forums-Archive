---
title: "&quot;Unable to load page&quot; when accessing help"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by horseatingweeds on 2010-09-08
Ubuntu 10.04
GNOME 2.30.0

I can only access the home page under Help. The other links give me a "Unable to load page - The requested URI "ghelp:internet#connecting" is invalid" error. 

I checked under Ubuntu Software Center, and I have Help installed. Any ideas why this would occur?

I also tried opening it through the terminal using "yelp" and got this:

```
(yelp:3490): Gtk-CRITICAL **: gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(yelp:3490): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(yelp:3490): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(yelp:3490): Gtk-CRITICAL **: gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

(yelp:3490): Gtk-CRITICAL **: gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(yelp:3490): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(yelp:3490): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(yelp:3490): Gtk-CRITICAL **: gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed
```

---

### Post by horseatingweeds on 2010-09-09
ideas?

---

