---
title: "Which filters does ubuntu add to Firefox's about:config?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by sonickydon on 2009-11-09
Hello, excuse me if i'm posting to the wrong thread but i just discovered the "distribution.canonical.bookmarksProcessed" filter in about:config and I can't find any information on it from google or mozillazine. The filter name sounds like a privacy threat, does anyone know what it is about?

---

### Post by sonickydon on 2009-11-11
Does anyone know something about it?

---

### Post by SoFl W on 2011-08-05
I will bump this because I am searching for an answer.  This thread is a few years old, but this about:config item could have survived through all the upgrades.

---

### Post by Gryllida on 2011-08-06
Hi!

I found that the extension is installed with "xul-ext-ubufox" package. Its description and source may be found here:

[http://packages.ubuntu.com/natty/xul-ext-ubufox](http://packages.ubuntu.com/natty/xul-ext-ubufox)

1) The function is described as:

--------------------
Integrates the browser with Ubuntu to:

 * Enable searching for missing plugins from Ubuntu software catalog
 * Add the following options to the Help menu
   - Get help on-line
   - Help translating Firefox
   - Ubuntu Release Notes
 * Set homepage to Ubuntu Start Page
 * Display a restart notification after upgrading Firefox
 * Add ask.com to the search engines.
--------------------

2) The list of modified preferences can be found in this directory on your own system:

**/usr/share/mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/ubufox@ubuntu.com/defaults/preferences**

3) If you prefer to use a pristine Firefox install, you can disable the extension; alternatively this line would remove the extension from the system:

**$ sudo apt-get remove xul-ext-ubufox**

4) If this resolves the issue, please mark the thread as "solved".


Enjoy!

Gryllida.

---

