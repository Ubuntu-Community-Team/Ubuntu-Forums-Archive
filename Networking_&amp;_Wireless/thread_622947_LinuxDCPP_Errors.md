---
title: "LinuxDCPP Errors"
date: 2007-11-25
forum: Networking &amp; Wireless
---

### Post by MrSpiffdifilous on 2007-11-25
I recently installed LinuxDCPP because I had the windows version back in college and it was great. It worked fine for about an hour and now all of a sudden I'm getting this error.

> (linuxdcpp:8243): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed

(linuxdcpp:8243): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
 
And it repeats that last error multiple times...like 20-30 times. I'm unable to read the chat window, search,...do anything so I just have to quit. I tried upgrading to 1.0, to no avail. Still the same issue. Is/has anyone having/had this problem? I'd really appreciate some help! Thanks in advance!

---

### Post by stevensheehy on 2007-11-27
> **MrSpiffdifilous said:**
> I recently installed LinuxDCPP because I had the windows version back in college and it was great. It worked fine for about an hour and now all of a sudden I'm getting this error.

 
And it repeats that last error multiple times...like 20-30 times. I'm unable to read the chat window, search,...do anything so I just have to quit. I tried upgrading to 1.0, to no avail. Still the same issue. Is/has anyone having/had this problem? I'd really appreciate some help! Thanks in advance!

That error is normal to see every once in a while. If you see it too often then that means you need to adjust the character encoding of the hub. You can do this globally in the first tab of the preferences or in the favorite hubs on a per hub basis. If you visit mainly western european hubs, then set it to CP1252, etc.

---

